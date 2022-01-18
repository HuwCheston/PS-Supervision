# Section 3: Data Cleaning
We will now switch to analysing our data in a statistical program. Excel and Google Sheets will be referred to here, and can be accessed for free online using your Cambridge ID. If you are used to using a different program such as RStats, SPSS, Stata or Python you may also use this to clean and analyse your data. 

## Load the duration data and split into columns. 
Create a new spreadsheet in whichever program you are using and copy the .txt file for the **exposition duration** you created in Sonic Visualiser into it. It will load in as a single column. Highlight this column, then click Data - Text to Columns and apply (on Excel) or Data - Split Text to Columns (Google Sheets). In both cases, make sure that the delimiter is set to Commas or Spaces - whichever you selected in Sonic Visualiser. You can now delete the column with the point labels.

**Expected result:**

| Location    |
| ----------- |
| 0.667353 |
| 90.3367 |

With this out of the way, load in the second .txt file for the **second theme BPMs** into a seperate column and repeat the process of splitting.

:::{note}
Some spreadsheet or data packages may carry out this splitting process for you automatically.
:::

## Calculate the exposition duration.
Working with our duration data, we can easily calculate the duration of the exposition by subtracting the ending position marker from the starting position marker. We can use this command to do this in Excel or Sheets:

`
=ending_marker-starting_marker
`

Enter this formula in a cell adjacent to your data, replacing the values with your own.

**Expected result:**

| Location    | Duration |
| ----------- | -------- |
| 0.667353 | 89.669347 |
| 90.3367 | NaN  |

We can see now that the duration of the exposition here was 89.67 seconds, or about a minute and a half. Unfortunately for us, Bowen does not provide his data in this format. We'll need to divide the number of seconds in our duration by 60 to get it into Bowen's format. Type the following formula into a new cell:

`
=duration_seconds/60
`

**Expected result:**

`
Exposition duration = 1.404478
`

## Calculate the BPM of the second theme.
The BPM of the second theme is somewhat harder to calculate. First, we need to calculate the duration of each beat. We already used a formula to calculate the duration of the whole exposition, so we can repurpose that here:

`
=second_beat-first_beat
`

Type this into a blank column next to your BPM data and drag it downwards to calculate the duration of every beat you measured.

**Expected result:**

| Location    | Duration    |
| ----------- | ----------- |
| 44.642 | 0.334 |
| 44.976      | 0.364 |
| 45.34 | 0.34	    |
| 45.68 | 0.306667        |
| 45.98667 | 0.309333         |
| 46.296 | NaN |

:::{warning}
You won't be able to calculate the duration of the final beat you measured, as you won't have a successive beat to compare it to.
:::

To calculate the overall BPM of the second theme, we should first calculate the BPM of every *beat* within the second theme, then average this. In a new cell, enter this formula and drag it down:

`
=60/note_duration
`

**Expected result:**

| Location    | Duration    | BPM |
| ----------- | ----------- | --- |
| 44.642 | 0.334 | 179.6407 |
| 44.976      | 0.364 | 164.8352 |
| 45.34 | 0.34	    | 176.4706 |
| 45.68 | 0.306667        | 195.6522 |
| 45.98667 | 0.309333         | 193.9655 |
| 46.296 | NaN | NaN |

Now we can calculate our average BPM across the second theme by using the following inbuilt command in Excel or Sheets:

`
=AVERAGE(first_BPM:last_BPM)
`

**Expected result:**

`
Average BPM = 183.1128
`