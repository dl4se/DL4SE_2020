# Studying the Usage of Text-To-Text Transfer Transformer to Support Code-Related Tasks

In this work, we study a novel transformers architecture T5(text-to-text Transfer Transformer) to support Code-Related Tasks.

#### Learning Pipeline

In order to pre-train and then finetune a [T5 small](https://github.com/google-research/text-to-text-transfer-transformer) we need a new sentencepiece model to accomodate the expanded vocabulary given by the java programming language, an abstracted version of the java tokens and tecnical natural language.

*  ##### How to train a new <a href='https://github.com/google/sentencepiece/blob/master/python/README.md'>SPmodel</a>

    *Pythonic way*

    ```
    pip install sentencepiece
    import sentencepiece as spm
    spm.SentencePieceTrainer.train('--input=pretraining.txt --model_prefix=dl4se --vocab_size=32000 --bos_id=-1  --eos_id=1 --unk_id=2 --pad_id=0') 
    ```
    The new model has to be trained on the entire pre-training corpus.

* ##### Set up a GCS Bucket
    To Set up a new GCS Bucket for training and fine-tuning a T5 Model, please follow the orignal guide provided by <a href='https://www.google.com'> Google </a>. 
    Here the link: https://cloud.google.com/storage/docs/quickstart-console
    Subsequently, by following the jupyter notebook we provide for pre-train and fine-tune the network, you should be able to set up the final environment.

* ##### About the datasets

    The datasets for the pre-training and the fine-tuning can be found here: https://drive.google.com/drive/folders/1uJv-kljY1Q59fa-TdkpXOOd9QEG5OZDa?usp=sharing


* ##### Pre-trainig/Fine-tuning 
  
    To pre-train and then, fine-tune T5, please use the script we provide here:
    - <a href ='https://github.com/dl4se/DL4SE_2020/blob/master/Code/fine-tuning.ipynb'>Pre-Training</a> 
    -  <a href ='https://github.com/dl4se/DL4SE_2020/blob/master/Code/pre-training.ipynb'>Fine-Tuning</a> 

* ##### How to generate the predictions

    First you need to convert the TF model into a pytorch model by using <a href='https://github.com/dl4se/DL4SE_2020/blob/master/Code/run-on-test-set/tf_2_pytorch_T5.py'> TF_to_Pytorch </a>, then run <a href='https://github.com/dl4se/DL4SE_2020/blob/master/Code/run-on-test-set/generate_results.ipynb'> Generate Results </a>
