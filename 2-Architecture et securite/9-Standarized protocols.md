
X-Road utilise des **protocoles standardisés** pour que les Members n’aient pas à gérer eux-mêmes la sécurité des échanges.

- **Message Protocol** → `IS ↔ Security Server` pour envoyer/recevoir les requêtes.

- **Message Transport Protocol** → `SS ↔ SS` ; HTTPS + authentification TLS mutuelle par certificats.

- **Configuration Download Protocol** → `Central Server → SS/Configuration Proxy` pour télécharger la configuration globale.

- **Service Metadata Protocol** → découvrir les Members et les services disponibles.

- **Download Signed Document Protocol** → récupérer les documents signés depuis le Message Log.

- **Management Services Protocol** → gérer les Security Servers, clients, certificats, etc.

- **OCSP** → vérifier la validité des certificats. Le Security Server met les résultats en cache.

- **Time-Stamping Protocol** → horodater les messages/logs pour conserver une preuve à long terme.

- **ACME** → automatiser l’obtention et le renouvellement des certificats.


### À retenir

`IS ↔ SS → Message`

`SS ↔ SS → Transport`

`Central → SS → Configuration`

`OCSP → Certificats`

`TSA → Horodatage`

`ACME → Certificats automatisés`