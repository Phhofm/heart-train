# HEART — training

Train your own [HEART](https://huggingface.co/Phips/HEART) model.

**NERVE links:** [models & configs](https://huggingface.co/Phips/NERVE) · [try it online (ZeroGPU)](https://huggingface.co/spaces/Phips/nerve) · [convert a checkpoint](https://huggingface.co/spaces/Phips/nerve-convert) · [local app](https://github.com/Phhofm/nerve-app) · [train your own (Colab)](https://github.com/Phhofm/nerve-train)

## Google Colab (easiest, free GPU)

Open **[`heart_train_colab.ipynb`](heart_train_colab.ipynb)** in Colab
(*File → Open notebook → GitHub*, or upload it), then run the cells in order.
The last cell gives you a small form:

- **Scale**: 4x / 2x
- **Data**: OTF degradation (HR folder only) or paired HR/LR folders
- optional **validation** HR/LR folders
- a **warm-start** dropdown (start from a released HEART model)
- **Iterations** and a run **name**
- press **Start training**

It clones traiNNer-redux, drops in the HEART architecture, and trains. Put your
images in Google Drive (the notebook mounts it for you).

HEART is larger than a conv net: on a free Colab GPU start with batch size 2, and
set `use_checkpoint: true` in the generated config if you run out of memory.

## Locally

HEART is a normal traiNNer-redux architecture:

```bash
cp heart_arch.py <traiNNer-redux>/traiNNer/archs/
cp configs/4x_HEART_release.yml <traiNNer-redux>/options/
cd <traiNNer-redux>
python train.py -opt options/4x_HEART_release.yml --auto_resume
```

Sample configs, ONNX files and released pretrains (great warm-starts) live at
[huggingface.co/Phips/HEART](https://huggingface.co/Phips/HEART).

Apache-2.0.
