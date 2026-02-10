# opus-ogg-mka-(libopus-vorbis)--bitrate-vs-time-plot-analyzer

A python script that analyzes the bitrate-time of audio files created with the libopus codec in .opus format.

Can analyze libopus and vorbis codecs.
Supports opus, ogg, mka formats.

It supports both .ogg, .mka and .opus files made with the libopus codec(opus). For good results, choose .ogg or .opus.

It supports both .ogg and .opus files made with the vorbis codec(ogg-vorbis).

The file 'audio_bitrate_analyzer.bat' is recommended for Windows 10+ OSs. Allows you to select the audio file you want to analyze, no code needed. Allows you to choose the folder location where you want to save the output files.

Output Analysis file names:

    <file_name>_bitrate.csv
    <file_name>_bitrate.png
    <file_name>_plot.svg
    <file_name>_interactive.html

----
----

Test:

192kbps, vbr on, libopus codec, compression level 10 ( Applies compression according to the selected bitrate setting, determines the print strength. A value of 10 is HQ. There is no compression. Quality is at the highest value. A value of 0 is LQ. Compression is the highest value. Quality is the lowest (LQ). ) . 
Code to convert file to opus:

    ffmpeg -i input.ext -vn -c:a libopus -b:a 192k -vbr on -compression_level 10 output.opus

Example:

size of the opus file: 6.528KB

![Best_for_Last_192kbps-compress_level_10_bitrate](https://github.com/user-attachments/assets/5c68f41c-4cd9-4693-9d0b-3d344f2b2bb6)

-------
-------
192kbps, vbr on, libopus codec, compression level 0, LQ, max compression (Keeps the bitrate as close as possible to bitrate value.)

    ffmpeg -i input.ext -vn -c:a libopus -b:a 192k -vbr on -compression_level 00 output.opus   

Example:

size of the opus file: 5.953KB

![Best_for_Last _192kbps-compress_level_0_bitrate](https://github.com/user-attachments/assets/b6594a92-ad3c-498c-b957-ce7f7f019d8e)


--------
--------
With this software we can understand whether an opus file is compressed in high quality or low quality.
--------
If you examine the two graphs, the music file that is highly compressed with 0 has a bitrate very close to 192kbps. This indicates a high level of compression, low quality and low size. Also, since the bitrate axis of the graph is up to 320kbps, the perception may be perceived as a higher compression level. If the bitrate axis were plotted with a maximum level of 510kbps, it would look and be perceived as a curve above 192kbps. the perception is that it is of higher quality than it actually is.

Looking at the other graph, there is a very wide range of bitrate levels. Data was recorded up to 400kbps. This shows that the compression level is low and the quality is high. The reason why the file size is larger is because of the quality. 

(In the second graph, the maximum point of the bitrate axis level is 510kbps. To compare the two graphs in terms of perception, imagine that both graphs are 510kbps and think about the actual graph. This way you will understand and perceive that the first graph is much more compressed).

The video bitrate analyzer was created using a python script:
https://github.com/InB4DevOps/bitrate-viewer/blob/main/_bitrate_analyzer.py

Thanks to [@InB4DevOps](https://github.com/InB4DevOps) 

Development is accelerated with the help of DeepSeek R1 DeepThink.

First it analyzes the opus file and creates a .csv table data file with bitrate - time columns.

This file creates a bitrate-time graph and saves it in .svg format.

It also saves in .png format.

Generates detailed bitrate-time graph in .html format for interactive and detailed graphing.

Requirements:

    Python 3.6+
    pip install -r requirements.txt
    FFprobe in your PATH.

System requirements:

    ffmpeg>=4.0
    ffprobe>=4.0

ffmpeg for Windows 11:

    choco install ffmpeg

    winget install Gyan.FFmpeg

------
------

Run the 'run_audio_bitrate_analyzer.bat' file for Windows OSs. 

For Windows OSs, if you double-click run_audio_bitrate_analyzer.bat, audio_bitrate_analyzer.py runs in the cmd.exe window. Then the audio file selection window opens. You select the file in .opus .mka or .ogg format. By default .opus files are selected. For other formats, click on " All Files(*.*) " and select your audio file. Analyzes. The File Explorer window opens for you to choose the location to save the output files (.csv, .svg, .png, .html). You select the location where you want to save. It saves the files to that location.

Output files:    <file_name>_bitrate.csv , <file_name>_bitrate.png , <file_name>_plot.svg , <file_name>_interactive.html

What bitrate_analyzer.py and audio_bitrate_analyzer.py have in common is that they open a File Explorer window where you can easily select the audio file. I've made it easy to work with for those who don't want to write code.
The only difference between bitrate_analyzer.py and audio_bitrate_analyzer.py is that audio_bitrate_analyzer.py opens a File Explorer window that lets you choose the folder where you want to save the analysis files. 

bitrate_analyzer.py saves the output files in the folder where bitrate_analyzer.py is located.

audio_bitrate_analyzer.py additionally needs Thinker to run.
If you don't have Thinker installed (it is usually installed with python):

    winget install Python.Python.3 --override "/InstallAllUsers=1 /AddToPath=1 /Include_tkinter=1"

Usage:

Double click on the run_audio_bitrate_analyzer.bat file.

Or

    python .\audio_bitrate_analyzer.py
    # Or with specific file
    python .\audio_bitrate_analyzer.py "C:\path_to_file\audio_file.opus"

If you have a PATH problem:

    C:\<path_to_python.exe_file>\python.exe .\audio_bitrate_analyzer.py
    

------

Using powershell with ps1 file:
(to run audio_bitrate_analyzer.py with powershell)

    .\audio_bitrate_analyzer.ps1
    # Or with specific file
    .\audio_bitrate_analyzer.ps1 -filePath "C:\<path_to_file>\audio_file.opus"

Double click on 'run_bitrate_analyzer-ps1.bat' to run bitrate_analyzer.ps1 for easy execution.

------
------

Run the 'bitrate_analyzer.bat' file for Windows OSs.

For Windows OSs, if you double-click bitrate_analyzer.bat, bitrate_analyzer.py runs in the cmd.exe window. Then the audio file selection window opens. You select the file in .opus .mka or .ogg format. By default .opus files are selected. For other formats, click on " All Files(*.*) " and select your audio file.


The only difference between bitrate_analyzer.py and opus_bitrate_analyzer is that bitrate_analyzer.bat opens a File Explorer window where you can easily select the audio file. opus_bitrate_analyzer.py is used entirely from the terminal. I made it easy to work with for those who don't want to write code.

bitrate_analyzer.py additionally needs Thinker to run.
If you don't have Thinker installed (it is usually installed with python):

    winget install Python.Python.3 --override "/InstallAllUsers=1 /AddToPath=1 /Include_tkinter=1"

Usage:

Double click on the bitrate_analyzer.bat file.

Or

    python .\bitrate_analyzer.py
    # Or with specific file
    python .\bitrate_analyzer.py "C:\path_to_file\audio_file.opus"

If you have a PATH problem:

    C:\<path_to_python.exe_file>\python.exe .\bitrate_analyzer.py

Example:

C:\Python311\python.exe .\bitrate_analyzer.py

C:\Program Files\Python313\python.exe .\bitrate_analyzer.py

------

Using powershell with ps1 file:
(to run bitrate_analyzer.py with powershell)

    .\bitrate_analyzer.ps1
    # Or with specific file
    .\bitrate_analyzer.ps1 -filePath "C:\<path_to_file>\audio_file.opus"

Double click on 'run_bitrate_analyzer-ps1.bat' to run bitrate_analyzer.ps1 for easy execution.

------
------

Manual Usage or for all OS:

    python opus_bitrate_analyzer.py <file_name>.opus

Do not use space characters or unrecognized characters in the file name.


Use with powershell (for the opus file inside the opus bitrate analyzer main folder) :

    python opus_bitrate_analyzer.py '.\<file_name>.opus'

The characters, the emptiness doesn't matter.


Use with Powershell (path to the opus file in any folder):

    python opus_bitrate_analyzer.py "<path_to_file>.opus"

--------

Analysis file names:

It registers with the name

    <file_name>_bitrate.csv
    <file_name>_bitrate.png
    <file_name>_plot.svg
    <file_name>_interactive.html

The location to save the files is the directory where opus_bitrate_analyzer.py is located.
 


