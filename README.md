# PEMOGRAMAN MOBILE

NAMA      : Ririn Nofrima

NIM       : 312210025

KELAS     : TI.22.B1

**Membuat tombol yang setiap diklik dapat bertambah angkanya, namun dengan urutan angka fibonacci, lalu lengkapi dengan fitur toast**  

link video aplikasi yang di jalankan 

![backhand-index-pointing-down_1f447](https://github.com/ririn27/UTS-/assets/115934294/6b5b20e5-b9a6-45af-90d3-cb36b7495ca7)

https://youtu.be/lsaJa-Uzh5Q?si=b_D-VOy5igGBxHsR


![backhand-index-pointing-down_1f447](https://github.com/ririn27/UTS-/assets/115934294/d91e47ef-e2db-499d-a93e-26037ae78031)


# Code Activitymain.java ( Relativ Layout )

![backhand-index-pointing-down_1f447](https://github.com/ririn27/UTS-/assets/115934294/d91e47ef-e2db-499d-a93e-26037ae78031)

package id.co.belajarandroid;

import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;

import android.os.Bundle;

import android.view.View;

import android.widget.Button;

import android.widget.TextView;

import android.widget.Toast;


public class MainActivity extends AppCompatActivity {

    private int mCount = 0;
    
    private int mCountFibo = 0;
    
    private TextView mShowCount;
    
    private TextView mShowCountFibo;
    
    private Button buttonToast;
    
    private Button buttonHitung;
    
    private Button buttonReset;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.toast_activity);
        mShowCount = (TextView) findViewById(R.id.textViewNumber);
        mShowCountFibo = (TextView) findViewById(R.id.textViewNumberFibo);
        buttonToast = (Button) findViewById(R.id.button_toast);
        buttonHitung = (Button) findViewById(R.id.button_hitung);
        buttonReset = (Button) findViewById(R.id.button_reset);

        buttonHitung.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                hitungIncrement(view);
            }
        });
        buttonToast.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                showToast(view);
            }
        });
        buttonReset.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                resetCountDanFibo(view);
            }
        });
    }
    public void showToast(View view){
        Toast toast = Toast.makeText(this, "Berhasil diklik", Toast.LENGTH_SHORT);
        toast.show();
    }



    public void hitungIncrement(View view){
        mCount++;
        int Fibo = hitungFibonacci(mCount);
        mCountFibo = Fibo;
        if(mShowCount != null && mShowCountFibo != null){
            mShowCount.setText(Integer.toString(mCount));
            mShowCountFibo.setText(Integer.toString(mCountFibo));
        }

    }
    public int hitungFibonacci(int n){
        if(n <= 1){
            return n;
        }
        int prev = 0;
        int current = 1;
        for(int i = 2; i<= n; i++){
            int next = prev + current;
            prev = current;
            current = next;
        }
        return current;
    }
    public void resetCountDanFibo(View view){
        mCount = 0;
        mCountFibo = 0;
        mShowCount.setText(Integer.toString(mCount));
        mShowCountFibo.setText(Integer.toString(mCountFibo));
    }
}

# Toast Activity

![backhand-index-pointing-down_1f447](https://github.com/ririn27/UTS-/assets/115934294/6b5b20e5-b9a6-45af-90d3-cb36b7495ca7)

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@color/pink"
        android:gravity="center"
        android:orientation="vertical"
        android:paddingLeft="40dp"
        android:paddingRight="40dp">


        <TextView
            android:id="@+id/textView3"
            android:layout_marginBottom="100dp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Belajar Toast!"
            android:textAlignment="center"
            android:textSize="30sp"/>

        <TextView
            android:id="@+id/textView2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Increment"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textViewNumber"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Fibonacci"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textViewNumberFibo"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textAlignment="center"
            android:textColor="@color/black"
            android:textFontWeight="600"
            android:textSize="24sp" />


    </LinearLayout>

    <Button
        android:id="@+id/button_toast"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentLeft="true"
        style="@style/Widget.AppCompat.Button"
        android:text="Toast"/>

    <Button
        android:id="@+id/button_reset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:layout_marginBottom="10dp"
        android:backgroundTint="@color/Kuning"
        android:text="Reset"
        android:textAlignment="center"
        android:textColor="@color/red" />

    <Button
        android:id="@+id/button_hitung"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:backgroundTint="@color/SteelBlue"
        android:layout_marginRight="10dp"
        android:textColor="@color/white"
        android:text="Hitung"/>


</RelativeLayout>

