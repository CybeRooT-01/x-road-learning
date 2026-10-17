## Input Validation

X-Road valide les données **côté serveur** pour éviter les entrées malveillantes.

### Web UI

Le Central Server UI et le Security Server UI :

- suppriment les espaces inutiles ;

- vérifient les champs obligatoires ;

- limitent les entrées à **255 caractères**.

### Messages

Les données XML sont validées avec leur **schéma XML** avant traitement.

→ Réduit les risques d’**XML Injection** et bloque les données invalides dès la frontière de confiance.

## Logging

Les logs permettent notamment la **non-répudiation** : les échanges peuvent servir de preuve numérique.

### 3 logs principaux

- **Audit log** → actions et changements effectués via l’interface, réussis ou échoués.

- **Message log** → requêtes/réponses échangées, signées et horodatées pour pouvoir prouver un échange.

- **System service log** → fonctionnement interne des services du Security Server.


### Message Log

- 1 enregistrement par transaction.

- Les messages peuvent être **chiffrés au repos**.

- Archivage périodique sur disque.

- Suppression automatique des anciennes archives selon une durée configurée.

- Les archives peuvent être exportées vers un stockage long terme.

- Un audit peut produire une archive **ZIP protégée contre la modification**, avec une signature/hash de l’arbre des logs.

### Digital Seals

X-Road supporte les **digital seals** :

- **Advanced**

- **Qualified** → nécessite notamment un **HSM** et une CA répondant aux exigences de confiance.

**À retenir :**

`Input validation → empêcher les données invalides`

`Audit log → actions`

`Message log → preuve des échanges`

`System log → fonctionnement`

`Digital seal → intégrité + preuve`