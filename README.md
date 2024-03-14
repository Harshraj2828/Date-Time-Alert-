# Date-Time-Alert-
package com.example.date_app;

import androidx.appcompat.app.AppCompatActivity;

import android.app.AlertDialog;
import android.app.DatePickerDialog;
import android.app.TimePickerDialog;
import android.content.DialogInterface;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.DatePicker;
import android.widget.TextView;
import android.widget.TimePicker;

public class MainActivity extends AppCompatActivity {
    private TextView text;
    private Button btn;
    private TextView time;
    private Button btn1;
    private Button btn2;
    private TextView Alr ;
    AlertDialog.Builder builder;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        text=findViewById(R.id.txt);
        btn=findViewById(R.id.btn);

        time=findViewById(R.id.time);
        btn1=findViewById(R.id.btn1);

        Alr=findViewById(R.id.Alr);
        btn2=findViewById(R.id.btn2);
        builder=new AlertDialog.Builder(this);

        btn2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                builder.setTitle("Alert!!!")
                        .setMessage("Do you want to close the application")
                        .setCancelable(true)
                        .setPositiveButton("Yes", new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialogInterface, int i) {
                                finish();
                            }
                        })
                        .setNegativeButton("No", new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialogInterface, int i) {
                                dialogInterface.cancel();
                            }
                        })
                        .show();


            }
        });

        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
            opendialog();

            }
        });
        btn1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                opentime();

            }
        });


    }
    private void opendialog(){
        DatePickerDialog dialog=new DatePickerDialog(this, new DatePickerDialog.OnDateSetListener() {
            @Override
            public void onDateSet(DatePicker datePicker, int year, int month, int day) {

                text.setText(String.valueOf(year)+"/"+String.valueOf(month+1)+"/"+String.valueOf(day)+"");

            }
        }, 2024, 1, 17);
    dialog.show();
    }
     private void opentime(){
         TimePickerDialog time=new TimePickerDialog(this, new TimePickerDialog.OnTimeSetListener() {
             @Override
             public void onTimeSet(TimePicker timePicker,int hr,int min) {
                 text.setText(String.valueOf(hr)+":"+String.valueOf(min)+".");

             }
         }, 12, 20, false);

    time.show();
    }



}
