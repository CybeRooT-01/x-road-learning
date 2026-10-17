
X-Road accepte uniquement les certificats délivrés par des **CA approuvées** et définies dans le Central Server.

- Plusieurs CA peuvent être approuvées dans une même instance.

- Les **clés/certificats d’authentification du Security Server** sont stockés sur un **software token**.

- Les clés de signature peuvent être stockées sur un **software token ou un HSM**.


### ACME

**ACME** peut automatiser la gestion et le renouvellement des certificats si :

- la CA supporte ACME ;

- l’opérateur l’active dans le Central Server.

### Signer

Le composant **Signer** gère les clés et certificats de signature.

Il est utilisé pour :

- créer/vérifier les signatures ;
    
- générer les clés ;
    
- générer les demandes de certificats.
    

### Clés

Par défaut, X-Road utilise des clés **RSA 2048 bits**.

Des clés **2048, 3072 et 4096 bits** peuvent être utilisées simultanément.

**À retenir :**

`CA approuvée → certificats autorisés`

`Software token / HSM → protection des clés`

`ACME → gestion automatique des certificats`

`Signer → gestion des signatures`