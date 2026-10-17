- **Central Server** → gère les Members, Security Servers et la **configuration globale**.
- **Security Server** → fait transiter les appels, gère **sécurité, clés, signatures, certificats, timestamps et logs**.
- **Information System (IS)** → application qui **utilise ou fournit** les services X-Road.
- **TSA** → fournit les **horodatages** pour prouver l’existence des données à un moment donné.
- **CA** → délivre les **certificats** aux Security Servers et Members + vérifie leur validité via OCSP.
- **Configuration Proxy** → copie et redistribue la configuration globale pour **réduire la charge** du Central Server et améliorer la disponibilité.
- **Operational Monitoring Daemon** → collecte les données sur l’**activité** du Security Server.
- **Environmental Monitoring Daemon** → surveille l’**environnement technique** du Security Server.

### Security Server : clés

- **Authentication key** → sécurise la connexion entre Security Servers.
- **Signing key** → signe les messages du Member.

### Schéma
![[X-Road_Protocols.png]]