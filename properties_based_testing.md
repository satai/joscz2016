title: Properties Based Testing

theme: satai/cleaver-dark

author:
  name: Ondra Nekola
  twitter: satai
  url: http://www.nekola.cz

--

# Tests

1. motivation
1. solution(?)

--

# Motivation

* double-book entry
* kinda specification
* let the machine do the job

--

# Tests 101

* ?Unit

--

# Tests 101

```java
@Test
public void testAddition() {
    assertEquals("27 + 3 should be 30", 30, addition(27, 3));
}
```

--

# Make it readable

```groovy
def "adding works"() {
    given:
    when:
    then:
}
```

--

# Make it readable

```groovy
def "adding works"() {
    given:
    	def adder = new Adder()
    when:
    	result = adder.add(27, 3)
    then:
    	30 == result
}
```
--

# Make it readable

```groovy
def "adding works"() {
    given:
        def adder = new Adder()
    when:
        result = adder.add(a, b)
    then:
        expectedResult == result
    where:
        a |  b || expectedResult
        2 |  1 || 3
        2 |  1 || 3
        3 | 27 || 30
}
```
--
# Make the machine do the work

```groovy
def "adding is commutative"() {
    given:
        def adder = new Adder()
    when:
        result1 = adder.add(a, b)
        result2 = adder.add(b, a)
    then:
        result1 == result2
    where:
        a |  b
        2 |  1
        0 |  1
        3 | 27
}
```
--
# Rotate it 90 degrees!

```groovy
def "adding is commutative"() {
    given:
        def adder = new Adder()
    when:
        result1 = adder.add(a, b)
        result2 = adder.add(b, a)
    then:
        result1 == result2
    where:
        a << [2, 0,  3]
        b << [1, 1, 27]
}
```
--
# Make the machine do the work

```groovy
def "adding is commutative"() {
    given:
        def adder = new Adder()
    when:
        result1 = adder.add(a, b)
        result2 = adder.add(b, a)
    then:
        result1 == result2
    where:
        a << *MAGIC*
        b << *MAGIC*
}
```
--
# Unroll it

```groovy
@Unroll
def "adding is commutative for #a and #b"() {
    given:
        def adder = new Adder()
    when:
        result1 = adder.add(a, b)
        result2 = adder.add(b, a)
    then:
        result1 == result2
    where:
        a << *MAGIC*
        b << *MAGIC*
}
```
--
![Genesis](preacher.jpg)
--
# Genesis

```groovy
@Unroll
def "adding is commutative for #a and #b"() {
    given:
        def adder = new Adder()
    when:
        result1 = adder.add(a, b)
        result2 = adder.add(b, a)
    then:
        result1 == result2
    where:
        a << Gen.int.take(100)
        b << Gen.int.take(100)
}
```
--
# With all the respect...

## ...adding examples is pretty useless...

## ...sir.
--

# What is next next

* we can see
  * I would like to see the EL

--

# Q&A?
