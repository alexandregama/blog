---
title: "CDI in Java - Part 1 - Creating a Factory with @Produces Annotation"
date: 2020-05-27T20:00:47+06:00
draft: false

# post thumb
image: "images/post/java/cdi-series/cdi-in-java-series-part-1-creating-a-factory-using-produces-annotation.png"

# meta description
description: "In this post, we're going to take a look at the amazing @Produces annotation, which is probably one of the most important and used annotations in the CDI world in Java!"

# taxonomies
categories: 
  - "Java"
tags:
  - "CDI Series"
  - "Beginners Tutorial"

# post type
type: "post"
---

Hey friend!

This is **Part 1** of the [CDI Series in Java](https://www.alexgama.io/tags/cdi-series/) that contains:

- Part 1: Factory in CDI with the @Produces annotation
- [Part 2](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-2-qualifiers): CDI Qualifiers
- [Part 3](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-3-events-and-observers): Events and Observers in CDI
- [Part 4](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-4-lazy-initialization): CDI and Lazy Initialization
- [Part 5](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-5-interceptors): Interceptors in CDI
- [Part 6](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-6-dependency-injection-alternatives): CDI Dependency Injection and Alternatives
- [Part 7](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-7-decorators): Working with CDI Decorators

In this post, we're going to take a look at the amazing `@Produces` annotation, which is probably one of the most important and used annotations in the CDI world in Java!

**Setting the expectation**

Before getting started, let's be on the same page. I'm not gonna go into so much detail about CDI and Dependency Injection because I'm kind of assuming you already know something about it. Forgive me if I'm wrong. Don't be mad.

This series will be about some specific points on how to use CDI in your code. Let me know if you want more detailed points :)

**Problem contextualization**

It's time to contextualize our challenge! We'd like to create the following steps for our pseudo online store:

- Create a **Checkout** class to... you know... buy something
- **Log** the operations on the console.
- Create a **Logger** class to keep this log on its own class. The famous cohesion.
- Customize this **Logger** to receive a **Configuration,** which indicates which **Log Mode** should be used

Pretty simple, isn't? Let's jump crazily into code!

### #1: Creating the Main Class in CDI 2.0

Before creating the main class to execute our CDI code, let's create the important Checkout class:

```java
public class Checkout {
  public void finishCheckout() {
    System.out.println("Finishing Checkout");
  }
}
```

Great!

In this example, we're going to use **CDI 2.0**, which allows us to use CDI in a **standalone fashion**!

Let's bring the CDI power by creating a **CDI Container**, which allows us to instantiate objects

```java
CDI<Object> container = new Weld().initialize()
```

Nice! Below we have a **Checkout** object instance created by CDI:

```java
public class MainApplication {

   public static void main(String[] args) {
      try (CDI<Object> container = new Weld().initialize()) {
          Checkout checkout = container.select(Checkout.class).get();
          checkout.finishCheckout();
      }
   }

}
```

Pretty easy, isn't? Notice the following code:

```java
Checkout checkout = container.select(Checkout.class).get();
```

That code is the same as the following, which is injecting a Checkout object using the remarkable **@Inject** annotation:

```java
@Inject 
private Checkout checkout;
```

Now, it's time to execute our CDI example, to validate our environment!

You will see on your console something like this:

```
INFO: WELD-ENV-002003: 
Weld SE container STATIC_INSTANCE initialized Finishing Checkout
```

Great! Everything is up and running!

### #2: Creating a Specialized Class for Logger

Logging is something important for us. To have a good cohesion, let's create a class that is responsible for logging messages. 

This class will be called **SpecialLogger**, as you can see below:

```java
public class SpecialLogger {

   public void log(String message) {
      System.out.println("LOG: " + message); //ok, not that special 😒
   }

}
```

Perfect! Now we'd like to update the Checkout class to use the newest Logger class:

```java
public class Checkout {

   private SpecialLogger logger;

   public void finishCheckout() {
      logger.log("Finishing Checkout");
   }
}
```

Sounds good, because now the Checkout class doesn't know how a Logger works under the hood, we're just using it!

### #3: Logging Mode to Log Messages Through a Special Configuration

it would be great to have a way to change the mode that the log is printed out. These modes could be the following:

- Debug Mode
- Info Mode
- Error Mode
- Etc.

Our **SpecialLogger** should receive the desired Log Mode and print out the message using it.

It's time to create the Configuration class that will receive the Log mode:

```java
public class LogConfiguration {

   private boolean infoMode;

   private boolean debugMode;

   public LogConfiguration(boolean infoMode, boolean debugMode) {
      this.infoMode = infoMode;
      this.debugMode = debugMode;
   }

   public boolean isInInfoMode() {
      return infoMode;
   }

   public boolean isInDebugMode() {
      return debugMode;
   }
}
```

I know, that's not the best code design, but I just want to keep the example clean and simple.

Let's change the **SpecialLogger** class to be able to Log a message based on the **LogConfiguration**:

```java
public class SpecialLogger {

    @Inject
    private LogConfiguration configuration;

    public SpecialLogger(LogConfiguration configuration) {
        this.configuration = configuration;
    }

    public void log(String message) {
        if (configuration.isInDebugMode()) {
            System.out.println("DEBUG LOG: " + message);
        }
        else if (configuration.isInInfoMode()) {
            System.out.println("DEBUG LOG: " + message);
        } else {
            System.out.println("DEFAULT LOG: " + message);
        }
    }
}
```

As you can see, we're validating whether the log should use the **Debug** or **Info** mode, otherwise, the message must be printed out by using the **Default** mode.

Let's try to run it:

```
WELD-001408: 
Unsatisfied dependencies for type SpecialLogger with qualifiers @Default
 at injection point [BackedAnnotatedField] 
 @Inject 
 private com.hackingcode.cdi.produces.Checkout.logger
```

Yes, an exception will be thrown on our face. And that makes sense. CDI does not know how to inject the **SpecialLogger** object yet.

CDI, behind the scenes, will execute the following steps:

- Hey, I can see that you need a **SpecialLogger** object here. That's ok for me. I'll try to find this class around your classpath
- I've found this **SpecialLogger** class on your classpath
- I'll try to create a new **SpecialLogger** instance for you right now
- Ohhh, **I can't do that**! The **SpecialLogger** receives a LogConfiguration in its constructor. I don't even know what it is and I don't know how to create it!

It's time to teach CDI how to get the job done and create the **LogConfiguration** class!

### #4: Creating a Factory With the @Produces Annotation

It's time to create a Factory to create the **SpecialLogger** based on the **LogConfiguration**:

```java
public class SpecialLoggerFactory {

    public SpecialLogger createLogger() {
        LogConfiguration logInDebugMode = new LogConfiguration(true, false);
        return new SpecialLogger(logInDebugMode);
    }

}
```

It's a pretty simple Factory class. It has the method **createLogger()**, which returns a **LogConfiguration** object.

But CDI **doesn't know** about this class yet or its method! Let's use the annotation `@Produces`.

```java
public class SpecialLoggerFactory {

    @Produces
    public SpecialLogger createLogger() {
        LogConfiguration logInDebugMode = new LogConfiguration(true, false);
        return new SpecialLogger(logInDebugMode);
    }

}
```

> **@Produces** indicates to CDI that the method **createLogger()** should be used when a **LogConfiguration** object is needed

The @Produces annotation will say to CDI:

> Hey CDI, please, use the **createLogger()** method when you need to Inject a **SpecialLogger** object in some place

Of course, the returned object of the method **createLogger()** must be the same type that you're interested in, in this case, the **SpecialLogger**. Generics for an upcoming post 😏.

That's it! I really hope that this article could be helpful to you!

In the [next part](https://www.alexgama.io/cdi-in-java-series-part-2-qualifiers) we're going to be hacking some code with [CDI and Qualifiers](https://www.alexgama.io/cdi-in-java-series-part-2-qualifiers)

See you on [Twitter](https://twitter.com/_alex_gama/) for more updates :)

Let's keep in touch and don't forget to signup for my weekly newsletter 🙂

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)