
X-Road permet une **communication sécurisée entre organisations**. Son architecture repose sur plusieurs composants et protocoles.

### Principes clés

- **Décentralisé** : échange direct entre organisations, sans intermédiaire.
- **Propriété des données** : le fournisseur garde le contrôle de ses données et des accès.
- **Disponibilité** : pas de point unique de panne ni de gros goulot d’étranglement.
- **Preuve numérique** : les messages peuvent servir de preuves grâce aux signatures et horodatages.
- **REST / SOAP** : les échanges utilisent ces deux types de services.
- **Cross-border** : possibilité d’appeler un service d’une autre instance X-Road.
- **Sécurité intégrée** : X-Road gère la sécurité dans ses composants, pas besoin de la réimplémenter.
- **Standardisation** : même protocole pour communiquer avec différents fournisseurs. Pas de conversion automatique REST ↔ SOAP.
- **Rôles flexibles** : un Member peut être **client et fournisseur** sans nouvelle inscription.
- **Double authentification** :
    - X-Road → authentifie l’organisation et contrôle les accès.
    - Information System → authentifie l’utilisateur final.

**À retenir :** X-Road standardise et sécurise les échanges sans centraliser les données.