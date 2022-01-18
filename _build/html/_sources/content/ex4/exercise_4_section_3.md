# Section 3: Data Cleaning
We will now switch to analysing our data in a statistical program. Excel and Google Sheets will be referred to here, and can be accessed for free online using your Cambridge ID. If you are used to using a different program such as RStats, SPSS, Stata or Python you may also use this to clean and analyse your data. 

## Load the duration data and split into columns. 
Create a new spreadsheet in whichever program you are using and copy the .txt file for the **fundamental pitch** you created in Sonic Visualiser into it. It will load in as a single column. Highlight this column, then click Data - Text to Columns and apply (on Excel) or Data - Split Text to Columns (Google Sheets). In both cases, make sure that the delimiter is set to Commas or Spaces - whichever you selected in Sonic Visualiser. 

The first two columns refer to the time of the start and end point of the box; we are not interested in these, so feel free to delete them. You should be left with two columns and one data point, showing the high and low point of the fundamental frequency.

With this out of the way, load in the second .txt file for the **vibrato wobbles** into two seperate columns and repeat the process of splitting.

:::{note}
Some spreadsheet or data packages may carry out this splitting process for you automatically.
:::

## Calculate the fundamental frequency.
Next, we need to average the two values for the fundamental frequency to get the true pitch. Use this formula:

`
=AVERAGE(high_point:low_point)
`

**Expected result:**

| Frequency   |
| ----------- |
| 670.6685 |

## Calculate the 'wobble' within each vibrato.
As mentioned, vibrato is the deviation from a fundamental pitch. We need to work out how far away the 'high' and 'low' parts of each wobble are from the fundamental. Enter this command into a blank cell next to your data and drag it down to calculate the deviations:

`
=wobble_frequency-$fundamental_$frequency
`

:::{warning}
The dollar signs here are really important, as they tell the program to read from the same value for multiple calculations. So, if your fundamental is in cell A1 and your 'low' wobble note in A2, your formula should be `=A2=$A$1`.
:::

**Expected result:**

| Low Pitch | High Pitch | Low Dev.  | High Dev. |
| --------- | ---------- | --------- | --------- |
| 624.127   | 717.21     | \-46.5415 | 46.5415   |
| 613.539   | 717.21     | \-57.1295 | 46.5415   |
| 618.81    | 718.746    | \-51.8585 | 48.0775   |
| 618.81    | 714.149    | \-51.8585 | 43.4805   |
| 624.127   | 712.623    | \-46.5415 | 41.9545   |
| 618.81    | 712.623    | \-51.8585 | 41.9545   |
| 625.463   | 717.21     | \-45.2055 | 46.5415   |
| 629.489   | 712.623    | \-41.1795 | 41.9545   |


## Calculate the average deviations.
OK, great - we now know by the depth of each individual vibrato cycle, in relation to the fundamental frequency. We are now interested in the average deviation either side of the fundamental frequency. We can use this formula to calculate both the high and low average vibrato depth:

`
=AVERAGE(ABS(first_pitch:last_pitch))
`

:::{note}
I've added the ABS() command - short for absolute - here to make sure that any differences in sign across your data doesn't affect the result. This command converts all negative numbers to positive.
:::

**Expected result:**
| Low Avg. | High Avg. |
| -------- | --------- |
| 49.021625 | 44.63075 |

## Calculate the average depth of a vibrato cycle.
We should now have ended up with two positive values. The low average number shows the lower bound of a typical vibrato cycle; vice-versa, the high average number shows the upper bound of a typical cycle. In combination with our fundamental frequency, we can use these values to get an indication of the average vibrato extent.

We need to subtract the low average number from our fundamental frequency, like so:

`
=fundamental_frequency-low_avg
`

We then need to add the high average number to our fundamental frequency:

`
=fundamental_frequency+high_avg
`

**Expected result:**

`
Lower bound of vibrato = 626.04 Hz
Fundamental frequency = 670.67 Hz
Upper bound of vibrato = 715.30 Hz
`