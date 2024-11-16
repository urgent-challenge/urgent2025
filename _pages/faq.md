---
layout: page
permalink: /faq/
title: FAQ
description:
nav: true
nav_order: 8
---

Below we summarize some frequently asked questions (FAQ) about the URGENT Challenge. If you have any other questions, please feel free to [contact us](/urgent2025/contact).

<!--
#### 1. How can I check why my submission failed in the [leaderboard website](https://urgent-challenge.com/competitions/5)?

**Answer:** You could go to `Participate` → `Submit / View Results` and unfold the corresponding failed submission. Then click the text `View scoring error log` to download the error message file. It should display the detailed information about the failure.

<details><summary>expand to see instructions in a screenshot</summary><div>
<img alt="error_message" src="/urgent2025/assets/img/error_log.png" style="max-width: 100%;"/>
</div></details>

#### 2. What does the following error message mean?

Message 1:
```
  data_pairs.append((uid, refs[uid], audio_path))
KeyError: 'fileid_10009'
```

**Answer:** Your submission contains an invalid file name that is not included in the provided test dataset. Please carefully check whether you are using the correct dataset corresponding to the current evaluation phase.

Message 2:
```
  assert ref.shape == inf.shape, (ref.shape, inf.shape)
AssertionError: ((315934,), (315936,))
```

**Answer:** You submission contains an audio sample that has a different length from the corresponding test sample provided in the official test dataset. Please carefully check your enhanced audios to make sure all sample lengths are consistent with the original audio length. Please also check whether you are using the correct test dataset corresponding to the current evaluation phase.

Message 3:
```
RuntimeError: Error : flac decoder lost sync.
```

**Answer:** You submission contains an invalid audio sample that cannot be properly decoded by the FLAC decoder on the server. Please validate the enhanced audios on your side. FLAC v1.4.3 is recommended.

Message 4:
```
RuntimeError: Error : unknown error in flac decoder.
```

**Answer:** You submission contains an invalid audio sample that cannot be properly decoded by the FLAC decoder on the server. Please validate the enhanced audios on your side. FLAC v1.4.3 is recommended.

Message 5:
```
slurmstepd: error: *** JOB 24880048 ON r288 CANCELLED AT 2024-08-02T04:17:40 DUE TO TIME LIMIT ***
```

or 

```
Timeout: The evaluation server is busy. Please try to resubmit later.
```

**Answer:** Evaluation jobs for your submission were killed due to a timeout. This may be caused by unexpected long queuing in our SLURM system on the server. Please contact us and we will rerun the evaluation for you.


Message 6:
```
RuntimeError: CUDA error: uncorrectable ECC error encountered
CUDA kernel errors might be asynchronously reported at some other API call, so the stacktrace below might be incorrect.
For debugging consider passing CUDA_LAUNCH_BLOCKING=1.
Compile with `TORCH_USE_CUDA_DSA` to enable device-side assertions.
```

**Answer:** Evaluation jobs for your submission were terminated likely due to a hardware issue of the specific node assigned to evaluate your submission. Please contact us and we will rerun the evaluation using another node for you.

-->