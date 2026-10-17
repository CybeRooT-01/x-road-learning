
Le **Security Server doit être protégé par un firewall**.

- Autoriser uniquement les connexions nécessaires.
    
- Pour les connexions entrantes, limiter les sources avec un **filtrage IP**.
    
- Une mauvaise configuration du firewall peut exposer le SS à des attaques.
    

### Connexions principales

|Source|Destination|Ports|
|---|---|---|
|SS|Central Server|`80, 443, 4001`|
|SS|SS partenaire|`5500, 5577`|
|SS|OCSP / TSA|`80, 443`|
|SS|IS Provider|`80, 443, autres`|
|SS|ACME|`80, 443`|
|Monitoring SS|SS|`5500, 5577`|
|SS partenaire|SS|`5500, 5577`|
|IS Consumer|SS|`8080, 8443`|
|Admin|SS|`4000`|

**Ports importants :**

`5500 / 5577 → communication SS ↔ SS`

`8080 / 8443 → IS → SS`

`4000 → administration du SS`

`80 / 443 → services HTTP/HTTPS`

### Monitoring

Le **Monitoring Security Server** doit pouvoir accéder au SS sur :

`5500 + 5577`

Cela permet à l’Operator de superviser l’écosystème.

### Ports internes (loopback)

Ces ports servent aux communications **locales entre composants du SS** :

- PostgreSQL → `5432`
    
- Operational Monitoring → `2080`
    
- Environmental Monitoring → `2552`
    
- Signer → `5559, 5560`
    
- Proxy → `5566, 5567`
    
- Configuration Client → `5675`
    
- Audit Log → `514/UDP`
    

**À retenir :**

`Firewall → limiter les accès au SS`

`5500/5577 → SS ↔ SS`

`8080/8443 → IS ↔ SS`

`4000 → administration`