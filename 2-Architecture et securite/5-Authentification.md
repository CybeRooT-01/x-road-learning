L’authentification vérifie **qui est l’organisation ou le composant** qui communique.

- **Certificat + clé d’authentification** → identifient le Security Server.

- Le **Security Server** est le point d’entrée de l’organisation vers X-Road.

- L’authentification de l’utilisateur final est gérée par le **Information System**.

- Un Security Server compromis peut être bloqué en révoquant son certificat ou en le retirant de la configuration centrale.

## Contrôle d’accès

Principe : **moindre privilège** → chacun accède uniquement à ce qui est nécessaire.

### Échanges de données

Le Security Server contrôle l’accès au niveau de l’organisation.

Le **fournisseur du service** décide quels Members peuvent utiliser ses services.

`Service publié ≠ accès automatique`

### Interface Web

L’accès est refusé **par défaut**.

Les permissions dépendent du **rôle de l’utilisateur**.

**À retenir :**

`Authentification → Qui es-tu ?`

`Autorisation → Qu’as-tu le droit de faire ?`

`Deny by default → aucun accès sans autorisation`