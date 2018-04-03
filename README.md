# geometry
belajar ngoding
Layout

// activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
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
