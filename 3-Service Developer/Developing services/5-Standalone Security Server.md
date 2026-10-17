
Le **Standalone Security Server** est une version préconfigurée du Security Server, prête à utiliser en quelques minutes, sans installation ni enregistrement classiques.

### Caractéristiques

- Destiné aux **tests et au développement** de services X-Road.
- Contient 2 subsystems préconfigurés : un fournisseur et un consommateur.
- Permet de publier et d'appeler des services via le même SS.
- Ne nécessite ni Central Server, ni service OCSP, ni service d'horodatage.
- Peut fonctionner hors ligne après téléchargement.

### Limitation importante

Il **ne peut pas communiquer avec les autres Security Servers**. Il ne convient donc pas aux échanges réels entre organisations.

### Quand l'utiliser ?

Pour tester rapidement un service SOAP/REST compatible X-Road sans déployer un écosystème complet.

Disponible sur [Docker Hub — Standalone Security Server](https://hub.docker.com/r/niis/xroad-security-server-standalone).

**À retenir :** idéal pour le développement local et les tests, mais pas pour les échanges entre Security Servers.