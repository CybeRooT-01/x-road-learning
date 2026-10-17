## Central Server

Le **Central Server** gère :

- les **Members** et leurs Security Servers ;
- la **politique de sécurité** de l’instance :

    - CA de confiance ;
    
    - TSA de confiance ;
    
    - paramètres de sécurité (ex. durée maximale d’un OCSP).
    

Ces informations forment la **Global Configuration**, distribuée aux Security Servers via HTTP/HTTPS.

La Global Configuration est **signée par le Central Server** puis vérifiée par les Security Servers.

### Configuration Anchor

Le **Configuration Anchor** permet au Security Server :

- de trouver la source de configuration ;
    
- de vérifier l’authenticité de la Global Configuration.
    

C’est un fichier **XML**, fourni par l’opérateur et installé lors de l’initialisation du Security Server.

## Security Server

Le **Security Server (SS)** est l’intermédiaire sécurisé entre :

`Information System → SS → Internet → SS → Information System`

Il sécurise et conserve la valeur de preuve des échanges.

### Identité

Un Security Server est identifié par :

`Server ID = Member ID + Server Code`

Il possède :

- une ou plusieurs clés/certificats d’authentification locaux ;
    
- **un seul certificat d’authentification actif et enregistré** dans le Central Server ;
    
- une adresse DNS ou IP.
    

### Vérification SS ↔ SS

Lors d’un échange, chaque SS vérifie que le certificat de l’autre :

1. vient d’une **CA approuvée** ;
    
2. correspond au certificat enregistré dans la **Global Configuration** ;
    
3. possède un **OCSP valide**.
    

Si une vérification échoue → **message rejeté**.

Les échanges utilisent :

`Signature numérique + TLS/HTTPS`

### Contrôle d’accès

Le Security Server du **fournisseur** vérifie que le Member consommateur possède bien le droit d’utiliser le service.

`Service publié ≠ accès automatique`

**À retenir :**

`Central Server → configuration + politique de confiance`

`Security Server → sécurité + échanges + contrôle d’accès`