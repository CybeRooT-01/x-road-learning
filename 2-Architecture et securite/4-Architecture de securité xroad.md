X-Road est une **couche d’échange de données open source** qui permet aux organisations d’échanger des informations de manière sécurisée.

### Identité et échanges

- **CA** → délivre les certificats aux organisations et Security Servers.

- Les identités sont gérées centralement.

- Les données circulent **directement entre les organisations**, sans intermédiaire.

- **Signature + horodatage** → garantissent la non-répudiation.

- Les preuves des échanges sont conservées localement.


### 3 principes de sécurité

**Confidentialité**

- Chiffrement + TLS → empêchent l’écoute et la modification des messages.
- Seuls les membres authentifiés et autorisés peuvent accéder aux données.

**Intégrité**

- Les messages sont **signés** par l’organisation qui les envoie.
- Les messages sont enregistrés dans les logs.
- PKI + certificats → vérifient l’identité et l’intégrité.

**Disponibilité**

- Aucun composant ne doit être un point unique de panne.

- Les Security Servers peuvent continuer à fonctionner temporairement si le Central Server, OCSP ou TSA est indisponible.

- Plusieurs Security Servers peuvent être utilisés en parallèle avec **load balancing + failover**.

### Schéma

```text
Organisation A                         Organisation B
     IS                                      IS
      │                                      │
      ▼                                      ▼
    SS A ──────── échange sécurisé ─────── SS B
      │                                      │
      └────────────── X-Road ───────────────┘
```

**À retenir :**

`Confidentialité → chiffrement / TLS`

`Intégrité → signatures / PKI`

`Disponibilité → redondance / failover`