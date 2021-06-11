# kafka-cluster

## Resumo

Estudos de um kafka cluster, executado em ambiente Docker, com 3 nós e comandos via terminal para envio e recebimento de mensagens

## Tutoriais

https://www.youtube.com/watch?v=PppMhofKzy4
https://medium.com/better-programming/a-simple-apache-kafka-cluster-with-docker-kafdrop-and-python-cf45ab99e2b9

## Links

https://github.com/confluentinc/cp-docker-images
https://github.com/lbrack1/kafka-tutorial/blob/master/docker-compose.yml

## Servidor Kafka

Abaixos comandos para interagir com o cluster Kafka rodando em Docker

```bash
# Docker

    # Entrar em um dos nós do cluster Kafka:
    docker-compose exec kafka sh

# Tópicos

    # Listar tópicos
    kafka-topics --list --bootstrap-server kafka:9092

    # Criar um tópico no Kafka
    kafka-topics --create --replication-factor 1 --partitions 1 --topic meutopico --bootstrap-server kafka:9092 

    # Descrever tópico
    kafka-topics --describe --topic meutopico --bootstrap-server kafka:9092

    # Listar tópicos
    kafka-topics --list --bootstrap-server kafka:9092

    # Alterar Partições de um Tópico
    kafka-topics --alter --bootstrap-server kafka:9092 --topic orders-order-created --partitions 10

    # Deletar Topico
    kafka-topics --bootstrap-server kafka:9092 --delete --topic someTopic

# Producer

    # Iniciar um produtor de mensagens
    kafka-console-producer --broker-list kafka:9092 --topic meutopico

# Consumer

    # Iniciar um consumer de mensagens
    kafka-console-consumer --bootstrap-server kafka:9092 --topic meutopico

    # Ler as mensagens desde o início
    kafka-console-consumer --bootstrap-server kafka:9092 --topic meutopico --from-beginning

    # Especificando um grupo para escalar os consumers. Dica: Executar em pelo menos uns 3 consumers para testar a escalabilidade.
    kafka-console-consumer --bootstrap-server kafka:9092 --topic meutopico --group a

    # Descrever um grupo de consumidores:
    kafka-consumer-groups --group a --bootstrap-server kafka:9092 --describe

```