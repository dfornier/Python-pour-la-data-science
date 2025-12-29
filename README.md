# Etude de l'offre médicale et de le présence de *désert médicaux* en France

*Ce projet est réalisé dans le cadre du cours de Python pour la Data Science donné par Lino Galiana à l'ENSAE Paris en 2025.* 

### Introduction 

Un récent rapport du Sénat [1](#1) (29 mars 2022) met en évidence une dégradation très alarmante de l’accès aux soins en France. Chaque année, près de 1,6 million de Français renoncent à des soins médicaux, tandis qu’environ un tiers de la population vivrait dans un « désert médical ».
Si le terme de *désert médical* est aujourd’hui omniprésent dans le débat public, il ne repose pourtant pas sur une définition précise. Il suggère ainsi une vision trop simplifiée de l’accès aux soins en France, opposant des territoires supposés totalement dépourvus d’offre médicale à d’autres beaucoup mieux lotis. Une telle approche masque la complexité des situations locales et soulève un enjeu méthodologique majeur : sur quelle réalité statistique et démographique fonder la notion de désert médical ? Celle d’un seuil ? Concerne-t-elle uniquement les médecins généralistes, ou faut-il également intégrer les médecins spécialistes, les autres professionnels de santé, l’offre hospitalière, l’accès aux urgences ou encore aux pharmacies ?
Si les déserts médicaux n’existent pas à proprement parler d’un point de vue administratif, ils n’en constituent pas moins une réalité du terrain. En effet, toujours selon ce même rapport du Sénat, plus d’un Français sur dix n’a pas de médecin traitant, alors même que le nombre de médecins est en constante augmentation.


### Objectif et méthodologie

Notre approche se scinde en trois phases
  1) Récupération des données
  2) Statistique et étude descriptive
  3) Modélisation


## 1) Récupération des données


Pour mener cette étude, nous avons eu recours à différentes bases de données, présentées ici par ordre d'importance :
    1) *La démographie des professionnels de santé depuis 2012*[2](#2), publiée par la DREES, construite à partir d'une extraction du RPPS (Répertoire Partagé des Professionnels de Santé). En effet, la profession de médecin est une profession réglementée, ce qui signifie que tous les praticiens exerçant en France doivent être enregistrés auprès du conseil de l’Ordre. Elle présente des données de 2012 à 2025.
    2)*Statistiques locales*[3](#3), publiée par l'Insee. Cette carte interactive met à disposition de nombreux indicateurs à l’échelle régionale et infra-communale pour l’année 2025, tels que le nombre de médecins par commune ou la densité des foyers familiaux. Les fichiers *Indicateur_Departementale.xlsx* et *Indicateurs_communale.csv* correspondent à des extractions de cette carte interactive.
    3)*L'accessibilité potentielle localisée (APL)*[4](#4), publiée par la DREES. L’APL est un indicateur local, disponible au niveau de chaque commune, qui tient compte de l’offre et de la demande issues des communes environnantes. On le définira plus en détail ultérieurement
    4)*Professionnels de santé libéraux : patientèle par territoire (département, région)*[5](#5), publiée par la caisse nationale d'assurance maladie. Elle apporte le nombre moyen de patient annuel par médecin, en fonction du département d'exercice, entre 2012 et 2024



## 2) Première étude descriptive



## 3) Modélisation


## Conclusion


<a id="1"></a>
[1] [Sénat, *Rapport sur l’accès aux soins*, 29 mars 2022.](https://www.senat.fr/rap/r21-589/r21-589.html)
<a id="2"></a>
[2] [DREES, *La démographie des professionnels de santé depuis 2012*, 28 juillet 2025.](https://data.drees.solidarites-sante.gouv.fr/explore/dataset/la-demographie-des-professionnels-de-sante-depuis-2012/information/)
<a id="3"></a>
[3] [INSEE, *Statistiques locales*](https://statistiques-locales.insee.fr/#c=indicator)
<a id="4"></a>
[4] [DREES, **L'accessibilité potentielle localisée (APL)*](https://data.drees.solidarites-sante.gouv.fr/explore/dataset/530_l-accessibilite-potentielle-localisee-apl/information/)
<a id="5"></a>
[5] [Caisse nationale de l'Assurance Maladie (Cnam), *Rapport sur l’accès aux soins*, 15 Décembre 2025.](https://www.data.gouv.fr/datasets/professionnels-de-sante-liberaux-patientele-par-territoire-departement-region)