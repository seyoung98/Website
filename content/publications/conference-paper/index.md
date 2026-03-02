---
title: 'Emerging Property of Masked Token for Effective Pre-training'

# Authors
# If you created a profile for a user (e.g. the default `me` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Hyesong Choi
  - Hunsang Lee
  - me
  - Hyejin Park
  - Jiyeong Kim
  - Dongbo Min

# # Author notes (optional)
# author_notes:
#   - 'Equal contribution'
#   - 'Equal contribution'

date: '2024-10-31T00:00:00Z'

# Schedule page publish date (NOT publication's date).
publishDate: '2026-02-01T00:00:00Z'

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ['paper-conference']

# Publication name and optional abbreviated publication name.
publication: In *European Conference on Computer Vision*
publication_short: In *ECCV*

abstract: Driven by the success of Masked Language Modeling (MLM), the realm of self-supervised learning for computer vision has been invigorated by the central role of Masked Image Modeling (MIM) in driving recent breakthroughs. Notwithstanding the achievements of MIM across various downstream tasks, its overall efficiency is occasionally hampered by the lengthy duration of the pre-training phase. This paper presents a perspective that the optimization of masked tokens as a means of addressing the prevailing issue. Initially, we delve into an exploration of the inherent properties that a masked token ought to possess. Within the properties, we principally dedicated to articulating and emphasizing the ‘data distinctiveness’ attribute inherent in masked tokens. Through a comprehensive analysis of the heterogeneity between masked tokens and visible tokens within pre-trained models, we propose a novel approach termed masked token optimization (MTO), specifically designed to improve model efficiency through weight recalibration and the enhancement of the key property of masked tokens. The proposed method serves as an adaptable solution that seamlessly integrates into any MIM approach that leverages masked tokens. As a result, MTO achieves a considerable improvement in pre-training efficiency, resulting in an approximately 50% reduction in pre-training epochs required to attain converged performance of the recent approaches. Code is available at https://github.com/doihye/MTO.

# Summary. An optional shortened abstract.
summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags:
  - Computer Vision
  - Self-supervised Learning

# Display this page in the Featured widget?
featured: true

# Standard identifiers for auto-linking
hugoblox:
  ids:
    doi: 10.1007/978-3-031-73116-7_16

# Custom links
links:
  - type: PDF
    name: PAPER
    url: https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/09774.pdf
  - type: code
    url: https://drive.google.com/drive/folders/1Q7b5EmcA-670HqNfAqhuSbQO9yAncfMA
  - type: PDF
    name: supplement
    url: https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/09774-supp.pdf

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  focal_point: ''
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
  - example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---

<!-- > [!NOTE]
> Click the _Cite_ button above to demo the feature to enable visitors to import publication metadata into their reference management software.

> [!NOTE]
> Create your slides in Markdown - click the _Slides_ button to check out the example. -->

## 1. Motivation

   Despite the plenteous successes of MIM in diverse downstream tasks, the long pre-training phase that it entails tends to impede its efficiency. Concretely, to attain the convergence of the Transformer for transfer learning, a substantial amount of pre-training, typically from 800 to 1600 epochs in advance, is essential. In this paper, as a fundamental approach, we cast this problem from the perspective of the optimization of masked tokens which arises as a result of the modality gap from NLP systems.

## 2. Properties of Masked Token
  - **Spatial randomness**: Masked tokens must be randomly selected from the corpus of input patches, so that the model can learn to predict tokens in various locations and types. 

  - **Substitutional consistency**: In the process of masking at the initial embedding, tokens that are masked should consistently be replaced with the same parameter.

  - **Data singularity**:  Masked tokens in the initial embedding should be unique tokens that have a low likelihood of manifesting in the training data.

## 3. Proposed Optimization
  The proposed Masked Token Optimization (MTO) approach encompasses the selective exclusion of semantically inconsequential masked tokens from the weight aggregation process pertaining to visible tokens, and at the same time, it enforces data singularity constraints based on the depth of the layer to enhance the model’s capability to accurately identify regions necessitating semantic restoration.