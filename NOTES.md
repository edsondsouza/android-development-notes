# Boilerplate code
```kotlin
package com.example.greetingcard

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.tooling.preview.Preview
import com.example.greetingcard.ui.theme.GreetingCardTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            GreetingCardTheme {
                // A surface container using the 'background' color from the theme
                Surface(modifier = Modifier.fillMaxSize(), color = MaterialTheme.colorScheme.background) {
                    Greeting("Android")
                }
            }
        }
    }
}

@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text(
            text = "Hi, my name is $name!",
            modifier = modifier
    )
}

@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    GreetingCardTheme {
        Greeting("Edson")
    }
}
```

- onCreate() function is the entry point to this Android app and calls other functions to build the user interface.
- In Kotlin programs, the main() function is the entry point/starting point of execution. In Android apps, the onCreate() function fills that role.
- The setContent() function within the onCreate() function is used to define your layout through composable functions.
- All functions marked with the @Composable annotation can be called from the setContent() function or from other Composable functions. The annotation tells the Kotlin compiler that this function is used by Jetpack Compose to generate the UI.

# Composable function
![image](https://github.com/edsondsouza/android-development-notes/assets/93525771/3d59f020-cbd1-45c0-8830-8c177fd1ec57)

- You add the @Composable annotation before the function.
- @Composable function names are capitalized.
- @Composable functions can't return anything.

The GreetingPreview() function is a cool feature that lets you see what your composable looks like without having to build your entire app. To enable a preview of a composable, annotate it with @Composable and @Preview. The @Preview annotation tells Android Studio that this composable should be shown in the design view of this file.

As you can see, the @Preview annotation takes in a parameter called showBackground. If showBackground is set to true, it will add a background to your composable preview.

Since Android Studio by default uses a light theme for the editor, it can be hard to see the difference between showBackground = true and showBackground = false.

# Color
`import androidx.compose.ui.graphics.Color`

# Padding
A Modifier is used to augment or decorate a composable. One modifier you can use is the padding modifier, which adds space around the element (in this case, adding space around the text). This is accomplished by using the Modifier.padding() function.

Every composable should have an optional parameter of the type Modifier. This should be the first optional parameter.

`import androidx.compose.ui.unit.dp`

`import androidx.compose.foundation.layout.padding`

# Optimizing imports
In your code, the best practice is to keep your imports listed alphabetically and remove unused imports. To do this press Help on the top toolbar, type in optimize imports, and click on Optimize Imports.

You could open the Optimize Imports directly from the menu: Code > Optimize Imports. Using Help's search option will help you locate a menu item if you don't remember where it is.

# Solution Code
```kotlin
package com.example.greetingcard

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.ui.graphics.Color
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import com.example.greetingcard.ui.theme.GreetingCardTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            GreetingCardTheme {
                // A surface container using the 'background' color from the theme
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                    Greeting("Android")
                }
            }
        }
    }
}

@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Surface(color = Color.Cyan) {
        Text(text = "Hi, my name is $name!", modifier = modifier.padding(24.dp))
    }
}

@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    GreetingCardTheme {
        Greeting("Meghan")
    }
}
```
