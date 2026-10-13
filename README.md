# CNN plant health classifier

This was homework 1 in Artificial Neural Networks and Deep Learning (AN2DL) at Politecnico di Milano, autumn 2023. We did it as a team of three (Axel Friberg Hagen, Vegard Sjåvik and Lasse Uttian, team name RedstoneRookies). The task was to classify 96x96 images of plants as healthy or unhealthy, and the teams competed on a hidden test set.

The dataset has 5,200 images, and roughly 62% of them are healthy. Some of the images weren't plants at all (the same pictures of Shrek and the Trololo guy, over and over), and there were also quite a few exact duplicates. We removed both before doing a stratified 60/20/20 train/validation/test split. A LeNet-style CNN did no better than always guessing the majority class, so we switched to transfer learning. Of the ImageNet backbones we tried, MobileNetV2 did best. We fine-tuned it from layer 100 onwards, using augmentation (brightness, translation, rotation, contrast and flips) and class weights, and that became the final model.

On our own held-out test split (970 images), the fine-tuned model got 0.808 accuracy and 0.784 macro F1. The report (`AN2DL_homework1.pdf`) goes through the experiments and who did what.

## Running it

Everything is in `RedstoneRookies05.ipynb`. You need the course dataset `public_data.npz`, which isn't included, and the packages in `requirements.txt`. The notebook ran on TensorFlow 2.14 in Colab. The paths point to our Google Drive, so you'll have to change them first.
