---
layout: page
permalink: /faq/
title: FAQ
description:
nav: true
nav_order: 8
---

Below we summarize some frequently asked questions (FAQ) about the URGENT Challenge. If you have any other questions, please feel free to [contact us](/urgent2025/contact).

<details>
  <summary><strong> 1. How can I check why my submission failed in the leaderboard?  </strong></summary>

  <br>

  **Answer:** You could go to `Participate` → `Submit / View Results` and unfold the corresponding failed submission. Then click the text `View scoring error log` to download the error message file. It should display the detailed information about the failure.

  <details><summary>expand to see instructions in a screenshot</summary><div>
  <img alt="error_message" src="/urgent2025/assets/img/error_log.png" style="max-width: 100%;"/>
  </div></details>

</details>

<br>

<details><summary>  2. What does the error message from the leaderboard mean? </summary>

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

</details>

<br>


<details><summary>  3. I would like to speecd up calculate_wer.py </summary>

<br>

`calculate_wer.py` takes around 30~40 minutes (depending on the environment) to evaluate 1000 samples using a single GPU.
It takes some time since it does beam search in decoding.

To make it faster, you can skip the beam search by setting `BEAMSIZE` to 1 [here](https://github.com/urgent-challenge/urgent2025_challenge/blob/2de19bab56c7d7fa5f61f5fdda193a7710c62475/evaluation_metrics/calculate_wer.py#L16).

Note that `BEAMSIZE` is set to 5 in the leaderboard evaluation.
If you would like to check the consistency of the scores between your local and the leaderbord, `BEAMSIZE` should be set to 5.

</details>

<br>


<details><summary>  4. How long is the maximum duration of the speech in the test set? </summary>

<br>

The maximum duration will be around 15 seconds.
Please note that this number may change.

</details>

<br>


<details><summary>  5. Why is not my leaderboard registration approved? </summary>

<br>

The leaderboard registration is usually approved at least within a day.

If your application is not approved for more than a day, please check if you have submitted the Google Form.
We do not approve the registration until we receive it.

If you have done it but have not gotten the approval yet, please reach out to the organizers.

</details>
