---
icon: material/github
library: KotPreferences
demo_link: https://github.com/MFlisar/KotPreferences/blob/master/demo/src/main/java/com/michaelflisar/kotpreferences/demo
screenshots: https://raw.githubusercontent.com/MFlisar/KotPreferences/master/screenshots
modules:
  - core: 
    - core
  - storage:
    - datastore
    - encryption-aes
  - extension:
    - compose
---

{% include 'badges_header.md' %}

<i>With this library you can declare preferences via **kotlin delegates** and observe and update them via kotlin Flows. This works with any storage implementation, an implementation for JetPack DataStore is provided already.</i>

## :material-check-all: Features

With this library you can declare preferences via kotlin `delegates` and observe and update them via kotlin `Flows`. This works with any storage implementation, an implementation for JetPack DataStore is provided already. Additionally there's also an extension to easily integrate this library into your compose app.

**All features are splitted into separate modules, just include the modules you want to use!**

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

???+ code "Define Preferences"

    ```kotlin
    object UserSettingsModel : SettingsModel(DataStoreStorage(name = "user")) {

        // main data types
        val someString by stringPref("value")
        val someBool by boolPref(false)
        val someInt by intPref(123)
        val someLong by intPref(123L)
        val someFloat by intPref(123f)
        val someDouble by intPref(123.0)
        
        // enum
        val someEnum by enumPref(Enum.Value1)
        
        // custom
        val someCustomClass by anyPref(TestClass.CONVERTER, TestClass())
        
        // sets
        val someStringSet by stringSetPref(setOf("a"))
        val someIntSet by intSetPref(setOf(1))
        val someLongSet by longSetPref(setOf(1L))
        val someFloatSet by floatSetPref(setOf(1f))
        val someDoubleSet by doubleSetPref(setOf(1.0))
        
        // NULLABLE vs NON NULLABLE
        val nonNullableString by stringPref()
        val nullableString by nullableStringPref()
        val nonNullableInt by intPref()
        val nullableInt by nullableIntPref()
        val nonNullableFloat by floatPref()
        val nullableFloat by nullableFloatPref()
        val nonNullableDouble by doublePref()
        val nullableDouble by nullableDoublePref()
        val nonNullableLong by longPref()
        val nullableLong by nullableLongPref()
        val nonNullableBool by boolPref()
        val nullableBool by nullableBoolPref()
    }
    ```

???+ code "Observe/Read Preferences"

    ```kotlin
    // 1) simply observe a setting
    UserSettingsModel.name.observe(lifecycleScope) {
        L.d { "name = $it"}
    }

    // 2) direct read (not recommended if not necessary but may be useful in many cases => simply returns flow.first() in a blocking way)
    val name = UserSettingsModel.name.value

    // 3) observe a setting once
    UserSettingsModel.name.observeOnce(lifecycleScope) {
        L.d { "name = $it"}
    }

    // 4) observe ALL settings
    UserSettingsModel.changes.onEach {
        L.d { "[ALL SETTINGS OBSERVER] Setting '${it.setting.key}' changed its value to ${it.value}" }
    }.launchIn(lifecycleScope)

    // 5) observe SOME settings
    UserSettingsModel.changes
        .filter {
            it.setting == UserSettingsModel.name ||
            it.setting == UserSettingsModel.age
        }.onEach {
            // we know that either the name or the age changes
            L.d { "[SOME SETTINGS OBSERVER] Setting '${it.setting.key}' changed its value to ${it.value}" }
        }.launchIn(lifecycleScope)
        
    // 6) read multiple settings in a suspending way
    lifecycleScope.launch(Dispatchers.IO) {
        val name = UserSettingsModel.childName1.flow.first()
        val alive = DemoSettingsModel.alive.flow.first()
        val hairColor = DemoSettingsModel.hairColor.flow.first()
        withContext(Dispatchers.Main) {
            textView.text = "Informations: $name, $alive, $hairColor"
        }
    }
    ```

???+ code "Lifedata"

    ```kotlin
    val lifedata = UserSettingsModel.name.flow.asLiveData()
    ```

???+ code "Update preferences"

    ```kotlin
    lifecycleScope.launch(Dispatchers.IO)  {
        UserSettingsModel.name.update("Some new name")
        UserSettingsModel.age.update(30)
    }
    ```

???+ code "Compose"

    Add the `compose` module to get following extensions for compose.

    ```kotlin
    val name = UserSettingsModel.name.collectAsState()
    val name = UserSettingsModel.name.collectAsStateWithLifecycle()

    // simply use the state inside your composables, the state will change whenever the setting behind it will change
    ```

## :dna: Demo

{% include 'github_demo.md' %}

## :material-view-module: Modules and Extensions

??? info-primary "Encryption Module"

    Currently there only exists the AES encryption module. It simple implements a predefined interface that encrypts and decrypts all data before it get's persisted by a storage implementation.

    This module is placed inside the `encrpytion-aes` artifact and can simply be used like following:

    **Step 1/2: define the encryption**

    ```kotlin
    private const val ALGORITHM = StorageEncryptionAES.DEFAULT_ALGORITHM
    private const val KEY_ALGORITHM = StorageEncryptionAES.DEFAULT_KEY_ALGORITHM
    // also check out StorageEncryptionAES::generateKey and StorageEncryptionAES::generateIv if you need some helper functions
    private val KEY = StorageEncryptionAES.getKeyFromPassword(KEY_ALGORITHM, "my key", "my salt")
    private val BYTE_ARRAY = listOf(0x16, 0x09, 0xc0, 0x4d, 0x4a, 0x09, 0xd2, 0x46, 0x71, 0xcc, 0x32, 0xb7, 0xd2, 0x91, 0x8a, 0x9c)
        .map { it.toByte() }
        .toByteArray()
    private val IV = StorageEncryptionAES.getIv(BYTE_ARRAY) // byte array must be 16 bytes!
    val ENCRYPTION = StorageEncryptionAES(ALGORITHM, KEY, IV)
    ```

    **Step 2/2: attach the encryption to your storage instance**

    ```kotlin
    object MyEncryptedSettingsModel : SettingsModel(
        DataStoreStorage(
            name = "encrypted",
            encryption = ENCRYPTION
        )
    ) {
        // ...
    }
    ```

??? info-primary "Storage DataStore Module"

    The `Storage` is an abstraction to support any storage implementation. The `datastore` module provides an implementation based on the [Android JetPack DataStore](https://developer.android.com/topic/libraries/architecture/datastore).

    This module is placed inside the `datastore` artifact and can simple be used like following:

    ```kotlin
    object SettingsModel : SettingsModel(
        DataStoreStorage(
            name = "demo_settings" // file name of preference file
        )
    ) {
        // ...
    }
    ```

    It supports following data types:

    * `String`
    * `Bool`
    * `Int`
    * `Long`
    * `Float`
    * `Double`
    * Sets:
        * `Set<String>`
        * `Set<Int>`
        * `Set<Long>`
        * `Set<Float>`
        * `Set<Double>`