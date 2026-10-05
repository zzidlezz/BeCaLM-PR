# BeCaLM-PR

Download [BeCaLM-PR.zip](./BeCaLM-PR.zip) and extract it before running the commands below. The source archive preserves the full project directory structure and contains no prior Git history.

Code for BeCaLM: Behavioral Calibration for LLM Debiasing.

## Directory Structure

```text
BeCaLM/
├── cache/
├── checkpoints/
├── config/
├── data/
├── dataset/
├── editor/
├── glue_eval/
├── outputs/
├── scripts/
├── main.py
├── model.py
├── nets.py
├── util.py
├── requirements.txt
└── README.md
```

## Environment Setup

```bash
conda create -n becalm python=3.9 -y
conda activate becalm
pip install -r requirements.txt
```

Base models need to be downloaded manually, and the local paths should be set in the config files.
Different experiment settings are annotated in:
`editor/base.py`
Please refer to the comments in this file for switching between different setups.

Example commands for different models and methods:

```bash
python main.py \
    data=stereoset \
    model=llama3.yaml \
    editor=BeCalm \
    data.n_edits=128 \
    data.batch_size=16 \
    model_device=cuda:0 \
    editor_device=cuda:0 \
    early_stop_patience=3 \
    +retain_loss=true

python main.py \
    data=stereoset \
    model=mistral.yaml \
    editor=BeCalm \
    data.n_edits=128 \
    data.batch_size=16 \
    model_device=cuda:0 \
    editor_device=cuda:0 \
    early_stop_patience=3 \
    +retain_loss=true

python main.py \
    data=stereoset \
    model=gemma.yaml \
    editor=BeCalm \
    data.n_edits=128 \
    data.batch_size=16 \
    model_device=cuda:0 \
    editor_device=cuda:0 \
    early_stop_patience=3 \
    +retain_loss=true

python main.py \
    data=stereoset \
    model=gpt2m.yaml \
    editor=BeCalm \
    data.n_edits=128 \
    data.batch_size=16 \
    model_device=cuda:0 \
    editor_device=cuda:0 \
    early_stop_patience=3 \
    +retain_loss=true
```

## Acknowledgements

Parts of the implementation build on [BiasEdit](https://github.com/zjunlp/BiasEdit), including model, data-loading, editing, and utility infrastructure. BeCaLM-specific calibration code and experiment configurations are provided in this repository. The BiasEdit project also acknowledges [MALMEN](https://github.com/ChenmienTan/malmen) and [bias-bench](https://github.com/McGill-NLP/bias-bench).

Please cite the relevant original work when using those components, including [BiasEdit: Debiasing Stereotyped Language Models via Model Editing](https://arxiv.org/abs/2503.08588).
