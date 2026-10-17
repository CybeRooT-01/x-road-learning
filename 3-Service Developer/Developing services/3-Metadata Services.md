Les **Metadata Services** permettent aux participants X-Road de découvrir les Members, les services disponibles et leurs descriptions techniques.

Ils sont exposés par le **Security Server** via les protocoles de métadonnées SOAP et REST.

### Services disponibles

| Méthode               | Fonction                                          | Protocole       |
| --------------------- | ------------------------------------------------- | --------------- |
| `listClients`         | Liste les Members et subsystems                   | SOAP / REST     |
| `listCentralServices` | Liste les services centraux                       | SOAP uniquement |
| `listMethods`         | Liste les services d'un fournisseur               | SOAP / REST     |
| `listAllowedMethods`  | Liste les services accessibles au client appelant | SOAP / REST     |
| `getWsdl`             | Récupère la description d'un service SOAP         | SOAP            |
| `getOpenApi`          | Récupère la description d'une API REST            | REST            |

**Attention :** les versions SOAP et REST de `listMethods` et `listAllowedMethods` sont distinctes. Pour inventorier les deux types de services, il faut appeler les deux versions.

### Découverte d'un service

1. `**listClients**` → découvrir les Members et subsystems.
2. `**listMethods**` → découvrir les services proposés par un fournisseur.
3. `**listAllowedMethods**` → filtrer les services selon les droits du client.
4. `**getWsdl**` **/** `**getOpenApi**` → récupérer la description technique du service.
### À quoi ça sert ?

Ces métadonnées permettent aux outils de générer automatiquement :

- des catalogues de services ;
- des interfaces utilisateur ;
- des clients et des stubs pour appeler les services.
**À retenir :**

- `listMethods` = services proposés.
- `listAllowedMethods` = services autorisés pour le client.
- `getWsdl` = description SOAP.
- `getOpenApi` = description REST.
- `listCentralServices` = SOAP uniquement.