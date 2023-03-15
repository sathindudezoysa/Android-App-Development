# Android-App-Development
## View Binding
![](/images/view_binding.png)

## Enable view binding
1. Open the app's build.gradle file ( Gradle Scripts > build.gradle (Module: Tip_Time.app) )
2. In the android section, add the following lines:

```kotlin
buildFeatures {
    viewBinding = true
}

```
3. Note the message Gradle files have changed since last project sync.
4. Press Sync Now.

## Initialize the binding object
1. Open MainActivity.kt (app > java > com.example.tiptime > MainActivity).
2. Replace all of the existing code for MainActivity class with this code to setup the MainActivity to use view binding:

```kotlin
class MainActivity : AppCompatActivity() {

    lateinit var binding: ActivityMainBinding //The lateinit keyword is something new. It's a promise that your code will initialize the variable before using it. If you don't, your app will crash.

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater) //This line initializes the binding object which you'll use to access Views in the activity_main.xml layout.
        setContentView(binding.root) //Set the content view of the activity. Instead of passing the resource ID of the layout, R.layout.activity_main, this specifies the root of the hierarchy of views in your app, binding.root.
    }
}
```
3. This line declares a top-level variable in the class for the binding object. It's defined at this level because it will be used across multiple methods in MainActivity class.

##Example Code
```kotlin
// Old way with findViewById()
val myButton: Button = findViewById(R.id.my_button)
myButton.text = "A button"

// Better way with view binding
val myButton: Button = binding.myButton
myButton.text = "A button"

// Best way with view binding and no extra variable
binding.myButton.text = "A button"
```
