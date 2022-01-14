# Exercise 1 – Body Motion in Musical Performance

## Research Question:
---
> Does an increase in the intensity of a musical performance correlate with an increase in the bodily motion of a performer?

To investigate this issue, we will be utilising the open-source [Motion Energy Analysis](https://psync.ch/mea-motion-energy-analysis/) software, developed by Fabian Ramseyer at the University of Bern. This software was developed initially to aid in the analysis of non-verbal synchrony during psychotherapy; however, it has applications in all situations that require the quantification of human movement.

MEA works by using image differencing. The user defines a series of Regions of Interest (ROIs) – for instance, the head or arm of a musician – and, for each frame of the video, a score is given that shows how much movement occurs within this region. The software is a powerful alternative to expensive motion capture suites and, unlike computer vision approaches, does not require any previous knowledge of coding.

## Section 1: Pre-Reading
---
### Task: complete the pre-reading.

Please begin by reading the following text, which is accessible online [here](https://idiscover.lib.cam.ac.uk/permalink/f/1nb04c1/TN_cdi_oup_oso_acprof_9780198529361)

Davidson, J. W. (2005). Bodily communication in musical performance. In Musical Communication, ed. by Miell, R., MacDonald, R., Hargreaves, D. J. Oxford: Oxford University Press.

:::{note}
If you have time and are interested in reading more on motion energy analysis, read section 3.1 from the following:

Ramseyer, F., & Tschacher, W. (2008). Synchrony in dyadic psychotherapy sessions. In Simultaneity: Temporal Structures and Observer Perspectives, ed. by Rossler, O. E. et al. Hackensack, NJ: World Scientific.
:::

## Section 2: Motion Energy Analysis
---
### Task: download Motion Energy Analysis software from OneDrive and extract it to your system.
Open up this OneDrive folder linked [here](https://universityofcambridgecloud-my.sharepoint.com/:f:/r/personal/hwc31_cam_ac_uk/Documents/Part%20II%20M%26S%20Teaching%20Materials/Exercise%20-%20Movement?csf=1&web=1&e=eg4LCB)

Inside the folder, download either the MEA_WIN_4_11a.zip or the MEA_4_11a_MAC.zip, depending on whether you are using a Windows or Mac system and extract the files.

:::{note}
The Windows version of MEA requires at least Windows 7. The Mac version requires OSX 10.13 or later.
:::

### Task: select ONE performance for further study and download both of the video recordings from the OneDrive (high AND low intensity).
In the same OneDrive where you found the Motion Energy Analysis downloadable, you will find a folder called ‘Videos’. Inside this folder are a series of recordings of Jazz, Classical, Free Improvisation, Folk, and Indian Classical music. 

Each performance has two files, one deemed to be of an especially intense moment in the music and the other of a moment of lower intensity. Choose one genre and download the two files.

:::{note}
If you would prefer to select your own videos, you may – however, please ensure that it is comparable to the examples I’ve selected (approx. 1 minute in total length across the two videos, with a stationary camera that does not cut away and shows as much of the musician as possible).
:::

### Task: run MEA and load the low intensity video you chose earlier into it.
Load MEA by double clicking on the executable file (MEA_WIN_4_11a.exe for windows). Read the low intensity video file in by clicking the ‘read’ button in the top left of MEA and verify that it can play. 

In the box labelled ‘2. ROI Size’, select medium. Next, choose ROI 1 in the ‘4. Select ROIs’ box. The red and green buttons next to this should light up. ROI refers to region of interest – this is the area of the video that motion will be tracked in.

### Task: in MEA, highlight the area in which the performer moves their head to set the ROI.

With the video paused, proceed to draw over area in which the performer’s head and shoulders moves in. You may not be able to see exactly where you are drawing at first, but this should appear when you next play the video. 

Play the video through and make sure that you are covering most of the area where the performer moves their head. If at any point you need to clear the ROI and start over, you can do this by pressing the ‘delete all ROIs’ button. 

:::{note}
You may also choose to define additional ROIs, perhaps for the hands or body, and include these in the analysis as well.
:::

**Expected result:**

![](ex1_mea.png)

### Task: run MEA on the video and generate a text file showing the frame-differenced motion in the ROI.

In MEA, scroll down so that you can see the boxes labelled 5 to 10. If you can’t scroll down, you may need to make sure that the MEA window is full screen – or you can try pressing the Window drop down menu and selecting ‘bring all to front’.

Scroll the video back to the very beginning. Then, in the box labelled ‘7. Start MEA’, click the red button underneath screens to turn the displays off, and click the button labelled ‘Start MEA’. Allow the video to run all the way through.

Once the video has finished running completely, press the ‘save TXT’ button to save the results of the analysis as a text file to your system. Verify this has worked successfully – it should look like a long list of numbers, most of which will be zero (these are the ROIs we did not use). 

:::{note}
When exporting, MEA may not automatically set the file extension for this text file to allow you to open it properly. If you cannot open the file, try renaming it to *.txt manually, where * is the filename you chose.
:::

**Expected result:**

### Task: repeat MEA for the high intensity video to generate a second text file.

Now repeat these steps for the high intensity video. You may find that you need to increase the amount of space you cover in the head ROI if the performer is moving more compared to the low intensity video.

:::{note}
If you have problems running MEA, first check the manual (included in the OneDrive). Some problems can be solved by installing MaxMSP from Cycling74. If you still cannot solve your problem, email me a description of it and I will be able to send you data that you can use to continue with the exercise.
:::

Section 3: data cleaning

We will now switch to analysing or data in a statistical program. Excel and Google Sheets will be referred to here, and can be accessed for free online using your Cambridge ID. If you are used to using a different program such as RStats, SPSS, Stata or Python you may also use this to clean and analyse your data. 

	You now need to find a way to clean the data before you can analyse it. By default, the text files created in MEA consist of a series of numbers, each separated by a space. Each line represents a frame of video, and each number is the amount of motion within an ROI during that frame.

Unfortunately, we cannot tell MEA to ignore the ROIs we have not specified, so we’ll need to remove them. One way to do this is to copy the whole text file and paste it into Excel as a single column. Highlight the whole column then, click Data – Text to Columns and apply (make sure ‘Space’ is selected under delimiter). In Google Sheets, the same tool is available under Data – Split Text to Columns. You may then delete the columns filled with zeros.

Task: copy the text files created for each video into a spreadsheet and remove the unnecessary data by splitting and deleting it. You should end up with a single column for both videos, with each data value showing the amount of motion within the ROI during any one frame.

Expected result: 

	You might have also noticed that, depending on how large you made each ROI, the range of values given out by MEA can be very large – from 0 to several thousand, for instance. To help here, we can convert each data point into a z-score. This is a standardised figure that expresses how far each data point is away from the mean in units of standard deviation. The formula for calculating the z-score for each data point is as follows:

z=(Data Value-Mean)/(Standard Deviation)

The mean and standard deviation of a dataset can be calculated in Excel or Google Sheets using the =AVERAGE(Start Cell: End Cell) and =STDEV(Start: End). Save both of these values in their own cell. Then, calculate the z-score for the first data point by typing =(Value Cell – Mean Cell)/Standard Deviation Cell into a blank cell. You can then drag this down to get the z-score for every other data point. 

Important: the mean and standard deviation must remain the same for each z-score calculation; only the data value should vary. If you find yourself getting DIV/0 errors when using the z-score calculation, you’ll need to add dollar signs into the coordinates of the mean and standard deviation cell (e.g. if cell A2 contains your mean, write this as $A$2).

Task: convert your cleaned raw data for both videos into z-scores to enable easier comparison between them.

Section 4: interpreting and presenting the data

You should now have generated two clean quantitative data sets, each showing the amount of physical motion in a single musical performance at varying moments of intensity. Depending on your experience working with data and statistical methods, there are a number of options you could explore here.

If you have previous experience with statistics, you might want to try a formal method of statistical analysis (such as a paired sample t-test) to compare the means of both samples. There is no in-built support for statistical methods in Google Sheets or Excel, so you may need to use a different program such as Stata or RStats for this.

If you have no previous experience with formal statistical methods, you may instead wish to represent both datasets visually using a chart; for instance, a line chart showing how the amount of motion changes over time, or a pie chart showing the proportion of high- versus low-motion frames in each video or ROI. Additionally, if creating a line chart, you could try adding annotations to show when particular moments in the performance occur.

Task: interpret your data statistically and/or visually to help answer your research question – are there differences in the amount of body motion between high- and low-intensity extracts from the same performance? 

Expected result: 













Conclusion:

Does an increase in the intensity of a musical performance correlate with an increase in the bodily motion of a performer?

Yes/No (delete as appropriate)

Checklist of tasks for Exercise 1:

☐ Read texts by Davidson and Ramseyer/Tschacher
☐ Download Motion Energy Analysis software from OneDrive and extract.
☐ Select performance videos from OneDrive and download – or find your own.
☐ Run MEA and load first video into it.
☐ Identify and select first ROI in MEA.
	☐ Optional: identify and select additional ROIs, e.g. for the performer’s body.
☐ Run analysis in MEA and generate a text file for the first video.
☐ Repeat the previous steps for the second video.
☐ Import the data into a statistical package (Google Sheets or Excel) and separate the columns.
☐ Convert the data to z-scores.
☐ Compare both datasets using statistical techniques or visually with graphs. 
