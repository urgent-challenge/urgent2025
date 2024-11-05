---
layout: page
permalink: /template/
title: Template for README.yaml in each submission
description:  
nav: false
nav_order: 10
---

```yaml
#-------------------------------------------
# Basic information
#-------------------------------------------
team: your_teamname
team_email: email_for_receiving_notification
team_members:
    # Member 1
    1:
        name: member1_name
        affiliation: member1_affiliation
    # Member 2
    2:
        name: member2_name
        affiliation: member2_affiliation
    # Member 3
    3:
        name: member3_name
        affiliation: member3_affiliation

#-------------------------------------------
# Data description
#-------------------------------------------
training_data: simulated on the fly using the official configuration
use_additional_rirs: True
additional_rir_info:
    # RIR 1 (for real RIRs, only those included in the official data list are allowed)
    1:
        is_real: True
        source: https://url.to.real.rirs
        number_of_samples: 1000
    # RIR 2
    2:
        is_real: False
        source: https://url.to.rir.simulator
        number_of_samples: 10000

validation_data: same as official validation data (39 hours)


#-------------------------------------------
# Additional information
# If any pre-trained model is used to develop the speech enhancement system, please provide its information below. For example:
#-------------------------------------------
use_pretrained_models: True
pretrained_models:
    # Pre-trained model 1
    1:
        name: HuBERT-Large
        link: https://huggingface.co/facebook/hubert-large-ll60k
        usage: used for converting the input speech signal into discrete tokens
    # Pre-trained model 2
    2:
        name: EnCodec
        link: https://github.com/facebookresearch/encodec
        usage: used for generating compressed speech features
```
