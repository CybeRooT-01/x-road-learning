FYI: IS = Information system et SS = Security Server
- **Message Protocol** → `IS ↔ Security Server`  
	Échange des requêtes/réponses REST ou SOAP.

- **Configuration Download** → `Central Server → Security Server / Proxy`  
    Télécharge la configuration globale signée.

- **Message Transport Protocol** → `Security Server ↔ Security Server`  
    Échange sécurisé via **HTTPS + TLS mutuel**, avec signatures et données de sécurité.

- **Service Metadata Protocol** → `IS → X-Road`  
    Permet de découvrir les Members et services disponibles.

- **Download Signed Document** → `IS → Security Server`  
    Récupère des documents signés depuis le message log.

- **Management Services** → `Security Server → Central Server`  
    Gestion des clients et certificats.

- **OCSP** → `Security Server → OCSP Responder`  
    Vérifie la validité des certificats. Les réponses sont mises en cache.

- **ACME** → `Security Server ↔ CA`  
    Automatise l’émission et le renouvellement des certificats.

- **Time-Stamping** → `Security Server → TSA`  
    Horodate les messages pour conserver leur valeur de preuve. Fonctionne par **batch**.

### Monitoring

- **Store Operational Monitoring Data** → Security Server → Daemon
    
- **Operational Monitoring Query** → Security Server ← Daemon
    
- **Operational Monitoring Protocol** → Système externe → Daemon
    
- **Operational Monitoring JMX** → Monitoring local → Security Server
    
- **Environmental Monitoring Protocol** → Monitoring → Security Server
    
- **Environmental Monitoring JMX** → Monitoring local → Security Server
    
- **Environmental Monitoring Query** → Security Server ← Daemon
    

### Interfaces utilisateur

- **Security Server UI** → administration du Security Server.

- **Central Server UI** → administration du Central Server.FYI

### Le schéma à retenir

```text
IS
 │
 │ Message Protocol
 ▼
Security Server
 │
 │ Message Transport Protocol
 ▼
Security Server
 │
 ▼
IS

Central Server
     │
     │ Configuration
     ▼
Security Servers

Security Server ──► CA      (certificats)
Security Server ──► OCSP    (validité)
Security Server ──► TSA     (horodatage)
```

**Les 3 protocoles centraux :**

`IS ↔ SS` → Message Protocol  
`SS ↔ SS` → Message Transport Protocol  
`Central → SS` → Configuration