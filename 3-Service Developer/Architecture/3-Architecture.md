## Architecture

Un écosystème X-Road repose sur **5 composants principaux** :

`Central Services + Security Servers + Information Systems + TSA + CA`

### Central Services

**Central Server**

- registre des Members et Security Servers ;
    
- politique de sécurité : CA/TSA de confiance + paramètres ;
    
- distribue la **Global Configuration**.
    

**Configuration Proxy** _(optionnel)_

- récupère la Global Configuration du Central Server ;
    
- la redistribue aux Security Servers ;
    
- réduit la charge du Central Server et améliore la disponibilité.
    

### Security Server

Point d’entrée obligatoire pour utiliser X-Road.

Il :

- relaie les requêtes/réponses entre IS ;
    
- gère clés, certificats, signatures et canaux sécurisés ;
    
- horodate et journalise les messages ;
    
- supporte REST et SOAP ;
    
- peut héberger plusieurs organisations (**multi-tenancy**).
    

**Clés :**

- `Authentication key → SS ↔ SS`
    
- `Signing key → signature des messages du Member`
    

Le SS conserve une copie locale valide de la Global Configuration et des informations de validité des certificats → il peut continuer à fonctionner temporairement même si les sources sont indisponibles.

Il possède un **load balancer interne** et peut aussi utiliser un load balancer externe.

### Information System (IS)

Application métier qui **produit ou consomme** des services via X-Road.

- Supporte REST et SOAP.
    
- REST → description avec **OpenAPI 3**.
    
- SOAP → description avec **WSDL**.
    
- Un service REST existant peut être publié sans modification.
    
- X-Road ne convertit pas automatiquement REST ↔ SOAP.
    
- Le Metadata Protocol permet de découvrir Members et services.
    

### TSA

**Time-Stamping Authority**

Fournit les **horodatages** utilisés par les Security Servers pour prouver qu’un message existait à un moment donné.

X-Road utilise principalement le **batch time-stamping** → plusieurs messages traités ensemble, ce qui réduit la charge du TSA.

### CA

**Certification Authority**

Délivre :

- **Authentication certificates → Security Servers**
    
- **Signing certificates → Members**
    

Les certificats servent respectivement à sécuriser `SS ↔ SS` et à signer les messages.

Le **OCSP** vérifie leur validité.

Seuls les certificats provenant de **CA approuvées dans le Central Server** sont acceptés.

### Vue globale

```text
             Central Server
                   │
          Global Configuration
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
       SS A  ─────────────── SS B
        │       X-Road        │
        ▼                     ▼
       IS A                  IS B
        │                     │
       CA                    TSA
```

**À retenir :**

`Central Server → configuration`

`SS → sécurité + échanges`

`IS → application métier`

`CA → certificats`

`TSA → horodatage`