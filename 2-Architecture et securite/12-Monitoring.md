## Monitoring

X-Road sépare le monitoring en **2 catégories** :

### Environmental Monitoring

Surveille l’état **technique** du Security Server :

- OS

- RAM

- disque

- CPU

- processus

- packages installés

- version X-Road


Le nombre d’informations retournées peut être limité, notamment aux **certificats, OS et version X-Road**.

### Operational Monitoring

Surveille les **échanges de messages** entre Security Servers :

- ID du client et du service

- informations du message

- date/heure des requêtes et réponses

- taille du message

- temps de traitement


### Contrôle d’accès

Les données de monitoring sont accessibles uniquement à :

- l’**owner** du Security Server ;

- le **central monitoring client**, s’il est configuré ;

- un client normal, mais uniquement pour **ses propres données opérationnelles**.


Toute tentative non autorisée → **AccessDenied**.

**À retenir :**

`Environmental → état technique du SS`

`Operational → activité des échanges`

`Monitoring → accès limité aux données`