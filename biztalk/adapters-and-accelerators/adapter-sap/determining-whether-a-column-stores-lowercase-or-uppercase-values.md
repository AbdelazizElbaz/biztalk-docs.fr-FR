---
title: "Déterminer si une colonne stocke des valeurs en minuscules ou majuscules | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1edc8332-d8c7-4040-895b-f121fb03df44
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b54c00b43192462fb095dbfbfda4cbf0b248a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="determining-whether-a-column-stores-lowercase-or-uppercase-values"></a>Déterminer si une colonne stocke les valeurs en minuscules ou majuscules
Cette section répertorie les tâches principales à effectuer sur le système SAP pour déterminer si une colonne dans une table SAP stocke des caractères en minuscules ou majuscules. Pour obtenir des instructions détaillées sur la façon d’effectuer cette tâche, vous devez contacter votre administrateur SAP ou consultez la documentation de SAP.  
  
### <a name="to-determine-the-case-of-values-stored-in-a-column"></a>Pour déterminer le cas des valeurs stockées dans une colonne  
  
1.  Démarrez l’interface utilisateur graphique SAP.  
  
2.  Transaction SE37 et exécutez DDIF_TABL_GET.  
  
3.  Pour le paramètre NAME, spécifiez le nom de la table contenant la colonne pour laquelle vous souhaitez déterminer les informations de cas de caractères. Par exemple, KNA1.  
  
4.  Le premier paramètre de la table est DD03P_TAB. Cliquez sur le paramètre pour voir les lignes de la table. Chaque ligne de cette table correspond à une colonne dans la table (par exemple, KNA1) que vous avez spécifié à l’étape 3.  
  
5.  Dans DD03P_TAB, recherchez la valeur de la colonne en minuscules pour chaque ligne. Si la valeur de la colonne en minuscules est « X », la colonne correspondante dans la table (par exemple, KNA1), peut stocker des caractères minuscules et majuscules. Si la valeur de la colonne en minuscules est vide, la colonne correspondante ne peut stocker que les caractères majuscules.  
  
     Par exemple, pour la ligne de nom les minuscules colonne est X. Par conséquent, la colonne NAME dans KNA1 peut stocker des caractères majuscules et minuscules. Toutefois, pour la ligne LAND1 les minuscules colonne est vide. Par conséquent, la colonne LAND1 KNA1 table ne peut stocker que les caractères majuscules.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de tâches à l’aide de l’interface utilisateur graphique SAP pour les scénarios de l’adaptateur SAP spécifique](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)