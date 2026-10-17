Les 3 entités principales de X-Road :

### 1. Member

Organisation participante à X-Road, autorisée à échanger des données.

- Un Member peut avoir plusieurs **Security Servers**.
    
- Un Security Server peut être associé à **maximum 2 Members**.
    

### 2. Subsystem

Représente une partie du système d'information d'un Member.

- Un Member doit déclarer ses parties de SI comme **subsystems** pour utiliser X-Road.
    
- Chaque subsystem possède ses **propres droits d'accès**.
    
- Un Member peut avoir plusieurs subsystems.
    
- Un subsystem peut être associé à plusieurs Security Servers.
    
- Plusieurs subsystems de différents Members peuvent utiliser le même Security Server.
    
- Les messages du subsystem sont signés avec le **certificat de signature du Member** qui le gère.
    

### 3. Service

Service **SOAP ou REST** fourni par un subsystem et cons