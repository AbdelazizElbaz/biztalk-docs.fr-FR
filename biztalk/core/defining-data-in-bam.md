---
title: "Définition des données de l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], dimensions
- monitoring business activities [BAM], BAM Activity Wizard
- monitoring business activities [BAM], time intervals
- aggregations [BAM], measurements
- monitoring business activities [BAM], views
- monitoring business activities [BAM], aggregations
- Excel add-in [BAM], collecting data
- aggregations [BAM], scheduling
- monitoring business activities [BAM], milestone groups
- aggregations [BAM], real-time data
ms.assetid: 501a1c08-3979-4a99-94d9-0d1b5ec4266b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6acbc0ea1d80ec129d691d6c54b6eefd626d0e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-data-in-bam"></a>Définition des données dans l'analyse BAM
Le complément Excel d'analyse BAM permet de définir les données à collecter par l'analyse BAM et la manière dont elles données seront partagées. Les activités BAM permettent de définir les données et via les vues BAM, il est possible de déterminer les données qui peuvent être visualisées par les autres utilisateurs.  
  
## <a name="activities"></a>Activités  
 Une activité BAM est créée pour définir les informations relatives à un processus d'entreprise à analyser via l'analyse BAM. Une activité BAM représente un processus d'entreprise spécifique, tel que la gestion des bons de commande ou l'expédition d'un produit. Un processus d'entreprise comporte un ensemble défini d'étapes majeures et de données de l'entreprise. Par exemple, un processus de bon de commande peut inclure des étapes majeures telles que Approuvé, Refusé et Envoyé, ainsi que des données d'entreprise telles que Nom du produit et Produit.  
  
 La fonction d'une activité BAM est de présenter aux travailleurs de l'information l'historique (les étapes majeures) et les données relatives à un processus. Les activités BAM sont des abstractions de haut niveau indépendantes de l'implémentation réelle de BizTalk Server. Pour obtenir une présentation conceptuelle de l'analyse, consultez la rubrique « Analyse de l'activité d'entreprise (BAM) » de l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 L'Assistant Activité BAM permet de définir des activités BAM contenant au moins un élément d'activité. Les éléments d'activité associés sont regroupés dans une activité. Ils permettent de décrire le type de données que vous souhaitez rendre disponible à partir d'un processus d'entreprise.  
  
 Le tableau suivant décrit les types d'éléments d'activité fournis par l'analyse BAM.  
  
|Type d’élément| Description|  
|---------------|-----------------|  
|Étape majeure commerciale|Valeur de date et heure. Par exemple, la date d'approbation d'un bon de commande.|  
|Données de l'entreprise - Texte|Chaîne de caractères alphanumériques. Par exemple, destinataire : code ville, Département/Province et Code Postal.|  
|Données de l'entreprise - Entier|Valeur de nombre entier. Par exemple, le nombre total d'achats.|  
|Données d’entreprise - flottant|Valeur décimale. Par exemple, le montant total en euros du bon de commande.|  
  
 Par exemple, dans une activité de bon de commande, vous pouvez créer les éléments d'activité dans le tableau suivant :  
  
|Élément d'activité|Type d’élément|  
|-------------------|---------------|  
|Product|Données d’entreprise-texte|  
|Ville|Données d’entreprise-texte|  
|État|Données d’entreprise-texte|  
|Montant|Données de l'entreprise - Flottant|  
|Quantité|Données d’entreprise-entier|  
|Approved|Étape majeure commerciale|  
|Remis|Étape majeure commerciale|  
|Refusées|Étape majeure commerciale|  
|Received|Étape majeure commerciale|  
  
 Notez que la valeur Montant est une valeur à virgule flottante, car il peut s'agir d'une valeur décimale. Quantité est un entier car, dans cet exemple, il s'agit toujours d'un nombre entier. Approuvé, Envoyé, Refusé et Reçu sont des étapes majeures du processus du bon de commande.  
  
## <a name="views"></a>Vues  
 Créer des vues permet de présenter des données d'une activité à des utilisateurs. Lorsque vous créez une vue basée sur l'activité de bon de commande, vous définissez les données sous-jacentes des éléments d'activité. Les données de vue dans l'analyse BAM sont définies en tant que dimensions, mesures, durées, groupes d'étapes majeures et dimensions de la progression.  
  
 Une vue contient un ou plusieurs éléments. Vous pouvez créer les types d'éléments de vue suivants :  
  
-   Durées  
  
-   Groupes d'étapes majeures  
  
-   Aggregations  
  
### <a name="durations"></a>Durées  
 Les durées sont des intervalles de temps, elles sont décrites en termes d'étapes majeures qui définissent le début et la fin des intervalles de temps. Le tableau suivant illustre les durées que vous pouvez définir à partir des étapes majeures répertoriées dans le tableau précédent.  
  
|Duration|Étape majeure de début|Étape majeure de fin|  
|--------------|---------------------|-------------------|  
|1|Received|Approved|  
|2|Received|Remis|  
|3|Received|Refusées|  
|4|Approved|Remis|  
  
 Dans ce tableau, vous pouvez constater que la première durée (Durée 1) est l'intervalle de temps qui commence lorsqu'un bon de commande est reçu par BizTalk Server et qui se termine lorsque le bon de commande est approuvé.  
  
### <a name="milestone-groups"></a>Groupes d'étapes majeures  
 Des groupes d'étapes majeures sont créés pour traiter un ensemble d'étapes majeures en tant qu'entité unique, par exemple, les étapes majeures de début et de fin d'un processus, qui permettent la création d'une étape majeure unique représentant l'intégralité du processus.  
  
### <a name="aggregations"></a>Aggregations  
 Les agrégations permettent d'améliorer le délai de réponse relatif à l'actualisation des données à partir de la base de données. Dans Excel, les agrégations sont des résumés précalculés de données qui améliorent le temps de réponse de requête, les réponses étant prêtes avant que les questions ne soient posées. Par exemple, lorsqu'une table de faits d'un entrepôt de données contient des centaines de milliers de lignes, la réponse à une requête demandant les calendriers d'expédition de deux produits particuliers peut s'avérer être longue si le calcul de la réponse nécessite l'analyse de la table de faits. En revanche, la réponse peut être presque immédiate si les données récapitulatives fournies en réponse à cette requête ont été précalculées.  
  
 L'illustration suivante montre un exemple de données d'agrégation précalculées.  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
  
 Elle récapitule les quantités de chaque produit expédiées sur des lieux spécifiques sur une période de deux mois. Excel définit généralement ces données comme une mesure. Les données utilisées pour le filtrage et la catégorisation sont définies dans Excel comme une dimension.  
  
 Vous pouvez définir deux types d'agrégations dans le classeur BAM :  
  
-   les agrégations RTA ;  
  
-   Agrégations planifiées  
  
### <a name="real-time-aggregations"></a>les agrégations RTA ;  
 Les agrégations RTA permettent de visualiser l'état actuel du processus d'entreprise et d'identifier facilement les éventuels goulots d'étranglement dans le processus.  
  
 Les données BAM sont affichées dans un tableau croisé dynamique. Vous pouvez définir un tableau croisé dynamique BAM en tant qu'agrégation RTA ou planifiée. Une valeur RTA vous donne un aperçu à la minute près de vos données, par exemple, lorsqu'un bon de commande particulier se trouve au sein du processus d'expédition. Vous pouvez actualiser votre écran pour mettre à jour l'affichage des données tout au long de la journée.  
  
 Dans certains cas, des tranches spécifiques d'agrégations multidimensionnelles varient tellement rapidement dans le temps qu'elles doivent être disponibles en temps réel. Supposons que votre entreprise vende des denrées périssables et que vous souhaitiez que l'agrégation des quantités de produits aux différentes étapes de la livraison soit disponible en temps réel. D'autre part, vous voulez disposer d'autres agrégations, comme celle de l'âge du consommateur moyen, mais uniquement à la fin du mois en vue d'une analyse Business Intelligence.  
  
> [!IMPORTANT]
>  Ne définissez pas plusieurs RTA utilisant une même activité BAM. Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.  
  
 Pour plus d’informations sur l’exploration de données multidimensionnelles, consultez la rubrique de tableau croisé dynamique dans l’aide d’Excel.  
  
### <a name="scheduled-aggregations"></a>Agrégations planifiées  
 Par défaut, toutes les agrégations BAM sont des agrégations planifiées. Une agrégation planifiée représente un instantané de l'activité à un moment donné, par exemple, un résumé des expéditions du matin. Demandez à votre administrateur de la base de données à quel moment vos agrégations sont traitées. Vous pouvez ensuite consulter les données historiques.  
  
### <a name="dimensions-and-measures"></a>Dimensions et mesures  
 Les dimensions et les mesures permettent de créer des agrégations de données :  
  
-   Les dimensions décrivent un fait.  
  
-   Les mesures sont des valeurs de fait.  
  
 Par exemple, dans l'inventaire, un fait peut être « 3 automobiles rouges ». La description du produit : « car » et « rouge » sont des dimensions. La valeur du fait, « 3 », est une mesure. Si le prix de chaque automobile est inclus dans le fait, le prix des automobiles est une dimension, mais le prix moyen des automobiles dans l'inventaire est une mesure. Dans la documentation en ligne de Microsoft SQL Server, une mesure est décrite comme correspondant aux « valeurs centrales agrégées et analysées. » En d'autres termes, si des valeurs peuvent être dénombrées, faire l'objet d'une moyenne ou si elles peuvent être obtenues via des fonctions mathématiques, il s'agit d'une mesure.  
  
 Vous pouvez créer les types de dimensions suivants :  
  
-   Dimension de progression  
  
-   Dimension de données  
  
-   Dimension de temps  
  
-   Dimension de plage numérique  
  
## <a name="progress-dimensions"></a>Dimensions de progression  
 BAM introduit un nouveau type de dimension : la dimension de progression. Vous pouvez créer des dimensions de progression pour créer des agrégations concernant la progression des activités en cours de traitement.  
  
 Par exemple, considérons un processus d'entreprise de type achat dans le cadre duquel 1 000 bons de commande sont reçus. Vous pouvez utiliser la dimension de la progression sur les lignes pour créer le tableau suivant.  
  
|OrderProgress_Level1|Compter|  
|---------------------------|-----------|  
|Received|1000|  
  
 Vous pouvez alors ouvrir le processus Reçu pour afficher des informations supplémentaires sur la progression des activités telles que :  
  
|||Compter|  
|------|------|-----------|  
|Received|Évaluation|300|  
||Approved|500|  
||Refusées|200|  
  
 Ceci signifie que sur 1 000 bons de commande reçus, 500 ont été approuvés, 200 ont été refusés et 300 sont en cours d'évaluation.  
  
 Reçu, Approuvé et Refusé représentent des étapes majeures. Les chiffres correspondants dans la colonne Nombre indiquent le nombre de bons de commande étant passés par ces étapes majeures. Le niveau Évaluation est une étape intermédiaire par laquelle passent les commandes entre les étapes majeures Reçu et Approuvé ou Refusé.  
  
 Les dimensions de la progression peuvent être combinées à d'autres dimensions. Par exemple, si vous utilisez la dimension de progression Progression de la commande sur les lignes et la dimension de données Produit sur les colonnes, le résultat est le suivant :  
  
|||Raquettes de tennis|Ballons de football|  
|------|------|---------------------|------------------|  
|Received|Évaluation|250|50|  
||Approved|200|300|  
||Refusées|150|50|  
  
 Les dimensions de la progression fournissent des informations particulièrement utiles pour les graphiques basés sur les agrégations RTA. Les RTA permettent de visualiser l'état actuel du processus d'entreprise et d'identifier facilement les éventuels goulots d'étranglement du processus.  
  
 Les étapes majeures dans un bon de commande dimension de progression peut être séquentielle : la première étape est terminée avant le démarrage de l’étape suivante. Les étapes majeures peuvent également être effectuées conjointement. Les étapes séquentielles sont des étapes enfants, les étapes couplées sont des étapes sœurs. Dans le processus de bon de commande, la vérification commence dès la réception du bon de commande. Il s'agit d'une étape transitoire qui est effectuée en même temps que l'étape majeure Reçu et constitue, par conséquent, une étape sœur de l'étape majeure Reçu. Un bon de commande est approuvé uniquement une fois qu'il a été reçu (l'étape majeure Approuvé est une étape enfant de l'étape majeure Reçu).  
  
## <a name="data-dimension"></a>Dimension de données  
 Une dimension de données est définie pour utiliser la valeur de certains éléments de texte dans l'activité BAM sur les lignes ou les colonnes. Par exemple, une dimension de données nommée produit peut être utilisée pour créer le tableau suivant :  
  
|Product|Compter|  
|-------------|-----------|  
|Raquettes de tennis|100|  
|Ballons de football|200|  
  
 En outre, vous pouvez définir plusieurs dimensions de données dans l’Assistant Vue BAM. Par exemple, la définition d'une dimension de données nommée Lieu avec les niveaux Département et Ville peut être utilisée pour créer le tableau suivant :  
  
|Product|Los Angeles|San Francisco|Seattle|  
|-------------|-----------------|-------------------|-------------|  
|Raquettes de tennis|50|20|30|  
|Ballons de football|130|50|20|  
  
 Dans ce tableau, la dimension Produit a été utilisée sur les lignes et la dimension Lieu sur les colonnes.  
  
## <a name="time-dimension"></a>Dimension de temps  
 Une dimension de temps permet de créer des agrégations temporelles. Par exemple, une dimension de temps peut être utilisée pour créer le tableau suivant :  
  
|Année|Mois|Compter|  
|----------|-----------|-----------|  
|2003|Janvier|120|  
||February|230|  
||Mars|350|  
||avril|280|  
  
 Vous pouvez combiner la dimension de temps avec n'importe quelle autre dimension. Par exemple, vous pouvez utiliser la dimension de temps sur les lignes et la dimension de données sur les colonnes pour créer le tableau suivant :  
  
|Mois|Raquettes de tennis|Ballons de football|  
|-----------|---------------------|------------------|  
|Janvier|50|70|  
|February|120|110|  
|Mars|300|50|  
|avril|220|60|  
  
## <a name="numeric-range-dimension"></a>Dimension de plage numérique  
 Les dimensions de plage numérique permettent de créer des agrégations qui catégorisent des plages numériques via des noms conviviaux. Par exemple, un analyste d'entreprise peut définir une dimension de plage numérique intitulée Montant du bon de commande par les plages suivantes :  
  
 Faible, pour les bons de commande d'une valeur comprise entre 0 et 100 euros ;  
  
 Moyen, pour les bons de commande d'une valeur comprise entre 100 et 1 000 euros ;  
  
 Élevé, pour les bons de commande d'une valeur supérieure à 1 000 euros.  
  
> [!NOTE]
>  Si le montant d'un bon de commande n'est pas compris dans les plages définies, par exemple, s'il est inférieur à 0, une ligne « hors limites » est automatiquement créée par BAM afin que ces données puissent y être placées.  
  
|Montant du bon de commande|Compter|  
|-------------|-----------|  
|Petit|500|  
|Moyenne|350|  
|Élevé|225|  
  
> [!NOTE]
>  Vous ne pouvez pas créer deux dimensions de plage numérique faisant référence au même alias de données.