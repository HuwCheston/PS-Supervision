# Section 2: Sonic Visualiser
---
## Download Sonic Visualiser software and extract it to your system.
Navigate to the download page for Sonic Visualiser linked [here](https://www.sonicvisualiser.org/download.html). 

If you are using a Mac computer, click the download link for Mac on the right of the page. If you are using Windows, you will likely need to use the 64-bit installer, on the left of the page. If you experience problems with this (or are using an older system, for instance), you may need to use the 32-bit installer.

:::{note}
The Windows version of Sonic Visualiser runs on most modern updates. The Mac version requires OSX 10.12 or later.
:::

Whatever version you are using, download the program using the primary link. Open up the .msi (Windows) or .dmg (Mac) file you downloaded and follow the installer through to the end to complete the installation. On Windows, you may need to wait a while before pressing 'Yes' when the User Account Control screen pops up.

## Select ONE performance for further study, download audio and transcription files.
Browse to the OneDrive folder linked [here](https://universityofcambridgecloud-my.sharepoint.com/:f:/g/personal/hwc31_cam_ac_uk/EtWN3T-F8tpGiQSsyAfNqqUB-J4-BQCdwoKS1D2637eH5w?e=fQKdcK), you should find a folder called 'Audio Files'.

Inside this folder are six very short (under 5 seconds) .mp3 excerpts of recordings by notable musicians including Miles Davis, Ella Fitzgerald, and Wes Montgomery. These are all taken from performances of the piece 'A Night in Tunisia'. Have a listen to these and download ONE of the performances that you want to work with in this exercise.

There is also a single .pdf file containing transcriptions of all six performances on one page. You should download this also.

:::{note}
Once you have completed the exercise with one of the six .mp3s included here, you are more than welcome to repeat it using another file I have provided - or your own!
:::

## Open the audio spectrogram in Sonic Visaliser.
Open up Sonic Visualiser by locating it in the start menu (Windows) or Applications folder (Mac). You should be presented with the logo splash screen. The next thing you will see will be a welcome window that requests access to your internet network. Although we won't be using any network features in this exercise, I'd recommend that you allow network access in case you want to use Sonic Visualiser in the future - it makes installing updates and plugins much easier.

![](ex2_svdata.png)

The next screen you should see is a blank Sonic Visualiser window:

![](ex2_svopen.png)

We now need to load in some audio. Open up the location where you saved the recording earlier in the file explorer (Windows) or finder (Mac), and drag and drop it onto the Sonic Visualiser window. You should see the waveform of the audio appear:

![](ex2_svwave.png)

While interesting, this doesn't help us much in locating the exact timing of individual notes. A spectrogram is a better option, so click Layer at the top of the window, then Add Spectrogram and [NAME OF AUDIO].mp3: All Channels Mixed. This will shift to the Spectrogram view, where we can see the individual frequencies:

![](ex2_svspectrogram.png)

:::{note}
The spectrogram view will default to green. For some people this might not be the best option, so you can choose the colour on the side panel. You can also adjust the threshold and colour rotation of the spectrogram using the two dials either side of the colour drop-down option, which may help when identifying note onsets. I find that the White on Black option with the threshold at approx -60dB and rotation -30 leads to good initial results.
:::

We also need to be able to hear the recording in Sonic Visualiser. To do this, we can use the large transport buttons at the top of the window (next to the file open and save buttons), or press the spacebar.

:::{note}
If you find that the tempo of the recording is too fast, you can slow the recording down using the large dial in the bottom right of the screen (immediately to the right of the waveform).
:::

## Identify the note onsets.
Once you've played through the recording, we need to tell the computer where the start of each note played by the musician is. This will allow us to calculate the duration of every note played and then - eventually - the beat-upbeat ratio.

To do this, add a new time instants layer by clicking the Layer drop-down menu - Add New Time Instants Layer. You can now click anywhere on the spectrogram to add a point, which will be shown as a line across the spectrogram. To adjust the placement of a point, click the edit button at the top (next to the pencil and cursor icons) and drag the point to where you want it. You can also delete a point by clicking the eraser (next to the pencil and compass) then clicking on the point again.

:::{note}
By default, Sonic Visualiser renders time instants as white lines. This can be confusing, as the playback line is also white. You can change the colour of the instants on the right-hand menu.
:::

Once you've tried creating some time instant values, the next task is to place them at the start of each note in the excerpt. Open up the transcription .pdf provided and then, with the help of the recording and the spectrogram, place a time instant value onto the onset of each note in Sonic Visualiser in accordance with the transcription.

![](ex2_svtimeinstants.png)

:::{note}
You can zoom into the spectrogram by using the scroll wheel on your mouse, the page up key on your keyboard, or the horizontal wheel on the bottom-right of the spectrogram display.
:::

## Export your data for analysis.

Once you've labelled all the note onsets for the recording (there should be no more than 30, depending on which excerpt you chose), it's time to get the data out of Sonic Visualiser. Make sure your time instants layer is active by selecting it in the panel on the right of the screen: it will likely be layer 5. Then, go to File - Export Annotation Layer. Choose where to save your file, select the file type .txt in the drop-down menu and press save.

:::{note}
If you find that you get an error when trying to save, you may need to put .txt manually at the end of your filename - e.g. Timings.txt
:::

In the 'Export Layer' dialogue window that follows, change the column seperator from Tabs (default) to Commas or Spaces: this will help us when we come to importing our data. Make sure that the timing format is in seconds and press OK to export.

![](ex2_svexport.png)