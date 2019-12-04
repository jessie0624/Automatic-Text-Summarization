# Automatic-Text-Summarization

Now this task is on-going. I will update my progress here.


- Step-1: Read text summarization paper and related blogs. The summary blog is on-going including seq2seq/pointer-generation and unilm.(WIP)
        
- Step-2: Get Chinese text summarization data. (Done -- 11.29)
        LCSTS A Large Scale Chinese Short Text Summarization Dataset.You can get paper here: https://arxiv.org/abs/1506.05865.
        To get the data, you'd better sent application mail to the team. They are very nice, you will get data about 1 day later.
        
- Step-3: Data process. (Done -- 12.03)
       I highly recommend you read the 'README_IMPORTANT.txt' and their paper, it will help you know well about the data.
       Here is part of 'README_IMPORTANT.txt' which tells us how to use it.
       
        1. PART I: is the main contents of LCSTS that contains 2,400,591 (short text, summary) pairs. It can be used to train supervised learning models for summary generation.
        2. PART II: contains 10,666 human labled (short text, summary) pairs which can be used to train classifier to filter the noises of the PART I.
        3. PART III: contains 1,106 (short text, summary) pairs, this part is labled by 3 persons with the same labels. These pairs with score 3,4 and 5 can be used as test set for evaluating summary generation systems. 

     Let process the data getting clean data files for trainning. It is very easy just extracting id/summary/short_text/(human_label) in each file and saving to three csv files.
      
- Step-4: Model Create. (WIP)
        There are 2 models will be created.
            - One is BertForSequenceClassification trained with PART_II.txt and tested with PART_III.txt which include 'human_label' to note the summarization quality (1-5, 1 is least related summarization, 5 is most related summarization).
            With the classification model, we can label the PART_I.txt, and drop those items with label 1 and 2 (least related summarization)
            - The other one is text summarization model BERT+Seq2seq. As there is no chinese version pretrained model from unim, I'm going to use BERTBase + Seq2seq mask method creating text summarization model, with this model , we can use BERT Chinese pretrained model.
        
