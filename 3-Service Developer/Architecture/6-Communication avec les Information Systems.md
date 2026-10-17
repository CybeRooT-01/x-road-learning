

### Service Consumer — `IS → SS`

Le Security Server peut communiquer avec l’IS client en **HTTP, HTTPS ou HTTPS NOAUTH**.

**HTTPS est recommandé et utilisé par défaut.**

- **HTTP** → uniquement sur un réseau privé isolé et sécurisé.
    
- **HTTPS** → chiffre la communication + vérifie le certificat TLS de l’IS.
    
- **HTTPS NOAUTH** → HTTPS mais sans vérifier le certificat TLS de l’IS.
    

Pour HTTPS, il faut créer et installer un **certificat TLS interne** pour l’IS.

**Important :** en environnement multi-Members, garder **HTTPS** pour tous les clients afin d’éviter les accès non autorisés.

### Service Provider — `SS → IS`

Le protocole dépend de l’URL du service :

- `http://...` → **HTTP**
    
- `https://...` + _Verify TLS certificate_ activé → **HTTPS**
    
- `https://...` + _Verify TLS certificate_ désactivé → **HTTPS NO AUTH**
    

En HTTPS, le Security Server peut donc **vérifier ou non** le certificat TLS de l’IS.

Cette vérification concerne :

- `SS ↔ service endpoint`
    
- `SS ↔ URL de description du service` (WSDL/OpenAPI).
    

### À retenir

`HTTPS → recommandé`

`HTTP → réseau privé isolé`

`HTTPS NOAUTH → HTTPS sans vérification du certificat IS`

`Verify TLS certificate → contrôle du certificat de l’IS`