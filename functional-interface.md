# Predefined Functional Interfaces

## Supplier

### Supplier\<T\>

* Represents a function that takes no arguments and returns a result of type `T`.

```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}

Supplier<String> getHello = () -> "Hello, World!";
String result = getHello.get();
```

### IntSupplier

* Represents a function that takes no arguments and returns an `int`.

```java
@FunctionalInterface
public interface IntSupplier {
    int getAsInt();
}

IntSupplier randomIntSupplier = () -> (int) (Math.random() * 100);
int result = randomIntSupplier.getAsInt();
```

### LongSupplier

* Represents a function that takes no arguments and returns a `long`.

```java
@FunctionalInterface
public interface LongSupplier {
    long getAsLong();
}

LongSupplier currentTimeSupplier = () -> System.currentTimeMillis();
long result = currentTimeSupplier.getAsLong();
```

### DoubleSupplier

* Represents a function that takes no arguments and returns a `double`.

```java
@FunctionalInterface
public interface DoubleSupplier {
    double getAsDouble();
}

DoubleSupplier piSupplier = () -> 3.14159;
double result = piSupplier.getAsDouble();
```

### BooleanSupplier

* Represents a function that takes no arguments and returns a `boolean`.

```java
@FunctionalInterface
public interface BooleanSupplier {
    boolean getAsBoolean();
}

BooleanSupplier isEven = () -> 10 % 2 == 0;
boolean result = isEven.getAsBoolean(); 
```

## Predicate

### Predicate\<T\>

* Represents a function that takes a single argument of type `T` and returns a `boolean`.
* Chaining Methods:
  * `and()`
  * `or()`
  * `negate()`

```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);

    default Predicate<T> and(Predicate<? super T> other) {}
    default Predicate<T> or(Predicate<? super T> other) {}
    default Predicate<T> negate() {}
}

Predicate<String> isNotEmpty = str -> !str.isEmpty();
Predicate<String> isShort = str -> str.length() < 10;

// chaining
boolean result = isNotEmpty.and(isShort).test("Hello");
```

### BiPredicate\<T, U\>

* Represents a function that takes two arguments of types `T` and `U`, and returns a `boolean`.
* Chaining Methods:
  * `and()`
  * `or()`
  * `negate()`

```java
@FunctionalInterface
public interface BiPredicate<T, U> {
    boolean test(T t, U u);

    default BiPredicate<T, U> and(BiPredicate<? super T, ? super U> other) {}
    default BiPredicate<T, U> or(BiPredicate<? super T, ? super U> other) {}
    default BiPredicate<T, U> negate() {}
}

BiPredicate<String, Integer> isLengthGreaterThan = (str, length) -> str.length() > length;
BiPredicate<String, Integer> isNotEmpty = (str, length) -> !str.isEmpty();

// chaining
boolean result = isLengthGreaterThan.and(isNotEmpty).test("Hello", 3);
```

### IntPredicate

* Represents a predicate that takes an `int` and returns a `boolean`.
* Chaining Methods:
  * `and()`
  * `or()`
  * `negate()`

```java
@FunctionalInterface
public interface IntPredicate {
    boolean test(int value);

    default IntPredicate and(IntPredicate other) {}
    default IntPredicate or(IntPredicate other) {}
    default IntPredicate negate() {}
}

IntPredicate isEven = num -> num % 2 == 0;
IntPredicate isGreaterThanFive = num -> num > 5;

// chaining
boolean result = isEven.and(isGreaterThanFive).test(6);
```

### LongPredicate

* Represents a predicate that takes a `long` and returns a `boolean`.
* Chaining Methods:
  * `and()`
  * `or()`
  * `negate()`

```java
@FunctionalInterface
public interface LongPredicate {
    boolean test(long value);

    default LongPredicate and(LongPredicate other) {}
    default LongPredicate or(LongPredicate other) {}
    default LongPredicate negate() {}
}

LongPredicate isPositive = num -> num > 0;
LongPredicate isEven = num -> num % 2 == 0;

// chaining
boolean result = isPositive.and(isEven).test(4);
```

### DoublePredicate

* Represents a predicate that takes a `double` and returns a `boolean`.
* Chaining Methods:
  * `and()`
  * `or()`
  * `negate()`

```java
@FunctionalInterface
public interface DoublePredicate {
    boolean test(double value);

    default DoublePredicate and(DoublePredicate other) {}
    default DoublePredicate or(DoublePredicate other) {}
    default DoublePredicate negate() {}
}

DoublePredicate isGreaterThanZero = num -> num > 0;
DoublePredicate isLessThanTen = num -> num < 10;

// chaining
boolean result = isGreaterThanZero.and(isLessThanTen).test(5.5);
```

## Consumer

### Consumer\<T\>

* Represents a function that takes a single argument of type `T` and returns no result.
* Chaining Methods:
  * `andThen()`

```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);

    default Consumer<T> andThen(Consumer<? super T> after) {}
}

Consumer<String> print = str -> System.out.println(str);
Consumer<String> upperCasePrint = str -> System.out.println(str.toUpperCase());

// chaining
print.andThen(upperCasePrint).accept("hello");
```

### BiConsumer\<T, U\>

* Represents a function that takes two arguments of type `T` and `U` and returns no result.
* Chaining Methods:
  * `andThen()`

```java
@FunctionalInterface
public interface BiConsumer<T, U> {
    void accept(T t, U u);

    default BiConsumer<T, U> andThen(BiConsumer<? super T, ? super U> after) {}
}

BiConsumer<String, Integer> printPair = (str, num) -> System.out.println(str + ": " + num);
printPair.accept("Score", 100);
```

### IntConsumer

* Represents a consumer that takes an `int` as input and returns `void`.
* Chaining Methods:
  * `andThen()`

```java
@FunctionalInterface
public interface IntConsumer {
    void accept(int value);

    default IntConsumer andThen(IntConsumer after) {}
}

IntConsumer print = n -> System.out.println(n);
print.accept(10);
```

### LongConsumer

* Represents a consumer that takes a `long` as input and returns `void`.
* Chaining Methods:
  * `andThen()`

```java
@FunctionalInterface
public interface LongConsumer {
    void accept(long value);

    default LongConsumer andThen(LongConsumer after) { ... }
}

LongConsumer print = n -> System.out.println(n);
print.accept(100L);
```

### DoubleConsumer

* Represents a consumer that takes a `double` as input and returns `void`.
* Chaining Methods:
  * `andThen()`

```java
@FunctionalInterface
public interface DoubleConsumer {
    void accept(double value);

    default DoubleConsumer andThen(DoubleConsumer after) { ... }
}

DoubleConsumer print = d -> System.out.println(d);
print.accept(3.14);
```

### ObjIntConsumer\<T\>

* Represents a consumer that accepts an object of type `T` and an `int` and returns no result.

```java
@FunctionalInterface
public interface ObjIntConsumer<T> {
    void accept(T t, int value);
}

ObjIntConsumer<String> printLength = (str, length) -> System.out.println(str + ": " + length);
printLength.accept("Hello", 5);
```

### ObjLongConsumer\<T\>

* Represents a consumer that accepts an object of type `T` and a `long` and returns no result.

```java
@FunctionalInterface
public interface ObjLongConsumer<T> {
    void accept(T t, long value);
}

ObjLongConsumer<String> printLength = (str, length) -> System.out.println(str + ": " + length);
printLength.accept("Hello", 5L);
```

### ObjDoubleConsumer\<T\>

* Represents a consumer that accepts an object of type `T` and a `double` and returns no result.

```java
@FunctionalInterface
public interface ObjDoubleConsumer<T> {
    void accept(T t, double value);
}

ObjDoubleConsumer<String> printLength = (str, length) -> System.out.println(str + ": " + length);
printLength.accept("Hello", 5.5);
```

## Function

### Function\<T, R\>

* Represents a function that takes an argument of type `T` and returns a result of type `R`.
* Chaining Methods:
  * `andThen()`
  * `compose()`

```java
@FunctionalInterface
public interface Function<T, R> {
    R apply(T t);

    default <V> Function<T, V> andThen(Function<? super R, ? extends V> after) {}
    default <V> Function<V, R> compose(Function<? super V, ? extends T> before) {}
}

Function<String, Integer> stringLength = str -> str.length();
Function<Integer, String> intToString = i -> "Length: " + i;

// chaining
String result = stringLength.andThen(intToString).apply("Hello");
```

### UnaryOperator\<T\>

* A special case of `Function<T, T>`, which represents a function that takes an argument of type `T` and returns a result of the same type `T`.
* Chaining Methods:
  * `andThen()`
  * `compose()`

```java
@FunctionalInterface
public interface UnaryOperator<T> extends Function<T, T> {
    T apply(T t);

    default UnaryOperator<T> andThen(UnaryOperator<T> after) {}
    default UnaryOperator<T> compose(UnaryOperator<T> before) {}
}

Function<Integer, Integer> doubleValue = x -> x * 2;
Function<Integer, Integer> addFive = x -> x + 5;

// simple version of the above code
UnaryOperator<Integer> doubleValue = x -> x * 2;
UnaryOperator<Integer> addFive = x -> x + 5;

// chaining
int result = doubleValue.andThen(addFive).apply(3);
```

### BiFunction\<T, U, R\>

* Represents a function that takes two arguments of types `T` and `U`, and returns a result of type `R`.
* Chaining Methods:
  * `andThen()`
  * `compose()`

```java
@FunctionalInterface
public interface BiFunction<T, U, R> {
    R apply(T t, U u);

    default <V> BiFunction<T, U, V> andThen(Function<? super R, ? extends V> after) {}
    default <V> BiFunction<V, U, R> compose(Function<? super V, ? extends T> before) {}
}

BiFunction<String, Integer, String> repeat = (str, times) -> str.repeat(times);
BiFunction<String, Integer, String> prefix = (str, times) -> "Repeated: " + str;

// chaining
String result = repeat.andThen(prefix).apply("Hello", 3);
```

### BinaryOperator\<T\>

* A special case of `BiFunction<T, T, T>`, which represents a function that takes two arguments of type `T` and returns a result of the same type `T`.
* Chaining Methods:
  * `andThen()`

```java
@FunctionalInterface
public interface BinaryOperator<T> extends BiFunction<T, T, T> {
    T apply(T t1, T t2);

    default BinaryOperator<T> andThen(BinaryOperator<T> after) {}
}

BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
BiFunction<Integer, Integer, Integer> multiply = (a, b) -> a * b;

// simple version of the above code
BinaryOperator<Integer> add = (a, b) -> a + b;
BinaryOperator<Integer> multiply = (a, b) -> a * b;

// chaining
int result = add.andThen(multiply).apply(2, 3);
```

### IntFunction\<R\>

* Represents a function that takes an `int` and returns a result of type `R`.

```java
@FunctionalInterface
public interface IntFunction<R> {
    R apply(int value);
}

IntFunction<String> intToString = i -> "Number: " + i;
String result = intToString.apply(10);
```

### LongFunction\<R\>

* Represents a function that takes a `long` and returns a result of type `R`.

```java
@FunctionalInterface
public interface LongFunction<R> {
    R apply(long value);
}

LongFunction<String> longToString = l -> "Long: " + l;
String result = longToString.apply(100L);
```

### DoubleFunction\<R\>

* Represents a function that takes a `double` and returns a result of type `R`.

```java
@FunctionalInterface
public interface DoubleFunction<R> {
    R apply(double value);
}

DoubleFunction<String> doubleToString = d -> "Double: " + d;
String result = doubleToString.apply(3.14);
```

### ToIntFunction\<T\>

* Represents a function that takes an argument of type `T` and returns an `int`.

```java
@FunctionalInterface
public interface ToIntFunction<T> {
    int applyAsInt(T value);
}

ToIntFunction<String> stringToInt = str -> str.length();
int result = stringToInt.applyAsInt("Hello");
```

### ToLongFunction\<T\>

* Represents a function that takes an argument of type `T` and returns a `long`.

```java
@FunctionalInterface
public interface ToLongFunction<T> {
    long applyAsLong(T value);
}

ToLongFunction<String> stringToLong = str -> str.length();
long result = stringToLong.applyAsLong("Hello");
```

### ToDoubleFunction\<T\>

* Represents a function that takes an argument of type `T` and returns a `double`.

```java
@FunctionalInterface
public interface ToDoubleFunction<T> {
    double applyAsDouble(T value);
}

ToDoubleFunction<String> stringToDouble = str -> str.length() * 1.5;
double result = stringToDouble.applyAsDouble("Hello");
```

### ToIntBiFunction\<T, U\>

* Represents a function that takes two arguments of types `T` and `U` and produces an `int` result.

```java
@FunctionalInterface
public interface ToIntBiFunction<T, U> {
    int applyAsInt(T t, U u);
}

ToIntBiFunction<String, String> stringLengthDifference = (str1, str2) -> str1.length() - str2.length();
int result = stringLengthDifference.applyAsInt("Hello", "World");
```

### ToLongBiFunction\<T, U\>

* Represents a function that takes two arguments of types `T` and `U` and produces an `long` result.

```java
@FunctionalInterface
public interface ToLongBiFunction<T, U> {
    long applyAsLong(T t, U u);
}

ToLongBiFunction<String, Integer> multiplyLengthByFactor = (str, factor) -> str.length() * (long) factor;
long result = multiplyLengthByFactor.applyAsLong("Hello", 1000);
```

### ToDoubleBiFunction\<T, U\>

* Represents a function that takes two arguments of types `T` and `U` and produces an `double` result.

```java
@FunctionalInterface
public interface ToDoubleBiFunction<T, U> {
    double applyAsDouble(T t, U u);
}

ToDoubleBiFunction<Integer, Integer> average = (a, b) -> (a + b) / 2.0;
double result = average.applyAsDouble(5, 15);
```

### IntToLongFunction

* Represents a function that takes an `int` and returns a `long`.

```java
@FunctionalInterface
public interface IntToLongFunction {
    long applyAsLong(int value);
}

IntToLongFunction intToLong = i -> i * 10L;
long result = intToLong.applyAsLong(5);
```

### IntToDoubleFunction

* Represents a function that takes an `int` and returns a `double`.

```java
@FunctionalInterface
public interface IntToDoubleFunction {
    double applyAsDouble(int value);
}

IntToDoubleFunction intToDouble = i -> i * 1.5;
double result = intToDouble.applyAsDouble(5);
```

### LongToIntFunction

* Represents a function that takes a `long` and returns an `int`.

```java
@FunctionalInterface
public interface LongToIntFunction {
    int applyAsInt(long value);
}

LongToIntFunction longToInt = l -> (int) l;
int result = longToInt.applyAsInt(100L);
```

### LongToDoubleFunction

* Represents a function that takes a `long` and returns a `double`.

```java
@FunctionalInterface
public interface LongToDoubleFunction {
    double applyAsDouble(long value);
}

LongToDoubleFunction longToDouble = l -> l * 2.5;
double result = longToDouble.applyAsDouble(10L);
```

### DoubleToIntFunction

* Represents a function that takes a `double` and returns an `int`.

```java
@FunctionalInterface
public interface DoubleToIntFunction {
    int applyAsInt(double value);
}

DoubleToIntFunction doubleToInt = d -> (int) d;
int result = doubleToInt.applyAsInt(10.5);
```

### DoubleToLongFunction

* Represents a function that takes a `double` and returns a `long`.

```java
@FunctionalInterface
public interface DoubleToLongFunction {
    long applyAsLong(double value);
}

DoubleToLongFunction doubleToLong = d -> (long) d;
long result = doubleToLong.applyAsLong(10.5);
```

