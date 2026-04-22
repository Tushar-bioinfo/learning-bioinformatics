---
layout: post
title: "Nuclei Segmentation in H&E Histopathology: Methods, Challenges, and Future Directions"
date: 2026-04-21 12:00:00 -0400
categories: [Computational Pathology, Review]
tags: [histopathology, nuclei-segmentation, cell-segmentation, digital-pathology, deep-learning]
description: "A review of nuclei segmentation in H&E histopathology"
image:
  path: /assets/img/review-he-segmentation/cover-he-nuclei-segmentation-review.png
  alt: "H&E tissue patch with nuclei overlays and computational contour motifs"
---

Hematoxylin and eosin (H&E) slides are central to diagnostic pathology, but turning them into reliable quantitative data remains technically difficult. Among the many tasks in computational pathology, nuclei segmentation stands out because it is both biologically meaningful and visually tractable: nuclei are often easier to identify than full-cell boundaries, yet they remain difficult to segment robustly across crowded, noisy, and heterogeneous tissue regions.

> **Abstract:** In H&E histopathology, segmentation is not a single problem but a family of related tasks. Nuclei segmentation is the most mature and best-supported target in routine H&E, while whole-cell segmentation remains harder because cytoplasmic and membrane boundaries are often ambiguous. Deep learning has substantially improved performance over traditional methods, but the decisive issues are no longer only average accuracy. Boundary quality, robustness across heterogeneous datasets, and computational practicality now define the real frontier. [CIT-REV1]
{: .prompt-tip }

![Conceptual roadmap for the review, linking H&E image characteristics to task definitions, model families, evaluation criteria, and future directions.](/assets/img/review-he-segmentation/figure-01-review-roadmap.svg)

*Figure 1. Conceptual roadmap for the review, linking H&E image characteristics to task definitions, model families, evaluation criteria, and future directions.*

---

## H&E Background
H&E is the most widely used stain in routine histopathology. Hematoxylin colors nuclei in dark blue to purple tones, while eosin stains cytoplasm, extracellular matrix, and other tissue components in shades of pink. This contrast is one reason nuclei are so important in digital pathology: even in a visually complex tissue scene, nuclei often remain the most recognizable cellular structure.

That visual prominence should not be confused with simplicity. H&E slides are shaped by fixation, sectioning, staining, scanning, and compression, and each step can introduce variability. Nuclei may therefore appear crowded, faint, hyperchromatic, elongated, overlapping, or partially obscured by surrounding tissue. The same diagnostic category can also look different across organs, scanners, and laboratories. In practice, H&E combines rich biological information with substantial visual heterogeneity. [CIT-REV1]

Because segmentation is a pixel-level task, these variations matter directly. Small changes in stain intensity, contour sharpness, and background texture can alter whether a pixel is interpreted as nucleus, surrounding tissue, or background. In H&E pathology, segmentation therefore sits at the intersection of biology, imaging, annotation practice, and computer vision. That context makes precise task definitions essential.

![Annotated H&E patch highlighting nuclei, surrounding tissue context, crowded regions, and ambiguous boundaries.](/assets/img/review-he-segmentation/figure-02-labeled-he-patch.png)

*Figure 2. Illustrative H&E patch highlighting nuclei, surrounding tissue context, crowded regions, and the boundary ambiguity that complicates segmentation.*

---

## From Detection to Segmentation to Instance Segmentation
The terminology of image analysis is often used loosely, so it is worth defining the core terms clearly. *Detection* usually means locating an object approximately, for example with a point, center, or bounding box. Detection can be useful for counting or coarse localization, but it does not define exact nuclear shape.

*Segmentation* is stricter. It assigns pixels to a target class such as nucleus versus background. This makes it possible to measure morphology rather than merely estimate position. Within segmentation, however, another distinction is essential. *Semantic segmentation* labels pixels by class, but it does not necessarily separate neighboring objects of the same class. If two touching nuclei are predicted as one connected mass, the semantic output may still look plausible while failing the practical goal of identifying individual nuclei.

*Instance segmentation* solves that problem by assigning a separate mask to each object. In pathology this difference is not a technical detail; it is often the difference between a useful result and an unusable one. Downstream analyses frequently require per-nucleus measurements such as area, shape, density, neighborhood relations, or spatial organization, which depend on separating individual nuclei rather than merely labeling nuclear pixels in aggregate. Once those distinctions are clear, the central role of nuclei becomes easier to understand. [CIT-REV1]

| Task | Typical output | Main strength | Practical use | Typical failure mode |
|---|---|---|---|---|
| Detection | Point, center, or bounding box per nucleus | Fast coarse localization | Screening, rough counting, proposal generation | Does not recover exact nuclear shape or contour |
| Semantic segmentation | One shared mask for all nuclear pixels | Strong dense foreground-background labeling | Estimating nuclear regions or pixel occupancy | Touching nuclei can merge into one connected mass |
| Instance segmentation | Separate mask for each nucleus | Supports per-nucleus morphology and spatial analysis | Quantitative pathology workflows that need individual objects | Still sensitive to crowding, weak borders, and irregular contours |

*Table 1. Comparison of detection, semantic segmentation, and instance segmentation in pathology image analysis.* [CIT-REV1]

---

## Why Nuclei Segmentation Matters
Nuclei segmentation matters because nuclei are not only visible structures; they are biologically informative objects. Nuclear size, shape, orientation, chromatin pattern, and spatial distribution all reflect tissue organization and disease state. In computational workflows, nuclear masks support cell counting, density estimation, morphology analysis, tissue composition studies, and broader pathology pipelines. If the masks are poor, the downstream features inherit that error. [CIT-REV1]

This is why segmentation should not be treated as a cosmetic preprocessing step. A classifier or prognostic model may appear sophisticated, but if its upstream nuclei are fragmented, merged, or systematically missed, the resulting measurements become unstable. Segmentation is therefore an infrastructure problem for quantitative pathology rather than a narrow vision benchmark. [CIT-REV1]

There is also a practical reason for centering nuclei in H&E. Compared with full cells, nuclei are often more consistently visible and more defensible to annotate. This gives nuclei segmentation a useful balance of biological relevance and technical feasibility, which helps explain why it has become a focal benchmark task in the literature. The same balance does not hold for whole-cell segmentation. [CIT-REV1]

<div style="display:flex; flex-wrap:wrap; gap:1rem; margin:1.5rem 0;">
  <div style="flex:1 1 320px; min-width:280px;">
    <img src="/assets/img/review-he-segmentation/figure-03-downstream-workflow_1.png" alt="Workflow from H&amp;E tissue image to nuclei segmentation masks and object-level outputs." style="width:100%; height:auto; display:block;">
  </div>
  <div style="flex:1 1 320px; min-width:280px;">
    <img src="/assets/img/review-he-segmentation/figure-03-downstream-workflow_2.png" alt="Examples of downstream analyses supported by nuclei segmentation, including counts, morphology, density, and spatial features." style="width:100%; height:auto; display:block;">
  </div>
</div>

*Figure 3. Segmentation as an infrastructure step: paired workflow panels showing how H&E patches become nuclei masks and how those masks support counts, morphology, density, and spatial analysis.*

---

## Why Whole-Cell Segmentation Is Harder
Whole-cell segmentation is not simply nuclei segmentation with larger masks. It is a qualitatively harder problem. In many H&E images, nuclei are conspicuous because hematoxylin marks them strongly, but the full extent of the cell is far less explicit. Cytoplasmic signal is weaker, membranes are not consistently highlighted, and neighboring cells may adhere closely without visible separation. As a result, the outer boundary of a cell is often ambiguous even for expert annotators.

The available review source makes this distinction clear. Nuclear segmentation benefits from relatively more stable morphology, even though overlap and uneven staining remain difficult. Cytoplasmic and whole-cell segmentation face lower contrast, more uncertain boundaries, and higher annotation cost. Whole-cell masks are therefore harder to define, harder to annotate consistently, and harder to predict algorithmically. [CIT-REV1]

For H&E histopathology, this distinction should shape how the problem is framed. Progress in nuclei segmentation does not automatically solve whole-cell analysis. In many routine settings, nuclear masks remain the most reliable cellular representation available, while whole-cell boundaries may still require stronger priors, additional stains, or multimodal information. Even after restricting the target to nuclei, however, the task remains challenging.

| Target | Visual signal in routine H&E | Annotation burden | Boundary ambiguity | Typical downstream use | Practical status |
|---|---|---|---|---|---|
| Nuclei segmentation | Usually strong hematoxylin contrast and relatively stable morphology | Moderate, though dense regions remain hard | Lower than whole-cell, but overlap and stain variability still matter | Counting, density, morphology, and spatial organization | Most mature and best-supported target in routine H&E |
| Whole-cell segmentation | Cytoplasm and membranes are weakly or inconsistently defined | High because full cell extent is expensive to label consistently | High because membrane separation and outer cell extent are often unclear | Cell-level phenotyping and neighborhood analysis | Important, but often needs stronger priors, extra stains, or multimodal information |

*Table 2. Why nuclei segmentation is more mature than whole-cell segmentation in routine H&E histopathology.* [CIT-REV1]

---

## Why the Task Is Hard
If nuclei are often easy to see, why is segmentation still hard? The answer is that visibility alone does not guarantee robust delineation. A model may perform well on isolated, well-stained nuclei and still fail on dense tumor regions, variable section quality, atypical morphology, or tissue with substantial background texture. The task becomes difficult when instance separation, contour precision, and cross-domain stability must all be achieved at once. [CIT-REV1]

Several failure modes recur across the literature. Dense nuclear clusters make it difficult to separate touching objects. Uneven staining changes contrast and boundary sharpness. Morphology varies across tissues and disease states, producing domain shift. Background texture can create false positives, while low-contrast regions can cause missed nuclei. Very crowded regions often lead to merged instances even when nuclei are detected correctly at a coarse level. [CIT-REV1]

These are not interchangeable errors. Over-segmentation inflates counts. Under-segmentation removes valid objects. Merged instances distort density and morphology. Poor boundaries corrupt shape-based features even when detection is otherwise successful. A useful review therefore has to treat segmentation difficulty as a structured collection of failure modes rather than as one abstract problem.

![Error taxonomy for H&E nuclei segmentation showing false positives, missed nuclei, merged nuclei, and inaccurate contours.](/assets/img/review-he-segmentation/figure-04-error-taxonomy.png)

*Figure 4. Common failure modes in H&E nuclei segmentation, including false positives, missed nuclei, merged instances, and inaccurate contours.*

---

## Evolution of Methods
The evolution of segmentation methods can be understood as a response to increasingly difficult image conditions rather than a simple march of technical fashion. Early approaches relied on traditional image processing, including thresholding, morphology-based operations, edge detection, and Watershed segmentation. These methods were fast, interpretable, and easy to run, but they depended heavily on regular image structure. Once nuclei became crowded, irregular, or unevenly stained, their assumptions weakened. [CIT-REV1]

Classical machine learning methods attempted to improve flexibility by combining engineered features with shallow classifiers such as support vector machines, random forests, k-nearest neighbors, or clustering-based systems. This was an important step because it introduced data-driven decision rules, but the feature engineering bottleneck remained. Performance still depended on whether the chosen descriptors captured the relevant morphology across tissues and staining conditions. [CIT-REV1]

Deep learning shifted the field by learning features directly from images. Semantic segmentation architectures such as fully convolutional networks and U-Net-style encoder-decoder models made dense pixel-level prediction practical at scale. These models were especially influential because they combined broad contextual information with fine spatial detail, which is crucial for biomedical imaging. [CIT-REV1]

The next major step focused on a central pathology difficulty: touching nuclei. Instance-aware models, including Mask R-CNN-style systems and later transformer-based variants, were designed to separate individual objects more explicitly. At the same time, specialized biomedical tools introduced useful priors. StarDist represented nuclei using star-convex shapes. Splinedist extended that idea to more flexible spline contours. Cellpose used flow fields to support more general-purpose segmentation. DeepCell and Mesmer emphasized strong image-based deep learning pipelines, while multimodal approaches such as GeneSegNet added spatial molecular information when such data were available. [CIT-REV1]

The most defensible conclusion is not that newer automatically means better. Each generation addresses a different weakness of the one before it. Traditional methods are efficient but brittle. Semantic CNNs improve pixel labeling but may still merge adjacent nuclei. Instance-aware and shape-aware systems improve separation, but often with higher computational cost or stronger geometric assumptions. Multimodal methods are promising, but they remain less broadly benchmarked in the current local evidence base. [CIT-REV1]

![Conceptual evolution of segmentation methods from traditional image processing to classical machine learning, semantic CNNs, instance-aware models, and multimodal approaches.](/assets/img/review-he-segmentation/figure-05-method-evolution.png)

*Figure 5. Simplified evolution of segmentation methods, from heuristic image processing to deep instance-aware and multimodal models.*

---

## Datasets and Metrics
Benchmarking shapes how the field understands progress. A method that looks strong on one dataset may behave differently on another because segmentation quality depends on stain, tissue type, image size, annotation practice, and object density. For an H&E-focused review, dataset description is therefore part of the scientific argument rather than background information. [CIT-REV1]

In the available review source, the most directly relevant H&E datasets are PanNuKe and MoNuSeg. PanNuKe is large and multi-tissue, which makes it valuable for studying variation across organs and contexts. MoNuSeg is smaller but historically important and expert-annotated, which helps explain its continued influence in histopathology benchmarking. The same benchmark also includes non-H&E or non-routine settings such as BBBC041Seg, BSST265, and the multimodal mouse brain dataset MSBDS. These are useful for understanding broader robustness and multimodal trends, but they should not be treated as interchangeable with routine H&E evidence. [CIT-REV1]

The evaluation metrics also require interpretation. The benchmark uses IoU as an object-overlap criterion and evaluates effectiveness through precision, recall, F1-score, and Dice. These metrics capture different behaviors. Precision reflects false positive control. Recall reflects sensitivity to missed nuclei. F1-score balances the two. Dice reflects pixel-level mask agreement. A method can therefore perform well on one axis and weakly on another. High recall with low Dice, for example, may mean that nuclei were found but not contoured accurately. [CIT-REV1]

The review also treats robustness and efficiency as first-class properties. Robustness is assessed through standard deviation and confidence intervals across datasets, while efficiency is measured by runtime per image. That framing is valuable because a useful pathology model is not just accurate on average. It also needs to remain stable across changing data conditions and be computationally realistic for large-scale use. [CIT-REV1]

> **Metric caution:** In histopathology, one summary score is rarely enough. A model can detect most nuclei but still draw weak contours, or it can achieve decent pixel overlap while merging adjacent instances. Metrics should therefore be read together rather than in isolation. [CIT-REV1]
{: .prompt-warning }

| Dataset | Modality / stain | Typical image size | Annotation scale | Relevance to routine H&E |
|---|---|---|---|---|
| PanNuKe | Brightfield, H&E | `256 x 256` | `7,901` images; `189,744` nuclei; `19` tissue types | Large multi-tissue H&E benchmark directly relevant to pathology variation |
| MoNuSeg | Brightfield, H&E | `1000 x 1000` | `30` images; `>21,000` expert-annotated nuclei from `7` organs | Smaller but historically important expert-annotated H&E benchmark |
| BBBC041Seg | Brightfield, Giemsa | `1600 x 1200` | `1,328` images; `93,539` leukocyte nuclei | Useful for robustness comparison, but not routine H&E |
| BSST265 | Fluorescence, DAPI | Multiple sizes | `79` images; `7,813` nuclei | Useful non-H&E microscopy benchmark |
| MSBDS | Spatial transcriptomics + optical microscopy, DAPI | `20,000 x 20,000` | `1` image from adult mouse brain sections | Multimodal reference dataset, not interchangeable with routine H&E |

*Table 3. Datasets referenced in the review, with stain or modality, scale, annotation scope, and relevance to H&E pathology.* [CIT-REV1]

| Measure | Plain-language meaning | What it captures well | What it can miss |
|---|---|---|---|
| IoU threshold | Whether a predicted object overlaps a true object enough to count as a match; the benchmark uses `IoU > 0.5` | Basic object-level agreement | Fine contour quality once the threshold is passed |
| Precision | Of predicted nuclei, how many are real | False positive control | Missed nuclei |
| Recall | Of true nuclei, how many were found | Sensitivity to missed objects | Extra false positives or sloppy masks |
| F1-score | Balance between precision and recall | Overall object-detection tradeoff | Whether errors come more from misses or false alarms |
| Dice coefficient | Pixel overlap between predicted and reference masks | Mask agreement at the pixel level | Instance merging or splitting can hide behind decent overlap |
| Standard deviation / confidence intervals | How much performance varies across datasets or runs | Robustness and stability | Absolute quality on any one dataset |
| Runtime per image | How long inference takes per image | Practical efficiency and scalability | Accuracy and robustness tradeoffs |

*Table 4. Evaluation measures for segmentation quality, including what each captures and what it may fail to capture.* [CIT-REV1]

---

## Comparing Model Families
A synthesis-first review is most useful when it compares model families by assumptions and tradeoffs rather than by listing tool names mechanically. Traditional methods remain useful as baselines because they are fast, simple, and easy to interpret. Their main weakness is brittleness under complexity. When morphology becomes irregular or nuclei adhere closely, fixed heuristics often break down. [CIT-REV1]

Semantic encoder-decoder CNNs are a major improvement because they learn image features directly and produce dense pixel predictions. They are strong when the main challenge is distinguishing foreground from background. Their limitation is that pathology often requires more than class labeling. In crowded tissue, semantic masks alone may not separate neighboring nuclei cleanly, which reduces their value for per-cell quantification. [CIT-REV1]

Instance-aware and shape-aware deep models respond to that problem in different ways. Region-based and transformer-inspired systems aim to separate objects explicitly. Shape-prior methods such as StarDist and Splinedist can be efficient and effective when nuclei have relatively regular geometry, but less reliable when pathology produces atypical or highly variable shapes. Generalist systems such as Cellpose aim for broader adaptability, while tools such as DeepCell and Mesmer emphasize strong learned representations for challenging images. The broader lesson is that performance depends on how well model assumptions match the image regime rather than on any universally dominant architecture. [CIT-REV1]

Multimodal models form a distinct category because they incorporate information beyond image appearance. Methods such as GeneSegNet use spatial molecular cues to refine boundaries when image-only evidence is insufficient. This direction is conceptually important, but the current local evidence base supports it with limited breadth. It should therefore be presented as promising rather than settled. [CIT-REV1]

| Family | Examples | Core idea | Strengths | Limits | Best fit |
|---|---|---|---|---|---|
| Traditional image processing | Watershed, thresholding, edge and morphology methods | Hand-crafted rules based on intensity, gradients, and simple shape cues | Fast, interpretable, and easy to run as a baseline | Brittle under stain variation, crowding, and irregular nuclei | Clean or simple images and baseline comparisons |
| Classical machine learning | SVM, random forest, k-NN, k-means, ilastik | Engineered features paired with shallow classifiers | More flexible than fixed thresholds while remaining relatively interpretable | Feature engineering bottleneck and weaker transfer across tissues | Smaller or structured settings with curated features |
| Semantic encoder-decoder CNNs | FCN, U-Net, V-Net, multi-scale CNNs | Learn dense pixel labels directly from images | Strong foreground-background separation and scalable pixel prediction | Often merge touching nuclei because they are not inherently instance-aware | When the main need is robust foreground extraction |
| Instance-aware deep models | Mask R-CNN, nucleAlzer, Cell-DETR, CellT-Net, transformer variants | Predict individual objects rather than one shared mask | Better separation of touching nuclei and direct support for per-object analysis | Higher complexity and compute; still sensitive to weak boundaries | Crowded tissue where per-nucleus quantification matters |
| Shape-aware and generalist image-based models | StarDist, Splinedist, Cellpose, DeepCell, Mesmer | Add shape priors, flow fields, or strong learned image representations | Often practical and strong for biomedical instance separation | Performance depends on how well model assumptions match nuclear morphology | Routine image-only segmentation when morphology is not wildly mismatched to the model prior |
| Multimodal models | GeneSegNet, SCS, BIDCell, CellBin | Combine image cues with sequencing or spatial molecular information | Can refine boundaries when image-only evidence is insufficient | Narrower benchmark base and more complex data requirements | Specialized research settings with aligned multimodal data |

*Table 5. Comparison of segmentation model families by core idea, strengths, weaknesses, and best-fit use case.* [CIT-REV1]

---

## Major Challenges and Open Problems
The strongest current methods still face three linked problems: unstable generalization, imperfect boundaries, and incomplete translation to real pathology workflows. The first is robustness. The reviewed benchmark shows that method behavior can shift substantially across datasets, especially when morphology and imaging conditions become more heterogeneous. This means that leaderboard-style reporting can overstate practical reliability. [CIT-REV1]

The second is boundary quality. Instance recognition and contour accuracy are related but not identical. Some methods identify nuclei successfully at the object level yet trace weak contours, which matters when downstream analysis depends on shape, border texture, or local cell-cell relations. In dense tissue, the difference between "found the nucleus" and "traced the nucleus correctly" is scientifically important. [CIT-REV1]

The third is the gap between benchmark design and deployment reality. The reviewed source is strong on taxonomy and comparative benchmarking, but it is less developed on annotation uncertainty, inter-observer variability, deployment across laboratories, interpretability, and workflow integration. These are not minor details; they shape whether a model is truly usable outside a controlled benchmark. [CIT-REV1]

Additional open problems follow from these themes. Whole-slide images remain computationally demanding. Multimodal methods may improve boundaries, but they increase system complexity and often depend on data not routinely available in standard pathology workflows. Whole-cell segmentation in H&E remains under-defined relative to nuclei segmentation. The field also still lacks a broadly accepted framework for matching task, dataset, and algorithm in a principled way. [CIT-REV1]

![Tradeoff map comparing effectiveness, robustness, and efficiency across segmentation model families.](/assets/img/review-he-segmentation/figure-06-tradeoff-map.png)

*Figure 6. Conceptual tradeoff between effectiveness, robustness, and efficiency across segmentation model families.*

---

## Future Directions
Future progress is likely to come less from chasing a single best architecture and more from aligning models with the actual structure of the pathology problem. One priority is better boundary modeling. Since many current errors occur at object borders, especially in dense tissue, future systems should emphasize contour-sensitive learning, stronger separation of adjacent nuclei, and more faithful instance delineation under low contrast. [CIT-REV1]

A second priority is stronger generalization. Models need to remain stable across tissue types, stain variability, image acquisition settings, and morphological extremes. This implies not only better architectures, but also better evaluation. Robustness should be reported centrally rather than as an afterthought. A method that performs slightly less impressively on one curated dataset but remains stable across many conditions may be more valuable than a narrow benchmark leader. [CIT-REV1]

A third direction is selective multimodal fusion. Sequencing-integrated methods suggest that image-only segmentation is not the final endpoint, but multimodal systems will only become broadly useful if they improve boundaries without introducing prohibitive cost or excessive data requirements. In routine H&E workflows, the near-term priority is likely stronger image-based nuclei segmentation. In specialized research settings, multimodal approaches may become more decisive. [CIT-REV1]

Finally, deployment needs more attention. That includes computational efficiency, interpretable failure analysis, and explicit reporting of where a method should or should not be used. It also requires a realistic stance on whole-cell analysis. In standard H&E, the most immediate gains will probably continue to come from robust nuclei segmentation, while reliable whole-cell segmentation may require additional staining information or stronger cross-modal priors. These constraints also explain the practical emphasis of the key takeaways below. [CIT-REV1]

![Roadmap from current bottlenecks to future directions, including boundary quality, generalization, multimodal fusion, and deployment.](/assets/img/review-he-segmentation/figure-07-future-roadmap.png)

*Figure 7. Roadmap from current bottlenecks to future directions, including boundary quality, generalization, multimodal fusion, and deployment.*

---

## Conclusion
H&E histopathology presents a deceptively simple visual problem. Nuclei are often easy to see, but difficult to segment reliably across the full range of real tissue variation. That tension explains why nuclei segmentation has become both a central benchmark task and an unresolved research problem. The current literature supports a clear conclusion: deep learning methods generally outperform traditional baselines in complex settings, but their value depends on robustness, boundary quality, and computational practicality rather than on headline accuracy alone. [CIT-REV1]

This review supports a second conclusion that is just as important conceptually: nuclei segmentation and whole-cell segmentation should not be treated as equivalent in H&E pathology. Nuclei are currently the stronger and more defensible target because they are biologically informative and visually better defined. Whole-cell analysis remains important, but it is harder precisely because H&E provides weaker information about full cellular extent. [CIT-REV1]

The field has made real progress, especially in moving from brittle heuristics to learned instance-aware systems. Yet the hardest problems are now better defined rather than fully solved: separating dense nuclei, tracing accurate boundaries, generalizing across heterogeneous pathology data, and narrowing the gap between benchmark performance and deployable reliability. That is where the next phase of progress is most likely to emerge. [CIT-REV1]

---

## Key Takeaways
- In H&E histopathology, *cell segmentation* is an umbrella term; nuclei segmentation and whole-cell segmentation are not interchangeable tasks.
- Nuclei segmentation is currently the most mature and defensible segmentation target in routine H&E analysis.
- Whole-cell segmentation is harder because cytoplasmic and membrane boundaries are often weak or ambiguous in H&E.
- Deep learning has substantially improved segmentation quality, but average accuracy alone is not enough.
- Practical model selection should weigh effectiveness, robustness, and efficiency together.
- Multimodal methods are promising, but in the current local evidence base they remain less broadly supported than image-only nuclei segmentation.

---

## Further Reading
- `[CIT-REV1]` Yang R, Xue G, Wang Z, Cai Y, Yang W, Que J, Tan R, Sun H, Wang P, Xu Z, Jiang Q, Zhou W. *Systematic evaluation of computational methods for cell segmentation*. *Briefings in Bioinformatics*. 2026;27:bbag066. DOI: `10.1093/bib/bbag066`.
