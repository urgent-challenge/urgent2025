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


<img alt="introduction" src="/urgent2025/assets/img/intro.png" style="max-width: 100%;"/>

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

URGENT 2025 (Universality, Robustness, and Generalizability for EnhancemeNT) is a speech enhancement challenge held at [**Interspeech 2025**](https://www.interspeech2025.org/home). We aim to build universal speech enhancement models for unifying speech processing in a wide variety of conditions.

## Goal

Based on the increasing interest in the generalizability of speech enhancement models, we propose the URGENT Challenge that aims to: 

1. Bring more attention to constructing universal speech enhancement models with strong generalizability.
2. Push forward the progress of speech enhancement research towards more realistic scenarios with a comprehensive evaluation.
3. Provide insightful and systematic comparison between SOTA discriminative and generative methods in a wide range of conditions, including different distortions and input formats (sampling frequencies and number of microphones).
4. Provide a benchmark for this direction so that researchers can easily compare different methods.
5. Allow conclusiveness of method comparisons by providing a set of training data that is exclusive and mandatory for all models.


## Task Introduction

The task of this challenge is to build **a single speech enhancement system** to adaptively handle input speech with different distortions (corresponding to different SE subtasks) and different input formats (e.g., sampling frequencies) in different acoustic environments (e.g., noise and reverberation).

The training data will consist of several public corpora of speech, noise, and RIRs. Only the specified set of data can be used during the challenge. We encourage participants to apply data augmentation techniques such as dynamic mixing to achieve the best generalizability. The data preparation scripts are released in our GitHub repository<d-footnote><a href="https://github.com/urgent-challenge/urgent2024_challenge/" target="_blank">https://github.com/urgent-challenge/urgent2024_challenge/</a></d-footnote>. Check the [`Data`](/urgent2025/data) tab for more information.

We also provide baselines in the [ESPnet](https://github.com/espnet/espnet) toolkit to facilitate the system development. Check the [`Baseline`](/urgent2025/baseline) tab for more information.

We will evaluate enhanced audios with a variety of metrics to comprehensively understand the capacity of existing generative and discriminative methods. They include four different categories of metrics<d-footnote>An additional category (subjective SE metrics) will be added for the final blind test phase for evaluating the MOS score.</d-footnote>:

1. non-intrusive metrics (e.g., DNSMOS, NISQA) for reference-free speech quality evaluation.
2. intrusive metrics (e.g., PESQ, STOI, SDR, MCD) for objective speech quality evaluation.
3. downstream-task-independent metrics (e.g., Levenshtein phone similarity) for language-independent, speaker-independent, and task-independent evaluation.
4. downstream-task-dependent metrics (e.g., speaker similarity, word accuracy or WAcc) for evaluation of compatibility with different downstream tasks.

More details about the evaluation plan can be found in the [`Rules`](/urgent2025/rules) tab.

## Communication

[Join our Slack workspace](https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g) for real-time communication.

<!-- ## Paper Submission

Participants may feel free to submit their system description paper to any conference. -->

## Motivation

Recent decades have witnessed rapid development of deep learning-based speech enhancement (SE) techniques, with impressive performance in matched conditions. However, most conventional speech enhancement approaches focus only on a limited range of conditions, such as single-channel, multi-channel, anechoic, and so on.
In many existing works, researchers tend to only train SE models on one or two common datasets, such as the VoiceBank+DEMAND<d-footnote><a href="https://datashare.ed.ac.uk/handle/10283/2791">https://datashare.ed.ac.uk/handle/10283/2791</a></d-footnote> and Deep Noise Suppression (DNS) Challenge datasets.

The evaluation is often done only on simulated conditions that are similar to the training setting. Meanwhile, in earlier SE challenges such DNS series, the choice of training data was also often left to the participants. This led to the situation that models trained with a huge amount of private data were compared to models trained with a small public dataset. This greatly impedes understanding of the generalizability and robustness of SE methods comprehensively. In addition, the model design may be biased towards a specific limited condition if only a small amount of data is used. The resultant SE model may also have limited capacity to handle more complicated scenarios.

Apart from conventional discriminative methods, generative methods have also attracted much attention in recent years. They are good at handling different distortions with a single model<d-cite key="UNIVERSE-Serra2022,VoiceFixer-Liu2022"/> and tend to generalize better than discriminative methods<d-cite key="Conditional-Lu2022"/>. However, their capability and universality have not yet been fully understood through a comprehensive benchmark.

Meanwhile, recent efforts<d-cite key="Toward-Zhang2023,Improving-Zhang2024"/> have shown the possibility of building a single system to handle various input formats, such as different sampling frequencies and numbers of microphones.
However, a well-established benchmark covering a wide range of conditions is still missing, and no systematic comparison has been made between state-of-the-art (SOTA) discriminative and generative methods regarding their generalizability.

Existing speech enhancement challenges have fostered the development of speech enhancement models for specific conditions, such as denoising and dereverberation<d-cite key="DNS1-Reddy2020,DNS2-Reddy2021,DNS3-Reddy2021,DNS4-Dubey2022,DNS5-Dubey2024"/>, speech restoration<d-cite key="SIG1-Cutler2024,SIG2-Ristea2024"/>, packet loss concealment<d-cite key="PLC1-Diener2022,PLC2-Diener2024"/>, acoustic echo cancellation<d-cite key="AEC1-Sridhar2021,AEC2-Cutler2021,AEC3-Cutler2022,AEC4-Cutler2024"/>, hearing aids<d-cite key="Clarity1-Graetzer2021,Clarity2-Akeroyd2023,Clarity2-Cox2023"/>, 3D speech enhancement<d-cite key="L3DAS21-Guizzo2021,L3DAS22-Guizzo2022,L3DAS23-Marinoni2023,L3DAS23-Gramaccioni2024"/>, far-field multi-channel speech enhancement for video conferencing<d-cite key="ConferencingSpeech-Rao2021"/>, unsupervised domain adaptation for denoising<d-cite key="CHiME7-Leglaive2023"/>, and audio-visual speech enhancement<d-cite key="AVSE-Blanco2023"/>. These challenges have greatly enriched the corpora in speech enhancement studies. However, there still lacks a challenge that can benchmark the generalizability of speech enhancement systems in a wide range of conditions.

Similar issues can also be observed in other speech tasks such as automatic speech recognition (ASR), speech translation (ST), speaker verification (SV), and spoken language understanding (SLU).
Among them, speech enhancement is particularly vulnerable to mismatches since it is heavily reliant on paired clean/noisy speech data to achieve strong performance. Unsupervised speech enhancement that does not require groundtruth clean speech has been proposed to address this issue, but often merely brings benefit in a final finetuning stage<d-cite key="Employing-Xu2024"/>. Therefore, we focus on speech enhancement in this challenge to address the aforementioned problems.

<!-- Be sure to list "URGENT Challenge: Universality, Robustness, and Generalizability for EnhancemeNT" as your paper subject area when making a submission. -->
