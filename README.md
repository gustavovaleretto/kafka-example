O serviço zookeeper será criado a partir da imagem confluentinc/cp-zookeeper, representando a instância do ZooKeeper;

Já o serviço kafka fará uso da imagem confluentinc/cp-kafka, correspondendo a uma instância do Apache Kafka acessível externamente na porta 9092 (e internamente para a network broker-kafka na porta 29092). Este container também referencia a instância do ZooKeeper em depends_on;

Quanto ao serviço kafdrop, o container deste serviço possibilitará o acesso via browser à interface de gerenciamento do Kafdrop na porta 19000. A variável de ambiente KAFKA_BROKERCONNECT foi configurada para se comunicar com o container kafka (vínculo também indicado em depends_on) internamente na porta 29092 (com isto acontecendo a partir da rede broker-kafka);


Nas seções environment de zookeeper, kafka e kafdrop foram definidas configurações (variáveis de ambientes) necessárias para a geração dos 3 containers;

Por meio da network broker-kafka ocorrerá a comunicação entre os containers zookeeper, kafka e kafdrop.