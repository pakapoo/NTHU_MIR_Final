# NTHU_MIR_Final
#### Final project for NTHU music information retrieval

### Introduction
Fingerstyle guitar refers to a style of guitar playing technique in which a player plucks guitar with finger instead of pick. There are fingerstyle players who play accompaniment for a singer and players who solo without a singer.  In our research, we focus on the latter, and specifically those who “cover” another song. By “cover”, we mean that a player tries to perform another song with merely a guitar. It is an arduous and painstaking work to compose fingerstyle music, because one not only has to take care of the melody of the original song but also its chord and bass notes. \
We want to see if there are rules to compose fingerstyle music. Here, we aim to identify the notes difference between fingerstyle music and their corresponding band music.

### Process
We can break down the process into several steps:
1. Extract chorus from fingerstyle music and original band music
2. Perform source separation on band music, and get the vocal and bass track
3. Perform bass and melody extraction on fingerstyle music, and get two tracks of audio
4. Perform music transcription on the output of step 3 and 4
5. Side by side comparison for the result of step 4 and see the difference between fingertsyle composition and original music
<br>
<img width="896" alt="nthu_mir_final_process" src="https://github.com/pakapoo/NTHU_MIR_Final/assets/45991312/df05de77-b5d5-4130-8865-e4301e4d1569">

### File structure
All the code is placed in the **code** folder:
* download_YT_wav.ipynb: download audio files from Youtube and convert to wav format
* pychorus.ipynb: excerpt chorus with pychorus library
* track_separation.ipynb: perform source separation with Demucs v4 and Open-Unmix model
* low_high_separation.ipynb: separate low (bass) and high frequency (melody) with STFT/iSTFT and butterworth filter
* music_transcription.ipynb: convert audio files to MIDI format with onset detection and pitch redection. Finally visualize with matplotlib.

Audio inputs and outputs are placed in **audio** folder:
* Chorus Extraction:
  - Input
    - Band music: audio/band/full
    - Fingerstyle music: audio/fingerstyle/full
  - Output
    - Band music: audio/band/chorus/original
    - Fingerstyle music: audio/fingerstyle/chorus/original
* Source separation for band music:
  - Input: audio/band/chorus/original
  - Output
    - Separation using Demucs: audio/band/chorus/demucs_separated/htdemucs
    - Separation using Open-Unmix: audio/band/chorus/Open-Unmix_separated
* Bass and melody separation for fingerstyle music:
  - Input: audio/fingerstyle/chorus/original
  - Output: audio/fingerstyle/chorus/separated
* Music Transcription:
  - Input
    - Band music using Demucs: audio/band/chorus/demucs_separated/htdemucs
    - Band music using Open-Unmix: audio/band/chorus/Open-Unmix_separated
    - Fingerstyle music: audio/fingerstyle/chorus/separated
  - Output: presented in jupyter notebook
