# aleph-formatter

`AlephFormatter` is a lightweight String Formatter for Java that supports named parameters with a twist: it has a very limited support for object introspection. 

```java
String result = template("#{errNo} -> #{c.simpleName} -> #{c.package.name}")
                .arg("errNo", 101)
                .arg("c", String.class)
                .fmt();


System.out.println(result);
```
Output:
```
Error number: 101 -> String -> java.lang
```

### API

The API is very simple, and has a [fluid](https://en.wikipedia.org/wiki/Fluent_interface) feel to it. 

There a few ways you can achieve the same thing as above. 

For example instead of using `arg()` you can use `args()` and specify the list of parameters on a single line, alternating the argument to be replaced with it's value:

```java
String result = template("#{errNo} -> #{c.simpleName} -> #{c.package.name}")
                .args("errNo", 101, "c", String.class)
                .fmt();
```

Escaping the `"#{"` can be done using the ``` ` ``` character:

```java
String result = template("#{errNo} + escaped: `#{errNo}")
                 .arg("errNo", 101)
                 .fmt();

System.out.println(result);
```

Output: 
```
101 + escaped: #{errNo}
```
