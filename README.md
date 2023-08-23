- 👋 Hi, I’m @47PrinceYT
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
47PrinceYT/47PrinceYT is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
package com.example.age_calculator;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private EditText etCurrentDate;
    private EditText etDateOfBirth;
    private TextView tvAge;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etCurrentDate = findViewById(R.id.etCurrentDate);
        etDateOfBirth = findViewById(R.id.etDateOfBirth);
        tvAge = findViewById(R.id.tvAge);

        Button btnCalculate = findViewById(R.id.btnCalculate);
        btnCalculate.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get the current date and the date of birth from the edit text fields.
                String currentDate = etCurrentDate.getText().toString();
                String dateOfBirth = etDateOfBirth.getText().toString();

                // Calculate the age.
                int age = calculateAge(currentDate, dateOfBirth);

                // Set the age to the text view.
                tvAge.setText(String.valueOf(age));
            }
        });
    }

    private int calculateAge(String currentDate, String dateOfBirth) {
        // Split the date strings into their component parts.
        String[] currentDateParts = currentDate.split("-");
        String[] dateOfBirthParts = dateOfBirth.split("-");

        // Get the year, month, and day of the current date and the date of birth.
        int currentYear = Integer.parseInt(currentDateParts[0]);
        int currentMonth = Integer.parseInt(currentDateParts[1]);
        int currentDay = Integer.parseInt(currentDateParts[2]);
        int birthYear = Integer.parseInt(dateOfBirthParts[0]);
        int birthMonth = Integer.parseInt(dateOfBirthParts[1]);
        int birthDay = Integer.parseInt(dateOfBirthParts[2]);

        // Calculate the age.
        int age = currentYear - birthYear;
        if (currentMonth < birthMonth) {
            age--;
        } else if (currentMonth == birthMonth && currentDay < birthDay) {
            age--;
        }

        return age;
    }
}
