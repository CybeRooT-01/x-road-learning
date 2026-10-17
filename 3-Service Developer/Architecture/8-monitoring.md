X-Road distingue **2 types de monitoring** on l'avais deja vu dans la section fundamentals : dans [[12-Monitoring]]
### 1. Environmental Monitoring

Surveille l’état technique du **Security Server (SS)** :

- OS
    
- RAM, disque, CPU
    
- Processus
    
- Packages installés
    
- Version X-Road
    
- Certificats
    

Le jeu de données peut être limité au **certificat, OS et version X-Road** pour le client central de monitoring.

### 2. Operational Monitoring

Surveille les **échanges de requêtes entre Security Servers** :

- ID du client et du service
    
- Attributs du message
    
- Date/heure requête et réponse
    
- Taille du message
    
- Temps de traitement
    

### Accès au monitoring

Peuvent interroger les données :

- **Owner du Security Server**
    
- **Central Monitoring Client** configuré par l’Operator
    
- Un **client normal**, mais uniquement pour **ses propres échanges**
    

Si un client tente d'accéder aux données d’un autre client → **`AccessDenied`**.

**À retenir :**

- Environmental = **état technique du SS**
    
- Operational = **activité des échanges**
    
- Accès limité selon le rôle et le client