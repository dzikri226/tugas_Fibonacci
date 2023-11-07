# tugas_Fibonacci
# Nama           : M.Dzikri Hidayat 
### NIM          : 312210136
### Kelas        : TI.22 A1
## Matkul        : pemograman mobile 1 
### Dosen Pengampu : Donny Maulana S.Kom., M.M.S.I

# ProjectFibonacci

# Tugas Pertemuan 6
![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/fd32d3c2-755f-4638-ac8a-a79fa56f78c6)

# Langkah-Langkah

1. Hal yang pertama kita harus lakukan adalan membuat project barunya terlebih dahulu dengan nama project "tugasenam"

2. Kemudian pada layout activity_main kita tambahkan 3 "button" dan 1 "textview" seperti berikut

3. Pada button yang pertama itu berfungsi sebagai tombol "Toast" yang nantinya ketika kita tekan akan muncul sebuah toast message yaitu "Bilangan Fibonacci". Dan button yang kedua, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya. lalu kemudian yang terakhir Textview, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.

4. langkah yang perlu kita lakukan selajutnya adalah masukkan codingan didalam activity_fibonacci seperti berikut
    * activity_fibonacci.xml
  <?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button_toast"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:background="@color/colorPrimary"
        android:onClick="showToast"
        android:textColor="@android:color/white"
        android:text="@string/button_label_toast"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize"/>


    <Button
        android:id="@+id/button_count"
        android:layout_width="186dp"
        android:layout_height="51dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="4dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.061"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_kembali"
        android:layout_width="179dp"
        android:layout_height="53dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="4dp"
        android:background="@color/colorPrimary"
        android:onClick="Restart"
        android:text="@string/button_label_kembali"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.97"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="@string/count_initial_values"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_toast"
        tools:ignore="RtlCompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
       
   
  * strings.xml
 
        <resources>
    <string name="app_name">Fibonacci</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="button_label_kembali">Restart</string>
    <string name="count_initial_values">1</string>
    <string name="toast_message">Bilangan Fibonacci</string>
    <string name="count_initial_value">1</string>
</resources>
    
* colors.xml
   
            <?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="color1">1</color>
    <color name="color2">2</color>
    <color name="color3">3</color>
</resources>

  
  # Tampilan Design
![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/c2581013-ef3e-4725-b3f0-56f67adbcd7a)


 # MainActivity.java

  Dalam MainActivity.java ini berisi semua codingan untuk fungsi-fungsinya. Seperti, fungsi untuk 
  tombol-tombol dan rumus bilangan fibonaccinya.
      package com.tugasenam;
    
   package com.fibonacci;

import android.annotation.SuppressLint;
import android.app.AlertDialog;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private TextView showCount;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private int limit = -1; // Inisialisasi limit dengan nilai default

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_fibonacci);

        showCount = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            showCount.setText("0");
        } else if (count == 1) {
            showCount.setText("1");
        } else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                showCount.setText(getString(R.string.count_initial_value));
            } else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                // Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.color1; // Warna default
                switch (count % 3) {
                    case 1:
                        colorResId = R.color.color1; // Warna merah
                        break;
                    case 2:
                        colorResId = R.color.color2; // Warna hijau
                        break;
                    case 0:
                        colorResId = R.color.color3; // Warna biru
                        break;
                }
                showCount.setTextColor(getResources().getColor(colorResId));
                showCount.setText(String.valueOf(fibCurrent));
            }
        }

        count++;
    }

    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        limit = -1;
        showCount.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set limit bilangan yang ditampilkan :");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", (dialog, which) -> {
            String limitStr = input.getText().toString();
            limit = Integer.parseInt(limitStr);
        });

        builder.setNegativeButton("Cancel", (dialog, which) -> dialog.cancel());

        builder.show();
    }
}

    # Hasil Run

Untuk run app ini saya menggunakan hp android . Berikut ini adalah tampilan dari aplikasi yang telah saya buat :

* Tombol Toast ditekan, maka akan muncul message "Bilangan Fibonacci" seperti berikut
* # Hasil Run

Untuk run app ini saya menggunakan hp android . Berikut ini adalah tampilan dari aplikasi yang telah saya buat :
![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/9af8d6a7-318c-4472-aee8-e03a7990e26b)

![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/f4a02527-74af-49f1-a8b5-5ae03bb44c0e)
![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/669fe9ea-2a7f-46b9-9856-41380dbfdd68)


* Tombol Count ditekan, maka angka "1" akan berubah menjadi





