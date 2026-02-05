# Knowledge Distillation using Whitened-CLIP
<p align="center">
  <a href="Docs/W_CLIP_KD_Report.pdf"><b>📄 Read Full Report</b></a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="Docs/W_CLIP_KD_Presentation.pdf"><b>📊 View Presentation Slides</b></a>
</p>

## Abstract
While Vision-Language Models like CLIP have shown excellent zero-shot performance on a variety of computer vision tasks, the huge compute and memory needs of state-of-the-art CLIP models limit their practical deployment on edge devices like IoT sensors. Knowledge Distillation (KD) is a widely used model compression technique that solves this by distilling the essence of a larger teacher model into smaller student models. Although standard KD works reasonably well, we identify that standard KD strategies are hindered by the double-ellipsoid geometry of the teacher CLIP, which forces the student models to learn geometric biases rather than semantic content. In this work, we propose Whitened-CLIP KD, a geometry-aware distillation framework that uses ZCA whitening to transform the teacher's embedding space into an isotropic hypersphere. We hypothesize and validate that this transformation of the teacher's latent space enables significantly faster convergence and superior semantic alignment. Our experiments on MS-COCO (training) and CIFAR-10 (zero-shot evaluation) demonstrate that whitening significantly helps low-capacity students: our whitened MobileNet-V3 student outperforms the raw baseline by over 8% in accuracy, while the ResNet-18 student achieves near-convergence performance in a single epoch. Geometric analysis using t-SNE plots reveals that our method mitigates the modality gap and prevents feature collapse.
## Training Setup
Our training setup is illustrated in the figure below: ![W_CLIP_KD Setup](Images/W_KD_Setup.png)
\
We train the models on MS-COCO dataset and evaluate on CIFAR-10. We found that ZCA whitening significantly improved the training convergence speed for models with whitened ResNet-18 achieving 57.15% accuracy in one epoch while unwhitened ResNet-18 took 5 epochs to reach 56.71%. For very lighter models like MobileNet-V3, there was a huge accuracy improvement with the whitened student outperforming the unwhitened student by ~8% after 5 epochs.

## References
1. Betser, R., Levi, M. Y., and Gilboa, G. Whitened clip as a
likelihood surrogate of images and captions, 2025. URL
https://arxiv.org/abs/2505.06934.
2. Levi, M. Y. and Gilboa, G. The double-ellipsoid geometry of
clip, 2025. URL https://arxiv.org/abs/2411.14517.
3. Yang, C., An, Z., Huang, L., Bi, J., Yu, X., Yang, H., Diao,
B., and Xu, Y. Clip-kd: An empirical study of clip model
distillation, 2024. URL https://arxiv.org/abs/2307.12732.