
Le **TSA (Time-Stamping Authority)** fournit une preuve qu’un message existait à un moment précis. On avais un peu effleure sa ici [[1-Introduction/3-Architecture]]

- Les messages et leurs signatures sont enregistrés par les Security Servers.

- Les logs sont périodiquement **horodatés** pour conserver une preuve à long terme.

- X-Road utilise par défaut le **batch time-stamping** → plusieurs messages horodatés ensemble.

- Cela réduit la charge du TSA : la charge dépend surtout du **nombre de Security Servers**, pas du nombre de messages.

- L’horodatage peut aussi être fait **pour chaque message**, de manière synchrone, si la politique de sécurité l’exige.


`TSA → prouve quand le message existait`

## Updatability

X-Road permet d’installer des mises à jour, notamment de sécurité, de manière fiable.

Les packages X-Road sont **signés**, ce qui permet de vérifier leur origine.

`Package signé → origine vérifiable → mise à jour fiable`