

<h2 align="center"> <a href="">NACrash: [TODO: Full Paper Title]</a></h2>

<h4 align="center"> <a href="https://liangkd.github.io/">Kaidi Liang</a>, <a href="">[TODO: Co-author]</a>, <a href="">[TODO: Co-author]</a>, <a href="">Ruwen Qin*</a></h4>

<h5 align="center"> If our project helps you, please give us a star ⭐ on GitHub to support us. 🙏🙏 </h5>

<h5 align="center">

[![WACV](https://img.shields.io/badge/WACV-2027-4B8BBE.svg)](https://wacv.thecvf.com/)
[![hf_checkpoint](https://img.shields.io/badge/🤗-Checkpoints-9C276A.svg)](https://huggingface.co/KDliang/NACrash)
[![hf_dataset](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Dataset-blue)](https://huggingface.co/datasets/KDliang/NACrash)
[![paper](https://img.shields.io/badge/Paper-PDF-red)](https://arxiv.org/pdf/XXXX.XXXXX)
[![arXiv](https://img.shields.io/badge/Arxiv-XXXX.XXXXX-AD1C18.svg?logo=arXiv)](https://arxiv.org/abs/XXXX.XXXXX)
</h5>

## 📰 News
- [26.10.16] ![NEW!](https://img.shields.io/badge/NEW!-red) Our paper has been accepted by **WACV 2027**. 🎉🎉🎉
- [TODO] The [paper](https://arxiv.org/abs/XXXX.XXXXX) has been published on arXiv.
- [TODO] Release the [Weights](https://huggingface.co/KDliang/NACrash) and [Datasets](https://huggingface.co/datasets/KDliang/NACrash) of **NACrash**.
- [26.10.16] Release the initial version of **NACrash**.


## 🌟 Introduction
- **NACrash** is a traffic crash video benchmark for evaluating and improving Multimodal Large Language Models (MLLMs) on crash video analysis. Our main contributions are:
  - (1) [TODO: contribution 1, e.g., the dataset and its annotation protocol];
  - (2) [TODO: contribution 2, e.g., the unified multitask formulation of crash video analysis];
  - (3) [TODO: contribution 3, e.g., a comprehensive benchmark of open- and closed-source MLLMs].
- NACrash contains **4,024 crash videos** collected from real-world dashcam footage (Nexar and YouTube), annotated for **9 tasks** that cover scene recognition, crash attribute classification, temporal localization, and dense description, with a total of [TODO] video-QA pairs.

<p align="center" width="100%">
<a target="_blank"><img src="figs/overview.png" alt="NACrash" style="width: 80%; min-width: 400px; display: block; margin: auto;"></a>
</p>


## 📊 Benchmark Tasks

| Category | Task | Annotation File |
|----------|------|-----------------|
| Scene recognition | Atmospheric recognition | `NACrash_*_atmospheric_recognition.jsonl` |
| Scene recognition | Light recognition | `NACrash_*_light_recognition.jsonl` |
| Scene recognition | Urban / rural classification | `NACrash_*_urban_rural_classification.jsonl` |
| Crash attributes | Collision type classification | `NACrash_*_collision_type_classification.jsonl` |
| Crash attributes | Collision manner classification | `NACrash_*_collision_manner_classification.jsonl` |
| Crash attributes | Involvement identification | `NACrash_*_involvement_identification.jsonl` |
| Temporal grounding | Pre-crash localization | `NACrash_*_pre_crash_localization.jsonl` |
| Temporal grounding | Crash localization | `NACrash_*_crash_localization.jsonl` |
| Language understanding | Dense description | `NACrash_*_dense_description.jsonl` |

**Data sources:**

| Source | # Videos |
|--------|---------:|
| Nexar | 1,458 |
| YouTube | 2,566 |
| **Total** | **4,024** |


## 🤗 Example Outputs
- **[TODO: caption of the qualitative example figure]**

<p align="center" width="100%">
<a target="_blank"><img src="figs/qualitative_analysis.png" alt="Qualitative_analysis" style="width: 60%; min-width: 400px; display: block; margin: auto;"></a>
</p>


<details>
  <summary>💡Click here to show detailed performance of MLLMs on the NACrash benchmark</summary>
  <img src="figs/benchmark_results.png" style="max-width: 100%; height: auto;">
</details>

<details>
  <summary>💡Click here to show [TODO: ablation / per-task analysis]</summary>
  <img src="figs/ablation.png" style="max-width: 100%; height: auto;">
</details>




## 🤖 Model Zoo (Fine-tuned Checkpoints)

| Checkpoint | MLLM backbone | Training Strategy - Task | Link |
|----------|-------------|-------------|--------------|
| [TODO] | [TODO] | Baseline | [Weights](https://huggingface.co/KDliang/NACrash) |
| [TODO] | [TODO] | Multitask - all tasks | [Weights](https://huggingface.co/KDliang/NACrash) |


**Notes:**
- Fine-tuned on instruction-tuning data from
  - [NACrash](https://huggingface.co/datasets/KDliang/NACrash)



## 🛠️ Requirements and Installation

#### Environment Preparation

Step 1: Clone repository:
```
git clone git@github.com:Liangkd/NACrash.git
cd NACrash
```

Step 2: Create and activate a Conda environment:
```
conda create -n nacrash python=3.10 -y
conda activate nacrash
```

Step 3: Install PyTorch ([TODO: version / CUDA]):
```
pip install --upgrade pip
pip install torch==[TODO] torchvision==[TODO] --extra-index-url https://download.pytorch.org/whl/[TODO]
```

Step 4: Install required Python dependencies:
```
pip install -r requirements.txt
```

Step 5: Install FFmpeg:
```
conda install -c conda-forge ffmpeg -y
```

#### Prerequisites

To use our code, please organize the video data and annotation files under `data`. For example:
```bash
data
├── videos
│   ├── nexar_xxxx.mp4
│   ├── youtube_xxxx.mp4
│   └── ...
├── JSON_bench                      # benchmark (evaluation) split
│   ├── NACrash_bench_ALL.json
│   ├── NACrash_bench_atmospheric_recognition.jsonl
│   ├── ...
│   └── NACrash_bench_urban_rural_classification.jsonl
├── JSON_remain                     # remaining videos (training split)
│   ├── NACrash_remain_ALL.json
│   └── ...
└── JSON_ALL                        # all videos
    ├── NACrash_all_ALL.json
    └── ...
```


## 🗝️ Training

#### Step 1: Prepare dataset and checkpoint
Download the dataset and model weights from Hugging Face; the file organization is as described above.

#### Step 2: Start training
```bash
# single GPU
CUDA_VISIBLE_DEVICES=0 bash scripts/train/[TODO].sh 1
# multiple GPUs
CUDA_VISIBLE_DEVICES=0,1 bash scripts/train/[TODO].sh 2
```

## ✅ Evaluation

#### Step 1: Run inference on the benchmark
```bash
# single GPU
CUDA_VISIBLE_DEVICES=0 bash scripts/eval/[TODO].sh
# multiple GPUs
CUDA_VISIBLE_DEVICES=0,1 bash scripts/eval/[TODO].sh 2
```

#### Step 2: Compute metrics
```bash
python scripts/eval/[TODO].py
```

## 📑 Citation

If you find NACrash useful for your research and applications, please cite using this BibTeX:

```bibtex
@inproceedings{liang2027nacrash,
  title     = {NACrash: [TODO: Full Paper Title]},
  author    = {Liang, Kaidi and [TODO] and Qin, Ruwen},
  booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
  year      = {2027}
}
```

## 👍 Acknowledgement

We gratefully acknowledge the open-source projects and datasets that inspired and supported this work, including [TODO: base MLLM], Nexar, and [CrashChat](https://github.com/Liangkd/CrashChat). Their contributions to vision-language modeling and real-world traffic understanding have been invaluable.


## :earth_americas: Contact

If you have any question, please feel free to email me (kaidi.liang@stonybrook.edu) or leave a comment under the 'Issues' module. Thank you!

