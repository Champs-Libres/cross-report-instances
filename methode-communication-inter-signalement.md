**Avertissement** Ce document se veut être une base à une discussion future. Les propositions de ce document présentent l'état actuel de notre réflexion dans le but de le partager, d'en discuter et surtout de l'améliorer.

# Pourquoi une méthode de communication entre systèmes de signalement ?

Nous assistons depuis quelques années à une multiplication des systèmes de signalement.

La mise en place de tels systèmes s'explique par une demande de transparence de la population. Pour les pouvoirs publics, c'est également l'occasion de renouveler le lien avec les citoyens : ces derniers échangent de l'information avec leurs admnistrations. Ils sont, de plus en plus, considérés comme partenaires : ils fournissent de l'information sur l'objet du travail de l'administration (les routes, la propreté publique, etc.) et, en échange, l'administration les tient au courant de son propre travail.

La multiplication des outils par chaque acteur s'explique par :
- le fait que certains acteurs veulent conserver une gestion des données reçues ;
- le fait que la gestion des signalements dépend de l'organisation du service qui traitera la demande,
- ...

Il nous semble donc peu probable d'arriver à un outil unique à court et moyen terme.

Pourtant, cette multiplicité est un réel problème : les systèmes de signalement fonctionnent seulement si des citoyens y participent ; demander aux citoyens de savoir quel site utiliser selon le type de signalement nous semble utopique (le risque de décourager le citoyen est possible).

Nous pensons qu'il existe des moyens informatiques pour résoudre cette difficulté: faire en sorte que les différentes instances de systèmes de signalement communiquent entre elles et gèrent, par elles-mêmes, l'orientation des signalements vers les bonnes instances.

# Les fonctionnalités couvertes par le système

Voici les fonctionnalités que ce système doit proposer.

## Les instances doivent pouvoir s'identifier les unes aux autres

L'identification des instances de systèmes de signalement doit être sécurisée afin d'avoir la certitude que chaque instance est bien celle qu'elle prétend être.

## Les instances devraient gérer leur découverte

Politiquement, il apparaît nécessaire de moduler la capacité des instances :

- recevoir des signalements de la part de l'une ou l'autre instance (soit l'instance accepte de n'importe quelle instance, soit uniquement parmi une liste d'instances 'connues', ...
- transférer des signalements à d'autres instances

En parrallèlle, il pourrait être intéressant d'ajouter la capacité à auto-découvrir d'autres instances (à chaque fois qu'une instance découvre une nouvelle, cette dernière lui transfère les autres instances de sa connaissance, ce qui lui permet d'élargir son "réseau" d'instances).

## Renvoi des signalements à d'autres instances

Si une instance reçoit un signalement pour lequel elle n'est pas compétente, elle le transfèrerait à une autre instance. Cette dernière pourrait répondre si elle est capable de prendre en charge, ou pas, le signalement et si, éventuellement, elle peut le transférer.

## Suivi des signalements sur d'autres instances

Une instance peut demander à une autre d'être informée des modifications d'un signalement géré par cette dernière.

## Méthodes pour informer que 2 signalements sont identiques

Un instance doit pouvoir indiquer que 2 signalement sont identiques.

# Points techniques du système

Voici les points techniques qu'il nous semble important d'investiguer :

## Identification unique

Il serait nécessaire de permettre l'identification unique d'un signalement à travers tous les systèmes.

Une idée est que cette identification soit définie par deux données :
- une identification de l'instance qui a reçu en premier le signalement
- un identifiant interne à cette instance

## Identification des instances par lesquel le signalement est passé

Pour chaque signalement, il faut indiquer la liste des instances par lesquels le signalement est passé. Cette donnée est utile pour un instance qui veut rediriger un signalement pour lequel elle n'est pas comptétente: il serait judicieux qu'elle ne tente pas à nouveau de le transférer à une instance qui l'a refusé.

## Méthodes de passation du signalement

Lorsqu'une instance envoie un signalement à une autre instance, que va-t'il se passer si cette instance est incompétente pour gérer le signalement ?

Il nous semble que le système émetteur doit informer le sytème receveur de :
- soit s'occuper d'envoyer le signalement à un autre système si le receveur n'est pas compétent (en utilisant la liste des systèmes contactés)
- soit de lui renvoyer le signalement si le receveur n'est pas compétent
