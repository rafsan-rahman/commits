# SA_Inference_restAPI 
​
###  Overall Architecture
![screenshot](./figs/sa_inference_architecture.png)
​
###  Process of running the project 
​
This repository has two main components/processes. Namingly they are, model_server and web_server. Following tree structure shows the project structure for both components.
​
```
model_server
│   
└───checkpoint
│   │
│   └───BERT
│   │   electra_emotion.pth
│   │   electra_polarity.pth
│   │   electra_subjectivity.pth
│   │   
│   └───BCA
│   │   bca_sub_pol_emo_demo.hdf5
|   |
│   └───HAN
│   |    han_sub_pol_emo_demo.hdf5
|   |    han_word_sub_pol_emo_demo.hdf5
|   |
│   └───Topic
│   │   bert_topic.pth
│   │
│   └───Topic_Segment
│   |    combined_20k_global_keys.json
|   |    model/*
|   |
│   └───Language_Models
│   |    banglabert/*
|   |    gt_bert_1/*
​
```
​
```
web_server
│   
└───checkpoint
│     tokenizer.pickle
```
​
​
# Deployment
## Deploy locally
- model server
  - **Step-0:** cd into the model_server directory
  - **Step-1:** copy model_server related checkpoints to model_server
  - **Step-2:** Make sure you create a `.env` file in both model_server and web_server. the `.env` file should be similar to the provided `sample.env` file.          
  - **Step-3:** run `pip install -r requirements.txt`
  - **Step-4:** run  `python main.py`
​
- web server
  - **Step-0:** cd into the web_server directory
  - **Step-1:** copy web_server related checkpoints to web_server
  - **Step-2:** Make sure you create a `.env` file in both model_server and web_server. the `.env` file should be similar to the provided `sample.env` file.          
  - **Step-3:** run `pip install -r requirements.txt`
  - **Step-4:** run  `uvicorn main:app --reload --workers 5`
    
## Deploy with docker
  - **Step-0:** cd to `<root of your project>`
  - **Step-1:** make 2 directories called `ml_checkpoint` and `web_checkpoint`
  - **Step-3:** move `model_server` related checkpoints to `ml_checkpoint` directory
  - **Step-4:** move `web_server` related checkpoints to `web_checkpoint` directory
  - 
         cd <root of your project>
         docker-compose up --build -d
## anything
  -step 1: do anythong
    -step2: do **something**
  ​
