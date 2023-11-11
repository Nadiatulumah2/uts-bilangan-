# uts-bilangan-deret fibonnaci
### Nama           :  Nadiatul umah ###
### NIM            : 312210500 ###
### Kelas          : TI.22.A5 ### 
### Dosen Pengampu : Donny Maulana S.Kom., M.M.S.I

![gambar tugas](![1](https://github.com/Nadiatulumah2/uts-bilangan-/assets/129835302/afb2272f-a945-4c6e-92eb-6473397c5a3a)

# Langkah-Langkah

1. Hal yang pertama kita harus lakukan adalan membuat project barunya terlebih dahulu dengan nama project "tugasenam"

2. Kemudian pada layout activity_main kita tambahkan 3 "button" dan 1 "textview" seperti berikut



3. Pada button yang pertama itu berfungsi sebagai tombol "Toast" yang nantinya ketika kita tekan akan muncul sebuah toast message yaitu "Bilangan Fibonacci". Dan button yang kedua, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya. lalu kemudian yang terakhir Textview, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.

4. langkah yang perlu kita lakukan selajutnya adalah masukkan codingan didalam activity_fibonacci seperti berikut
# activity_toast.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/setLimit"
        android:layout_width="421dp"
        android:layout_height="48dp"
        android:background="@color/colorPrimary"
        android:onClick="setLimit"
        android:text="Set limit"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button2"
        android:layout_width="176dp"
        android:layout_height="45dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="411dp"
        android:layout_height="636dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="@string/count_initial_value"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/button2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.571"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/setLimit"
        app:layout_constraintVertical_bias="0.0"
        tools:ignore=",Rtlcompat" />

    <Button
        android:id="@+id/button"
        android:layout_width="189dp"
        android:layout_height="45dp"
        android:background="@color/colorPrimary"
        android:onClick="Reset"
        android:text="Back"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toEndOf="@+id/button2"
        app:layout_constraintTop_toBottomOf="@+id/show_count"
        app:layout_constraintVertical_bias="1.0" />

</androidx.constraintlayout.widget.ConstraintLayout>
6. Strings.xml
<resources>
    <string name="app_name">Fibonacci</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">0</string>
    <string name="coast_message">Hello Toast</string>
    <string name="set_Limit">Set limit</string>
    <string name="Reset">Reset</string>
</resources>
7.Colors.xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
</resources>
#Java class
Pada Java class MainActivity.java berisi semua coding untuk menjalankan aplikasi. Seperti fungsi untuk tombol-tombol, dialog set limit, warna yang berbeda pada setiap angka, lalu warna background yang bisa berubah dan rumus bilangan fibonacci.
package com.example.deretfebonnaci;

import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;


public class MainActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private int limit = -1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        show_count = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("1");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                count = 1;
                fibNMinus1 = 0;
                fibNMinus2 = 1;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                int colorResId = R.color.orange;
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.orange;
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda;
                        break;
                    case 3:
                        colorResId = R.color.purple;
                        break;
                    case 4:
                        colorResId = R.color.salem;
                        break;
                    case 5:
                        colorResId = R.color.birumuda;
                        break;
                    case 6 :
                        colorResId = R.color.kuning;
                        break;
                    case 7:
                        colorResId = R.color.hijau;
                        break;
                    case 8:
                        colorResId = R.color.cream;
                        break;
                    case 9:
                        colorResId = R.color.pink;
                        break;
                    case 10:
                        colorResId = R.color.biru;
                        break;
                    case 11:
                        colorResId = R.color.colorAccent;
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
                show_count.setBackgroundColor(Color.DKGRAY);
            }
        }

        count++;
    }

    public void Reset(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });

        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });

        builder.show();
    }
}
#Tampilan Design
![image](https://github.com/Nadiatulumah2/uts-bilangan-/assets/129835302/bc818d5f-b7c7-48c6-8a78-c8409d02b590)
#Hasil Run


https://github.com/Nadiatulumah2/uts-bilangan-/assets/129835302/2d7ba801-a797-462a-af4d-73cdacaa5d55





