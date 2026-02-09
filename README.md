1.Develop an application that uses GUI components, Font and Colors.

'''
MainActivity.java


package com.example.mobileapplicationbca;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.app.Activity;
import android.graphics.Typeface;
import android.graphics.Color;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    float font = 24; 
    int i = 1;
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
       final TextView t1 = (TextView)findViewById(R.id.textView1);
        Button b1 = (Button)findViewById(R.id.button1);
        b1.setOnClickListener(new View.OnClickListener(){
            public void onClick(View view) {
                t1.setTextSize(font);
                font = font+4;
                if(font==40)
                    font = 20;
            }});
        Button b2 = (Button)findViewById(R.id.button2);
        b2.setOnClickListener(new View.OnClickListener(){
            public void onClick(View view) {
                switch(i)
                {
                    case 1:
                        t1.setTextColor(Color.parseColor("#0000FF"));
                        break;
                    case 2:
                        t1.setTextColor(Color.parseColor("#00FF00"));
                        break; 
                    case 3:
                        t1.setTextColor(Color.parseColor("#FF0000"));
                        break;
                    case 4:
                        t1.setTextColor(Color.parseColor("#800000"));
                        break;
                }
                i++;
                if(i==5)
                    i = 1;
            }
        }); 
    }
}


  

acitivity_main.xml:


<?xml version="1.0" encoding="utf-8"?> 
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">
    <TextView
        android:id="@+id/textView1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" 
        android:layout_margin="20sp"
        android:gravity="center"
        android:text="@string/welcome"
        android:textSize="20sp"
        android:textStyle="bold" />
    <Button
         android:id="@+id/button1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20sp"
        android:gravity="center"
        android:text="@string/change_font_size"
        android:backgroundTint="#3F51B5"/>
        <Button
        android:id="@+id/button2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:layout_margin="20sp"
        android:text="@string/change_color"
        android:backgroundTint="#3F51B5"/>
</LinearLayout>



2.Develop an application that uses Layout Managers and event Listeners.

MainActivity.java:


package com.example.pgm2;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.app.Activity;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {
    EditText txtData1,txtData2;
    float num1,num2,result1,result2;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button add = (Button)findViewById(R.id.button1);
        add.setOnClickListener(new OnClickListener(){
            public void onClick(View v){
                try
                {
                    txtData1 = (EditText)findViewById(R.id.editText1);
                    txtData2 = (EditText)findViewById(R.id.editText2);
                    num1 = Float.parseFloat(txtData1.getText().toString());
                    num2 = Float.parseFloat(txtData2.getText().toString());
                    result1 = num1+num2;
                    Toast.makeText(getBaseContext(),"ANSWER:"+result1,Toast.LENGTH_SHORT).show();
                }
                catch(Exception e)
                {
                    Toast.makeText(getBaseContext(),e.getMessage(),Toast.LENGTH_SHORT).show();
                }
            }
        });
        Button sub = (Button)findViewById(R.id.button3);
        sub.setOnClickListener(new OnClickListener(){
            public void onClick(View v)
            {
                try
                {
                    txtData1 = (EditText)findViewById(R.id.editText1);
                    txtData2 = (EditText)findViewById(R.id.editText2);
                    num1 = Float.parseFloat(txtData1.getText().toString());
                    num2 = Float.parseFloat(txtData2.getText().toString());
                    result2 = num1-num2;    Toast.makeText(getBaseContext(),"ANSWER:"+result2,Toast.LENGTH_SHORT).show();
                }
                catch(Exception e)
                {
                    Toast.makeText(getBaseContext(),e.getMessage(),Toast.LENGTH_SHORT).show();
                }
            }
        });
        Button clear = (Button)findViewById(R.id.button2);
        clear.setOnClickListener(new OnClickListener() {
            public void onClick(View v)
            {
                try
                {
                    txtData1.setText("");
                    txtData2.setText("");
                }
                catch(Exception e)
                {
                    Toast.makeText(getBaseContext(),e.getMessage(),Toast.LENGTH_SHORT).show();
                }
            }
        });

    }
}


acitivity_main.xml:


<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    tools:context=".MainActivity"
    android:id="@+id/relativeLayout1">

  <LinearLayout
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:id="@+id/linearLayout1"
      android:layout_alignParentStart="true"
      android:layout_alignParentEnd="true"
      android:layout_alignParentTop="true"
      android:orientation="horizontal">

      <TextView
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:text="@string/calculation"
          android:layout_gravity="center"
          android:textSize="20sp">
      </TextView>

  </LinearLayout>
  
  <LinearLayout
        android:id="@+id/linearLayout2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_below="@+id/linearLayout1">
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/enter_first_number" />
        <EditText
            android:id="@+id/editText1"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="0.20"
            android:inputType="number">
        </EditText>
    </LinearLayout>


   <LinearLayout
        android:id="@+id/linearLayout3"
        android:layout_width="wrap_content" android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_below="@+id/linearLayout2">
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/enter_no_2" />
        <EditText
            android:id="@+id/editText2"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="0.20"
            android:inputType="number">
        </EditText>
    </LinearLayout>
    <LinearLayout
        android:id="@+id/linearLayout4"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_below="@+id/linearLayout3"
        android:orientation="horizontal">
        <Button
            android:id="@+id/button1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:text="Addition"
            />
        <Button
            android:id="@+id/button3"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:text="@string/subtraction" />
        <Button
            android:id="@+id/button2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:text="@string/clear" />
        <View
            android:id="@+id/linearLayout5"
            android:layout_width="fill_parent"
            android:layout_height="2dp"
            android:background="#DDFFDD" />
    </LinearLayout>
</RelativeLayout>

'''

3. Develop a native calculator application


MainActivity.java:

package com.example.pgm2_nativecalculator;
import androidx.appcompat.app.AppCompatActivity;
import android.annotation.SuppressLint;
import android.os.Bundle;
import android.text.TextUtils;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity implements OnClickListener {
    //Defining the Views
    EditText Num1;
    EditText Num2;
    Button Add;
    Button Sub;
    Button Mul;
    Button Div;
    TextView Result;
    Button clearButton;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        //Referring the Views
        Num1 = (EditText) findViewById(R.id.editText1);
        Num2 = (EditText) findViewById(R.id.editText2);
        Add = (Button) findViewById(R.id.Add);
        Sub = (Button) findViewById(R.id.Sub);
        Mul = (Button) findViewById(R.id.Mul);
        Div = (Button) findViewById(R.id.Div);
        Result = (TextView) findViewById(R.id.ResultView);
        clearButton = findViewById(R.id.clearButton);
        // set a listener
        Add.setOnClickListener(this);
        Sub.setOnClickListener(this);
        Mul.setOnClickListener(this);
        Div.setOnClickListener(this);
        clearButton.setOnClickListener(this);
    }

    @SuppressLint("SetTextI18n")
    public void onClick(View v) {
        float num1 = 0;
        float num2 = 0;
        float result = 0;
        String oper = "";

        // check if the fields are empty
        if (TextUtils.isEmpty(Num1.getText().toString()) || TextUtils.isEmpty(Num2.getText().toString()))
            return;

        // read EditText and fill variables with numbers
        num1 = Float.parseFloat(Num1.getText().toString());
        num2 = Float.parseFloat(Num2.getText().toString());

        // defines the button that has been clicked and performs the corresponding operation
        // write operation into oper, we will use it later for output
        int id = v.getId();
        if (id == R.id.Add) {
            oper = "+";
            result = num1 + num2;
        } else if (id == R.id.Sub) {
            oper = "-";
            result = num1 - num2;
        } else if (id == R.id.Mul) {
            oper = "*";
            result = num1 * num2;
        } else if (id == R.id.Div) {
            oper = "/";
            result = num1 / num2;
        }
        // form the output line
        Result.setText(num1 + " " + oper + " " + num2 + " = " + result);
        //Clear the textfields
        if(id == R.id.clearButton) {
            Num1.setText("");
            Num2.setText("");
            Result.setText("");
        }
    }
}


activity_main.xml:


<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

  <LinearLayout
        android:id="@+id/linearLayout1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp">
        <EditText
            android:id="@+id/editText1"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:inputType="numberDecimal"
            android:hint="Enter first number"
            android:textSize="18sp" />

        <EditText
            android:id="@+id/editText2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:inputType="numberDecimal"
            android:hint="Enter second number"
            android:textSize="18sp"/>

   </LinearLayout>

  <LinearLayout
        android:id="@+id/linearLayout2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp">

        <Button
            android:id="@+id/Add"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="+"
            android:textSize="30sp"
            android:backgroundTint="#A09CA6"/>

        <Button
            android:id="@+id/Sub"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="-"
            android:textSize="30sp"
            android:backgroundTint="#A09CA6"/>

        <Button
            android:id="@+id/Mul"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="*"
            android:textSize="30sp"
            android:backgroundTint="#A09CA6"/>

        <Button
            android:id="@+id/Div"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="/"
            android:textSize="30sp"
            android:backgroundTint="#A09CA6"/>
  </LinearLayout>
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:gravity="center">
        <Button
            android:id="@+id/clearButton"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Clear"
            android:textSize="30sp"
            android:backgroundTint="#A09CA6"/>
    </LinearLayout>
    <TextView
        android:id="@+id/ResultView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="50dp"
        android:text="Answer is"
        android:textSize="30sp"
        android:gravity="center"/>
</LinearLayout>


4. Write an application that draws basic graphical primitives on the screen

Mainactivity.java:  

package com.example.pgm4;

import android.app.Activity;
import android.graphics.Bitmap;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Mesh;
import android.graphics.Paint;
import android.graphics.drawable.BitmapDrawable;
import android.os.Bundle;
import android.widget.ImageView;

public class MainActivity extends Activity {
    @Override
    public void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        //Creating a Bitmap
        Bitmap bg = Bitmap.createBitmap(720, 1280, Bitmap.Config.ARGB_8888);

        //Setting the Bitmap as background for the ImageView
        ImageView i = (ImageView) findViewById(R.id.imageView);
        i.setBackgroundDrawable(new BitmapDrawable(bg));

        //Creating the Canvas Object
        Canvas canvas = new Canvas(bg);

        //Creating the Paint Object and set its color & TextSize
        Paint paint = new Paint();
        paint.setColor(Color.MAGENTA);
        paint.setTextSize(50);

        Paint paint1 = new Paint();
        paint1.setColor(Color.YELLOW);
        paint1.setTextSize(25);

        //To draw a Rectangle
        canvas.drawText("Rectangle", 420, 150, paint);
        canvas.drawRect(400, 200, 650, 700, paint);

        //To draw a Circle
        canvas.drawText("Circle", 120, 150, paint);
        canvas.drawCircle(200, 350, 150, paint);


        //To draw a Oval
        canvas.drawText("Oval", 130, 590, paint);
        canvas.drawOval(50,600,350,1000,paint);


        //To draw a Line
        canvas.drawText("Line", 480, 800, paint);
        canvas.drawLine(520, 850, 520, 1150, paint);
    }
}

activity_main.xml:

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/imageView"
        android:contentDescription="@string/todo" />

</RelativeLayout>


5. Develop an application that makes use of databas


MainActivity.java:
package com.example.pgm5;

import android.app.Activity;
import android.app.AlertDialog.Builder;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends Activity implements OnClickListener {
    EditText Rollno,Name,Marks;
    Button Insert,Delete,Update,View,ViewAll,Clear;
    SQLiteDatabase db;
    /** Called when the activity is first created. */
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Rollno=(EditText)findViewById(R.id.Rollno);
        Name=(EditText)findViewById(R.id.Name);
        Marks=(EditText)findViewById(R.id.Marks);
        Insert=(Button)findViewById(R.id.Insert);
        Delete=(Button)findViewById(R.id.Delete);
        Update=(Button)findViewById(R.id.Update);
        View=(Button)findViewById(R.id.View);
        ViewAll=(Button)findViewById(R.id.ViewAll);
        Clear=(Button)findViewById(R.id.Clear);
        Insert.setOnClickListener(this);
        Delete.setOnClickListener(this);
        Update.setOnClickListener(this);
        View.setOnClickListener(this);
        ViewAll.setOnClickListener(this);
        Clear.setOnClickListener(this);
        // Creating database and table
        db=openOrCreateDatabase("StudentDB", Context.MODE_PRIVATE, null);
        db.execSQL("CREATE TABLE IF NOT EXISTS student(rollno VARCHAR,name VARCHAR,marks VARCHAR);");
    }

    @Override
    public void onClick(View view){
        // Inserting a record to the Student table
        if(view==Insert)
        {
            // Checking for empty fields
            if(Rollno.getText().toString().trim().length()==0||
                    Name.getText().toString().trim().length()==0||
                    Marks.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter all values");
                return;
            }
            db.execSQL("INSERT INTO student VALUES('"+Rollno.getText()+"','"+Name.getText()+
                    "','"+Marks.getText()+"');");
            showMessage("Success", "Record added");
            clearText();
        }
        // Deleting a record from the Student table
        if(view==Delete)
        {
        // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }
            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst())
            {
                db.execSQL("DELETE FROM student WHERE rollno='"+Rollno.getText()+"'");
                showMessage("Success", "Record Deleted");
            }
            else
            {
                showMessage("Error", "Invalid Rollno");
            }
            clearText();
        }
        // Updating a record in the Student table
        if(view==Update)
        {
        // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }
            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst()) {
                db.execSQL("UPDATE student SET name='" + Name.getText() + "',marks='" +
                        Marks.getText() +
                        "' WHERE rollno='"+Rollno.getText()+"'");
                showMessage("Success", "Record Modified");
            }
            else {
                showMessage("Error", "Invalid Rollno");
            }
            clearText();
        }
        // Display a record from the Student table
        if(view==View)
        {
        // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }
            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst())
            {
                Name.setText(c.getString(1));
                Marks.setText(c.getString(2));
            }
            else
            {
                showMessage("Error", "Invalid Rollno");
                clearText();
            }
        }
        // Displaying all the records
        if(view==ViewAll)
        {
            Cursor c=db.rawQuery("SELECT * FROM student", null);
            if(c.getCount()==0)
            {
                showMessage("Error", "No records found");
                return;
            }
            StringBuffer buffer=new StringBuffer();
            while(c.moveToNext())
            {
                buffer.append("Rollno: "+c.getString(0)+"\n");
                buffer.append("Name: "+c.getString(1)+"\n");
                buffer.append("Marks: "+c.getString(2)+"\n\n");
            }
            showMessage("Student Details", buffer.toString());
        }
        if(view==Clear) {
            Rollno.setText("");
            Name.setText("");
            Marks.setText("");
            Rollno.requestFocus();

        }
    }
    public void showMessage(String title,String message) {
        Builder builder = new Builder(this);
        builder.setCancelable(true);
        builder.setTitle(title);
        builder.setMessage(message);
        builder.show();
    }

    public void clearText()
    {
        Rollno.setText("");
        Name.setText("");
        Marks.setText("");
        Rollno.requestFocus();
    }
}

activity_main.xml:

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="wrap_content"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="10dp"
        android:text="@string/student_details"
        android:textColor="#FF5722"
        android:textSize="35sp" />

    <TextView
        android:id="@+id/LabelRno"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="20dp"
        android:layout_marginTop="110dp"
        android:text="Enter Rollno:"
        android:textColor="#000000"
        android:textSize="20sp" />

    <TextView
        android:id="@+id/LabelName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/LabelRno"
        android:layout_marginStart="20dp"
        android:layout_marginTop="25dp"
        android:text="Name:"
        android:textColor="#000000"
        android:textSize="20sp" />

    <TextView
        android:id="@+id/LabelMarks"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/LabelName"
        android:layout_marginStart="20dp"
        android:layout_marginTop="30dp"
        android:text="Marks:"
        android:textColor="#000000"
        android:textSize="20sp" />

    <EditText
        android:id="@+id/Rollno"
        android:layout_width="fill_parent"
        android:layout_height="40dp"
        android:layout_marginTop="100dp"
        android:layout_toRightOf="@+id/LabelRno"
        android:hint="Enter Roll No" />


    <EditText
        android:id="@+id/Name"
        android:layout_width="fill_parent"
        android:layout_height="60dp"
        android:layout_below="@+id/Rollno"
        android:layout_centerVertical="true"
        android:layout_toRightOf="@+id/LabelName"
        android:hint="Name" />

    <EditText
        android:id="@+id/Marks"
        android:layout_width="fill_parent"
        android:layout_height="60dp"
        android:layout_below="@+id/Name"
        android:layout_centerVertical="true"
        android:layout_toRightOf="@+id/LabelMarks"
        android:hint="Marks" />

<LinearLayout
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:layout_marginTop="270dp"
    android:layout_centerHorizontal="true">

    <Button
        android:id="@+id/Insert"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Insert"
        android:backgroundTint="#3F51B5"
        android:textColor="@color/white"/>

    <Button
        android:id="@+id/Delete"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="15dp"
        android:text="Delete"
        android:backgroundTint="#3F51B5"
        android:textColor="@color/white"/>
</LinearLayout>
    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="320dp"
        android:layout_centerHorizontal="true">
        <Button
        android:id="@+id/Update"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Update"
            android:backgroundTint="#3F51B5"
            android:textColor="@color/white"/>

        <Button
            android:id="@+id/View"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:text="View"
            android:backgroundTint="#3F51B5"
            android:textColor="@color/white"/>
    </LinearLayout>

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="370dp"
        android:layout_centerHorizontal="true">
    <Button
        android:id="@+id/ViewAll"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="ViewAll"
        android:backgroundTint="#3F51B5"
        android:textColor="@color/white"/>

        <Button
            android:id="@+id/Clear"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:text="Reset"
            android:backgroundTint="#3F51B5"
            android:textColor="@color/white"/>
  </LinearLayout>
</RelativeLayout>
