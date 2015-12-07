# Simple Star Rating Using Checkbox

This assignment illustrates the basic star rating with a group of Checkboxes. 

## Keypoints:
In the MainActivity.java:
```Java
public class MainActivity extends AppCompatActivity {

    private LinearLayout rating;
    private  CheckBox star;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        rating = (LinearLayout) findViewById(R.id.ratings);

        /* Set listeners for each checkbox */
        for (int i = 1; i <= 5; i++) {
            star = (CheckBox) rating.findViewWithTag(String.valueOf(i));
            star.setOnClickListener(starsListener);
        }
    }

    private View.OnClickListener starsListener = new View.OnClickListener() {

        public void onClick(View view) {

            int tag = Integer.valueOf((String) view.getTag());

            /* Check all preceding checkbox and the current tag */
            for (int i = 1; i <= tag; i++) {
                star = (CheckBox) rating.findViewWithTag(String.valueOf(i));
                star.setChecked(true);
            }

            /* Uncheck the rest of the checkbox */
            for (int i = tag + 1; i <= 5; i++) {
                star = (CheckBox) rating.findViewWithTag(String.valueOf(i));
                star.setChecked(false);
            }
        }
    };

}
```

In the xml layout:
```xml
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:layout_below="@+id/textViewTitle"
        android:orientation="horizontal"
        android:id="@+id/ratings"
        >

        <CheckBox
            android:id="@+id/star1"
            style="?android:attr/starStyle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:tag="1" />

        <CheckBox
            android:id="@+id/star2"
            style="?android:attr/starStyle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:tag="2" />

        <CheckBox
            android:id="@+id/star3"
            style="?android:attr/starStyle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:tag="3" />

        <CheckBox
            android:id="@+id/star4"
            style="?android:attr/starStyle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:tag="4" />

        <CheckBox
            android:id="@+id/star5"
            style="?android:attr/starStyle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:tag="5" />

    </LinearLayout>
```
