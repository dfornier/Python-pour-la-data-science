# *Désert médicaux* en France : Répartition & Déterminants

*Ce projet est réalisé dans le cadre du cours de Python pour la Data Science donné par Lino Galiana à l'ENSAE Paris en 2025.* 

### Introduction 

Un récent rapport du Sénat [1](#1) (29 mars 2022) met en évidence une dégradation très alarmante de l’accès aux soins en France. Chaque année, près de 1,6 million de Français renoncent à des soins médicaux, tandis qu’environ un tiers de la population vivrait dans un « désert médical ».

Si le terme de *désert médical* est aujourd’hui omniprésent dans le débat public, il ne repose pourtant pas sur une définition précise. Il suggère ainsi une vision trop simplifiée de l’accès aux soins en France, opposant des territoires supposés totalement dépourvus d’offre médicale à d’autres beaucoup mieux lotis. Une telle approche masque la complexité des situations locales et soulève un enjeu méthodologique majeur : sur quelle réalité statistique et démographique fonder la notion de désert médical ? Celle d’un seuil ? Concerne-t-il uniquement les médecins généralistes, ou faut-il également intégrer les médecins spécialistes, les autres professionnels de santé, l’offre hospitalière, l’accès aux urgences ou encore aux pharmacies ?

Si les déserts médicaux n’existent pas à proprement parler d’un point de vue administratif, ils n’en constituent pas moins une réalité du terrain. En effet, toujours selon ce même rapport du Sénat, plus d’un Français sur dix n’a pas de médecin traitant, alors même que le nombre de médecins est en constante augmentation.

Face à ces constats, il apparaît nécessaire de dépasser le simple diagnostic des inégalités d’accès aux soins pour s’intéresser aux facteurs territoriaux sous-jacents. En particulier, comprendre les déterminants de l’implantation des médecins permet d’éclairer les mécanismes à l’origine des situations de faible accessibilité observées dans certaines communes.

#### Problématique

Comment les caractéristiques des territoires déterminent-elles le choix d’implantation des médecins, et dans quelle mesure participent-elles aux situations de faible accessibilité aux soins dans certaines communes ?

### Objectif et méthodologie

Notre objectif est de mettre en évidence l'existence de ces *déserts médicaux*, d'analyser les déterminants de l'installation des médecins et de comprendre les raisons de ces situations de faible accessibilité aux soins.

Notre approche se scinde en trois phases
  1) Récupération des données
  2) Statistique et étude descriptive, pour la mise en évidence des déserts
  3) Modélisation, pour l'interprétation des causes de l'apparition des déserts

## Base de données

Pour mener cette étude, nous avons eu recours à différentes bases de données, présentées ici par ordre d'importance :

1) *La démographie des professionnels de santé depuis 2012* [2](#2), publiée par la DREES, construite à partir d'une extraction du RPPS (Répertoire Partagé des Professionnels de Santé). En effet, la profession de médecin est une profession réglementée, ce qui signifie que tous les praticiens exerçant en France doivent être enregistrés auprès du conseil de l’Ordre. Elle présente des données de 2012 à 2025.  

2) *Statistiques locales* [3](#3), publiée par l'Insee. Cette carte interactive met à disposition de nombreux indicateurs à l’échelle régionale et infra-communale pour l’année 2025, tels que le nombre de médecins par commune ou la densité des foyers familiaux. Les fichiers *Indicateur_Departementale.xlsx* et *Indicateurs_communale.csv* correspondent à des extractions de cette carte interactive.  

3) *L'accessibilité potentielle localisée (APL)* [4](#4), publiée par la DREES. L’APL est un indicateur local, disponible au niveau de chaque commune, qui tient compte de l’offre et de la demande issues des communes environnantes. On le définira plus en détail ultérieurement. La base que nous avons sélectionnées traite de l'APL des médecins généralistes libéraux.

4) *Professionnels de santé libéraux : patientèle par territoire (département, région)* [5](#5), publiée par la caisse nationale d'assurance maladie. Elle apporte le nombre moyen de patient annuel par médecin, en fonction du département d'exercice, entre 2012 et 2024.

### Sur l'accessibilité potentielle localisée ou APL :

*L’indicateur d’accessibilité potentielle localisée (APL)*, développé par la DREES et l’Irdes, permet de mesurer l’accès aux soins de premier recours à échelle locale. Il a été conçu pour mesurer davantage la complexité de l'accès aux soins en France que les indicateurs classiques, comme la distance du médecin le plus proche ou la densité médicale à l’échelle d’un département.

L’APL utilise des données de l’Assurance maladie et de l’Insee. Calculé au niveau de chaque commune, il prend en compte à la fois les médecins disponibles localement et ceux des communes voisines, incluant une pondération par la population concernée.

#### Processus de calcul (selon Irdes, [5](#5)):

Pour chaque commune $j$ disposant de médecins, on définit un ratio :

$$
R_j = \frac{m_j}{\sum_{i \mid d_{ij} \le d_0} p_i}
$$

où :
- $m_j$ est l’offre de médecins dans la commune $j$ (en ETP),
- $p_i$ est la population de la commune $i$, pondérée par l’âge,
- $d_{ij}$ est la distance entre les communes $i$ et $j$,
- $d_0$ est le seuil de distance.

Pour chaque commune $i$, l’accessibilité potentielle localisée est donnée par :

$$
APL_i = \sum_{j \mid d_{ij} \le d_0} w(d_{ij}) \cdot R_j
$$

où $w(d_{ij})$ est une pondération liée à la distance.

Cet indicateur met ainsi en évidence des différences d’accès aux soins qui ne sont pas visibles avec des indicateurs calculés à grandes échelles. Il tient aussi compte de l’activité des médecins et de la densité de population.


## Conclusion

Ce projet a permis de mettre en évidence les inégalités territoriales d’accès aux soins à partir d’analyses statistiques descriptives et de modèles de régression. L’utilisation de la régression linéaire et du Lasso a permis d’identifier et de hiérarchiser les principaux facteurs associés aux situations de déserts médicaux, offrant ainsi une base quantitative pour l’analyse de ces déséquilibres territoriaux.

Bien que nous soyons tous deux fiers du travail réalisé, ce projet demeure perfectible. De nettes améliorations peuvent être apportées par l’accès à certaines données, en particulier les données communales détaillées et les données de remboursement de l’Assurance maladie, qu’elles concernent les médecins ou les patients. Ainsi, le projet est, en l'état, davantage un constat de l'état de l'art du système de soins en France, qu'une analyse déterministe de la répartition et des déterminants des déserts médicaux en France (ce qui pour un projet étudiant nous satisfait tout à fait). Par ailleurs, nous ne sommes pas parvenus à dépasser nos limites dans le calcul de certains indicateurs, comme l’accessibilité potentielle localisée (APL).

#### Références

<a id="1"></a>
[1] [Sénat, *Rapport sur l’accès aux soins*, 29 mars 2022.](https://www.senat.fr/rap/r21-589/r21-589.html)  
<a id="2"></a>
[2] [DREES, *La démographie des professionnels de santé depuis 2012*, 28 juillet 2025.](https://data.drees.solidarites-sante.gouv.fr/explore/dataset/la-demographie-des-professionnels-de-sante-depuis-2012/information/)  
<a id="3"></a>
[3] [INSEE, *Statistiques locales*](https://statistiques-locales.insee.fr/#c=indicator)  
<a id="4"></a>
[4] [DREES, *L'accessibilité potentielle localisée (APL)*](https://data.drees.solidarites-sante.gouv.fr/explore/dataset/530_l-accessibilite-potentielle-localisee-apl/information/)  
<a id="5"></a>
[5] [Caisse nationale de l'Assurance Maladie (Cnam), *Rapport sur l’accès aux soins*, 15 Décembre 2025.](https://www.data.gouv.fr/datasets/professionnels-de-sante-liberaux-patientele-par-territoire-departement-region)  
<a id="6"></a>
[6] [IRDES, *L ’Accessibilité potentielle localisée (APL) : une nouvelle mesure de l’accessibilité aux médecins généralistes libéraux*, Mars 2012.](https://www.irdes.fr/Publications/2012/Qes174.pdf)
