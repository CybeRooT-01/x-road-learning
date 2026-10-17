5 composants :

`Central Services → Security Server → Information System`

`↓`

`TSA / CA`

### 1-Central Services

**Central Server**

- Registre des Members + Security Servers
- Politiques de sécurité
- Liste des CA/TSA de confiance
- Configuration globale

**Configuration Proxy** _(optionnel)_

- Récupère la configuration du Central Server
- La redistribue aux Security Servers
- Réduit la charge + améliore la disponibilité

### 2-Security Server

**Point d’entrée de X-Road.**

- Obligatoire pour provider + consumer
- Transporte les requêtes/réponses
- Signature, authentification, chiffrement
- Horodatage + logs
- REST + SOAP
- Peut héberger plusieurs organisations

Deux types de clés :

- **Authentication key** → communication entre Security Servers
- **Signing key** → signature des messages du Member

Le Security Server garde une **copie locale de la configuration** → X-Road continue de fonctionner même si le Central Server est temporairement indisponible.

### 3-Information System

Application qui **fournit ou consomme** un service.

- REST → OpenAPI 3
- SOAP → WSDL
- Découverte des services → Metadata Protocol

Le Security Server sert d’intermédiaire entre l’application et X-Road.

### 4-TSA — Time-Stamping Authority

Ajoute un **horodatage** aux messages.

But : prouver qu’une donnée existait à un moment précis.

`Message → Security Server → TSA`

X-Road utilise le **batch time-stamping** pour réduire la charge.

### 5-CA — Certification Authority

Émet les certificats :

- **Authentication certificate** → Security Server ↔ Security Server
- **Signing certificate** → signature des messages

La CA vérifie aussi la validité des certificats via **OCSP**.

### À retenir

`Central Server = configuration`

`Security Server = échanges + sécurité`

`Information System = application`

`TSA = horodatage`

`CA = certificats`

C’est littéralement le cœur de l’architecture X-Road.