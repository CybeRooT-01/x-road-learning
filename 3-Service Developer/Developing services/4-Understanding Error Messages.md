
Pour diagnostiquer une erreur X-Road, il faut d’abord identifier **où elle a été générée**.

### Les 4 composants du flux

```
1. Service consumer (IS)
        ↓
2. Consumer-side SS (Client Proxy)
        ↓
3. Provider-side SS (Server Proxy)
        ↓
4. Service provider (IS)
```

Une erreur peut provenir du **Security Server client**, du **Security Server fournisseur** ou de l'**application fournisseur**.

### Structure des erreurs Security Server

Les erreurs possèdent 3 champs :

|REST|SOAP|Rôle|
|---|---|---|
|`type`|`faultCode`|Origine et type de l'erreur|
|`message`|`faultString`|Description de l'erreur|
|`detail`|`faultDetail`|ID permettant de retrouver les détails dans les logs|

### Identifier l'origine

- `Server.ClientProxy...` → erreur du **SS consommateur**.
- `Server.ServerProxy...` → erreur du **SS fournisseur**.
- Format d'erreur personnalisé ne respectant pas la structure X-Road → probablement erreur de l'**application fournisseur**.

### Où chercher les logs ?

Dans le Security Server concerné :

```
/var/log/xroad/proxy.log
```

Le champ `detail` contient un identifiant unique permettant de rechercher l'erreur dans ce fichier.

### Exemple

```
{
  "type": "Server.ClientProxy.SslAuthenticationFailed",
  "message": "Client specifies HTTPS but did not supply TLS certificate",
  "detail": "2ea02d93-e0b8-4e2b-8c6e-fac20f53a3e3"
}
```

Interprétation :

- `ClientProxy` → erreur côté consommateur.
- `SslAuthenticationFailed` → problème d'authentification TLS.
- Cause indiquée → HTTPS demandé, mais certificat TLS client absent.

En REST, le header HTTP `**X-Road-Error**` est ajouté à la réponse lorsque l'erreur provient de l'un des deux Security Servers.

**À retenir :** identifier le composant → lire le type et le message → rechercher `detail` dans `proxy.log`.