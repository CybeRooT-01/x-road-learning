
**X-Road** = couche d’échange de données **distribuée et sécurisée** entre systèmes d’information.

Fonctions principales :

- routage des messages ;

- gestion des adresses et droits d’accès ;

- authentification des organisations et machines ;

- chiffrement TLS ;

- signatures + horodatage ;

- logs + gestion des erreurs.


## X-Road Ecosystem

Un **écosystème** regroupe les organisations utilisant la même instance X-Road.

- **Operator** → gère l’écosystème, les adhésions et les règles.

- **Members** → fournissent ou consomment des services.

- Aucune limite technique stricte de taille.

## Trusted Network

L’identité des organisations et des points d’accès est vérifiée avec des **certificats d’une CA de confiance**.

Les identités sont gérées centralement, mais les données circulent **directement entre les parties**.

`Consumer → SS → SS → Provider`

Les preuves d’échange restent chez les parties concernées.

`Signature + horodatage → non-répudiation`

## Authorization

Publier un service ne le rend **pas automatiquement accessible**.

Le **Provider** possède ses données et décide quels Members/IS peuvent y accéder.

`Service publié ≠ accès automatique`

## Monitoring

X-Road permet de surveiller :

- utilisation des services ;
    
- état des services ;
    
- dépendances entre systèmes ;
    
- versions X-Road.
    

`Member → ses données`

`Operator → données de tous les Members`

## Cross-border / Federation

La **fédération** connecte plusieurs écosystèmes X-Road.

Les Members des écosystèmes fédérés peuvent échanger des services entre eux.

La fédération est **directe** : elle n'est pas transitive.

`A ↔ B` + `B ↔ C` ≠ `A ↔ C`

### À retenir

`X-Road = échanges sécurisés + standardisés + décentralisés`

`Operator → règles`

`Member → services`

`Provider → contrôle les accès`

`Federation → connecte les écosystèmes`