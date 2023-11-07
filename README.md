# PEMOGRAMAN MOBILE

NAMA      : Ririn Nofrima

NIM       : 312210025

KELAS     : TI.22.B1

**Membuat tombol yang setiap diklik dapat bertambah angkanya, namun dengan urutan angka fibonacci, lalu lengkapi dengan fitur toast**  

link video aplikasi yang di jalankan 

![backhand-index-pointing-down_1f447](https://github.com/ririn27/UTS-/assets/115934294/6b5b20e5-b9a6-45af-90d3-cb36b7495ca7)

https://youtu.be/lsaJa-Uzh5Q?si=b_D-VOy5igGBxHsR


![backhand-index-pointing-down_1f447](https://github.com/ririn27/UTS-/assets/115934294/d91e47ef-e2db-499d-a93e-26037ae78031)


# Code Activitymain.java

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
