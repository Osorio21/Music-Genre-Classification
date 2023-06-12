# Music-Genre-Classification
---

## Table of Contents

- [Project Structure](#project_structure)
- [Problem Statement](#problem_state)
- [Data Description](#data_used)
- [Extracted Feature Dataset](#data_d)
- [Methodology](#methodology)
- [Conclusions & Recommendations](#conclusion)
- [Next Steps](#next_steps)
- [Sources](#sources)


## Project Structure<a id='project_structure'></a>

```


├── code
│   ├── 01_Introduction.ipynb
│   ├── 02_EDA_and_Feature_Extraction.ipynb
│   ├── 03_Modeling.ipynb
│   └── 04_Neural_Networks.ipynb
├── data
│   └── genre_numerical_data.csv
├── images
│   └── external
├── presentation
│   └── Presentation.pdf
└── README.md

```


## Problem Statement<a id='problem_state'></a>
---

Music streaming services are quite ubiquitous in our society.

> * Global music subscribers surged 26.4% to 523.9 million during the Covid pandemic.
> * Music streaming makes up 84% of the U.S. music industry revenue.
> * 82.1 million Americans are paid subscribers to on-demand music streaming. <sup>1</sup>


The enormous demand for music streaming services presents a number of problems for companies that hosts large amounts of music. Each of these companies not only offers a large amount of music, they also gain new audio daily at an alarming rate. In 2022, Apple Music boasted 100 million songs in its library.<sup>2</sup> Luminate posits that 120,000 new songs are added to streaming platforms daily.<sup>3</sup> Streaming platforms need ways to accurately classify audio before assimilation into their libraries. This ensures the music is appropriately categorized for further use in effective segmentation efforts, personalized playlists, recommendations, and marketing. 

This project aims to develop music classification models with the utilization of the audio collected for the GTZAN study.<sup>4</sup> The audio collection consists of 1000, 30 second music samples from 10 different genres. As part of this study, participants classified music by genre with an accuracy of 70%. The goal of this project is to build a model that exceeds this accuracy level. A variety of classification models are tested such as Logistic Regression, Ridge Classifier, XGBClassifier, Linear Discriminant Analysis, and Linear Support Vectors. The developed models can become tools used by streaming companies to further create effective, personalized music experiences for their consumers. 

### Background Research

**Sound Waves**

Sound waves are a type of energy that’s released when an object vibrates. These acoustic waves travel from their source through air or another medium. Our brains translate the pressure waves into understandable words, music, or signals.

A sound's speed refers to how fast the waves move from peak to trough and back to peak. The technical term is frequency. It is measured in hertz (Hz), which represents cycles-per-second. Faster frequencies correspond to higher-pitched sounds. 

Amplitude equates to a sound’s volume or intensity. Amplitude is measured in decibels (dB), a logarithmic scale.

Timbre is determined by the unique harmonics formed by the combination of notes in a chord. "The way these sound together helps keep a piano from sounding like a guitar, or an angry grizzly bear from sounding like a rumbling tractor engine.<sup>5</sup>

**Analog-Digital Conversion**

Analog sound is a continuous signal with infinite amplitude values at any one point in time. Digital audio is a representation of sound converted into a digital signal. During the analog to digital conversion process, amplitudes of an analog sound wave are captured at a specified sample rate and bit depth and converted into data. The higher the sample rate and bit depth, the higher the audio resolution.<sup>6</sup>


## Data Description<a id='data_used'></a>

---

This audio collection was curated by George Tzanetakis and Perry Cook for use in their 2002 study, "Musical genre classification of audio signals".

> #### Dataset
"To ensure variety of different recording qualities the excerpts were taken from radio, compact disks, and
MP3 compressed audio files. The files were stored as 22 050 Hz, 16-bit, mono audio files. An effort was made to ensure that
the training sets are representative of the corresponding musical genres. The Genres dataset has the following classes: classical, country, disco, hiphop, jazz, rock, blues, reggae, pop, metal."<sup>4</sup>

> #### Human Study
"Using a ten-way forced-choice paradigm college students were able to accurately judge (53% correct) after listening to only 250-ms samples and (70% correct)after listening to 3 s (chance would be 10%). Listening to more than 3 s did not improve their performance. The subjects where trained using representative samples from each genre. The ten genres used in this study were: blues, country, classical, dance, jazz, latin, pop, R&B, rap, and rock."<sup>4</sup>

## Extracted Feature Dataset<a id='data_d'></a>

---

[Genre Dataset](./data/genre_numerical_data.csv) contains 1000 observations and 186 features.


## Methodology<a id='methodology'></a>

---

### 1. [Introduction](./code/01_Introduction.ipynb)

> * Overview of dataset and motivations for project are presented. 
> * Research  on several relevant features to be extracted from audio samples was displayed. 

### 2. [Exploratory Data Analysis & Feature Extraction](./code/02_EDA_and_Feature_Extraction.ipynb)

>* Samples from each genre were examined from a multitude of perspectives.
>* Numerous time and time-frequency domain features were extracted with the [`librosa`] library.
>* Similarities and differences among the genres was analyzed though use of extracted features.

### 3. [Modeling](./code/03_Modeling.ipynb)

>* A plethora of models were tested end evaluated on accuracy.
>* The best performing models were Logistic Regression, Ridge Classifier, XGBoost Classifier, Linear Discriminant Analysis, Linear Support Vectors, and various ensemble models. 
>* Confusion matrices were constructed to determine the strengths and weaknesses of each model. 

### 4. [Neural Networks](./code/04_Neural_Networks.ipynb)

>* Several neural networks were constructed using both numerical and image data.
>* The best performing model was the MLP Classifier. 
>* Confusion matrices were constructed to determine the strengths and weaknesses of each model. 

### Metrics Summary


|             **Model**            | **Training Accuracy** | **Testing Accuracy** |
|:--------------------------------:|-----------------------|----------------------|
| **Linear Discriminant Analysis** |          .93          |          .82         |
|      **Stacking Classifier**     |          .95          |          .82         |
|       **Voting Classifier**      |          .94          |          .79         |
|    **Linear Support Vectors**    |          .87          |          .77         |
|       **Ridge Classifier**       |          .89          |          .77         |
|        **MLP Classifier**        |           1           |          .77         |
|      **Logistic Regression**     |          .89          |          .76         |
|            **XGBoost**           |           1           |          .74         |



## Conclusions & Recommendations<a id='conclusion'></a>

---

Each of these models performed better than the people in the GTZAN study relevant to accuracy. However, all models are overfit. More work needs to be done to reduce the variance. As mentioned, the LDA and Stacking Classifiers are the best performers and most likely candidates for use in actual production. All models struggled in classfying genres most likely due to the number of classes and the similarities shared among the classes. Nevertheless, the performance of these models suggests that there can be effective use of machine learning in classifying music. Streaming companies can greatly benefit from the use of machine learning to better arrange its music to provide the best experience for its customers.

## Next Steps<a id='next_steps'></a>

---


* Data is limited to only 1000 samples. Increased training and testing sizes may lead to different conclusions.
* Some of the genres are immensely broad. Finding different data sets could be crucial for creating a more flexible model.
* Additionally, some of the samples may not be extremely representative of genre.
* Benchmark accuracy is based on participation in classification experiment. This may not have been random.
* All models could be improved with increased hyperparameter tuning and more sophisticated feature engineering.
* Experimenting with class imbalance may yield other interesting findings.

## Sources<a id='sources'></a>

---

1. [Music Streaming Statistics in 2023](https://musicalpursuits.com/music-streaming/)
1. [Celebrating 100 million songs](https://www.apple.com/uk/newsroom/2022/10/celebrating-100-million-songs/)
1. [120,000 NEW TRACKS RELEASED ON STREAMING SERVICES EVERY DAY, REPORT FINDS](https://mixmag.net/read/120-000-new-tracks-are-released-on-streaming-services-every-day-report-finds-tech#:~:text=A%20new%20report%2C%20made%20by,work%20%2D%20according%20to%20the%20report.)
1. [Musical Genre Classification of Audio Signals](https://www.cs.cmu.edu/~gtzan/work/pubs/tsap02gtzan.pdf)
1. [How do sound waves work?](https://www.popsci.com/reviews/what-are-sound-waves/)
1. [Digital Audio Basics: Audio Sample Rate and Bit Depth](https://www.izotope.com/en/learn/digital-audio-basics-sample-rate-and-bit-depth.html)
1. [What is Tempo in Music: How Time Connects All Music](https://blog.landr.com/what-is-tempo/)
1. [LearningfromAudio](https://github.com/Osorio21/LearningfromAudio/blob/master/2%20-%20Time%20Domain%20Features.ipynb)
1. [Analysis of the Amplitude Envelopes of Various Music Genre Tracks](https://www.analyticsvidhya.com/blog/2022/05/analysis-of-the-amplitude-envelopes-of-various-music-genre-tracks/)
1. [RMS Level for Mastering: Achieving the Perfect Loudness](https://emastered.com/blog/rms-level-for-mastering#:~:text=What%20is%20RMS%3F,average%20of%20the%20audio%20signal.)
1. [Comparison of the RMS Energy and the Amplitude Envelope](https://www.analyticsvidhya.com/blog/2022/05/comparison-of-the-rms-energy-and-the-amplitude-envelope/)
1. [Analysis of Zero Crossing Rates of Different Music Genre Tracks](https://www.analyticsvidhya.com/blog/2022/01/analysis-of-zero-crossing-rates-of-different-music-genre-tracks/#:~:text=Zero%2DCrossing%20Rate%3A%20The%20zero,retrieval%20for%20classifying%20percussive%20sounds)
1. [Fast Fourier Transformation FFT - Basics](https://www.nti-audio.com/en/support/know-how/fast-fourier-transform-fft)
1. [Short-time Fourier transform](https://en.wikipedia.org/wiki/Short-time_Fourier_transform)
1. [What is a Spectrogram?](https://pnsn.org/spectrograms/what-is-a-spectrogram#:~:text=A%20spectrogram%20is%20a%20visual,present%20in%20a%20particular%20waveform.)
1. [Learning from Audio: Spectrograms](https://towardsdatascience.com/learning-from-audio-spectrograms-37df29dba98c)
1. [Spectral Centroid](https://en.wikipedia.org/wiki/Spectral_centroid)
1. [A Tutorial on Spectral Feature Extraction for Audio Analytics](https://analyticsindiamag.com/a-tutorial-on-spectral-feature-extraction-for-audio-analytics/)
1. [Spectral Contrast](https://librosa.org/doc/0.10.0/generated/librosa.feature.spectral_contrast.html#librosa.feature.spectral_contrast)
1. [Spectral Flatness](https://en.wikipedia.org/wiki/Spectral_flatness)
1. [Learning from Audio: Pitch and Chromagrams](https://towardsdatascience.com/learning-from-audio-pitch-and-chromagrams-5158028a505)
1. [Librosa HPSS](https://librosa.org/doc/0.10.0/generated/librosa.effects.hpss.html#librosa.effects.hpss)
1. [Harmonic–Percussive Separation (HPS)](https://www.audiolabs-erlangen.de/resources/MIR/FMP/C8/C8S1_HPS.html)
1. [Intuitive understanding of MFCCs](https://medium.com/@derutycsl/intuitive-understanding-of-mfccs-836d36a1f779)