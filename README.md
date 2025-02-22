# HSS-IAD-Dataset
Dataset for paper "HSS-IAD: A Heterogeneous Same-Sort Industrial Anomaly Detection Dataset"

The dataset is preview version, so it could be really ugly with minor errors. We will try to reformat it after the paper is accepted.

Give me a star if you like it!!!

## Overview
This project introduce the Heterogeneous Same-Sort Industrial Anomaly Detection (HSSIAD) dataset, which contains 8,580 images of metallic-like industrial parts and precise anomaly annotations. These parts exhibit variations in structure and appearance, with subtle defects that closely resemble the base materials. We also provide foreground images for synthetic anomaly generation. The HSS-IAD dataset stands out for its focus on same-sort industrial products with variations in structure and appearance. It tackles the challenge of detecting subtle defects that closely resemble base materials, which are common in real-world industrial settings. The dataset's design—covering various defects and interference sources like machining marks and oil stains—is original and innovative. This is in contrast to previous datasets that do not address these practical issues effectively. we provide visualizations of three objects (Casting\_C1, Casting\_C2, Casting\_C3) and four textures (KolektorSDD, KolektorSDD2, Magnetic-tile-defect, STEEL) in HSS-IAD, as shown in Fig. 1.

<img src="/fu_data.png" width="400">

The left side displays the normal images of each type in the dataset, while the right side shows different anomalies within each type of object or texture. All anomaly regions are marked in red.


## Data Statistics

### Data Statistics Compared to Previous NRE Dataset

Dataset | # Image | # Word | # Sentence | # Entity | # Relation | # Instance
-- | -- | -- | -- | -- | -- | -- 
SemEval-2010 Task 8 | - | 205k | 10,717 | 21,434 | 9 | 8,853
ACE 2003-2004 | - | 297k | 12,783 | 46,108 | 24 | 16,771 
TACRED | - | 1,823k | 53,791 | 152,527 | 41 | 21,773
FewRel | - | 1,397k | 56,109 | 72,124 | 100 | 70,000 
MNRE | 9,201 | 258k | 9,201 | 30,970 | 23 | 15,485

This is the version 2 of our MNRE dataset. We refine and merge some categories for better understandings. The dataset contains 15,484 samples and 9,201 images with 23 relation categories. We split the dataset into training, development and testing set with 12247, 1624 and 1614 samples, respectively.


### Category Distribution

<img src="pic/statistic.png" width="600">

We start tagging relation types depending on the entity types. For example, the relations between one person and another person can be classified into ''alumni'', ''couple'' and ''relative'' et al.

## Data Collection

We build the original corpus from three sources: two available multimodal named entity recognition datasets - [Twitter15 and Twitter17](https://github.com/jefferyYu/UMT), and crawling data from [Twitter](https://archive.org/details/twitterstream).

We utilize a pretrained NER tagging tool [elmo](https://allennlp.org/elmo) for extracting both entities and their corresponding types.

## Data Usage

Our processed textual relations are in `./mnre_txt/`, the image data can be downloaded [here](https://drive.google.com/file/d/1FYiJFtRayWY32nRH0rdycYzIdDcMmDFR/view?usp=sharing). 

>Each sentence is split into several instances (depending on the number of relations).
>Each line contains
>```
>'token': Texts preprocessed by a tokenizer
>'h': Head entities and their positions in a sentence
>'t': Tail entities and their positions in a sentence
>'image_id': You can find the corresponding images using the link above
>'relation': The relations and entity categories
>```

## Case Study

<img src="pic/case1.png" width="900">

Four examples for illustrating the effectiveness of visual information in extracting relations. The first line shows that the visual objects and their attributes can help in identifying relations. Further more, we show that the interactions of person-to-person or person-to-object can also provide clues for classifying relations.


## Citation
If you find this repo helpful, please cite the following:
```latex
@inproceedings{zheng2021mnre,
  title={MNRE: A Challenge Multimodal Dataset for Neural Relation Extraction with Visual Evidence in Social Media Posts},
  author={Zheng, Changmeng and Wu, Zhiwei and Feng, Junhao and Fu, Ze and Cai, Yi},
  booktitle={2021 IEEE International Conference on Multimedia and Expo (ICME)},
  pages={1--6},
  year={2021},
  organization={IEEE}
}
```
