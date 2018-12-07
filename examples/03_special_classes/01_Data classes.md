# Data classes

_Data classes_ make it easy to declare classes that are used to store some values.
Some standard functionality is auto-generated, such as a useful string representation and everything that's needed to use the _data classes_ in collections or create copies.

<div class="language-kotlin" theme="idea" data-min-compiler-version="1.3">

```kotlin
data class User(val name: String, val id: Int)

fun main() {
    val user = User("Alex", 1)
    println(user)                                          // 1

    val secondUser = User("Alex", 1)
    val thirdUser = User("Max", 2)

    println("user == secondUser: ${user == secondUser}")   // 2
    println("user == thirdUser: ${user == thirdUser}")

    println(user.hashCode())                               // 3
    println(thirdUser.hashCode())

    // copy() function
    println(user.copy())                                   // 4
    println(user.copy("Max", 2))                           // 5
    println(user.copy("Max"))                              // 6
    println(user.copy(id = 2))                             // 7
    
    println("name = ${user.component1()}")                 // 8
    println("id = ${user.component2()}")
}
```

</div>

1. Method `toString` is auto-generated, which makes `println` output look nice.
2. Auto-generated `equals` makes data classes with equal information equals as well.
3. Equal data classes have equal `hashCode()`.
4. Predefined `copy` function makes it easy to obtain a new instance.
5. Property values can be changed on copy. The order corresponds to constructor argument order.
6. It is possible to change only some values.
7. Use named arguments to change the second value without altering the first one.
8. Additionally special `componentN` functions are generated.
