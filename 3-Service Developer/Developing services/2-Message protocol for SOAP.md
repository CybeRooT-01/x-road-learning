### OpenAPI 3

Lors de la publication d'une API REST, on peut fournir :

- l'**URL de base de l'API**
- ou une **description OpenAPI 3** en JSON ou YAML

OpenAPI 3 est **optionnel**, mais utile :

- permet aux autres Members de récupérer la description via **`getOpenAPI`**
- le SS récupère automatiquement les **endpoints** définis dans OpenAPI
- ces endpoints deviennent disponibles pour la **gestion des droits d'accès**

Des endpoints peuvent aussi être ajoutés **manuellement**.

- Endpoints OpenAPI → modifiés via le document OpenAPI puis **refresh**
- Endpoints manuels → modifiables/supprimables directement par l'administrateur SS
- Les endpoints ne servent au SS qu'à la **gestion des droits** : le SS ne vérifie pas qu'un endpoint demandé existe réellement.

### Droits d'accès REST

Les droits peuvent être définis à 2 niveaux :

**API**  
→ accès à **tous les endpoints** de l'API.

**Endpoint**  
→ accès plus précis selon :

- méthode HTTP
- chemin (`path`)
- wildcards possibles

X-Road fonctionne en **autorisation positive uniquement** :

- on peut **autoriser** l'accès
- on ne peut pas définir explicitement un **deny**

Donc si un client ne doit pas accéder à certains endpoints, il faut éviter de lui donner l'accès global à l'API et définir les droits endpoint par endpoint.

### SOAP ↔ REST

Le Security Server ne fait **aucune conversion automatique** SOAP ↔ REST.

Si les deux versions sont nécessaires :

- le fournisseur doit implémenter SOAP
- et REST

Sinon, un **REST Adapter Service** peut servir de convertisseur.

### Authentification machine-to-machine

Entre **Security Server ↔ Information System REST** :

- **mTLS** supporté
- **JWT directement par X-Road : non supporté**

Mais une application peut utiliser **JWT au niveau applicatif** entre le client et le fournisseur, car les headers HTTP peuvent être transmis par X-Road.

**À retenir :**

- OpenAPI 3 = optionnel mais utile pour décrire les endpoints
- `getOpenAPI` = récupérer la description REST
- Droits REST = **API ou endpoint**
- X-Road = **allow uniquement**, pas de deny explicite
- Pas de conversion SOAP ↔ REST automatique
- mTLS = supporté entre SS et IS
- JWT = pas géré par X-Road, mais possible au niveau application