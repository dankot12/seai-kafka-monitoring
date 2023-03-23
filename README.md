# seai-kafka-monitoring
Steps to install prometheus and run prometheus client

To come prepared for the recitation tomorrow, install the following on your team's VM (if not already installed):
1. Python (preferably 3.8, 3.9, 3.10)
2. Navigate to the folder `seai-kafka-monitoring`:
    - `cd seai-kafka-monitoring`
2. Install the dependencies required:
    - `pip install -r requirements.txt`
3. Install docker (follow steps described here: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
4. Run the following command containing the `docker-compose.yaml` file:
    - `docker compose up -d`
5. Open the file `kafka-monitoring.py` and update the `topic` variable (line 4) to match your team number.
6. (Not a pre-recitation step) Connect your VM to your Kafka Broker if not connected already:
    - `ssh -o ServerAliveInterval=60 -L 9092:localhost:9092 tunnel@128.2.204.215 -NTf`    
7. (Not a pre-recitation step) Run this command when you attend the recitation:
    - `python kafka-monitoring.py`

---

Link:
1. Grafana - http://128.2.24.106:3000/

---

Other commands:

1. Command to kill an already existing connection with Kafka Broker:
    - `lsof -ti:9092 | xargs kill -9`
2. Install kafkacat on your VM:
    - `sudo apt-get install kafkacat`
3. Query kafka topic events through kafkacat
    - `kcat -b localhost:9092 -t "movielog2" -p latest`

---

Notes: If you're not seeing any metric data on Prometheus or Grafana, please check if the kafka topic events are not throwing an error. If the topic has events that do not respond back with 200 status code, change the topic to some other topic `movielogN`
