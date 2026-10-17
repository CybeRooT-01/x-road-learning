Le **Message Transport Protocol** permet aux **Security Servers (SS) d’échanger les requêtes et réponses**.

### Fonctionnement

- Communication **synchrone** : le SS du client initie l’échange.
    
- Basé sur **HTTPS + TLS mutuel (mTLS)**.
    
- Chaque SS s’authentifie avec son **certificat d’authentification**.
    
- Les messages SOAP/REST sont encapsulés dans un message **MIME multipart** avec les données de sécurité : signatures, réponses OCSP, etc.
    

```text
IS client
   ↓
SS client
   ↓  HTTPS + mTLS
SS fournisseur
   ↓
IS fournisseur
```

### 2 couches

**1. Transport layer**

- HTTP over TLS mutuellement authentifié.
    
- Port SS↔SS par défaut : **5500**.
    

**2. Application layer**

- Messages X-Road au format **MIME multipart (`multipart/mixed`)**.
    
- Contient le message SOAP/REST + informations de sécurité.
    

### Authentification TLS

Lorsqu'un SS client contacte un SS fournisseur :

1. Le SS client détermine le SS fournisseur.
    
2. Il démarre le handshake TLS sur **5500**.
    
3. Le SS fournisseur présente son certificat d'authentification.
    
4. Le SS client vérifie le certificat et sa chaîne.
    
5. Il vérifie les **réponses OCSP**.
    
6. Si tout est valide → le message est envoyé.
    
7. Le SS fournisseur vérifie à son tour le certificat du SS client.
    

Si la vérification échoue → le message n'est pas transmis.

### OCSP

Les SS utilisent **OCSP** pour vérifier la validité des certificats.

- Les réponses OCSP sont **mises en cache**.
    
- Si elles ne sont pas disponibles, le SS client les récupère auprès du SS fournisseur.
    
- Canal utilisé pour cela : **HTTP port 5577** par défaut.
    

Donc :

- **5500 → échanges SS ↔ SS**
    
- **5577 → récupération des réponses OCSP**
    

### Application Layer : intégrité

Le message X-Road est **signé** par le Security Server pour garantir son intégrité.

Deux types :

- **Signature normale**
    
- **Batch signature** : notamment pour les messages contenant des pièces jointes ou pour signer plusieurs messages efficacement.
    

Le SS doit **mettre en cache le message reçu avant de vérifier sa signature**, car un message invalide ne doit jamais être transmis à l'autre côté.

### Transport Message

Le message X-Road est encodé en :

```text
MIME multipart/mixed
```

Il encapsule le message **SOAP ou REST** ainsi que les informations nécessaires à l'échange sécurisé.

Pour REST, certaines informations HTTP sont conservées via des parties spécifiques. Certains headers sont ajoutés ou supprimés par X-Road.

**À retenir :**

- **SS ↔ SS = Message Transport Protocol**
    
- **HTTPS + mTLS**
    
- **5500 = communication SS↔SS**
    
- **5577 = récupération OCSP**
    
- Certificat d'authentification = identité du SS
    
- OCSP = vérification de validité des certificats
    
- Signature = intégrité du message
    
- Format transport = **MIME multipart**
    
- Le SS vérifie le message **avant de le transmettre**