## Message Protocols & Transport Protocol

Ils constituent le **cœur des échanges de données X-Road**.

### 1. Message Protocol

Utilisé entre :  
**Information System (IS) ↔ Security Server (SS)**

Deux protocoles :

- **SOAP Message Protocol**
    
- **REST Message Protocol**
    

L’IS communique donc avec son SS en utilisant le protocole correspondant à son service.

### 2. Message Transport Protocol

Utilisé entre :  
**Security Server ↔ Security Server**

- Basé sur **HTTPS**
    
- Utilise **TLS avec authentification mutuelle par certificats**
    
- Permet de sécuriser les échanges entre les SS.
    

### SOAP ↔ REST

X-Road **ne convertit pas automatiquement SOAP en REST ou inversement**.

Si un service existe en SOAP et REST, le fournisseur doit implémenter **les deux versions**.

Pour faire une conversion automatique, on peut utiliser **REST Adapter Service**, une extension X-Road qui fournit un convertisseur REST/SOAP avec certaines limitations.

### Schéma mental

```text
IS consommateur
      ↓
Message Protocol (REST/SOAP)
      ↓
SS consommateur
      ↓
Message Transport Protocol
HTTPS + mTLS
      ↓
SS fournisseur
      ↓
Message Protocol (REST/SOAP)
      ↓
IS fournisseur
```

**À retenir :**

- **IS ↔ SS = Message Protocol**
    
- **SS ↔ SS = Message Transport Protocol**
    
- **Pas de conversion SOAP ↔ REST automatique**