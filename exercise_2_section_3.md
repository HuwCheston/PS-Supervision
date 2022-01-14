# Section 3: Data Cleaning
We will now switch to analysing our data in a statistical program. Excel and Google Sheets will be referred to here, and can be accessed for free online using your Cambridge ID. If you are used to using a different program such as RStats, SPSS, Stata or Python you may also use this to clean and analyse your data. 

## Load the data and split into columns. 
Create a new spreadsheet in whichever program you are using and copy the .txt file you created in Sonic Visualiser into it. It will load in as a single column. Highlight this column, then click Data - Text to Columns and apply (on Excel) or Data - Split Text to Columns (Google Sheets). In both cases, make sure that the delimiter is set to Commas or Spaces - whichever you selected in Sonic Visualiser. You can now delete the column with the point labels.

**Expected result:**

| Location    |
| ----------- |
| 0.667333333 |
| 0.854       |
| 0.998666667 |
| 1.178666667 |
| 1.338666667 |

## Calculate the beat duration.
You might have noticed that Sonic Visualiser cannot tell us the duration of each note we have identified, only its place in the file. This is easy to calculate, however, by subtracting the position of the next note from the previous. We can use this command to do this in Excel or Sheets:

`
=second_note-first_note
`

Enter this formula in a cell adjacent to your data, replacing the values, and drag it downwards to calculate the duration in seconds of every note in the extract.

:::{note}
You will find that you cannot calculate the duration of the last note, as you won't have the onset of the next note to compare it to - it'll appear as a negative value, which you'll need to delete.
:::

**Expected result:**

| Location    | Duration    |
| ----------- | ----------- |
| 0.667333333 | 0.186666667 |
| 0.854       | 0.144666667 |
| 0.998666667 | 0.18	    |
| 1.178666667 | 0.16        |
| 1.338666667 | NaN         |


## Calculate the BUR of every crotchet.
Recall that, on page 75 of his article, Benadon described how to calculate the BUR. The formula is as follows:

`
BUR = duration of first note in crotchet/duration of second note in crotchet
`

We can calculate this in Excel or Sheets with the following formula:

`
=first_note/second_note
`

:::{note}
We are only looking to obtain the BUR for each crotchet, not across crotchets. This means that, for every two duration values you have, you should only calculate one BUR value.
:::

**Expected result**

| Location    | Duration    | BUR |
| ----------- | ----------- | --- |
| 0.667333333 | 0.186666667 | 1.29032258 |
| 0.854       | 0.144666667 | NaN |
| 0.998666667 | 0.18	    | 1.125 |
| 1.178666667 | 0.16        | NaN |
| 1.338666667 | NaN         | NaN |