# JUnit JBang Catalog

This catalog provides easy access to the JUnit Platform Console Standalone via JBang, making it simple to run JUnit tests from the command line or as a JBang-installed app.

## Quick Start

To use JUnit with JBang, first ensure you have [JBang installed](https://www.jbang.dev/download).

Run the JUnit Platform Console Standalone directly:

```sh
jbang junit@junit-team
```

Or install it as a command for easier reuse:

```sh
jbang app install junit@junit-team
junit
```

## Running Tests

To run JUnit tests, provide your test classpath and scan for tests:

```sh
junit --class-path <your classpath with tests included> --scan-classpath
```

If your tests are packaged in a Maven artifact, you can use JBang to resolve the classpath:

```sh
junit --class-path `jbang info classpath org.your:app:1.2.3` --scan-classpath
```
_Replace `org.your:app:1.2.3` with your actual Maven coordinates._

## Advanced Usage

### Using a Specific Java Version

You can specify a Java version when running or installing:

```sh
jbang --java 25 junit@junit-team --class-path <your classpath> --scan-classpath
```

Or when installing:

```sh
jbang app install --java 25 junit@junit-team
```

### Using a Specific Version of JUnit

To use a specific version of the JUnit CLI, you can run it directly with Maven coordinates:

```sh
jbang org.junit.platform:junit-platform-console-standalone:1.13.3
```

Or use the catalog with version syntax:

```sh
jbang junit@junit-team/jbang-catalog/1.13.3
```

## JBang Script Tests

JBang provides a JUnit template to help you create and run tests for JBang scripts.

1. Create a script:
   ```sh
   jbang init helloworld.java
   ```
2. Create a test for it:
   ```sh
   jbang init -t junit@jbangdev helloworld.java
   ```
   This generates `helloworldTest.java` that includes `helloworld.java` for easy test setup.
3. Build the test:
   ```sh
   jbang build helloworldTest.java
   ```
4. Run the test:
   ```sh
   junit --class-path `jbang info classpath helloworldTest.java` --scan-classpath
   ```

Example output (with a failing test):

```
💚 Thanks for using JUnit! Support its development at https://junit.org/sponsoring

╷
├─ JUnit Platform Suite ✔
├─ JUnit Jupiter ✔
│  └─ helloworldTest ✔
│     └─ testhelloworld() ✘ You should add some testing code for helloworld here! ==> expected: <1> but was: <2>
└─ JUnit Vintage ✔

Failures (1):
  JUnit Jupiter:genTest:testgen()
    MethodSource [className = 'test.genTest', methodName = 'testgen', methodParameterTypes = '']
    => org.opentest4j.AssertionFailedError: You should add some testing code for gen here! ==> expected: <1> but was: <2>
       org.junit.jupiter.api.AssertionFailureBuilder.build(AssertionFailureBuilder.java:151)
       org.junit.jupiter.api.AssertionFailureBuilder.buildAndThrow(AssertionFailureBuilder.java:132)
       org.junit.jupiter.api.AssertEquals.failNotEqual(AssertEquals.java:197)
       org.junit.jupiter.api.AssertEquals.assertEquals(AssertEquals.java:150)
       org.junit.jupiter.api.Assertions.assertEquals(Assertions.java:563)
       helloworldTest.testhelloworld(helloworldTest.java:27)
       java.base/java.lang.reflect.Method.invoke(Method.java:580)
       java.base/java.util.ArrayList.forEach(ArrayList.java:1597)
       java.base/java.util.ArrayList.forEach(ArrayList.java:1597)

Test run finished after 35 ms
[         4 containers found      ]
[         0 containers skipped    ]
[         4 containers started    ]
[         0 containers aborted    ]
[         4 containers successful ]
[         0 containers failed     ]
[         1 tests found           ]
[         0 tests skipped         ]
[         1 tests started         ]
[         0 tests aborted         ]
[         0 tests successful      ]
[         1 tests failed          ]
```

=== Additonal Help

You can run `junit` and get command line help or read the [guide](https://docs.junit.org/current/user-guide/#running-tests-console-launcher)
