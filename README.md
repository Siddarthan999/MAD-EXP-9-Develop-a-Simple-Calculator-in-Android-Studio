# MAD-EXP-9-Develop-a-Simple-Calculator-in-Android-Studio

## AIM:

To develop a program to develop a simple calculator in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Display the calculator operation in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the text “calculator operation”.
Developed by: N.SIDDARTHAN
Registration Number: 212221040154
*/
```
activity_main.xml :
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/txt2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="Second Number"
        android:inputType="numberDecimal"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.271"
        tools:ignore="SpeakableTextPresentCheck,TouchTargetSizeCheck" />

    <EditText
        android:id="@+id/txt1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="First Number"
        android:inputType="numberDecimal"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.185"
        tools:ignore="TouchTargetSizeCheck,SpeakableTextPresentCheck" />

    <TextView
        android:id="@+id/result"
        android:layout_width="404dp"
        android:layout_height="24dp"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.366" />

    <Button
        android:id="@+id/btnsubs"
        android:layout_width="80dp"
        android:layout_height="50dp"
        android:text="-"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.359"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.466" />

    <Button
        android:id="@+id/btndiv"
        android:layout_width="80dp"
        android:layout_height="50dp"
        android:text="/"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.9"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.466" />

    <Button
        android:id="@+id/btnadd"
        android:layout_width="80dp"
        android:layout_height="50dp"
        android:text="+"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.087"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.466" />

    <Button
        android:id="@+id/btnmult"
        android:layout_width="80dp"
        android:layout_height="50dp"
        android:text="*"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.628"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.466" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SIMPLE CALCULATOR"
        android:textColor="@color/black"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.073" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity.java :
```
package com.example.simplecalculator;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;
public class MainActivity extends AppCompatActivity {
    Button btnadd,btnsubs,btnmult,btndiv;
    EditText txt1,txt2;
    TextView result;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnadd=findViewById(R.id.btnadd);
        btnsubs=findViewById(R.id.btnsubs);
        btndiv=findViewById(R.id.btndiv);
        btnmult=findViewById(R.id.btnmult);

        txt1=findViewById(R.id.txt1);
        txt2=findViewById(R.id.txt2);

        result=findViewById(R.id.result);

        btnadd.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Checking Input First Is Blank Or Not
                if (txt1.getText().toString().equals("")) {
                    // Showing Toast (Message)
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                } else if (txt2.getText().toString().equals("")) {
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                }

                // Both Inputs Are Not Blank , Starting Calculation
                else {
                    float a, b, c;
                    a = Float.parseFloat(txt1.getText().toString());
                    b = Float.parseFloat(txt2.getText().toString());
                    c = a + b; // Using Third Variable To Store Output Value
                    result.setText("The Addition Result Is " + c);

                }

            }
        });

        btnsubs.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Checking Input First Is Blank Or Not
                if (txt1.getText().toString().equals("")) {
                    // Showing Toast (Message)
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                } else if (txt2.getText().toString().equals("")) {
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                }

                // Both Inputs Are Not Blank , Starting Calculation
                else {
                    float a, b, c;
                    a = Float.parseFloat(txt1.getText().toString());
                    b = Float.parseFloat(txt2.getText().toString());
                    c = a - b; // Using Third Variable To Store Output Value
                    result.setText("The Subtraction Result Is " + c);

                }
            }
        });
        btnmult.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Checking Input First Is Blank Or Not
                if (txt1.getText().toString().equals("")) {
                    // Showing Toast (Message)
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                } else if (txt2.getText().toString().equals("")) {
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                }

                // Both Inputs Are Not Blank , Starting Calculation
                else {
                    float a, b, c;
                    a = Float.parseFloat(txt1.getText().toString());
                    b = Float.parseFloat(txt2.getText().toString());
                    c = a*b; // Using Third Variable To Store Output Value
                    result.setText("The Multiplication Result Is " + c);

                }
            }
        });
        btndiv.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Checking Input First Is Blank Or Not
                if (txt1.getText().toString().equals("")) {
                    // Showing Toast (Message)
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                } else if (txt2.getText().toString().equals("")) {
                    Toast.makeText(MainActivity.this, "Please Enter Number", Toast.LENGTH_SHORT).show();
                }

                // Both Inputs Are Not Blank , Starting Calculation
                else {
                    float a, b, c;
                    a = Float.parseFloat(txt1.getText().toString());
                    b = Float.parseFloat(txt2.getText().toString());
                    c = a/b; // Using Third Variable To Store Output Value
                    result.setText("The Division Result Is " + c);

                }
            }
        });
    }
}
```
## OUTPUT

![image](https://github.com/Siddarthan999/MAD-EXP-9-Develop-a-Simple-Calculator-in-Android-Studio/assets/91734840/ebe5fd82-aeae-469a-995d-855b091ec8c2)
![image](https://github.com/Siddarthan999/MAD-EXP-9-Develop-a-Simple-Calculator-in-Android-Studio/assets/91734840/f0b50fc7-d5e5-4458-9aef-9796100aa6f4)
![image](https://github.com/Siddarthan999/MAD-EXP-9-Develop-a-Simple-Calculator-in-Android-Studio/assets/91734840/6b8859db-d384-4259-b1e2-7b8251df1d9a)
![image](https://github.com/Siddarthan999/MAD-EXP-9-Develop-a-Simple-Calculator-in-Android-Studio/assets/91734840/dc5bb770-2d87-4b68-91d3-1dab1621c271)

## RESULT
Thus, a Simple Android Application develop a program to create simple calculator in Android Studio is developed and executed successfully.
