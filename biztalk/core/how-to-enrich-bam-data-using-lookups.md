---
title: "Enrichissement des données BAM à l’aide de recherches | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: BAM, data lookups
ms.assetid: 8d10659e-97d6-4cd1-9b4d-307afd43c763
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43b42b42158bc3b3c179d624340a97a890072a17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enrich-bam-data-using-lookups"></a>Enrichissement des données BAM à l'aide de recherches
Il pourra arriver que les données disponibles durant le fonctionnement ne contiennent pas tout ce dont vous avez besoin pour générer des rapports. Par exemple, il se peut que vous disposiez d'un ProductID mais pas d'un ProductName lors de l'exécution. L'Activité BAM représentant une abstraction indépendante de la manière dont les données sont véritablement collectées, elle doit contenir un élément dont le nom soit celui des données finales que vous souhaitez voir apparaître dans le rapport « ProductName ». Comme tout autre élément, vous pouvez utiliser cet élément dans des constructions d'interprétation telles que des groupes, des durées, des dimensions et des mesures d'étape majeure. Le ProductName n'étant pas disponible au moment de l'exécution, vous devez vous procurer d'autres données suffisant pour effectuer une recherche, le ProductID par exemple.  
  
 Il est préférable que vous collectiez les données dans une même colonne, à la place des données dont vous avez besoin pour les rapports. Par exemple, il vous faudra collecter le ProductID à la place de ProductName lors de l'exécution. Si davantage de colonnes sont nécessaires, vous êtes autorisé à créer d'autres éléments dans l'activité mais pas à les utiliser dans les vues.  
  
### <a name="to-enrich-bam-data-via-lookups"></a>Pour enrichir des données BAM à l'aide de recherches  
  
1.  Déployez votre définition BAM.  
  
2.  Dans SQL Server Management Studio, ajoutez le serveur qui contient les données d'intérêt en tant que serveur distant.  
  
3.  Recherchez le package d'analyse de données appelé BAM_AN_`<View Name>`. Par exemple, si la vue est SalesMgr, il s'appellera BAM_AN_SalesMgr.  
  
4.  Réglez le zoom de façon à agrandir l'affichage du package (par exemple à 100 %).  
  
5.  Ajoutez une connexion SQL que vous utiliserez dans les recherches.  
  
6.  Localisez la tâche de transformation des données après l'étape « Nettoyage du test ». C'est là où vous déplacez les données de la base de données d'importation principale dans la base de données de schémas en étoile. Il y a deux instances de cette tâche : l'une pour les activités terminées, l'autre pour celle en cours. Appliquez la suite des étapes aux deux tâches.  
  
7.  Cliquez sur la transformation.  
  
8.  Sélectionnez Recherche, puis ajoutez votre recherche « LookupProductByID » à l'aide de la connexion de recherche (voir la documentation en ligne de SQL à propos des recherches). Si la recherche est par exemple un simple tableau « LookupProduct » doté des colonnes ProductID et ProductName, le texte de la recherche sera le suivant :  
  
    ```  
    SELECT ProductName  
    FROM   LookupProduct  
    WHERE ProductID=?  
    ```  
  
9. Cliquez sur l'onglet Transformations. Effacez la transformation de données par défaut « Transformer » et créez une transformation ActiveX à la place. Cliquez sur Colonnes source et ajoutez toutes les colonnes. Cliquez sur Colonnes de destination et ajoutez toutes les colonnes.  
  
10. Cliquez sur l’onglet Général, puis sur Propriétés. Cela entraîne la génération automatique d'un script qui exécute la transformation de copie triviale comme illustré :  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("ProductName") = DTSSource("ProductName")  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
11. Modifiez la valeur en utilisant la recherche comme illustré :  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("Product")= _  
                      DTSLookups( "LookupProductByID" ).Execute(  _                                  DTSSource("Product"))  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
12. Enregistrez puis exécutez le package.  
  
13. Assurez-vous que les données qui arrivent dans le cube OLAP sont les bonnes. Il est conseillé que vous enregistriez le package en tant que VBScript ou en tant que fichier de stockage structuré car il contient votre code personnalisé et non pas uniquement des étapes auto-générées à partir de l'analyse BAM.  
  
> [!NOTE]
>  La recherche ne fonctionne qu'avec les rapports planifiés que vous exécutez avec DTS et OLAP. Si vous avez besoin d'autres données que celles collectées dans l'agrégation RTA, vous devez les extraire avant d'appeler l'API BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Business Activity Monitoring](../core/using-business-activity-monitoring.md)   
 [Déploiement des fichiers XML d’analyse BAM localisés](../core/deploying-localized-bam-xml-files.md)