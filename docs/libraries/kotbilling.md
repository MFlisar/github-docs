---
icon: material/github
library: KotBilling
demo_link: https://github.com/MFlisar/KotBilling/blob/master/demo/src/main/java/com/michaelflisar/kotbilling/demo
screenshots:
module: core
---

{% include 'badges_header.md' %}

<i>A kotlin coroutine based solution for handling in app purchases for **billing library version 6**.</i>

## :material-check-all: Features

* exception save, each functions returns a non null sealed class / interface instance
* simple query function to query a product state: `val result = KotBilling.queryProducts(... products ...)`
* simple purchase function to buy a product and acknowledge/consume it: `val result = KotBilling.purchase(actvity, product, offerToken)`

## :link: Dependencies

| Dependency | Version |
|:-|-:|
| [com.android.billingclient:billing-ktx](https://mvnrepository.com/artifact/com.android.billingclient/billing-ktx?repo=google) | `6.0.1` |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

```kotlin

// --------------------
// Quering available product(s)
// --------------------

lifecycleScope.launch(Dispatchers.IO) {

    val result = KotBilling.queryProducts(
        listOf(/* products to query */)
    )
    when (result) {
        is KBError -> {
            val connectionState = result.connectionState
            val errorType = result.errorType
            // errorType is a sealed class which will tell you the reason and type for the error (connection error, purchase error, acknowledge error, ...)
            // connectionState will tell you what the connection state was
        }
        is KBProductDetailsList -> {
            if (result.details.isEmpty()) {
                // most probably only happens if you try this inside a debug app or an app that's not released on the playstore yet
            } else {
                // in all other cases you will get a list with products and all their details (same size as the queried products) which you can handle here
                result.details.forEach {
                    val product = it.product
                    val details = it.details
                    // ... 
                }
            }
        }
    }
}

// --------------------
// Quering purchase(s)
// --------------------

lifecycleScope.launch(Dispatchers.IO) {
    
    val result = KotBilling.queryPurchases(ProductType.InApp) // or ProductType.Subscription
    when (result) {
        is KBError -> {
            val connectionState = result.connectionState
            val errorType = result.errorType
            // errorType is a sealed class which will tell you the reason and type for the error (connection error, purchase error, acknowledge error, ...)
            // connectionState will tell you what the connection state was
        }
        is KBPurchaseQuery -> {
            if (result.details.isEmpty()) {
                // user did not purchase anything yet
            } else {
                val productType = result.productType
                val details = result.details
                // details holds a list of all purchase details which you can handle here
            }
        }
    }
}

// --------------------
// Purchasing a product
// --------------------

lifecycleScope.launch(Dispatchers.IO) {
    val result = KotBilling.purchase(
        context,
        /* product */,
        /* optional offerToken */
    )
    when (result) {
        is KBError -> {
            val connectionState = result.connectionState
            val errorType = result.errorType
            // errorType is a sealed class which will tell you the reason and type for the error (connection error, purchase error, acknowledge error, ...)
            // connectionState will tell you what the connection state was
        }
        is KBPurchase -> {
            // success
            val purchase = result.purchase
            // purchase holds the purchase details which you can handle here
        }
    }
}

```

## :dna: Demo

{% include 'github_demo.md' %}

But be aware, the demo app is not deployed on google play so it won't return any results - still it shows how to use the library.