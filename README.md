# ANJ-Photobox.
Tugas 3-Kelompok 8_L0324007_L0324028_L0324034

#MainActivity.kt
package com.example.anjphotobox

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import android.content.Intent
import android.net.Uri
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.widget.Toast

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

            val email = findViewById<EditText>(R.id.etEmail)
            val password = findViewById<EditText>(R.id.etPassword)
            val btnLogin = findViewById<Button>(R.id.btnLogin)
            val lupaPassword = findViewById<TextView>(R.id.tvLupaPassword)

            // 🔐 LOGIN
            btnLogin.setOnClickListener {

                val inputEmail = email.text.toString()
                val inputPassword = password.text.toString()

                if (inputEmail.isNotEmpty() && inputPassword.isNotEmpty()) {

                    Toast.makeText(this, "Login Berhasil", Toast.LENGTH_SHORT).show()

                    // 👉 PINDAH HALAMAN (Explicit Intent)
                    val intent = Intent(this, DashboardActivity::class.java)
                    startActivity(intent)

                } else {
                    Toast.makeText(this, "Isi semua data!", Toast.LENGTH_SHORT).show()
                }
            }

            // 📧 LUPA PASSWORD (Implicit Intent)
            lupaPassword.setOnClickListener {

                val intent = Intent(Intent.ACTION_SENDTO)
                intent.data = Uri.parse("mailto:admin@anjphotobox.com")
                intent.putExtra(Intent.EXTRA_SUBJECT, "Lupa Password")
                intent.putExtra(Intent.EXTRA_TEXT, "Halo admin, saya lupa password akun saya.")

                startActivity(intent)
            }
        }
    }

#activity_main.xml
    <?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:background="#F5F5F5"
    android:padding="24dp">

    <!-- Judul -->
    <TextView
        android:text="ANJ Photobox 📸"
        android:textSize="26sp"
        android:textStyle="bold"
        android:textColor="#000000"
        android:layout_marginTop="60dp"
        android:layout_marginBottom="40dp"
        android:layout_gravity="center"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

    <!-- Card Login -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="20dp"
        android:background="#FFFFFF"
        android:elevation="6dp">

        <!-- Email -->
        <EditText
            android:id="@+id/etEmail"
            android:hint="Masukkan Gmail"
            android:inputType="textEmailAddress"
            android:padding="12dp"
            android:background="#EEEEEE"
            android:layout_marginBottom="16dp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>

        <!-- Password -->
        <EditText
            android:id="@+id/etPassword"
            android:hint="Masukkan Password"
            android:inputType="textPassword"
            android:padding="12dp"
            android:background="#EEEEEE"
            android:layout_marginBottom="24dp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>

        <!-- Tombol Login -->
        <Button
            android:id="@+id/btnLogin"
            android:text="LOGIN"
            android:textColor="#FFFFFF"
            android:textStyle="bold"
            android:backgroundTint="#000000"
            android:layout_width="match_parent"
            android:layout_height="50dp"/>
        <TextView
            android:id="@+id/tvLupaPassword"
            android:text="Lupa Password?"
            android:textColor="#0000FF"
            android:textSize="14sp"
            android:layout_marginTop="16dp"
            android:layout_gravity="center"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>

    </LinearLayout>

</LinearLayout>

#dashboard_activity.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:background="#F5F5F5">

    <TextView
        android:text="Selamat Datang di ANJ Photobox 📸"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginBottom="20dp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

</LinearLayout>

#DashboardActivity.kt
package com.example.anjphotobox

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class DashboardActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_dashboard)
    }
}

#
