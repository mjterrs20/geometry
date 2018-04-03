# geometry
belajar ngoding
Layout

// 1. activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.bso.android.geometryapp.MainActivity">

    <LinearLayout
        android:layout_height="0dp"
        android:layout_width="match_parent"
        android:orientation="horizontal"
        android:layout_weight="1">

        <Button
            android:id="@+id/btn_persegi"
            android:text="@string/persegi"
            android:textColor="@color/putih"
            android:textSize="30sp"
            android:background="@color/colorPrimaryDark"
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="match_parent" />

        <Button
            android:id="@+id/btn_persegipanjang"
            android:text="@string/persegi_panjang"
            android:textColor="@color/colorPrimaryDark"
            android:textSize="30sp"
            android:background="@color/putih"
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="match_parent" />

    </LinearLayout>

    <LinearLayout
        android:layout_height="0dp"
        android:layout_width="match_parent"
        android:orientation="horizontal"
        android:layout_weight="1">

        <Button
            android:id="@+id/btn_lingkaran"
            android:onClick="lingkaran"
            android:text="@string/lingkaran"
            android:textColor="@color/colorPrimaryDark"
            android:textSize="30sp"
            android:background="@color/putih"
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="match_parent" />

        <Button
            android:id="@+id/btn_segitiga"
            android:onClick="segitiga"
            android:text="@string/segitiga"
            android:textColor="@color/putih"
            android:textSize="30sp"
            android:background="@color/colorPrimaryDark"
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="match_parent" />

    </LinearLayout>

</LinearLayout>

// 2. MainActivity.java

package com.bso.android.geometryapp;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {
    Button btnpersegi, btnpersegipanjang, btnlingkaran, btnsegitiga;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnpersegi=findViewById(R.id.btn_persegi);
        btnpersegipanjang=findViewById(R.id.btn_persegipanjang);
        btnlingkaran=findViewById(R.id.btn_lingkaran);
        btnsegitiga=findViewById(R.id.btn_segitiga);

        btnpersegi.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(MainActivity.this, PersegiActivity.class);
                startActivity(intent);
            }
        });

        btnpersegipanjang.setOnClickListener(persegipanjang);
    }

    public View.OnClickListener persegipanjang = new View.OnClickListener() {
        @Override
        public void onClick(View view) {
            Intent intent = new Intent(MainActivity.this, PersegiPanjangActivity.class);
            startActivity(intent);
        }
    };

    public void lingkaran(View v){
        Intent intent = new Intent(MainActivity.this, LingkaranActivity.class);
        startActivity(intent);
    }

    public void segitiga(View v){
        Intent intent = new Intent(MainActivity.this, SegitigaSikusikuActivity.class);
        startActivity(intent);
    }


}


// 3. activity_persegi.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.bso.android.geometryapp.PersegiActivity">

    <TextView
        android:text="@string/persegi"
        android:textColor="@color/putih"
        android:textSize="25sp"
        android:textAlignment="center"
        android:padding="10dp"
        android:background="@color/colorPrimaryDark"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

        <RadioGroup
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <RadioButton
                android:id="@+id/rb_keliling"
                android:onClick="Pilih"
                android:checked="true"
                android:text="@string/keliling"
                android:layout_marginLeft="50dp"
                android:layout_width="0dp"
                android:layout_weight="1"
                android:layout_height="wrap_content" />

            <RadioButton
                android:id="@+id/rb_luas"
                android:onClick="Pilih"
                android:text="@string/luas"
                android:layout_marginLeft="50dp"
                android:layout_width="0dp"
                android:layout_weight="1"
                android:layout_height="wrap_content" />

        </RadioGroup>

    <EditText
        android:id="@+id/et_sisi"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="numberDecimal"
        android:hint="sisi"
        android:textSize="30sp"
        android:padding="20dp"
        android:textAlignment="center"
        />

    <Button
        android:id="@+id/btn_hasil"
        android:onClick="Hasil"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="HASIL"
        android:layout_gravity="center"/>

    <TextView
        android:id="@+id/tv_hasil"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="0"
        android:textColor="#000000"
        android:textSize="30sp"
        android:padding="20dp"
        android:textAlignment="center" />

</LinearLayout>


// 4. PersegiActivty.java

package com.bso.android.geometryapp;

import android.icu.text.NumberFormat;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.TextView;
import android.widget.Toast;

public class PersegiActivity extends AppCompatActivity {


    RadioButton rbkeliling, rbluas;
    Button btnhasil;
    TextView tvhasil;
    EditText etsisi;
    public float sisi = 0;
    public float hasil = 0;
    public Integer pilihan = 0; //untuk opsi pada prosedur Hasil

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_persegi);

        //inisialisasi material
        rbkeliling = findViewById(R.id.rb_keliling);
        rbluas = findViewById(R.id.rb_luas);
        etsisi = findViewById(R.id.et_sisi);
        btnhasil = findViewById(R.id.btn_hasil);
        tvhasil = findViewById(R.id.tv_hasil);

    }

    public float Pilih(View view) {
        // radio button mana yang di ceklis saat ini?
        boolean checked = ((RadioButton) view).isChecked();
        // mengecek pada radio button mana yang di klik
        switch(view.getId()) {
            case R.id.rb_keliling:
                if (checked)
                    pilihan = 0;
                break;
            case R.id.rb_luas:
                if (checked)
                    pilihan = 1;
                break;
            default:

                break;
        }
        return pilihan;
    }

    public float keliling(){
        float k = 0;
        sisi = Float.parseFloat(etsisi.getText().toString());
        k = sisi+sisi+sisi+sisi;
        return k;
    }

    public float luas(){
        float l = 0;
        sisi = Float.parseFloat(etsisi.getText().toString());
        l = sisi*sisi;
        return l;
    }

    public void displayToast(String message) {
        Toast.makeText(getApplicationContext(), message,
                Toast.LENGTH_SHORT).show();
    }

    public void Hasil(View view){
        if(etsisi.getText().toString().equals("")){
            displayToast("Pastikan kamu sudah mengisi kolom sisi!");
            tvhasil.setText("Tidak Diketahui");
        }
        else {
            switch (pilihan){
                case 0:
                    hasil = keliling();
                    tvhasil.setText(""+hasil+ " cm");
                    break;
                case 1:
                    hasil = luas();
                    tvhasil.setText(""+hasil+ " cm2");
                    break;
                default:
                    tvhasil.setText(""+hasil);
            }
        }
    }
}


// 5. activty_lingkaran.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.bso.android.geometryapp.LingkaranActivity">

    <TextView
        android:text="@string/lingkaran"
        android:textColor="@color/putih"
        android:textSize="25sp"
        android:textAlignment="center"
        android:padding="10dp"
        android:background="@color/colorPrimaryDark"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <RadioButton
            android:id="@+id/rb_keliling"
            android:onClick="Pilih"
            android:checked="true"
            android:text="@string/keliling"
            android:layout_marginLeft="50dp"
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="wrap_content" />

        <RadioButton
            android:id="@+id/rb_luas"
            android:onClick="Pilih"
            android:text="@string/luas"
            android:layout_marginLeft="50dp"
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="wrap_content" />

    </RadioGroup>

    <EditText
        android:id="@+id/et_jarijari"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="numberDecimal"
        android:hint="@string/r"
        android:textSize="30sp"
        android:padding="20dp"
        android:textAlignment="center"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/phi"
        android:textColor="#000000"
        android:textSize="30sp"
        android:padding="20dp"
        android:textAlignment="center" />

    <Button
        android:id="@+id/btn_hasil"
        android:onClick="Hasil"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="HASIL"
        android:layout_gravity="center"/>

    <TextView
        android:id="@+id/tv_hasil"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="0"
        android:textColor="#000000"
        android:textSize="30sp"
        android:padding="20dp"
        android:textAlignment="center" />

</LinearLayout>

// 6. LingkaranActivity.java

package com.bso.android.geometryapp;

import android.icu.text.NumberFormat;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.TextView;
import android.widget.Toast;

public class LingkaranActivity extends AppCompatActivity {

    RadioButton rbkeliling, rbluas;
    Button btnhasil;
    TextView tvhasil;
    EditText etjari2;
    public float phi = 22/7;
    public float r = 0;
    public float hasil = 0;
    public Integer pilihan = 0; //untuk opsi pada prosedur Hasil

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_lingkaran);

        //inisialisasi material
        rbkeliling = findViewById(R.id.rb_keliling);
        rbluas = findViewById(R.id.rb_luas);
        etjari2 = findViewById(R.id.et_jarijari);
        btnhasil = findViewById(R.id.btn_hasil);
        tvhasil = findViewById(R.id.tv_hasil);

    }

    public float Pilih(View view) {
        // radio button mana yang di ceklis saat ini?
        boolean checked = ((RadioButton) view).isChecked();
        // mengecek pada radio button mana yang di klik
        switch(view.getId()) {
            case R.id.rb_keliling:
                if (checked)
                    pilihan = 0;
                break;
            case R.id.rb_luas:
                if (checked)
                    pilihan = 1;
                break;
            default:

                break;
        }
        return pilihan;
    }

    // ini nama fungsi
    public float keliling(){
        //rumus keliling lingkaran
        float k = 0;
        r = Float.parseFloat(etjari2.getText().toString());
        k = 2 * r * phi;
        return k;
    }

    public float luas(){
        //rumus luas lingkaran
        float l = 0;
        r = Float.parseFloat(etjari2.getText().toString());
        l = r * r * phi;
        return l;
    }

    public void displayToast(String message) {
        //menampilkan toast prosedur
        Toast.makeText(getApplicationContext(), message,
                Toast.LENGTH_SHORT).show();
    }

    // menampilkan hasil sekaligus logikanya
    public void Hasil(View view){
        if(etjari2.getText().toString().equals("")){
            displayToast("Pastikan kamu sudah mengisi kolom jari-jari!");
            tvhasil.setText("Tidak Diketahui");
        }
        else {
            switch (pilihan){
                case 0:
                    hasil = keliling();
                    tvhasil.setText(""+hasil+ " cm");
                    break;
                case 1:
                    hasil = luas();
                    tvhasil.setText(""+hasil+ " cm2");
                    break;
                default:
                    tvhasil.setText(""+hasil);
            }
        }
    }
}

