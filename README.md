# clip-robustness
Project for CS444@UIUC, Spring 2022. Examine the robustness of CLIP and its image/text encoders under various conditions.

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


# tmp

CLIP (and we) use [simple labels for ImageNet classes](https://github.com/anishathalye/imagenet-simple-labels) (see OpenAI's code [here](https://github.com/openai/CLIP/blob/main/notebooks/Prompt_Engineering_for_ImageNet.ipynb)
