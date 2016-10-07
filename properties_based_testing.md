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

# Make it radable

```groovy
def "adding works"() {
    given:
    when:
    then:
}
```

--

# What is next next

* we can see
  * I would like to see the EL

--

# Q&A?
