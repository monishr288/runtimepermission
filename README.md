# Ex.No:6 Create a simple application to request storage and camera permission at RunTime using android studio.


## AIM:

To develop a simple application for RunTime Permission in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Giraffe)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as runtimepermission and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display process of runtimepermission in android mobile devices.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the process of runtimepermission in android mobile devices”.
Developed by: MONISH R
Registeration Number : 212223220061
*/
```
## MainActivity.java
```
package com.example.runtime;


import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

import android.content.pm.PackageManager;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private Button storage, camera;

    // Permission codes
    private static final int CAMERA_PERMISSION_CODE = 100;
    private static final int STORAGE_PERMISSION_CODE = 101;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        storage = findViewById(R.id.button);
        camera = findViewById(R.id.button2);

        // Storage button click
        storage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                checkPermission(
                        android.Manifest.permission.WRITE_EXTERNAL_STORAGE,
                        STORAGE_PERMISSION_CODE);
            }
        });

        // Camera button click
        camera.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                checkPermission(
                        android.Manifest.permission.CAMERA,
                        CAMERA_PERMISSION_CODE);
            }
        });
    }

    // Method to check and request permission
    public void checkPermission(String permission, int requestCode) {

        if (ContextCompat.checkSelfPermission(
                MainActivity.this,
                permission)
                == PackageManager.PERMISSION_DENIED) {

            ActivityCompat.requestPermissions(
                    MainActivity.this,
                    new String[]{permission},
                    requestCode);

        } else {

            Toast.makeText(
                    MainActivity.this,
                    "Permission already granted",
                    Toast.LENGTH_SHORT).show();
        }
    }

    // Handling permission result
    @Override
    public void onRequestPermissionsResult(
            int requestCode,
            @NonNull String[] permissions,
            @NonNull int[] grantResults) {

        super.onRequestPermissionsResult(
                requestCode,
                permissions,
                grantResults);

        if (requestCode == CAMERA_PERMISSION_CODE) {

            if (grantResults.length > 0
                    && grantResults[0]
                    == PackageManager.PERMISSION_GRANTED) {

                Toast.makeText(
                        MainActivity.this,
                        "Camera Permission Granted",
                        Toast.LENGTH_SHORT).show();

            } else {

                Toast.makeText(
                        MainActivity.this,
                        "Camera Permission Denied",
                        Toast.LENGTH_SHORT).show();
            }

        } else if (requestCode == STORAGE_PERMISSION_CODE) {

            if (grantResults.length > 0
                    && grantResults[0]
                    == PackageManager.PERMISSION_GRANTED) {

                Toast.makeText(
                        MainActivity.this,
                        "Storage Permission Granted",
                        Toast.LENGTH_SHORT).show();

            } else {

                Toast.makeText(
                        MainActivity.this,
                        "Storage Permission Denied",
                        Toast.LENGTH_SHORT).show();
            }
        }
    }
}
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!-- Storage Permission Button -->

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Storage"
        android:textSize="18sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintVertical_bias="0.35" />

    <!-- Camera Permission Button -->

    <Button
        android:id="@+id/button2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Camera"
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@id/button"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="30dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>

<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.example.runtime">

    <!-- Permissions -->

    <uses-permission android:name="android.permission.CAMERA" />

    <uses-permission
        android:name="android.permission.READ_EXTERNAL_STORAGE" />

    <uses-permission
        android:name="android.permission.WRITE_EXTERNAL_STORAGE"
        tools:ignore="ScopedStorage" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Runtime"
        tools:targetApi="31">

        <!-- Main Activity -->

        <activity
            android:name=".MainActivity"
            android:exported="true">

            <intent-filter>

                <action android:name="android.intent.action.MAIN" />

                <category
                    android:name="android.intent.category.LAUNCHER" />

            </intent-filter>

        </activity>

    </application>

</manifest>
```

## OUTPUT


<img width="1759" height="979" alt="image" src="https://github.com/user-attachments/assets/613418c7-5df7-4e85-9dc1-f31ded27a378" />
<img width="1745" height="941" alt="image" src="https://github.com/user-attachments/assets/2e814d5f-b47e-4950-bf5f-db175afd5afc" />


## RESULT
Thus a Simple Android Application to request storage and camera permission at RunTime in Android Studio is developed and executed successfully.
