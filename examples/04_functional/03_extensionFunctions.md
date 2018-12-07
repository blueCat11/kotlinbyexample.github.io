# Extension Functions and Properties

<div class="language-kotlin" theme="idea" data-min-compiler-version="1.3">

```kotlin
data class Item(val name: String, val price: Float)                                   // 1  

data class Order(val items: Collection<Item>)  

fun Order.maxPricedItemValue(): Float = this.items.maxBy { it.price }?.price ?: 0F    // 2  
fun Order.maxPricedItemName() = this.items.maxBy { it.price }?.name ?: "NO_PRODUCTS"

val Order.commaDelimitedItemNames: String                                             // 3
    get() = items.map { it.name }.joinToString()

fun main() {

    val order = Order(listOf(Item("Bread", 25.0F), Item("Wine", 29.0F), Item("Water", 12.0F)))
    
    println("Max priced item name: ${order.maxPricedItemName()}")
    println("Max priced item value: ${order.maxPricedItemValue()}")
    println("Items: ${order.commaDelimitedItemNames}")

}
```

</div>

1. We define simple models of `Item` and `Order`. `Order` can contain arbitrary `Collection`s of `Item` s
2. We define extension functions for `Order` type. Later we call these functions directly on the instance of that type. 
3. We can also define extension properties.

Read more about the signature of [extensions](https://kotlinlang.org/docs/reference/extensions.html). It
is very much like the standard function or property signature, with the addition that we need to specify the type we're attaching function or property to.

It is even possible to execute extensions on `null` references. In their implementation we can check for `null` reference and based on that we can do any arbitrary logic. Example:
   
<div class="language-kotlin" theme="idea" data-min-compiler-version="1.3">

```kotlin
//sampleStart
fun <T> T?.nullSafeToString() = this?.toString() ?: "NULL"  // 1
//sampleEnd
fun main() {
    println(null.nullSafeToString())
    println("Kotlin".nullSafeToString())
}
```

</div>
