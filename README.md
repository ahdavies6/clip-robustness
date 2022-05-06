# clip-robustness
Project for CS444@UIUC, Spring 2022. Examine the robustness of CLIP and its image/text encoders under various conditions.

# Setup
`git clone --recurse-submodules https://github.com/ahdavies6/clip-robustness.git`


### Install Dassl dependencies
Dassl is already included as a submodule if you clone using recurse-submodules

All you have to do is follow the first few steps to install Dassl (from [here](https://github.com/KaiyangZhou/Dassl.pytorch#installation)):
```bash
cd Dassl.pytorch/
conda create -n dassl python=3.7
conda activate dassl
pip install -r requirements.txt
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
python setup.py develop
```
Note that the cudatoolkit version is specific to the `timan108` setup

### Install CoOp dependencies

make sure you're still in dassl conda environment, then do this:

```bash
cd ../CoOp/
pip install -r requirements.txt
```

### Download ILSVRC 2012 val and prep for CoOP

I already have this saved, so we shouldn't have to do this again. See `notebooks/convert_class_labels.ipynb` for synset conversion. CLIP (and we) use [simple labels for ImageNet classes](https://github.com/anishathalye/imagenet-simple-labels) (see OpenAI's code [here](https://github.com/openai/CLIP/blob/main/notebooks/Prompt_Engineering_for_ImageNet.ipynb)

### Simlink to shared dataset
```bash
cd ..
mkdir data
ln -s /shared/timan108/imagenet data/imagenet
```

# Running ImageNet Experiment

```bash
cd CoOp/scripts/
conda activate dassl
bash main.sh imagenet vit_b32 end 16 1 False
```

# Results from robustness_metrics

https://colab.research.google.com/drive/1hJN_TbwFxaQjuwdH24Ryrr6Qa3jaOoAW#scrollTo=DTwQ3hqH5FBE
|DatasetName|Accuracy|ModelName|
|---|---|---|
imagenet|0\.598|clip\_vit_b32|
imagenet\_v2|0\.531|clip\_vit_b32|
imagenet\_r|0\.447|clip\_vit_b32|
imagenet\_c_average|0\.391|clip\_vit_b32|
imagenet\_a|0\.147|clip\_vit_b32|

|DatasetName|Accuracy|ModelName|
|---|---|---|
|imagenet|0\.806|vit-b/32|
|imagenet\_v2|0\.696|vit-b/32|
|imagenet\_c_average|0\.608|vit-b/32|
|imagenet\_r|0\.431|vit-b/32|
|imagenet\_a|0\.120|vit-b/32|
