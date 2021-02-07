# keyword_spotting_system
This is a system for detecting 30 english keywords, based on [Google audio dataset](https://ai.googleblog.com/2017/08/launching-speech-commands-dataset.html). Here is the project pipeline:

The audio preprocessing output is MFCCs. THe modal training is CNN

# Installation
- Clone this code to your machine 
- If you want to take your hand on the project, download the [Google audio dataset](https://ai.googleblog.com/2017/08/launching-speech-commands-dataset.html). Go to prepare_dataset.py for preproceesing the dataset and train it at train.py 

- If you only want to test or use the system, pull the following docker images:
  - docker pull minhairtran/server_nginx:latest
  - docker pull minhairtran/server_training_flask:latest

Then create docker-compose.yml, paste:
``` 
version: "3.7"

  services:

  flask:
    build: ./flask
    container_name: flask
    restart: always
    expose:
      - 900

  nginx:
    build: ./nginx
    container_name: nginx
    restart: always
    ports:
      - "80:1234"
 ```
 
 Then build the docker-compose.yml by this command docker-compose build
 Finally run the docker-compose.yml by docker-compose up
