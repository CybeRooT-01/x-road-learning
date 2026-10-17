
Les **headers X-Road** permettent d’identifier le **client**, le **service appelé** et le **message**.

Le routage X-Road utilise ces identifiants pour retrouver la localisation réseau réelle du service.

### Headers principaux

|SOAP|REST|Rôle|
|---|---|---|
|`client`|`X-Road-Client`|Identifie le client qui appelle le service|
|`service`|`X-Road-Service`|Identifie le service appelé|
|`centralService`|—|Identifie un service central|
|`id`|`X-Road-Id`|ID unique du message, généralement UUID|
|`userId`|`X-Road-UserId`|Identifie l'utilisateur à l'origine de l'action|
|`issue`|`X-Road-Issue`|Référence à un dossier, document ou procédure|
|`protocolVersion`|—|Version du protocole SOAP (`4.0`)|
|`requestHash`|`X-Road-Request-Hash`|Hash de la requête, présent dans la réponse|
|`securityServer`|`X-Road-Security-Server`|Permet de cibler un SS précis|

### REST vs SOAP

**REST :**

- Le service est identifié dans **l'URL** de la requête.
    
- Le seul header X-Road obligatoire dans la requête est **`X-Road-Client`**.
    
- Le SS fournisseur ajoute automatiquement les headers X-Road dans la réponse.
    
- Un service REST existant peut donc généralement être publié **sans modification**.
    

**SOAP :**

- La requête doit contenir **`service` ou `centralService`**.
    
- Le service SOAP doit respecter les exigences des headers X-Road.
    
- Dans la réponse, le service doit **recopier les headers de la requête dans le même ordre et avec les mêmes valeurs**.
    
- Un **adapter service** peut être utilisé si le service existant n'est pas compatible X-Road.
    

### Headers HTTP personnalisés

Les applications peuvent aussi utiliser leurs propres headers.

- **REST** → les headers HTTP sont généralement transmis tels quels, sauf exceptions.
    
- **SOAP** → seuls certains headers HTTP sont conservés, notamment `Content-Type` et `SOAPAction`.
    

**À retenir :**

```
Headers X-Road
      ↓
Identifient client + service + message
      ↓
X-Road utilise ces identifiants pour router
      ↓
Security Server cible le bon service
```

Point important pour l'examen :

**REST = service dans l'URL + headers ajoutés automatiquement par le SS**

**SOAP = headers X-Road à respecter côté service**