X-Road n'impose aucune limite technique à la taille de son écosystème ni à celle des organisations membres.

Il peut être utilisé à différentes échelles :
- Nationale : connecter les systèmes de plusieurs administrations.
- Privée : connecter uniquement les entreprises clientes d'un service.
- Restreinte : réserver l'accès aux organisations répondant à certains critères.
Grâce à son architecture évolutive, X-Road s'adapte aussi bien aux petits écosystèmes qu'aux déploiements nationaux.

À retenir : X-Road n'est pas réservé aux gouvernements. Il peut aussi servir à créer des réseaux privés d'échange de données.

## 1-echange de donnée a l'echelle nationale

X-Road permet aux administrations et entreprises d’un pays d’échanger des données de manière sécurisée.

- Fédération : connecte les X-Road de plusieurs pays.
- Opérateur : généralement l’État. Gère les règles, les membres et les composants centraux. Peut sous-traiter la technique.

Exemples : Estonie, Finlande, Islande.

## 2-echange de donnée a l'echelle regionale

X-Road peut être déployé à l’échelle d’une région pour connecter ses administrations et entreprises.

- Opérateur : autorité régionale, qui peut sous-traiter la technique.
- Fédération : permet de communiquer avec d’autres régions ou l’État.

À retenir : un seul X-Road national est généralement préférable à plusieurs X-Road régionaux, car il nécessite moins de gestion.
## 3-Data Exchange par secteur

X-Road peut connecter des organisations d’un même secteur (santé, énergie, etc.), même dans plusieurs pays.
- Opérateur : définit les règles que tous les membres acceptent.
- Fédération : connecte différents secteurs ou écosystèmes nationaux et régionaux.
- Exemples : santé en Allemagne, énergie en Estonie.

À retenir : X-Road n’a pas de frontières géographiques. Les membres doivent simplement respecter les règles communes.

## 4-Échange de données dans une organisation

X-Road peut aussi connecter les systèmes d’une **même organisation** : filiales, départements, pays différents, etc.
- **Opérateur** : un département de l’organisation.
- **Membres** : autres départements/filiales.
- Fonctionne sur **Internet** ou un réseau privé.
- Garantit **confidentialité, intégrité et interopérabilité**.

**Attention :** X-Road ≠ **Service Mesh** comme Istio.
`X-Road → systèmes / organisations`
`Service Mesh → microservices`