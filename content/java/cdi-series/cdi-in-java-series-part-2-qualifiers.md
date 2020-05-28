---
title: "CDI in Java - Part 2 - Polymorphism with CDI Qualifiers"
date: 2020-05-28T20:00:47+06:00
draft: false

# post thumb
image: "images/post/java/cdi-series/cdi-in-java-series-part-2-qualifiers.png"

# meta description
description: "In this part, we're going to explore how CDI Qualifier works and how it can help us in Java with Dependency Injection and Polymorphism!"

# taxonomies
categories: 
  - "Java"
tags:
  - "CDI Series"
  - "Beginners Tutorial"

# post type
type: "post"
---

Hello!

This is **Part 2** of the long [CDI Series in Java](https://www.alexgama.io/tags/cdi-series/) that contains:

- [Part 1](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-1-creating-a-factory-using-produces-annotation/): Factory in CDI with the @Produces annotation
- Part 2: Polymorphism with CDI Qualifiers
- [Part 3](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-3-events-and-observers): Events and Observers in CDI
- [Part 4](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-4-lazy-initialization): CDI and Lazy Initialization
- [Part 5](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-5-interceptors): Interceptors in CDI
- [Part 6](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-6-dependency-injection-alternatives): CDI Dependency Injection and Alternatives
- [Part 7](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-7-decorators): Working with CDI Decorators

In this part, we're going to explore how **CDI Qualifier** works and how it can help us in Java with **Dependency Injection and Polymorphism**!

We'll use the scenario from the [previous part](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-1-creating-a-factory-using-produces-annotation/), when we talked about the famous **@Produces** annotation.

Let's remember that scenario and add a few more steps

- **Checkout** class and log on the console when a checkout is finished on our pseudo online store
- **SimpleLogger** class that will have the logic to print out a log message
- **Logger** object choosing the desired Log mode; Debug, Info, or Warn mode

Disclaimer: I'm not focusing on a good code design. I'm just playing around with some code snippets to be easier to understand :)

Are you ready? Let's get into it

## #**1: Using CDI 2.0 in a Standalone Mode**

It's a good time to review the code from the previous part of this series, which runs CDI in a standalone mode. it's nice and easier for our journey

First of all, let's create the **MainApplication** class that will start the **CDI Container**. 

Just a reminder, in the following code we're using CDI 2.0, but **Qualifiers** came out in the version 1.0. Cool

```java
public class MainApplication {
	
  public static void main(String[] args) {
		try (CDI<object> container = new Weld().initialize()) {
			Checkout checkout = container.select(Checkout.class).get();
			
			checkout.finishCheckout();
		}
	}
	
}
```

Of course, this code doesn't compile since we don't have the **Checkout** class yet.

## #**2: Creating the Checkout Class**

Let's create the **Checkout** class, which uses the **SimpleLogger** classes:

```java
public class Checkout {
	
	@Inject
	private SimpleLogger logger;
	
	public void finishCheckout() {
		logger.log("Finishing Checkout"); // our really advanced logger 😅
	}

}
```

That code doesn't compile either. It's time to create the **SimpleLogger** class.

## #**3: Creating the SimpleLogger Class**

This class will just log a message based on a configuration mode.

```java
public class SimpleLogger {
	
	private LogConfiguration configuration;
	
	public SimpleLogger(LogConfiguration configuration) {
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

As you can see, we have the class **LogConfiguration,** which configures the **mode** to be used when printing out a log message.

## #**4: Creating the LogConfiguration class**

This class will contain 3 modes to be passed to the **SimpleLogger** class:

```java
public class LogConfiguration {

    private boolean infoMode;

    private boolean debugMode;

    private boolean warnMode;

    public LogConfiguration(boolean infoMode, boolean debugMode, boolean warnMode) {
      this.infoMode = infoMode;
      this.debugMode = debugMode;
      this.warnMode = warnMode;
    }

    public boolean isInInfoMode() {
      return infoMode;
    }

    public boolean isInDebugMode() {
      return debugMode;
    }

    public boolean isInWarnMode() {
      return warnMode;
    }
}
```

Notice that the **SimpleLogger** class should have a **LogConfiguration** object built.

In this case, we should create a **Factory** to teach CDI how to create a **SimpleLogger** object.

Let's move on and create the factory!

## #**5: Factory With @Produces in CDI**

We're going to use the **@Produces** annotation to create a Factory to build a **SimpleLogger** object.

This object will be built with the boolean **debugMode** as **true** to indicate that a message should be printed out in the **debug** mode.

```java
public class SimpleLoggerFactory {

    @Produces
    public SimpleLogger createLogger() {
      LogConfiguration logInDebugMode = new LogConfiguration(false, true, false); // I know, taking 3 booleans as parameters...🙄

      return new SimpleLogger(logInDebugMode);
    }

}
```

Great! So far we've just taken a quick overview from the [previous post](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-1-creating-a-factory-using-produces-annotation/).

## #**6: More Logger Modes**

As you may notice, so far, we have just **1** mode to work with Logger, the **Debug** mode!

But we'd like to use another Logger mode, for example, **Info mode**. How can we do that?

The first and simplest way to solve this: Create another method in the Factory, which creates a Logger object that uses the **Info mode**

Let's explore this solution!

```java
public class SimpleLoggerFactory {

    @Produces
    public SimpleLogger createDebugLogger() { // yes, I renamed it
      boolean debugMode = true; // just to be clear that the debug mode is on

      LogConfiguration logInDebugMode = new LogConfiguration(false, debugMode, false);

      return new SimpleLogger(logInDebugMode);
    }

    @Produces
    public SimpleLogger createInfoLogger() { //new method here :)
      boolean infoMode = true;

      LogConfiguration logInInfoMode = new LogConfiguration(infoMode, false, false);

      return new SimpleLogger(logInInfoMode);
    }

}
```

Yes, we renamed the previous method just to be clearer that a Debug Logger will be created and, besides that, we've created a new method called **createInfoLogger()**.

Notice that both methods are using the **@Produces** annotation and, yes, CDI allows us to have many methods annotated with **@Produces** annotation in the same class.

Let's run the code?

```
WELD-001409: Ambiguous dependencies for type SimpleLogger with qualifiers @Default
  at injection point [BackedAnnotatedField] @Inject private com.craftcoder.cdi.qualifiers.Checkout.logger
  at com.craftcoder.cdi.qualifiers.Checkout.logger(Checkout.java:0)
  Possible dependencies: 
  - Producer Method [SimpleLogger] with qualifiers [@Any @Default] declared as [[BackedAnnotatedMethod] @Produces public com.hackingcode.cdi.qualifiers.SimpleLoggerFactory.createInfoLogger()],
  - Producer Method [SimpleLogger] with qualifiers [@Any @Default] declared as [[BackedAnnotatedMethod] @Produces public com.hackingcode.cdi.qualifiers.SimpleLoggerFactory.createDebugLogger()]
```

Nice, an exception has thrown on our faces! What happened?

When CDI tries to inject a **SimpleLogger** object based on the Factory:

> CDI doesn't understand and can't choose which method should be used when the SimpleLogger object is needed.

CDI will angrily say:

> Hey, I have 2 methods that create the object that you are interested in. You should teach me which one I should pick up.

And that really makes sense. CDI doesn't have the ability to understand your desire when you're injecting a dependency if you have more than 2 objects to be returned.

Let's teach CDI how to pick up the desired Logger to be injected.

## #**7: Polymorphism With @Qualifiers**

There is a brilliant annotation called **@Qualifiers** since the version 1.0. 

With this annotation, we can teach CDI which method should be used and CDI tries to create the correct object for us.

First of all, we need to **mark** our **createDebugLogger()** method, indicating that this method will use the **Debug mode**.

How can we mark classes or methods in Java? Using annotations! So, let's create our own annotation 😈

```java
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.METHOD, ElementType.FIELD})
public @interface DebugMode {

}
```

Easy, right? 

Notice that the **ElementType** on the annotation indicates where this annotation should be used. In our case, this will be used on methods and fields.

We've created the **DebugMode** annotation and we will mark the method **createDebugLogger()**

```java
public class SimpleLoggerFactory {

	@Produces @DebugMode
	public SimpleLogger createDebugLogger() {
		boolean debugMode = true;
		
		LogConfiguration logInDebugMode = new LogConfiguration(false, debugMode, false);
		
		return new SimpleLogger(logInDebugMode);
	}   
	//another method here..
}
```

It's time to CDI be aware of that new annotation by using the **@Qualifier** annotation:

```java
@Qualifier
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface DebugMode {

}
```

> Now CDI knows that the DebugMode annotation is a qualified annotation and will be used to filter which method should be used when a new Logger is requested.

Let's run it?

```java
INFO: WELD-ENV-002003: Weld SE container STATIC_INSTANCE initialized
INFO LOG: Finishing Checkout
Feb 15, 2017 8:09:57 AM org.jboss.weld.environment.se.WeldContainer shutdown
INFO: WELD-ENV-002001: Weld SE container STATIC_INSTANCE shut down
```

Is everything working properly?

Not so fast! As you can see, we are printing out the **INFO LOG**, right? But we'd like to print out the **DEBUG LOG**.

Yes, CDI requires us to specify **explicitly** which Qualifier should be used. If you **don't pass any Qualifier**, CDI will use its **default** Qualifier, called...**@Default**!

Behind the curtains, the method **createInfoLogger()** uses a **@Default** qualifier annotation:

```java
public class SimpleLoggerFactory {

    @Produces @Default // yes, it is here by default, however you dont't need to use it explicitly!
    public SimpleLogger createInfoLogger() {
      boolean infoMode = true;

      LogConfiguration logInInfoMode = new LogConfiguration(infoMode, false, false);

      return new SimpleLogger(logInInfoMode);
    }

}
```

And notice that CDI will configure the **@Default** Qualifier on the **injection point**:

```java
public class Checkout {

    @Inject @Default // it's here again!
    private SimpleLogger logger;

    public void finishCheckout() {
      logger.log("Finishing Checkout");
    }

}
```

So, keep in mind that we always have the **@Default** annotation when we don't specify a CDI Qualifier.

## #**8: Choosing Another Qualifier in the Injection Point**

Now it's easy to choose the Debug Mode on the Injection Point:

```java
public class Checkout {

    @Inject @DebugMode // debug mode now
    private SimpleLogger logger;

    public void finishCheckout() {
      logger.log("Finishing Checkout");
    }

}
```

Let's run it again!

```
INFO: WELD-ENV-002003: Weld SE container STATIC_INSTANCE initialized
DEBUG LOG: Finishing Checkout
Feb 15, 2017 8:26:41 AM org.jboss.weld.environment.se.WeldContainer shutdown
INFO: WELD-ENV-002001: Weld SE container STATIC_INSTANCE shut down
```

Now everything is working perfectly!

## #**9: Creating More Log Modes using Qualifiers**

It's worth mentioning that:

> Qualifiers bring to us the ability to use polymorphism at the Injection Point

So, it's time to create a new Qualifier to the **INFO** and **WARN** modes to get the benefits from Polymorphism and CDI:

```java
@Qualifier
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.METHOD, ElementType.FIELD})
public @interface InfoMode {

}
```

```java
@Qualifier
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.METHOD, ElementType.FIELD})
public @interface WarnMode {

}
```

And the entirely **SimpleLoggerFactory** class should be as follows:

```java
public class SimpleLoggerFactory {

    @Produces @DebugMode
    public SimpleLogger createDebugLogger() {
      boolean debugMode = true;

      LogConfiguration logInDebugMode = new LogConfiguration(false, debugMode, false);

      return new SimpleLogger(logInDebugMode);
    }

    @Produces @InfoMode
    public SimpleLogger createInfoLogger() {
      boolean infoMode = true;

      LogConfiguration logInInfoMode = new LogConfiguration(infoMode, false, false);

      return new SimpleLogger(logInInfoMode);
    }

    @Produces @WarnMode
    public SimpleLogger createWarnLogger() {
      boolean warnMode = true;

      LogConfiguration logInWarnMode = new LogConfiguration(false, false, warnMode);

      return new SimpleLogger(logInWarnMode);
    }

}
```

Using the **WARN** mode:

```java
@Inject @WarnMode
private SimpleLogger logger;
```

If you run the code again, the message will be printed out using **WARN** mode!

## #**10: @Qualifiers With Arguments**

We've created **3** Log modes so far. But what would be your life if we needed **5** more modes? 

Creating 5 more annotations doesn't sound like a good idea.

It's time to **refactor** our code by using Qualifiers with **arguments** to have less code being written. 

Yes, Qualifiers accept arguments in their annotations!

We'll create a new annotation called **@LoggerMode**, a more generic annotation:

```java
@Qualifier
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.METHOD, ElementType.FIELD})
public @interface LoggerMode {

}
```

We can use an **Enum** to indicate which mode we would like to use in the annotation:

```java
enum Mode {

    DEBUG, INFO, WARN

}
```

The complete Qualifier code will be:

```java
@Qualifier
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.METHOD, ElementType.FIELD})
public @interface LoggerMode {

  Mode desiredMode();

}
```

Pretty cool! We just need to change the methods on the **Factory** class to use the new annotation with the **desiredMode** option configured:

```java
public class SimpleLoggerFactory {

    @Produces @LoggerMode(desiredMode = Mode.DEBUG)
    public SimpleLogger createDebugLogger() { 
      ...
    }

    @Produces @LoggerMode(desiredMode = Mode.INFO)
    public SimpleLogger createInfoLogger() { 
      ...
    }

    @Produces @LoggerMode(desiredMode = Mode.WARN)
    public SimpleLogger createWarnLogger() {
      ...
    }

}
```

Now we can remove all the 3 annotations and end up by having only 1, the **@LoggerMode** annotation!

If we have **5** more Log Modes to be created, don't worry, you can create 5 more types on your Enum! Brilliant!

That's it! I hope you've learned 1 thing or 2 and thanks for stopping by, really appreciate :)

See you on the next [Part 3 - Observing Events](https://www.alexgama.io/java/cdi-series/cdi-in-java-series-part-3-events-and-observers/)

Let's keep in touch and don't forget to signup for my weekly newsletter 🙂

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)