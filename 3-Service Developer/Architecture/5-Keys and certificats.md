Depuis X-Road 7, les clés sont divisées en **2 catégories** :

`Data in transit → données en circulation`

`Data at rest → données stockées`

### Data in transit

**1. Authentication key + certificate**

- Identifie le **Security Server**.
    
- Utilisé pour authentifier `SS ↔ SS`.
    
- Stocké dans le **soft token**.
    

**2. Sign key + certificate**

- Identifie le **Member**.
    
- Signe les messages et garantit leur intégrité.
    
- Soft token ou **HSM**.
    

**3. Internal TLS certificate**

- Sécurise `SS ↔ Information System`.
    
- Peut servir de certificat client ou serveur.
    

**4. UI/API TLS certificate**

- Sécurise l’accès à l’interface d’administration et à l’API REST du SS.
    
- Par défaut sur le port `4000`.
    
- Généré automatiquement à l’installation.
    

**5. API Keys**

- Authentifient les appels à l’API REST d’administration.
    
- Associées à des rôles → déterminent les permissions.
    

### Data at rest

**1. Internal GPG key**

- Signe/vérifie les sauvegardes et archives.
    
- Permet leur chiffrement/déchiffrement selon la configuration.
    

**2. Backup/restore GPG keys**

- Clés supplémentaires pour chiffrer les sauvegardes.
    

**3. Database encryption key**

- Chiffre le contenu des messages dans la base du **Message Log**.
    

**4. Message log archive encryption keys**

- Clés publiques spécifiques à chaque Member.
    
- Chiffrent les archives du Message Log appartenant à ce Member.
    

### À retenir

`Authentication → identifie le SS`

`Sign → identifie le Member + signe les messages`

`Internal TLS → SS ↔ IS`

`UI/API TLS → administration du SS`

`API Key → accès API`

`GPG / DB keys → protection des données stockées`