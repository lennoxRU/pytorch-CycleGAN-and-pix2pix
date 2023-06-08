# pytorch-CycleGAN-and-pix2pix
CycleGan

Structure
This work makes use of two networks:
•             Image classifier (fully original effort): This network is trained to classify the given images into two decoration styles.
•             CycleGAN: We have modified the original implementation (https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) by removing the identity mapping loss, which yields better style classification results (section 5.3 in the final report) compared to the original implementation.

Dataset
The dataset used in this work was collected and processed by ourselves. It is available on Google Drive. https://drive.google.com/file/d/18cfRTjo2bohzSYs7oul3gSp9fgSME4eF/view?usp=sharing

Train Style Classifier
To train the image classifier using this dataset, please follow these steps:
1.          Download the dataset and navigate to the image-classifier directory.
2.          Create a new directory named dataset within image-classifier.
3.          Unzip the chinese_fresh.zip file, and move the resulting chinese_fresh folder to dataset. Rename it as style_transfer.
4.          Once the dataset is prepared, refer to the README file in image-classifier/ for instructions on training the decoration style classifier.
To save training effort, we have uploaded a pre-trained model to Google Drive (https://drive.google.com/file/d/1TgZow8fUxnytzl_MdQB-GFpELy0si5W8/view?usp=share_link). You can directly download it and execute the make infer command as mentioned in image-classifier/README.md. Pass the path of the pre-trained model to the model argument.

Train CycleGAN
To train CycleGAN for decoration style transfer, please follow these steps:
1.          Download the dataset and navigate to the pytorch-CycleGAN-and-pix2pix directory.
2.          Within the pytorch-CycleGAN-and-pix2pix directory, navigate to (or create) the datasets directory.
3.          Unzip the chinese_fresh.zip file within the datasets directory.

After the dataset is prepared, go to the root path of pytorch-CycleGAN-and-pix2pix and execute the following command to train the model:
bash scripts/train_cyclegan.sh
Once the training is finished, you can test the model by running the following command:
bash scripts/test_cyclegan.sh
The fake images will be generated and can be found at pytorch-CycleGAN-and-pix2pix/results/chinese_fresh_no_preprocess/test_latest/images after the command finishes.
To save training effort, we have uploaded two sets of pre-trained models to Google Drive (https://drive.google.com/file/d/1TgZow8fUxnytzl_MdQB-GFpELy0si5W8/view?usp=share_link). One includes the identity mapping loss, and the other does not. To utilize the pre-trained models, execute the following commands:
$ cd pytorch-CycleGAN-and-pix2pix && mkdir -p checkpoints/chinese_fresh_no_preprocess_no_map && cd checkpoints/chinese_fresh_no_preprocess_no_map
$ # Download the model that you want to try, either with or without identity mapping loss.
$ unzip $model_name.zip # Replace the model name with the actual name.
