---
layout: page
permalink: /data/
title: Data
description:  
nav: true
nav_order: 3

bibliography: data.bib
---

### Updates

❗️❗️**[2024-09-22]** We have released the labels for the non-blind test dataset. You can download them from [Google Drive](https://drive.google.com/file/d/1fvlrzw1K1YPZcC9GxY7nMNPIxu3-Dx78/view?usp=sharing).

❗️❗️**[2024-09-19]** We have released the official blind test dataset. This is the dataset that will be used for the final ranking. You can download it from [Google Drive](https://drive.google.com/file/d/1qBTHgII6o57tmO8GPIunqZVtZhAu0M__/view?usp=sharing).
> Note that unlike the non-blind test dataset, this dataset contains both simulated audios and real recordings<d-footnote>Their identities won't be revealed.</d-footnote>. The former contains clean reference signals while the latter only has reference transcripts.
>
> So we will only calculate **DNSMOS**, **NISQA**, and **WAcc** metrics for the real recordings.
> For simulated data, all objective metrics listed in the [Rules](/urgent2024/rules) tab will be calculated.
>
> After the leaderboard blind test phase ends (no further submissions accepted), we will additionally
>
>   1. calculate the **POLQA** objective metric for the best submission of each team and insert it into the leaderboard as a part of the `Intrusive SE metric` category.
>   2. obtain the **MOS** subjective score for the best submission of each team via crowd-sourcing based on the ITU-T P.808 standard<d-footnote>Due to our limited resource, we will subsample a fixed 300-sample subset from the full 1000-sample blind test set and use that for MOS evaluation of all teams' submissions. We will make sure the subset preserves as similar as possible the ranking structure of all teams as in the full blind test set. The utterance IDs of the subset will be released.</d-footnote>. This score will be counted as a fifth category (`Subjective SE metric`) in addition to the four categories defined in the [Rules](/urgent2024/rules) tab.
>
> The final ranking will be obtained using the same methodology as defined in the [Rules](/urgent2024/rules) tab, but based on the five categories of metrics.

❗️❗️**[2024-08-20]** We have released the official non-blind test dataset. You can download it from [Google Drive](https://drive.google.com/file/d/1Bcy7vtsZF5kzwrkklQwj6Um4AMlaUHe2/view?usp=sharing).

❗️❗️**[2024-08-20]** We have released the labels for the official validation dataset. You can download them from [Google Drive](https://drive.google.com/file/d/1qYaQKZtvGeRHaoFaeiaaKq5Akvbd2g-9/view?usp=sharing).

❗️❗️**[2024-06-20]** We have released the official (complete) validation dataset. You can download it from [Google Drive](https://drive.google.com/file/d/11D_3-Y1Iugj5jsUvlnaPLxdOSugV9TER/view?usp=sharing).
> Note that this complete validation dataset is intended for assisting the development of challenge systems as well as for a fair comparison. The official validation leaderboard will only use a small portion<d-footnote>This subset can be downloaded from https://urgent-challenge.com/competitions/5#participate-get_data.</d-footnote> of this dataset for evaluation.

### Data description

The training and validation data are both simulated based on the following source data:

<style>
/* Basic */

table {
border-spacing: 0px;
border-collapse: collapse;     /* Share borders between adjacent cells */
width: 100%;
max-width: 100%;
margin-bottom: 15px;
background-color: transparent; /* Change the background-color of table here */
text-align: left;              /* Change the text-alignment of table here */
}

th {
font-weight: bold;
border: 1px solid #cccccc;  /* Change the border-color of heading here */
padding: 8px;
}

td {
border: 1px solid #cccccc;  /* Change the border-color of cells here */
padding: 8px;
}

/* Stylized */

/* Adding Striped Effect for even rows */

tr {
/* background-color: transparent; Change the default background-color of rows here */
background-color: white; /* Change the default background-color of rows here */
}

tr:nth-of-type(2n) {
background-color: #f6f8fa;  /* Change the background-color of even rows here */
}

/* Reset styles for the shortcut helper */
.light-keys tr:nth-of-type(2n) {background-color: black;}
.light-keys tr:hover {background-color: black;}
.light-keys table {border: none;}
.light-keys tr {border: none;}
.light-keys td {border: none;}
.light-keys th {border: none;}

tr th {
background-color: white;    /* Change the background-color of heading here */
}

/* Adding Hover Effect for rows */

tr {
-moz-transition: background-color 300ms ease-in-out 0s;
-ms-transition: background-color 300ms ease-in-out 0s;
-o-transition: background-color 300ms ease-in-out 0s;
-webkit-transition: background-color 300ms ease-in-out 0s;
transition: background-color 300ms ease-in-out 0s;
}

tr:hover {
background-color: #fff176;  /* Change the hover background-color of rows here */
}

/* Removing left and right border of rows for modern UIs */

tr {
border-top: 1px solid #cccccc;
border-bottom: 1px solid #cccccc;
}
</style>
<table>
<colgroup>
<col>
<col>
<col>
<col>
<col>
<col>
</colgroup>
<thead>
  <tr>
    <th>Type</th>
    <th>Corpus</th>
    <th>Condition</th>
    <th>Sampling Frequency (kHz)</th>
    <th>Duration (after pre-processing)</th>
    <th>License</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="5">Speech</td>
    <td>LibriVox data from <a href="https://github.com/microsoft/DNS-Challenge/blob/master/download-dns-challenge-5-headset-training.sh">DNS5 challenge</a></td>
    <td>Audiobook</td>
    <td>8~48</td>
    <td>~350 h</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>LibriTTS reading speech</td>
    <td>Audiobook</td>
    <td>8~24</td>
    <td>~200 h</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>CommonVoice 11.0 English portion</td>
    <td>Crowd-sourced voices</td>
    <td>8~48</td>
    <td>~550 h</td>
    <td>CC0</td>
  </tr>
  <tr>
    <td>VCTK reading speech</td>
    <td>Newspaper, etc.</td>
    <td>48</td>
    <td>~80 h</td>
    <td>ODC-BY</td>
  </tr>
  <tr>
    <td>WSJ reading speech</td>
    <td>WSJ news</td>
    <td>16</td>
    <td>~85 h</td>
    <td>LDC User Agreement</td>
  </tr>
  <tr>
    <td rowspan="2">Noise</td>
    <td>Audioset+FreeSound noise in DNS5 challenge</td>
    <td>Crowd-sourced + Youtube</td>
    <td>8~48</td>
    <td>~180 h</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>WHAM! noise</td>
    <td>4 Urban environments</td>
    <td>48</td>
    <td>~70 h</td>
    <td>CC BY-NC 4.0</td>
  </tr>
  <tr>
    <td rowspan="2">RIR</td>
    <td>Simulated RIRs from DNS5 challenge</td>
    <td><a href="https://www.openslr.org/28/">SLR28</a></td>
    <td>48</td>
    <td>~60k samples</td>
    <td>CC BY 4.0</td>
  </tr>
  <!-- <tr>
    <td>Other RIRs simulated by participants</td>
    <td>-</td>
    <td>8~48</td>
    <td>-</td>
    <td>-</td>
  </tr> -->
</tbody>
</table>

> For participants who need access to the WSJ data, please reach out to the organizers ([urgent.challenge@gmail.com](mailto:urgent.challenge@gmail.com)) for a temporary license supported by LDC.
>
> We also allow participants to simulate their own RIRs using existing tools<d-footnote>For example, <a href="https://github.com/ehabets/RIR-Generator">RIR-Generator</a>, <a href="https://github.com/LCAV/pyroomacoustics">pyroomacoustics</a>, <a href="https://github.com/DavidDiazGuerra/gpuRIR">gpuRIR</a>,  and so on.</d-footnote> for generating the training data.
> The participants can also propose publicly available real recorded RIRs to be included in the above data list during the grace period (See [`Timeline`](/urgent2024/timeline)).
> Note: If participants used additional RIRs to train their model, the related information should be provided in the README.yaml file in the submission. Check the [template](/urgent2024/template) for more information.

### Pre-processing

<img alt="pre-processing" src="/urgent2024/assets/img/preprocessing.png" style="max-width: 100%;"/>

Before simulation, all collected speech and noise data are pre-processed to filter out low-quality samples and to detect the true sampling frequency (SF).
The pre-processing procedure includes:

1. We first estimate the effective bandwidth of each speech and noise sample based on the energy thresholding algorithm proposed in<d-cite key="Hi_Fi-Bakhturina2021"/><d-footnote><a href="https://github.com/urgent-challenge/urgent2024_challenge/blob/main/utils/estimate_audio_bandwidth.py">https://github.com/urgent-challenge/urgent2024_challenge/blob/main/utils/estimate_audio_bandwidth.py</a></d-footnote>. This is critical for our proposed method to successfully handle data with different SFs. Then, we resample each speech and noise sample accordingly to the best matching SF, which is defined as the lowest SF among {8, 16, 22.05, 24, 32, 44.1, 48} kHz that can fully cover the estimated effective bandwidth.
2. A voice activity detection (VAD) algorithm<d-footnote><a href="https://github.com/urgent-challenge/urgent2024_challenge/blob/main/utils/filter_via_vad.py">https://github.com/urgent-challenge/urgent2024_challenge/blob/main/utils/filter_via_vad.py</a></d-footnote> is further used to detect “bad” speech samples that are actually non-speech or mostly silence, which will be removed from the data.
3. Finally, the non-intrusive DNSMOS scores (OVRL, SIG, BAK)<d-cite key="DNSMOS-Reddy2022"/><d-footnote><a href="https://github.com/microsoft/DNS-Challenge/blob/master/DNSMOS/dnsmos_local.py">https://github.com/microsoft/DNS-Challenge/blob/master/DNSMOS/dnsmos_local.py</a></d-footnote> are calculated for each remaining speech sample. This allows us to filter out noisy and low-quality speech samples via thresholding each score<d-footnote><a href="https://github.com/urgent-challenge/urgent2024_challenge/blob/main/utils/filter_via_dnsmos.py">https://github.com/urgent-challenge/urgent2024_challenge/blob/main/utils/filter_via_dnsmos.py</a></d-footnote>.

We finally curated a list of speech sample (~1300 hours) and noise samples (~250 hours) based on the above procedure that will be used for simulating the training and validation data in the challenge.

### Simulation

With the proviced scripts in the next section, the simulation data can be generated offline in two steps.

1. In the first step, a manifest `meta.tsv` is firstly generated by [`simulation/generate_data_param.py`](https://github.com/urgent-challenge/urgent2024_challenge/blob/main/simulation/generate_data_param.py) from the given list of speech, noise, and room impulse response (RIR) samples. It specifies how each sample will be simulated, including the type of distortion to be applied, the speech/noise/RIR sample to be used, the signal-to-noise ratio (SNR), the random seed, and so on.

2. In the second step, the simulation can be done in parallel via [`simulation/simulate_data_from_param.py`](https://github.com/urgent-challenge/urgent2024_challenge/blob/main/simulation/simulate_data_from_param.py) for different samples according to the manifest while ensuring reproducibility. This procedure can be used to generate training and validation datasets.

For the training set, we recommend dynamically generating degraded speech samples during training to increase the data diversity.

#### Simulation metadata

The manifest mentioned above is a `tsv` file containing several columns (separated by `\t`). For example:

| id | noisy_path | speech_uid | speech_sid | clean_path | noise_uid | snr_dB | rir_uid | augmentation | fs | length | text |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|unique ID|path to the generated degraded speech|utterance ID of clean speech|speaker ID of clean speech|path to the paired clean speech|utterance ID of noise|SNR in decibel|utterance ID of the RIR|augmentation type|sampling frequency|sample length|raw transcript|
|fileid_1|simulation_validation/noisy/fileid_1.flac|p226_001_mic1|vctk_p226|simulation_validation/clean/fileid_1.flac|JC1gBY5vXHI|16.106643714525433|mediumroom-Room119-00056|bandwidth_limitation-kaiser_fast->24000|48000|134338|Please call Stella.|
|fileid_2|simulation_validation/noisy/fileid_2.flac|p226_001_mic2|vctk_p226|simulation_validation/clean/fileid_2.flac|file205_039840000_loc32_day1|2.438365163611807|none|bandwidth_limitation-kaiser_best->22050|48000|134338|Please call Stella.|
|fileid_1561|simulation_validation/noisy/fileid_1561.flac|p315_001_mic1|vctk_p315|simulation_validation/clean/fileid_1561.flac|AvbnjyrHq8M|1.3502745341597029|mediumroom-Room076-00093|clipping(min=0.016037324066971528,<wbr>max=0.9890219800761639)|48000|114829|&lt;not-available&gt;|


**Note**

* If the `rir_uid` value is not `none`, the specified RIR is applied to the clean speech sample.

* If the `augmentation` value is not `none`, the specified augmentation is applied to the degraded speech sample.

* `<not-available>` in the `text` column is a placeholder for transcripts that are not available.

* The audios in `noisy_path`, `clean_path`, and (optional) `noise_path` are consistently scaled such that `noisy_path = clean_path + noise_path`.

* However, the scale of the enhanced audio is not critical for objective evaluation the challenge, as the evaluation metrics are made largely insensitive to the scale. For subjective listening in the final phase, however, it is recommended that the participants properly scale the enhanced audios to facilitate a consistent evaluation.

* For all different distortion types, the original sampling frequency of each clean speech sample is always preserved, i.e., the degraded speech sample also shares the same sampling frequency. For `bandwidth_limitation` augmentation, this means that the generated speech sample is resampled to the original sampling frequency `fs`.

### Code

The data preparation and simulation scripts are available at [https://github.com/urgent-challenge/urgent2024_challenge](https://github.com/urgent-challenge/urgent2024_challenge).

