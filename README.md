# INFO7390 Advanced Data Sciences and Architecture : Final Project

## Image summary generation or caption generation for images using CNN-LSTM and GRU network

 ![image](https://user-images.githubusercontent.com/13203059/165004536-6b233779-ebed-4570-9e1e-fc831f186b5a.png)

### Team


| Team Member     | NUID      | 
|-----------------|-----------|
| Ankana Asit Baran Samanta  | 001007431 |
| Kshitij Zutshi | 001021288 | 
| Parth Shah | 001006181 | 

### Abstract


Image caption generation/ image summarization is a task that involves generating a semantic
description of an image in natural language and is currently accomplished by techniques that use a
combination of computer vision (CV), natural language processing (NLP), and machine learning
methods. The inspiration for such an application can be inferred from Social media platforms like
Facebook(Now Meta), that summarize the image posted by the user and infer details like - where
you are, what you wear etc. This application also has a profound use in assisting visually impared
individuals in comprehending the images of the real world. In this task, we work on a model that
generates natural language description of an image. We intend to use a combination of
convolutional neural networks to extract features and then use recurrent neural networks to
generate text from these features. We incorporated the attention mechanism while generating
captions. We evaluated the model on the Flikr8k database.


### Problem Statement

Given an image, we want to obtain a sentence that describes what the image consists of.

### Approach

For image caption generation, we will be primarily using two models :

1. LSTM (Long Short Term Memory)
2. GRU (Gated Recurrent Unit)

For better accuracy we will be extending our model through Hyperparameter Tuning and provide
visualization for the outputs and the results of the models.

### Running the Notebooks

1. [Image Caption generation using LSTM and CNN Notebook :](https://github.com/shahparth0007/AdvanceDataScience/blob/main/image_caption_generator_with_cnn_lstm.ipynb)

In order to get the data pulled from kaggle and setup the dataset source directory -

```
# Setup the connection to kaggle using its API

!gdown --id 1jXH8vzpVy4gAkc-1lrWlwVUNF4w0B0dU
!pip install kaggle
! mkdir ~/.kaggle
! cp kaggle.json ~/.kaggle/
! chmod 600 ~/.kaggle/kaggle.json

# Download the Dataset from Kaggle 

! kaggle datasets download parthshah0007/flickerdataset

# Unzip the contents to your local directory

! unzip -q '/content/flickerdataset.zip' -d '/content/flickr8k/'

```

### Evaluation Metrics for Image Captioning 

The current codebase uses NLTK to calculate BLEU scores. However, BLEU-1 to BLEU-n can be easily implemented. We are using the NLTK library for doing this which provides a nice interface to achieve this.

Here is the explanation of how BLEU score computation is defined:

**BLEU-n** is just the geometric average of the n-gram precision.

```
(precisely it's string matching, at different n-gram levels, between references and hypotheses; 

that's why there has been much criticism on this metric. 

But, people still use it anyways because it has stuck with the community for ages)
```

For example, **BLEU-1** is simply the **unigram precision**, **BLEU-2** is the **geometric average of unigram and bigram precision**, **BLEU-3** is the **geometric average of unigram, bigram, and trigram precision** and so on.

Having said that, if you want to compute specific **n-gram BLEU scores**, you have to pass a weights parameter when you call **corpus_bleu** . Note that if you ignore passing this weights parameter, then by default BLEU-4 scores are returned, which is what happening in the evaluation here.

To compute, BLEU-1 you can call copus_bleu with weights as
```
weights = (1.0/1.0, )
corpus_bleu(references, hypotheses, weights)
```

To compute, BLEU-2 you can call corpus_bleu with weights as

```
weights=(1.0/2.0, 1.0/2.0,)
corpus_bleu(references, hypotheses, weights)
```

To compute, BLEU-3 you can call corpus_bleu with weights as

```
weights=(1.0/3.0, 1.0/3.0, 1.0/3.0,)
corpus_bleu(references, hypotheses, weights)
```

To compute, BLEU-5 you can call corpus_bleu with weights as

```
weights=(1.0/5.0, 1.0/5.0, 1.0/5.0, 1.0/5.0, 1.0/5.0,)
corpus_bleu(references, hypotheses, weights)
```


### References


https://cs224d.stanford.edu/reports/msoh.pdf

https://iopscience.iop.org/article/10.1088/1742-6596/1712/1/012015/pdf

https://arxiv.org/pdf/1412.3555.pdf

https://www.freecodecamp.org/news/building-an-image-caption-generator-with-deep-learning-in-tensorflow-a142722e9b1f

https://vision.cornell.edu/se3/wp-content/uploads/2018/03/1501.pdf
 

 
