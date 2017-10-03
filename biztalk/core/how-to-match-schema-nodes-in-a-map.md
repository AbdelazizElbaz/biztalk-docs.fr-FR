---
title: "Mise en correspondance des nœuds de schéma dans un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 584f85d2-6198-4ef3-90d9-a322f1457d9a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e2ce880489ca49b0b55d2e6f45b9e887d719a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-match-schema-nodes-in-a-map"></a>Mise en correspondance des nœuds de schémas à un mappage
Il peut être difficile de mapper des éléments lorsque les schémas source et de destination sont complexes. Le Mappeur BizTalk introduit le **de correspondance indicatives :** fonctionnalité, qui vous permet de mapper des éléments de schéma complexes en suggérant les meilleures correspondances possibles. Cette rubrique fournit les informations vous permettant d'effectuer cette opération.  
  
> [!NOTE]
>  Le Mappeur BizTalk suggère les correspondances possibles pour un nœud de schéma. Actuellement, cette fonctionnalité prend uniquement en charge les noms anglais.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent l'exécution du Mappeur BizTalk.  
  
### <a name="to-match-relevant-schema-nodes"></a>Pour mettre en correspondance des nœuds de schéma  
  
1.  Sélectionnez et cliquez sur l’élément de schéma pour lequel vous avez besoin connaître les meilleures correspondances, puis cliquez sur **indiquer les correspondances**. Le Mappeur BizTalk indique les meilleures correspondances (limitées à sept) en sélectionnant la correspondance optimale.  
  
     Vous pouvez également sélectionner **indiquer les correspondances** à partir du menu BizTalk, ou appuyez sur MAJ + touches de l’espace.  
  
     La figure suivante illustre les correspondances suggérées pour le nœud sélectionné dans le schéma de destination.  
  
     ![Mappage suggéré](../core/media/suggestive-mapping.gif "Suggestive_Mapping")  
  
    > [!NOTE]
    >  Maintenez appuyée la touche MAJ pour parcourir la liste des correspondances suggérées.  
  
2.  Vous pouvez maintenant effectuer les tâches suivantes :  
  
    -   appuyer sur ENTRÉE pour valider la (meilleure) correspondance en surbrillance ;  
  
    -   utiliser les flèches HAUT et BAS pour parcourir les correspondances en surbrillance dans l'ordre de préférence.  
  
        > [!NOTE]
        >  Appuyez sur la flèche BAS pour accéder à la meilleure correspondance suivante et sur la touche HAUT pour mettre en surbrillance la meilleure correspondance précédente.  
  
    -   Appuyez sur la touche DÉBUT pour retourner à la première correspondance.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)