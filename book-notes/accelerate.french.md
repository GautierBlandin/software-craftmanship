# Accelerate: notes

Accelerate est un livre basé sur 4 ans de recherches scientifiques qui identifie des facteurs clés pour mesurer la performance d'une équipe software.

## 4 facteurs clés mesurent la performance
- Deployment frequency / Fréquence de déploiement
- Lead time for Changes / Délai de MEP
- Mean time to recovery / Temps moyen de rétablissement
- Change failure rate / Taux d'échec des commits

Observation contre-intuitive :
Déployer plus souvent et plus rapidement est corrélé avec un taux d'échec plus bas.

Forte corrélation entre performance business (profitability, market share, productivity) et performance software (four metrics) (methologie: survey).

## Drivers des quatre facteurs

### Organisation générative (opposée à pathologique ou bureaucratique, ref Westrum)

Caractéristiques des organisations génératives :
- Failures are treated primarily as opportunities to improve the system
- New ideas are welcomed

### Pratiques techniques

#### Livraison continue (continuous delivery)

- Incorporer la qualité
- Travailler par petites itérations
- Automatisation d'un maximum de processus répétitifs
- Amélioration continue
- Responsabilité partagée
- Monitoring
- "Shift left" de la sécurité

Prérequis à la livraison continue:
- Versionnage de la configuration et du code
- Intégration continue
- Testing continu (et automatisé)

##### Comment mesurer la qualité ?

- Pourcentage de temps passé sur des rework ou des tâches non planifiées
- Pourcentage de temps passé sur des défaillances identifiées par les utilisateurs finaux

#### Caractéristiques de bons tests automatisés

- Fiabilité (Reliable) : Si les tests automatisés passent, le software est releasable (haute sensitivité)
- Précision : Si les tests automatisés ne passent pas, ils indiquent une vraie défaillance (haute spécificité)
- Rapide (Fast) : Les tests sont faciles et rapides à exécuter
- Compréhensible : Les tests sont faciles à comprendre et à maintenir
