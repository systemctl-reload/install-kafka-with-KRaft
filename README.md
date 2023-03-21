## 1) Install Java JDK version 11

      wget -O- https://apt.corretto.aws/corretto.key | sudo apt-key add - 
      sudo add-apt-repository 'deb https://apt.corretto.aws stable main'
      sudo apt-get update; sudo apt-get install -y java-11-amazon-corretto-jdk


Upon completion, you should get a similar output when doing  `java -version`:


    openjdk version "11.0.18" 2023-01-17 LTS
    OpenJDK Runtime Environment Corretto-11.0.18.10.1 (build 11.0.18+10-LTS)
    OpenJDK 64-Bit Server VM Corretto-11.0.18.10.1 (build 11.0.18+10-LTS, mixed mode)


## 2) Install Apache Kafka

    cd /opt/
    
    wget https://archive.apache.org/dist/kafka/3.0.0/kafka_2.13-3.0.0.tgz
    
    sudo tar xzf kafka_2.13-3.0.0.tgz
    
    cd kafka_2.13-3.0.0/
    
    sudo apt-get install vim -y
    
    vim ~/.bashrc
    
    PATH="$PATH:/opt/kafka_2.13-3.0.0/bin"
    
## 3) start kafka

The first step is to generate a new ID for your cluster

    sudo /opt/kafka_2.13-3.0.0/bin/kafka-storage.sh random-uuid
    
This returns a UUID, for example 76BLQI7sT_ql1mBfKsOk9Q

Next, format your storage directory (replace <uuid> by your UUID obtained above)

    sudo /opt/kafka_2.13-3.0.0/bin/kafka-storage.sh format -t <uuid> -c  /opt/kafka_2.13-3.0.0/config/kraft/server.properties
