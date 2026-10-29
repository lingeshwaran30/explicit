# 4. Develop an Android Application Implementing Explicit and Implicit Intents

[← Back to Index](README.md)

## Subject: Intents, Events and Listeners

## Project Name
`IntentDemo`

## Aim
To develop an Android application that demonstrates **Explicit Intents** and **Implicit Intents**.

## 1. File Name: `activity_main.xml`

**File Path:** `app/src/main/res/layout/activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:id="@+id/main"
    android:padding="20dp">

    <Button
        android:id="@+id/btnExplicit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Explicit Intent" />

    <Button
        android:id="@+id/btnImplicit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Implicit Intent"
        android:layout_marginTop="20dp" />

</LinearLayout>
```

## 2. Create the Second Activity

Follow these steps in Android Studio:

1. Right-click your Java package, `com.example.intentdemo`.
2. Select **New → Activity → Empty Views Activity** (the option may be named **Empty Views Activity** or similar, depending on your Android Studio version).
3. Set the Activity Name to `SecondActivity`.
4. Click **Finish**.

Android Studio should create `SecondActivity.java` and `activity_second.xml`.

## 3. File Name: `activity_second.xml`

**File Path:** `app/src/main/res/layout/activity_second.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/main"
    android:gravity="center">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome to Second Activity"
        android:textSize="24sp" />

</LinearLayout>
```

## 4. File Name: `MainActivity.java`

**File Path:** `app/src/main/java/com/example/intentdemo/MainActivity.java`

```java
package com.example.intentdemo;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Button btnExplicit, btnImplicit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnExplicit = findViewById(R.id.btnExplicit);
        btnImplicit = findViewById(R.id.btnImplicit);

        // Explicit Intent
        btnExplicit.setOnClickListener(v -> {
            Intent intent = new Intent(
                    MainActivity.this,
                    SecondActivity.class
            );

            startActivity(intent);
        });

        // Implicit Intent
        btnImplicit.setOnClickListener(v -> {
            Intent intent = new Intent(
                    Intent.ACTION_VIEW,
                    Uri.parse("https://www.google.com")
            );

            startActivity(intent);
        });
    }
}
```

## 5. File Name: `SecondActivity.java`

**File Path:** `app/src/main/java/com/example/intentdemo/SecondActivity.java`

```java
package com.example.intentdemo;

import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);
    }
}
```

## 6. AndroidManifest.xml

Ensure that `SecondActivity` is declared in your app's manifest. Android Studio normally adds this declaration when you create the activity.

**File Path:** `app/src/main/AndroidManifest.xml`

Inside the `<application>` element, ensure you have:

```xml
<activity
    android:name=".SecondActivity"
    android:exported="false" />
```

Do not add a duplicate declaration if Android Studio has already created it. Keep your existing launcher activity configuration unchanged.

## 7. Explanation

### Explicit Intent

- An Explicit Intent specifies the exact activity to open.
- When the user clicks the **Explicit Intent** button, `SecondActivity` opens.
- The second screen displays the message **Welcome to Second Activity**.

### Implicit Intent

- An Implicit Intent specifies an action rather than a particular application component.
- When the user clicks the **Implicit Intent** button, the app requests an application capable of viewing `https://www.google.com`.
- Android typically opens the link in a web browser. If no suitable application can handle the intent, Android may report an activity-not-found error.

## 8. Expected Output

1. The main screen displays two buttons: **Explicit Intent** and **Implicit Intent**.
2. Clicking **Explicit Intent** opens the second activity.
3. The second activity displays **Welcome to Second Activity**.
4. Returning to the main screen and clicking **Implicit Intent** opens the Google website in a compatible browser or application.

## 9. Result

Thus, an Android application demonstrating **Explicit and Implicit Intents** was developed successfully.

## 10. Upload the Project to GitHub

1. Open your project folder.
2. Create or update the `README.md` file with this content.
3. Save the file.
4. Open your GitHub repository.
5. Commit and push your changes.

### Git Commands

```bash
git add README.md
git commit -m "Add Explicit and Implicit Intents practical"
git push
```
