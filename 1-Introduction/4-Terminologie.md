## 1- X-Road Instance

- **Local instance** : Members gérés dans notre instance
- **External instance** : autre instance fédérée avec la nôtre
- **Federated X-Road** : plusieurs instances fédérées pour échanger des données
- **X-Road instance** : environnement technique, légal et organisationnel géré par une autorité
**Exemple :**  
`Instance A ↔ Instance B`  
A = local | B = external

## 2-Participants X-Road 

- **Approved trust service provider** : fournisseur de confiance approuvé par l’autorité X-Road
- **End user of dataservice** : système ou personne qui utilise un service de données
- **Local member** : Member géré par l’autorité de l’instance locale
- **Federated member** : Member d’une instance externe, autorisé à échanger sur le X-Road fédéré
- **X-Road Center** : participant qui administre les composants centraux X-Road
- **X-Road governing authority** : autorité qui définit les règles et gère les participants
- **X-Road member** : organisation autorisée à échanger des données via X-Road

**À retenir :**  
`Governing authority = règles`  
`X-Road Center = composants centraux`  
`Member = échange de données`  
`Trust provider = confiance`
## 3-Certificats & confiance
- **Approved CA provider** : fournisseur approuvé qui délivre les certificats Security Server + Member et fournit OCSP
- **Approved TSA provider** : fournisseur approuvé qui délivre les timestamps
- **CA** : autorité qui délivre les certificats numériques
- **Certification service CA** : CA de confiance utilisée comme référence dans X-Road
- **Authentication certificate** : certificat du Security Server pour s’authentifier auprès d’un autre Security Server
- **Signature certificate** : certificat du Member pour signer les messages
- **CSR** : demande générée par le Security Server pour obtenir un certificat auprès d’une CA
- **Internal TLS certificate** : sécurise la connexion Security Server ↔ Information System
- **TLS certificate** : authentifie l’Information System lors d’une connexion HTTPS
- **TSA** : autorité qui fournit les timestamps
- **Timestamp** : preuve qu’une donnée existait à un moment donné
- **OCSP** : service qui vérifie si un certificat est toujours valide
### À retenir
`CA → certificats`
`TSA → timestamps`
`OCSP → validité des certificats`
`Authentication cert → Security Server`
`Signature cert → Member`
`TLS cert → Security Server ↔ Information System`

## 4-Rôles
### Dataservice
- **Dataservice client** : envoie la requête pour utiliser un service
- **Dataservice provider** : fournit le service et renvoie la réponse
- **Dataservice host** : permet à des non-Members d’utiliser un service X-Road

`Client → requête → Provider → réponse → Client`

### Security Server

- **Security Server client** : Member autorisé à utiliser un Security Server
- **Security Server host** : Member qui héberge un Security Server pour d’autres
- **Security Server owner** : responsable du Security Server et du canal sécurisé

**À retenir :**  
`Client = utilise`  
`Provider = fournit`  
`Host = héberge`
##  5-X-Road interfacing

- **Affiliation of membership** : processus pour devenir Member et être enregistré dans le Central Server
- **Registration of Security Server** : associer un Security Server à un Member pour permettre les échanges sécurisés
- **Registration of subsystem** : enregistrer un subsystem comme client d’un Security Server
- **Dataservice interfacing** : préparer un service pour le fournir ou l’utiliser : développement, configuration, contrats, droits d’accès
- **Interaction** : échange réel entre client et provider

`Membership → Security Server → Subsystem → Dataservice → Interaction`

## 6-Services & messages

- **Dataservice** : service REST/SOAP permettant d’accéder aux données d’un Member
- **Central service** : service avec un nom de provider défini par l’autorité
- **Management service** : gestion des Security Servers et de leurs clients
- **Metadata service** : permet de découvrir les services, Members et droits disponibles
- **X-Road service** : API REST ou SOAP accessible via X-Road
- **Message** : données échangées → **request** ou **response**

### Monitoring
- **Environmental** : état technique du Security Server (CPU, RAM, disque...)
- **Operational** : activité des services (appels, fréquence, temps de réponse...)
- **Monitoring daemon** : collecte les données et calcule l’état du Security Server

### Service client
Entité autorisée à utiliser un service : Member, subsystem ou groupe de droits.

## 7-Subsystems & droits

- **Access right** : droit d’un subsystem à utiliser un service
- **Access right group** : groupe de subsystems partageant les mêmes droits
- **Global group** : géré dans le Central Server → toute la fédération
- **Local group** : géré dans un Security Server → uniquement local

**À retenir :**
`Dataservice = données`
`Metadata = découvrir`
`Management = gérer`
`Monitoring = surveiller`
`Access right = autoriser`
# 8-X-Road Protocols

- **Federation Protocol** : échange de configuration entre instances fédérées
- **Message Protocol** : Information System ↔ Security Server
- **Message Transport Protocol** : Security Server ↔ Security Server
- **Configuration Protocol** : Central Server → Security Servers
- **Service Metadata Protocol** : découverte des services + récupération de leurs descriptions
### À retenir
`Config ↔ instances → Federation`
`Config → Security Server → Configuration`
`IS ↔ SS → Message`
`SS ↔ SS → Transport`
`Découvrir services → Metadata`

# 9-Logging & Security
- **Audit log** : actions des utilisateurs + changements de configuration, succès ou échec
- **Batch signature** : signature unique pour un ensemble de documents
- **Message log** : messages X-Road échangés + signatures + timestamps, pour prouver un échange
- **System service log** : logs des services internes du Security Server
### À retenir
`Audit → actions`
`Message → échanges`
`System → fonctionnement`
`Batch signature → signature d’un ensemble genre une pierre plusieurs coups`
# 10-Identifiers & codes

- **Central service identifier** : identifie un service central → `Instance + Service code`
- **Global access group identifier** : identifie un groupe global → `Instance + Group code`
- **Local access group identifier** : identifie un groupe local → `Group ID`
- **Member class** : catégorie de Members ayant les mêmes caractéristiques
- **Member code** : identifie un Member dans sa classe
- **Member identifier** : identifie un Member → `Instance + Class + Code`
### À retenir
`Member identifier = Instance + Member class + Member code`
`Member class = catégorie`
`Member code = identifiant du Member`


## 11-Termes techniques

### Confiance et sécurité

- **ACME** — Automatic Certificate Management Environment : gestion automatique des certificats.
- **CA** — Certification Authority : autorité qui délivre les certificats.
- **HSM** — Hardware Security Module : matériel sécurisé pour protéger les clés cryptographiques.
- **OCSP** — Online Certificate Status Protocol : vérifie si un certificat est encore valide.
- **SSH** — Secure Shell : connexion sécurisée à une machine distante.
- **TLS** — Transport Layer Security : sécurise les communications réseau.
- **TSA** — Timestamping Authority : autorité qui fournit des horodatages.
- **TSP** — Time Stamp Provider : fournisseur de services d’horodatage.
### Logiciel / développement

- **API** — Application Programming Interface : permet à des applications de communiquer.
- **CI** — Continuous Integration : intégration et tests automatiques du code
- **DSL** — Domain Specific Language : langage conçu pour un domaine précis.
- **HTTP** — Hypertext Transfer Protocol : protocole de communication du Web.
- **HTTPS** — HTTP Secure : HTTP sécurisé avec TLS.
- **JMX** — Java Management Extensions : gestion et supervision d’applications Java.
- **JMXMP** — Java Management Extensions Messaging Protocol : protocole de communication pour JMX.
- **JSON** — JavaScript Object Notation : format léger pour échanger des données.
- **MBean** — Java Managed Bean : objet Java gérable via JMX.
- **MIME** — Multipurpose Internet Mail Extensions : indique le type d’un contenu (`application/json`, `text/html`, etc.).
- **RPC** — Remote Procedure Call : permet d’appeler une fonction sur une autre machine.
- **REST** — Representational State Transfer : architecture utilisée pour créer des API Web.
- **SDK** — Software Development Kit : outils permettant de développer pour une plateforme.
- **SOAP** — Simple Object Access Protocol : protocole d’échange de messages, souvent basé sur XML.
