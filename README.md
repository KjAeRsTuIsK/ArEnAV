# Tell me Habibi, is it Real or Fake? 

# 
<p align="center">
    <img src="https://i.imgur.com/waxVImv.png" alt="Oryx Video-ChatGPT">
</p>

#### [Kartik Kuckreja](https://www.linkedin.com/in/kartik-kuckreja-930531221/), [Parul Gupta](https://scholar.google.com.au/citations?user=Wik3mXsAAAAJ&hl=en), [Injy Hamed](https://scholar.google.com/citations?user=N_RhXusAAAAJ&hl=en), [ Thamar Solorio](http://solorio.uh.edu/), [Muhammad Haris Khan](https://m-haris-khan.com/) and [ Abhinav Dhall](https://research.monash.edu/en/persons/abhinav-dhall)

#### **Mohamed bin Zayed University of AI, Birla Institute of Technology & Science, Monash University**

---

## 📢 Latest Updates
- [ArEnAV-Full](https://huggingface.co/datasets/kartik060702/ArEnAV-Full) and [ArEnAV-Preview](https://huggingface.co/datasets/parulgupta/ArEnAV_preview/viewer/default/test?views%5B%5D=test) is open-sourced 🔥🔥🔥
---


## Dataset Link & Usage Guidelines
The dataset is under the [EULA](eula.pdf). You need to agree and sign the EULA to access the dataset.

The baseline Xception code [/examples/xception](/examples/xception) is under MIT Licence. The BA-TFD/BA-TFD+ code [/examples/batfd](/examples/batfd) is from [ControlNet/LAV-DF](https://github.com/ControlNet/LAV-DF) under CC BY-NC 4.0 Licence.

The other parts of this project is under the CC BY-NC 4.0 license. See [LICENSE](LICENSE) for details.

Once the EULA has been filled, access the dataset:
**Download** → [Hugging Face – ArEnAV-Full](https://huggingface.co/datasets/kartik060702/ArEnAV-Full)

1. `git lfs install && git clone https://huggingface.co/datasets/kartik060702/ArEnAV-Full`
---

## Overview
ArEnAV is the **first multimodal deepfake benchmark** that expressly targets Arabic ↔ English **code-switching**.  
It contains **387 k videos (~765 h)** generated with a three-stage pipeline that alters transcripts, clones speech, and diffusion-syncs lips, yielding highly realistic, hard-to-detect fakes.

---

## Content
- [Dataset Statistics](#dataset-statistics)
- [Data Generation](#data-generation)
- [Results](#results)
- [Conclusion](#conclusion)

---

## Dataset Statistics
![Dataset statistics](path/to/dataset_statistics_image.png)

### Cross-Dataset Comparison (Table 1)
| Dataset | Year | Tasks | Modality | Method | #Clips | Multilingual | Code-Switch |
|---------|------|-------|----------|--------|--------|--------------|-------------|
| Google DFD | 2019 | Cla | V | FS | 3 431 | ✗ | ✗ |
| DFDC | 2020 | Cla | AV | FS | 128 154 | ✗ | ✗ |
| DeeperForensics | 2020 | Cla | V | FS | 60 000 | ✗ | ✗ |
| Celeb-DF | 2020 | Cla | V | FS | 6 229 | ✗ | ✗ |
| KoDF | 2021 | Cla | V | FS/RE | 237 942 | ✗ | ✗ |
| FakeAVCeleb | 2021 | Cla | AV | RE | 25 500+ | ✗ | ✗ |
| ForgeryNet | 2021 | SL/TL/Cla | V | FS/RE | 221 247 | ✗ | ✗ |
| ASVSpoof2021-DF | 2021 | Cla | A | TTS/VC | 593 253 | ✗ | ✗ |
| LAV-DF | 2022 | TL/Cla | AV | RE/TTS | 136 304 | ✗ | ✗ |
| DF-Platter | 2023 | Cla | V | FS | 265 756 | ✗ | ✗ |
| **AV-1M** | 2023 | TL/Cla | AV | RE/TTS | 1 146 760 | ✗ | ✗ |
| **PolyGlotFake** | 2024 | Cla | AV | RE/TTS/VC | 15 238 | ✓ | ✗ |
| **Illusion** | 2025 | Cla | AV | FS/RE/TTS | 1 376 371 | ✓ | ✗ |
| **ArEnAV (ours)** | 2025 | Cla/TL | AV | RE/TTS/VC | **387 072** | **✓** | **✓** |

### Split-wise Distribution (Table 6)
| Subset | Unique Vids | Real | Fake | Non-Eng | CSW Vids | Arabic Vids | Arabic Variants |
|--------|-------------|------|------|---------|----------|-------------|-----------------|
| PolyGlotFake | 766 | 766 | 14 472 | 11 941 | 0 | 1 403 | – |
| Illusion | – | 141 440 | 1 234 931 | 4 385 | 0 | – | – |
| Train | 6 117 | 67 600 | 202 800 | 270 400 | 69 544 | 200 856 | Eg, MSA, Lev, Gulf |
| Val   | 876  | 9 560  | 28 680  | 38 240  | 10 416 | 27 824 | Eg, MSA, Lev, Gulf |
| Test  | 1 816| 19 608 | 58 824 | 78 432 | 19 832 | 58 600 | Eg, MSA, Lev, Gulf |
| **Total** | **8 809** | **96 768** | **290 304** | **387 072** | **99 792** | **287 280** | – |

---

## Data Generation
![Generation pipeline](path/to/data_generation_image.png)

1. **Transcript rewrite** – GPT-4.1-mini applies eight edit modes (meaning-only, dialect-shift, translation…).
2. **Speech synthesis** – XTTS-v2 / Fairseq-Arabic TTS / GPT-TTS + OpenVoice-v2 clone the original speaker.
3. **Lip-sync** – Diff2Lip & LatentSync diffusion models render mouth motion; 25 random audio/visual perturbations simulate real-world noise.

---

## Results
![Results overview](path/to/results_image.png)

### Temporal Localization (Table 8)  
*(Full table preserved for reproducibility)*  

| Set | Method | Mod. | AP@0.5 | AP@0.75 | AP@0.9 | AP@0.95 | AR@50 | AR@30 | AR@20 | AR@10 | AR@5 |
|-----|--------|------|--------|---------|--------|---------|-------|-------|-------|-------|------|
| **Full** | Meso4 | V | 0.02 | 0.01 | 0.00 | 0.00 | 0.09 | 0.09 | 0.09 | 0.09 | 0.09 |
|  | MesoInception4 | V | 0.56 | 0.18 | 0.04 | 0.01 | 4.11 | 4.11 | 4.11 | 4.11 | 4.08 |
|  | Xception | V | 22.50 | 10.26 | 2.29 | 0.58 | 19.13 | 19.13 | 19.13 | 19.13 | 19.13 |
|  | BA-TFD (ZS) | AV | 0.17 | 0.01 | 0.00 | 0.00 | 9.72 | 5.20 | 3.07 | 1.46 | 0.73 |
|  | BA-TFD+ (ZS) | AV | 0.11 | 0.00 | 0.00 | 0.00 | 5.77 | 2.95 | 2.09 | 0.87 | 0.37 |
|  | BA-TFD | AV | 2.42 | 0.55 | 0.01 | 0.00 | 22.30 | 10.31 | 3.41 | 2.54 | 1.67 |
|  | BA-TFD+ | AV | 3.74 | 1.10 | 0.06 | 0.01 | 30.75 | 9.42 | 4.55 | 3.05 | 1.83 |
| **Subset V** | *see paper* | | | | | | | | | | |
| **Subset A** | *see paper* | | | | | | | | | | |

### Deepfake Detection (Table 9)  
| Access | Pre-train | Method | Mod. | Full AUC | Full Acc | V AUC | V Acc | A AUC | A Acc |
|--------|-----------|--------|------|----------|----------|-------|-------|-------|-------|
| Zero-shot | ASVSpoof-19 | XLSR-Mamba | A  | 39.19 | 52.77 | 52.73 | 40.68 | 52.50 | 42.59 |
| Zero-shot | Web | Video-LLaMA-7B | V  | 51.48 | 26.29 | 51.47 | 34.21 | 51.43 | 34.18 |
| … | … | … | … | … | … | … | … | … | … |
| Fine-tuned | AV-1M + ArEnAV | **BA-TFD+** | AV | **79.97** | 27.44 | 84.20 | 36.47 | 72.89 | 34.56 |

### Cross-Dataset Temporal Localization (Table 10)
| Method | Dataset | AP@0.5 | AP@0.75 | AP@0.95 | AR@50 | AR@20 | AR@10 |
|--------|---------|--------|---------|---------|-------|-------|-------|
| BA-TFD | LAV-DF | 79.15 | 38.57 | 0.24 | 64.18 | 60.89 | 58.51 |
|  | AV-1M | 37.37 | 6.34 | 0.02 | 45.55 | 35.95 | 30.66 |
|  | **ArEnAV** | **2.42** | 0.55 | 0.01 | 22.30 | 3.41 | 2.54 |
| BA-TFD+ | LAV-DF | 96.30 | 84.96 | 4.44 | 80.48 | 79.40 | 78.75 |
|  | AV-1M | 44.42 | 13.64 | 0.03 | 48.86 | 40.37 | 34.67 |
|  | **ArEnAV** | **3.74** | 1.10 | 0.04 | 30.75 | 4.55 | 3.05 |

### Human Evaluation (Table 7)
| Metric | Value |
|--------|-------|
| Accuracy | 60 % |
| AP @ 0.1 | 8.35 |
| AP @ 0.5 | 0.79 |
| AR @ 1 | 1.38 |

---


## License

The dataset is under the [EULA](eula.pdf). You need to agree and sign the EULA to access the dataset.

The baseline Xception code [/examples/xception](/examples/xception) is under MIT Licence. The BA-TFD/BA-TFD+ code [/examples/batfd](/examples/batfd) is from [ControlNet/LAV-DF](https://github.com/ControlNet/LAV-DF) under CC BY-NC 4.0 Licence.

The other parts of this project is under the CC BY-NC 4.0 license. See [LICENSE](LICENSE) for details.


## Conclusion
ArEnAV reveals that state-of-the-art detectors **struggle badly** with cross-lingual, code-switched deepfakes (≥ 35 pp performance drop vs. monolingual benchmarks).  
We hope this dataset drives research toward **robust, multilingual, audio-visual deepfake detection**.

*Add acknowledgements & citation here.*
