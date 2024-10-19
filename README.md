# EX_5_SIMPLE-CALCULATOR_GIT


## AIM:
To develop a program to create a simple calculator using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min. required Artic Fox)


## ALGORITHM:
Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as SMSIntent and click Next.

Step 3: Select the Minimum SDK below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally, click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Perform the Calculator Operation in MainActivity.java

Step 7: Save and run the application.


## Program:
```
/*
Program to create simple calculator using Android Studio.
Developed by: MERCY A
RegisterNumber: 212223110027
*/
```

## MainActivity.java:

```java
package com.example.myapp3;
//check package name


import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.view.View;
import android.widget.EditText;


public class MainActivity extends AppCompatActivity {

    private EditText etNumber1, etOperator, etNumber2;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etNumber1 = findViewById(R.id.et_number1);
        etOperator = findViewById(R.id.et_operator);
        etNumber2 = findViewById(R.id.et_number2);
    }

    public void newsScreen(View view) {
        String number1 = etNumber1.getText().toString();
        String operator = etOperator.getText().toString();
        String number2 = etNumber2.getText().toString();

        Intent i = new Intent(this, MainActivity2.class);
        i.putExtra("number1", number1);
        i.putExtra("operator", operator);
        i.putExtra("number2", number2);
        startActivity(i);
    }
}

```

## MainActivity2.java:
```java
package com.example.myapp3;
//check package name

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.view.View;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {

    private TextView tvResult;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        tvResult = findViewById(R.id.tv_result);


        Intent intent = getIntent();
        String number1 = intent.getStringExtra("number1");
        String operator = intent.getStringExtra("operator");
        String number2 = intent.getStringExtra("number2");


        double num1 = Double.parseDouble(number1);
        double num2 = Double.parseDouble(number2);
        double result = 0;

        switch (operator) {
            case "+":
                result = num1 + num2;
                break;
            case "-":
                result = num1 - num2;
                break;
            case "*":
                result = num1 * num2;
                break;
            case "/":
                result = num1 / num2;
                break;

            default:
                tvResult.setText("Error: Invalid operator");
                return;
        }


        tvResult.setText("Result: " + result);
    }

    public void homeScreen(View view) {
        Intent i = new Intent(this, MainActivity.class);
        startActivity(i);
    }
}


```

## activity_main.xml:
```java
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv_title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="WELCOME!!"
        android:textAlignment="center"
        android:textSize="28sp"
        app:layout_constraintBottom_toTopOf="@id/et_number1"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.7" />

    <EditText
        android:id="@+id/et_number1"
        android:layout_width="311dp"
        android:layout_height="50dp"
        android:layout_marginTop="84dp"
        android:hint="Number 1"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.44"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/tv_title"
        app:layout_constraintWidth_percent="0.7" />

    <EditText
        android:id="@+id/et_operator"
        android:layout_width="293dp"
        android:layout_height="51dp"
        android:layout_marginTop="32dp"
        android:hint="Operator +, -, *,/"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.372"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/et_number1"
        app:layout_constraintWidth_percent="0.7" />

    <EditText
        android:id="@+id/et_number2"
        android:layout_width="299dp"
        android:layout_height="57dp"
        android:layout_marginTop="40dp"
        android:hint="Number 2"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.392"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/et_operator"
        app:layout_constraintWidth_percent="0.7" />

    <Button
        android:id="@+id/btn_calculate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="64dp"
        android:onClick="newsScreen"
        android:text="Calculate"
        android:shadowColor="@color/black"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.465"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/et_number2" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

## activity_main2.xml:
```java
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/tv_result"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Result"
        android:textAlignment="center"
        android:textSize="28sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintBottom_toTopOf="@id/imageButton" />

    <ImageButton
        android:id="@+id/imageButton"
        android:layout_width="88dp"
        android:layout_height="54dp"
        android:onClick="homeScreen"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/tv_result"
        app:srcCompat="?attr/actionModeCloseDrawable"
        android:contentDescription="@string/app_name"
        />


</androidx.constraintlayout.widget.ConstraintLayout>


```

## AndroidManifest.xml:
```java
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyApp3"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name=".MainActivity2"
            android:exported="true">
        </activity>
    </application>

</manifest>

```
## Output:
![WhatsApp Image 2024-10-19 at 11 06 27_6972feef](https://github.com/user-attachments/assets/6018c135-43c4-417e-b065-ef9d1e14ae68)

![WhatsApp Image 2024-10-19 at 11 06 17_2dd20106](https://github.com/user-attachments/assets/916e70b4-1791-4712-872e-035965be9dda)


## Result:
Thus a Simple Android Application to create a calculator using Android Studio was developed and executed successfully.
