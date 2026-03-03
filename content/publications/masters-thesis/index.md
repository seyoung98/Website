---
title: "DeCoMon: Depth Completion-Guided Monocular Depth Estimation via Knowledge Distillation"
summary: "A novel Knowledge Distillation framework resolving scale ambiguity in monocular depth estimation for LiDAR-free, scale-consistent prediction."
authors:
- me
date: "2024-08-31T00:00:00Z"

publication_types: ["thesis"]
publication: "Master's Thesis, *Ewha Womans University*"

abstract: "Monocular depth estimation (MDE) is a fundamental computer vision task crucial for applications in autonomous driving and robotics. However, accurately predicting absolute depth scale from monocular inputs alone is inherently challenging, significantly limiting its practical deployment. Although LiDAR-based depth completion (DC) techniques offer precise absolute depth measurements, they remain impractical for widespread use due to high cost and environmental constraints. In this paper, we propose an Inverse-Depth Knowledge Distillation (KD) framework, transferring accurate absolute depth information from a LiDAR-free adaptation of the DC teacher to a lightweight, self supervised monocular MDE student. Our domain-gap-aware distillation operates entirely in the inverse-depth domain. Concretely, we convert the teacher’s metric depth to inverse depth and align the student’s raw disparity predictions by applying an image-wise median-scale normalization. The resulting aligned target provides scale consistent supervision without additional learnable parameters. By enforcing this median-scale alignment at every training iteration, we ensure that each component of our unified distillation loss— absolute scale alignment (L1-KD), scale-invariant structure preservation (SiLog-KD), and feature level geometric consistency (AffinityKD)—operates in a depth-friendly representation that directly inherits the teacher’s absolute scale, while preserving the efficiency of monocular inference. Empirically, our distilled model significantly resolves the scale ambiguity inherent to monocular predictions, outperforming the baseline LiteMono by on KITTI Eigen and Make3D, thereby setting a new state-of-the-art performance among sub-10M-parameter monocular depth estimators."

tags:
- Computer Vision
- Knowledge Distillation
- Depth Estimation
- Autonomous Driving

featured: true

links:
- type: PDF
  name: paper
  url: uploads/master thesis.pdf

- type: code
  name: code
  url: https://github.com/seyoung98/DeCoMon-main
---

### Key Research Contributions
As the primary researcher, I developed the **DeCoMon** framework to bridge the gap between expensive LiDAR-based systems and accessible monocular camera-based depth estimation.

* **Scalable Knowledge Distillation**: Developed a novel KD framework using a **Depth Completion teacher model** to supervise a lightweight monocular student model.
* **Scale Ambiguity Resolution**: Successfully resolved chronic scale inconsistency issues in MDE by implementing **median-scale normalization** and multi-faceted loss functions.
* **Superior Generalization**: Proven robust performance through **zero-shot generalization** tests on diverse datasets including **KITTI and Make3D**, outperforming existing student-only models.
* **Practical Efficiency**: Proposed a paradigm for LiDAR-free, scale-consistent depth prediction, significantly reducing the hardware cost and computational load for autonomous robots and vehicles.