
# install Dassl

follow the first few steps to install Dassl (from [here](https://github.com/KaiyangZhou/Dassl.pytorch#installation)):

```bash
# Clone this repo
git clone https://github.com/KaiyangZhou/Dassl.pytorch.git
cd Dassl.pytorch/

# Create a conda environment
conda create -n dassl python=3.7

# Activate the environment
conda activate dassl

# Install dependencies
pip install -r requirements.txt
```

however, the torch installation in the `dassl` environment will be wrong (we need the updated cudatoolkit and torch), so instead of running the `conda install pytorch ...` command, run

```bash
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```

then run the last command (from [here](https://github.com/KaiyangZhou/Dassl.pytorch#installation)) to finish up:
```bash
python setup.py develop
```

# install CoOp

(I'm not sure how this will work with my having added CoOp as a `git submodule` -- if it's already there, then just install `requirements.txt`; if it's not, do the `git clone` command as well)

make sure you're still in dassl conda environment, then do this:

```bash
cd ..
git clone https://github.com/KaiyangZhou/CoOp.git
cd CoOp/

pip install -r requirements.txt
```

<!-- then, depending on how the `git submodule` bit works, you may or may not need to change the following: -->

now add a link to the dataset:

```bash
mkdir data  # (if it's not already there)
ln -s /shared/timan108/imagenet data/imagenet
```

# set up ImageNet

## download ILSVRC 2010 val

TODO: WE NEED TO SWITCH TO ILSVRC 2012 -- IT'S THE ONE WITH ALL THE RIGHT CLASSES (see `notebooks/convert_class_labels.ipynb`)

(I already have this saved, so we shouldn't have to do this again.)

## set up ImageNet for CoOp

(I already did this in a shared dir, but for reference, e.g. in case we need to do it again, see bottom of `notebooks/convert_class_labels.ipynb`)

# run experiment

I'm trying

```bash
cd CoOp/scripts/
conda activate dassl
bash main.sh imagenet vit_b32 end 16 1 False
```

(2022-04-23: This errors out because the image classes are misaligned. See "download ILSVRC 2010 val" section and bottom of `notebooks/convert_class_labels.ipynb` for more details.)
