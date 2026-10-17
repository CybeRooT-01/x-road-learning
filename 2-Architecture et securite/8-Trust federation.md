La **fédération** permet à deux instances X-Road d’échanger des services entre leurs Members.

Pour établir la confiance :

1. Chaque Central Server reçoit le **Configuration Anchor** de l’autre instance.

2. Il est ajouté comme **Trusted Anchor**.

3. Les Trusted Anchors sont distribués aux Security Servers via la **configuration interne**.

4. Les Security Servers utilisent ces anchors pour télécharger la **configuration externe** du partenaire.

5. Les informations récupérées permettent aux Security Servers des deux instances de communiquer.

Pour **arrêter la fédération**, il suffit de supprimer le Trusted Anchor du partenaire du Central Server.

`Central A ↔ Central B`  
`Trusted Anchor → configuration externe → SS ↔ SS`

**À retenir :** le **Trusted Anchor** permet à une instance de faire confiance à la configuration d’une autre instance.