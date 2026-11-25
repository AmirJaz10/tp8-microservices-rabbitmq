# MicroservicesApp - TP8 (Ocelot + RabbitMQ & MassTransit)

## Architecture
- **ApiGateway** : point d'entrée unique configuré avec Ocelot.
- **OrdersAPI** : gère les commandes (`POST /api/Orders`) et publie `OrderCreatedEvent` via MassTransit.
- **ProductsAPI** : gère les produits et écoute `OrderCreatedEvent` (`OrderCreatedConsumer`) pour décrémenter `StockQte`.

## Prérequis & lancement de RabbitMQ
Il n'y a pas de fichier `docker-compose.yml` dans ce dépôt : RabbitMQ est exécuté via Docker Desktop.

Démarrer RabbitMQ avec l'interface d'administration :
```bash
docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
