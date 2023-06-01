---
title: A processing framework to access large quantities of whispered speech found in ASMR
description: Extracting clean whispered speech from noisy samples based on whisper activity detection
permalink: /cwad
---
# A processing framework to access large quantities of whispered speech found in ASMR

##### [Pablo Pérez Zarazaga][pablo_profile], [Gustav Eje Henter][gustav_profile], [Zofia Malisz][zofia_profile]

<head> 
<link rel="apple-touch-icon" sizes="180x180" href="favicon/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="favicon/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="favicon/favicon-16x16.png">
<link rel="manifest" href="/site.webmanifest">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
</head>
<!-- This post presents CWAD, a deep-learning framework to automatically label large amounts of clean whispered speech, applied to ASMR recordings extracted from YouTube -->

[github_link]: https://github.com/perezpoz/CleanWhisperDetection
[gustav_profile]: https://people.kth.se/~ghe/
[pablo_profile]: https://www.kth.se/profile/pablopz
[zofia_profile]: https://www.kth.se/profile/malisz
[paper_link]: https://arxiv.org/abs/2303.07442
[youtubedl_link]: https://github.com/ytdl-org/youtube-dl
[edyson_link]: https://github.com/perfall/Edyson

## Citation information

```
@inproceedings{perez2023cwad,
   title={A processing framework to access large quantities of whispered speech found in ASMR},
   author={Pablo Pérez Zarazaga and Gustav Eje Henter and Zofia Malisz},
   booktitle={Proc. ICASSP},
   year={2023}
 }
```

## Summary

The goal of this work is to develop a framework for whisper activity detection (WAD) for extraction of clean whisper unaffected by noises for whispered data collection.

One of the main problems in the analysis of whispered speech is the limited amount of data available, and most specifically, spontaneous whispered speech. A great source of whispered speech data are ASMR recordings available in streaming platforms like YouTube or Twitch. For that reason we propose to use tools like [Youtube-DL][youtubedl_link] to collect ASMR recordings, which can be used as a source of whispered speech.

We propose to train a WAD method on a synthetic noisy whispered dataset. The trained model is then used to detect whispered speech in ASMR recordings. Using [Edyson][edyson_link] to more accurately separate segments into "clean whisper" - "noisy whisper" - "noise".

The separated ASMR data is used for speech data augmentation and the proposed clean WAD (CWAD) model is trained using the specific ASMR triggers as noise.

ASMR data is used as an example of a great source of whispered speech available online. However, this framework could be adapted to other noisy whispered speech sources.

For more information, please see [our paper at ICASSP 2023][paper_link].

## Visual overview

![Clean Whispered Activity Detector](./images/Pipeline.png "Pipeline for training of the proposed CWAD.")

## Code

Code will be made available in [our GitHub repository][github_link] shortly.

<style type="text/css">
  .tg {
    border-collapse: collapse;
    border-color: #9ABAD9;
    border-spacing: 0;
  }

  .tg td {
    background-color: #EBF5FF;
    border-color: #9ABAD9;
    border-style: solid;
    border-width: 1px;
    color: #444;
    font-family: Arial, sans-serif;
    font-size: 14px;
    overflow: hidden;
    padding: 0px 20px;
    word-break: normal;
    font-weight: bold;
    vertical-align: middle;
  }

  .tg th {
    background-color: #409cff;
    border-color: #9ABAD9;
    border-style: solid;
    border-width: 1px;
    color: #fff;
    font-family: Arial, sans-serif;
    font-size: 14px;
    font-weight: normal;
    overflow: hidden;
    padding: 0px 20px;
    word-break: normal;
    font-weight: bold;
    vertical-align: middle;

  }

  .tg .tg-0pky {
    border-color: inherit;
    text-align: center;
    vertical-align: top,
  }

  .tg .tg-fymr {
    border-color: inherit;
    font-weight: bold;
    text-align: center;
    vertical-align: top
  }
  .slider {
  -webkit-appearance: none;
  width: 75%;
  height: 15px;
  border-radius: 5px;  
  background: #d3d3d3;
  outline: none;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  border-radius: 50%; 
  background: #409cff;
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #409cff;
  cursor: pointer;
}
</style>

## Whisper activity detection

The following audio samples show the classification of ASMR segments by the CWAD method into clean whispered speech and speech affected by ASMR triggers or noise.

In the first set of recordings we observe relatively clean whispered speech with distinct noises like microphone rubbing or tapping. Whispered speech is clearly detected, and removed when it is combined with these type of distinctive noises. Breathing sounds, however, are more challenging as they are produced isolated from speech and also at the beginning of some words, therefore, the inintial moments of some words are still considered as noise.

<table class="tg">
  <thead>
    <tr>
      <th class="tg-0pky">Speaker</th>
      <th class="tg-0pky" colspan="1">Original ASMR sample</th>
      <th class="tg-0pky" colspan="1">CWAD Clean Whispered Segments</th>
      <th class="tg-0pky" colspan="1">CWAD Noisy Whispered Segments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td nowrap="" class="tg-0pky"><b>Male</b></td>
      <td class="tg-0pky">
        <audio id="audio-small" controls="">
          <source src="./Samples/Male1_Full.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Male1_Speech.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Male1_Noise.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td nowrap="" class="tg-0pky"><b>Female</b></td>
      <td class="tg-0pky">
        <audio id="audio-small" controls="">
          <source src="./Samples/Female3_Full.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Female3_Speech.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Female3_Noise.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
    </tr>
  </tbody>
</table>

In the second set of samples, we can see a different type of whispered speech used in ASMR, known as "inaudible whisper". This type of speech contains more breathing sounds and sometimes it is hard to distinguish the actual speech. However, it can still be detected as whispered speech when it is found in relatively clean environments.

<table class="tg">
  <thead>
    <tr>
      <th class="tg-0pky">Speaker</th>
      <th class="tg-0pky" colspan="1">Original ASMR sample</th>
      <th class="tg-0pky" colspan="1">CWAD Clean Whispered Segments</th>
      <th class="tg-0pky" colspan="1">CWAD Noisy Whispered Segments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td nowrap="" class="tg-0pky"><b>Male</b></td>
      <td class="tg-0pky">
        <audio id="audio-small" controls="">
          <source src="./Samples/Male2_Full.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Male2_Speech.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Male2_Noise.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
    </tr>
  </tbody>
  
  <tbody>
    <tr>
      <td nowrap="" class="tg-0pky"><b>Female</b></td>
      <td class="tg-0pky">
        <audio id="audio-small" controls="">
          <source src="./Samples/Female2_Full.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Female2_Speech.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Female2_Noise.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
    </tr>
  </tbody>
</table>

Finally, we can observe a set of different mouth sounds produced by the "ASMRtists" and more stationary noises due to the background in the recordings and continuous triggers like microphone rubbing. The system separates the segments with clean speech from those combined with noises like microphone rubbing and other mouth effects, but the constant background noise reduces the accuracy of the detection. It is still to be determined if a certain level of background noise would be acceptable in these recordings or it should be removed before the analysis.

<table class="tg">
  <thead>
    <tr>
      <th class="tg-0pky">Speaker</th>
      <th class="tg-0pky" colspan="1">Original ASMR sample</th>
      <th class="tg-0pky" colspan="1">CWAD Clean Whispered Segments</th>
      <th class="tg-0pky" colspan="1">CWAD Noisy Whispered Segments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td nowrap="" class="tg-0pky"><b>Male</b></td>
      <td class="tg-0pky">
        <audio id="audio-small" controls="">
          <source src="./Samples/Male3_Full.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Male3_Speech.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Male3_Noise.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
    </tr>
  </tbody>
  
  <tbody>
    <tr>
      <td nowrap="" class="tg-0pky"><b>Female</b></td>
      <td class="tg-0pky">
        <audio id="audio-small" controls="">
          <source src="./Samples/Female1_Full.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Female1_Speech.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
      <td class="tg-0pky">
        <audio controls="">
          <source src="./Samples/Female1_Noise.wav" type="audio/wav" preload="none"/>
        </audio>
      </td>
    </tr>
  </tbody>
</table>

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fperezpoz.github.io%2Fcwad%2F&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)
