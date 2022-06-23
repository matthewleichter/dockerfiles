# dockerfiles
files for docker compose and faust streaming 

Go to https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud?resource=download and download the creditcard.csv file in this root folder if using on your local. Once you have that, copy everything EXCEPT fraud_model folder. That will be created when you run the first jupyter notebook code at the mlflow command on the last line.

Note: make sure you are in this root folder when running any of these commands. Also there are a number of pip installs and conda installs you'll need:
a. Kafka-python
b. mlflow (mlflow[extras] recommended AND as a conda install using conda-forge)
c. zookeeper
d. faust-streaming

1. Run the fraud detection training file in jupyter notebook to create the model and set up the model in mlflow
2. run the command in your prompt "mlflow models serve -m fraud_model"
3. wait forever as it sets up the nlflow pipeline for the model (seriously go plan a vacation or something, maybe watch Avengers Endgame, nah not that long)
4. run the command in a new prompt window "docker-compose up" (make sure youre in the folder with docker-compose.yml)
5. run the command in prompt "faust -A fraud_detection_worker worker -l info" (this will turn on faust streaming and assign an agent to the kafka_topic "test")
6. You will then start to see logs of the model running and counting the number of fraud transactions

