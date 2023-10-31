# tugas_Fibonacci
# Nama           : M.Dzikri Hidayat 
### NIM            : 312210136
### Kelas          : TI.22 A1
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
            android:id="@+id/button_limit"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginEnd="8dp"
            android:layout_marginStart="8dp"
            android:layout_marginTop="8dp"
            android:background="@color/colorPrimary"
            android:onClick="setLimit"
            android:textColor="@android:color/white"
            android:text="@string/enter_fibonacci_limit"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            tools:ignore="UsingOnClickInXml,VisualLintButtonSize"/>
    
    
        <Button
            android:id="@+id/button_count"
            android:layout_width="190dp"
            android:layout_height="48dp"
            android:layout_marginStart="8dp"
            android:layout_marginEnd="8dp"
            android:layout_marginBottom="8dp"
            android:background="@color/colorPrimary"
            android:onClick="countUp"
            android:text="@string/button_label_count"
            android:textColor="@android:color/white"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
    
        <Button
            android:id="@+id/button_finish"
            android:layout_width="190dp"
            android:layout_height="48dp"
            android:layout_marginStart="8dp"
            android:layout_marginEnd="8dp"
            android:layout_marginBottom="8dp"
            android:background="@color/colorPrimary"
            android:onClick="back1"
            android:text="@string/button_label_finish"
            android:textColor="@android:color/white"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="1.0"
            app:layout_constraintStart_toStartOf="parent"
            tools:ignore="UsingOnClickInXml" />
    
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
            android:text="@string/count_initial_value"
            android:textAlignment="center"
            android:textColor="@color/colorPrimary"
            android:textSize="160sp"
            android:textStyle="bold"
            app:layout_constraintBottom_toTopOf="@id/button_count"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@id/button_limit"
            tools:ignore="RtlCompat" />
    
        </androidx.constraintlayout.widget.ConstraintLayout>
   
  * strings.xml
 
        <resources>
          <string name="app_name">Tugasenam</string>
          <string name="button_label_count">Count</string>
          <string name="count_initial_value"> </string>
          <string name="button_label_finish">Reset</string>
          <string name="enter_fibonacci_limit">Masukan Limit Angka</string>
        </resources>
    
* colors.xml
   
            <?xml version="1.0" encoding="utf-8"?>
            <resources>
                <color name="black">#FF000000</color>
                <color name="white">#FFFFFFFF</color>
                <color name="colorPrimary">#3F5185</color>
                <color name="colorPrimaryDark">#303F9F</color>
                <color name="colorAccent">#FF4081</color>
            </resources>

  
  # Tampilan Design
![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/62f4ce79-1eee-45a4-957b-3c609e3e7b34)

 # MainActivity.java

  Dalam MainActivity.java ini berisi semua codingan untuk fungsi-fungsinya. Seperti, fungsi untuk 
  tombol-tombol dan rumus bilangan fibonaccinya.
      package com.tugasenam;
    
    import android.app.AlertDialog;
    import android.content.DialogInterface;
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
                    showCount.setText(String.valueOf(fibCurrent));
                }
            }
    
            count++;
        }
    
        public void back1(View view) {
            count = 1;
            fibNMinus1 = 1;
            fibNMinus2 = 0;
            showCount.setText(getString(R.string.count_initial_value));
        }
    
        public void setLimit(View view) {
            // Create and display a dialog to set the limit
            AlertDialog.Builder builder = new AlertDialog.Builder(this);
            builder.setTitle("Set Limit");
    
            final EditText input = new EditText(this);
            input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
            builder.setView(input);
    
            builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
                @Override
                public void onClick(DialogInterface dialog, int which) {
                    // Get the limit from the input and set it for calculations
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

    # Hasil Run

Untuk run app ini saya menggunakan hp android . Berikut ini adalah tampilan dari aplikasi yang telah saya buat :

* Tombol Toast ditekan, maka akan muncul message "Bilangan Fibonacci" seperti berikut
* # Hasil Run

Untuk run app ini saya menggunakan hp android . Berikut ini adalah tampilan dari aplikasi yang telah saya buat :
![image](https://github.com/dzikri226/tugas_Fibonacci/assets/122372727/76f1df29-3913-4a94-8975-3bc65be8e2e9)
* Tombol Count ditekan, maka angka "1" akan berubah menjadi





