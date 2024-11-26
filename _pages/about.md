---
layout: default
title: About
permalink: /
subtitle: Universality, Robustness, and Generalizability for EnhancemeNT

profile:
  align: right
  image: 
  image_circular: false # crops the image to make it circular
  address: >

news: true  # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}"
social: false  # includes social icons at the bottom of the page

bibliography: about.bib
---


<div style="text-align: center;">
    <img alt="introduction" src="/urgent2025/assets/img/urgent2025.png" style="max-width: 90%;" />
</div>

<!-- <p>We can also cite <d-cite key="VoiceFixer-Liu2022"></d-cite> external publications.</p>

<d-math block>
  \mathbb{E}_{z \sim q_\phi(z|x)}
</d-math>

Hi <d-footnote>This is a footnote.</d-footnote> how are you?

<d-code block language="python">
import torch

if isinstance(speech_mix, np.ndarray):
    speech_mix = torch.as_tensor(speech_mix)
</d-code> -->

## Interspeech URGENT 2025 Challenge

The Interspeech 2025 URGENT challenge (Universality, Robustness, and Generalizability for EnhancemeNT) is a speech enhancement challenge held at [**Interspeech 2025**](https://www.interspeech2025.org/home). We aim to build universal speech enhancement models for unifying speech processing in a wide variety of conditions.

- Data preparation script: [https://github.com/urgent-challenge/urgent2025_challenge](https://github.com/urgent-challenge/urgent2025_challenge)
- Official validation set for leaderboard submission: [https://drive.google.com/file/d/1Ip-C5tUNGCssT8KAjHUUoh99jkzRH6nm/view](https://drive.google.com/file/d/1Ip-C5tUNGCssT8KAjHUUoh99jkzRH6nm/view)
- Baseline script: [https://github.com/kohei0209/espnet/tree/urgent2025/egs2/urgent25/enh1](https://github.com/kohei0209/espnet/tree/urgent2025/egs2/urgent25/enh1)
- Baseline pre-trained model [https://huggingface.co/kohei0209/tfgridnet_urgent25/tree/main](https://huggingface.co/kohei0209/tfgridnet_urgent25/tree/main)
- Slack channel: [https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g](https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g)


## Goal

The Interspeech 2025 URGENT challenge aims to bring more attention to constructing Universal, Robust and Generalizable speech EnhancemeNT models.
This year's challenge focuses on the following aspects:

1. To adress 7 types of distortions
    - To improve the universality of SE systems, we consider the following distortions: **additive noise, reverberation, clipping, bandwidth extension, codec artifacts, packet loss, and wind noise**.
2. To build a robust model on multilingual speech
    - Most SE research focuses on English data and language dependency of SE systems are still under-explored, particulary for generative models. This challenge includes 5 languages, **English, German, French, Spanish, and Chinese**. 
3. To leverage noisy but diverse data
    - How to incorporate noisy speech in training is an important topic to scale up the data amount and diversity. **We intentionally included some noisy dataset (CommonVoice) so that participants can investigate how to leverage such data (e,g, data filtering or semi-supervised learning)**.
4. To handle inputs with multiple smapling rates
    - As in the former "NeurIPS 2024 URGENT challenge", **the model has to accept audios with the following sampling rates**: 8k, 16k, 22.05k, 24k, 44.1k, and 48kHz.


## Task Introduction

The task of this challenge is to build **a single speech enhancement system** to adaptively handle input speech with different distortions (corresponding to different SE subtasks) and different input formats (e.g., sampling frequencies) in different acoustic environments (e.g., noise and reverberation).

The training data will consist of several public corpora of speech, noise, and RIRs. **Only the specified set of data can be used during the challenge**. We encourage participants to apply data augmentation techniques such as dynamic mixing to achieve the best generalizability. The data preparation scripts are released in our GitHub repository<d-footnote><a href="https://github.com/urgent-challenge/urgent2025_challenge/" target="_blank">https://github.com/urgent-challenge/urgent2025_challenge/</a></d-footnote>. Check the [`Data`](/urgent2025/data) tab for more information.

<!--
We also provide baselines in the [ESPnet](https://github.com/espnet/espnet) toolkit to facilitate the system development. Check the [`Baseline`](/urgent2025/baseline) tab for more information.
-->

We will evaluate enhanced audios with a variety of metrics to comprehensively understand the capacity of existing generative and discriminative methods. They include four different categories of metrics<d-footnote>An additional category (subjective SE metrics) will be added for the final blind test phase for evaluating the MOS score.</d-footnote>:

1. non-intrusive metrics (e.g., DNSMOS, NISQA) for reference-free speech quality evaluation.
2. intrusive metrics (e.g., PESQ, STOI, SDR, MCD) for objective speech quality evaluation.
3. downstream-task-independent metrics (e.g., Levenshtein phone similarity) for language-independent, speaker-independent, and task-independent evaluation.
4. downstream-task-dependent metrics (e.g., speaker similarity, word accuracy or WAcc) for evaluation of compatibility with different downstream tasks.

More details about the evaluation plan can be found in the [`Rules`](/urgent2025/rules) tab.


## Two tracks
The URGENT 2025 challenge has two tracks with different data scales. **Participants may participate in track 1, track 2, or both.** The same test set will be utilized in two tracks.
- **Track 1**: We limit the duration of some big corpora (MLS and CommonVoice). The first-track dataset has ~2.5k hours of speech and ~0.5k hours of noise.
- **Track 2**: We do not limit the duration of MLS and CommonVoice datasets, resulting in ~60k hours of speech.


**We characterize the first track as a primary track to compare the techniques with the same data and the second track as a secondary one to provide insights into data scaling**.
Since the data scale in the Track 2 is huge, **we encourage participants to participate in Track 1 first**.
However, if interested in data scaling or data-hungry methods (e.g., speechLM or SSL-based methods), the Track 2 welcomes you!

Note that although the dataset in Track 2 is huge, **participants do not have to use all the data**.
Participants may want to start by training the best system developed in track1 with some data from track2.
Data selection techniques (e.g., based on diversity or estimated MOS scores) would be helpful to efficiently train the model.


## Communication
We have a [Slack channel](https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g) for real-time communication.


## Motivation

Recent decades have witnessed rapid development of deep learning-based speech enhancement (SE) techniques, with impressive performance in matched conditions. However, most conventional speech enhancement approaches focus only on a limited range of conditions, such as single-channel, multi-channel, anechoic, monolingual, and so on.
In many existing works, researchers tend to only train SE models on one or two common datasets, such as the VoiceBank+DEMAND<d-footnote><a href="https://datashare.ed.ac.uk/handle/10283/2791">https://datashare.ed.ac.uk/handle/10283/2791</a></d-footnote> and Deep Noise Suppression (DNS) Challenge datasets.

The evaluation is often done only on simulated conditions that are similar to the training setting. Meanwhile, in earlier SE challenges such DNS series, the choice of training data was also often left to the participants. This led to the situation that models trained with a huge amount of private data were compared to models trained with a small public dataset. This greatly impedes understanding of the generalizability and robustness of SE methods comprehensively. In addition, the model design may be biased towards a specific limited condition if only a small amount of data is used. The resultant SE model may also have limited capacity to handle more complicated scenarios.

Apart from conventional discriminative methods, generative methods have also attracted much attention in recent years. They are good at handling different distortions with a single model<d-cite key="UNIVERSE-Serra2022,VoiceFixer-Liu2022"/> and tend to generalize better than discriminative methods<d-cite key="Conditional-Lu2022"/>. However, their capability and universality have not yet been fully understood through a comprehensive benchmark.

Meanwhile, recent efforts<d-cite key="Toward-Zhang2023,Improving-Zhang2024"/> have shown the possibility of building a single system to handle various input formats, such as different sampling frequencies and numbers of microphones.
However, a well-established benchmark covering a wide range of conditions is still missing, and no systematic comparison has been made between state-of-the-art (SOTA) discriminative and generative methods regarding their generalizability.

Existing speech enhancement challenges have fostered the development of speech enhancement models for specific conditions, such as denoising and dereverberation<d-cite key="DNS1-Reddy2020,DNS2-Reddy2021,DNS3-Reddy2021,DNS4-Dubey2022,DNS5-Dubey2024"/>, speech restoration<d-cite key="SIG1-Cutler2024,SIG2-Ristea2024"/>, packet loss concealment<d-cite key="PLC1-Diener2022,PLC2-Diener2024"/>, acoustic echo cancellation<d-cite key="AEC1-Sridhar2021,AEC2-Cutler2021,AEC3-Cutler2022,AEC4-Cutler2024"/>, hearing aids<d-cite key="Clarity1-Graetzer2021,Clarity2-Akeroyd2023,Clarity2-Cox2023"/>, 3D speech enhancement<d-cite key="L3DAS21-Guizzo2021,L3DAS22-Guizzo2022,L3DAS23-Marinoni2023,L3DAS23-Gramaccioni2024"/>, far-field multi-channel speech enhancement for video conferencing<d-cite key="ConferencingSpeech-Rao2021"/>, unsupervised domain adaptation for denoising<d-cite key="CHiME7-Leglaive2023"/>, and audio-visual speech enhancement<d-cite key="AVSE-Blanco2023"/>. These challenges have greatly enriched the corpora in speech enhancement studies. However, there still lacks a challenge that can benchmark the generalizability of speech enhancement systems in a wide range of conditions.

The first edition of the URGENT challenge series, NeurIPS 2024 URGENT challenge, aimed at comprehensively evaluate the universality, robustness, and generalizability of SE systems.
The systems which handles (i) 4 types of distortions (additive noise, reverberation, clipping, and bandwidth limitation) and (ii) various sampling rates were trained on a large-scale dataset and evaluated using as many as 12 objective metrics and human listening.
We provided one of the state-of-the-art models in SE, TF-GridNet, as the baseline and 14 teams improved performance over such a strong baseline, which greatly contributes to further development of universal SE systems.
However, the first challenge had some limitations: (i) it covered on 4 types of distortions (ii) it had only English data, and (iii) data filtering applied to some noisy corpora did not perfectly filter out noisy samples.

To go step further, the Interspeech 2025 URGENT challenge extends the former one as follows: (i) it covers 3 more types of distortions (7 in total) to improve universality, (ii) it has multlingual speech to investigate the language dependency of SE models, particularly that of generative models, and (iii) it intentionally includes some noisy samples to investigate how to effectively utilize/filter out them. In addition, the challenge has two tracks with different data scales, allowing participants to investigate the scalability of SE systems, which has so far been under-explored in SE community.
We believe that building robust and generalizable universal SE systems is one of the imporant topics and the challenge greatly contributes to future SE research.


<!-- Similar issues can also be observed in other speech tasks such as automatic speech recognition (ASR), speech translation (ST), speaker verification (SV), and spoken language understanding (SLU).
Among them, speech enhancement is particularly vulnerable to mismatches since it is heavily reliant on paired clean/noisy speech data to achieve strong performance. Unsupervised speech enhancement that does not require groundtruth clean speech has been proposed to address this issue, but often merely brings benefit in a final finetuning stage<d-cite key="Employing-Xu2024"/>. Therefore, we focus on speech enhancement in this challenge to address the aforementioned problems. -->

<!-- Be sure to list "URGENT Challenge: Universality, Robustness, and Generalizability for EnhancemeNT" as your paper subject area when making a submission. -->
