---
title: Comment calculer la mise en attente | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f2d09c-60db-4daf-b850-23f2c8915502
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a327695099ec575f2a13ccb75b4152e4a7de1af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-calculate-dehydration"></a>Calcul de la mise en attente
Pour calculer la mise en attente, vous utilisez les propriétés configurées et des valeurs d'exécution spécifiques. L'exemple de code suivant montre comment calculer un scénario de mise en attente hypothétique.  
  
### <a name="to-calculate-dehydration"></a>Pour calculer la mise en attente  
  
1.  Laissez alpha représenter un facteur compris entre 0 et 1 mesurant la contrainte de mémoire.  En pratique, alpha possède un composant pour chacun des 3 critères de limitation basée sur la mémoire (propriétés de mise en attente) ; dans cet exemple, ils sont désignés par alpha(virtual), alpha(private) et alpha(physical). Définissez les éléments suivants :  
  
    ```  
    IF ActualPrivateBytes < OptimalUsage  
       alpha(private) = 1  
    ELSE IF ActualPrivateBytes > MaximalUsage  
       alpha(private) = 0  
    ELSE  
       alpha(private) = (MaximalUsage - ActualPrivateBytes) / (MaximalUsage - OptimalUsage)  
    ```  
  
    > [!NOTE]
    >  Les éléments OptimalUsage et MaximalUsage possèdent des valeurs par défaut pour chaque propriété de mise en attente. Ces valeurs peuvent être modifiées dans le fichier BTSNTSvc.exe.config. Pour plus d’informations, consultez [propriétés par défaut de mise en attente](../core/dehydration-default-properties.md).  
  
2.  Définissez les autres composants alpha de la même façon. Définissez les éléments suivants :  
  
    ```  
    alpha = Minimum { alpha(virtual), alpha(private), alpha(physical) }  
    where alpha(…) = 1 whenever IsActive=false for that given memory unit  
    ```  
  
3.  Définissez ensuite l'élément TestThreshold (l'unité de TestThreshold, MinThreshold et MaxThreshold est la seconde) :  
  
    ```  
    TestThreshold = MinThreshold + (alpha * (MaxThreshold – MinThreshold))  
    ```  
  
    > [!NOTE]
    >  Valeur par défaut de MinThreshold = 1. Valeur par défaut de MaxThreshold = 1800. Ces valeurs peuvent être modifiées dans le fichier BTSNTSvc.exe.config. Pour plus d’informations, consultez [propriétés par défaut de mise en attente](../core/dehydration-default-properties.md).  
  
4.  Définissez ensuite les éléments TimeBlocked et EstimatedTime :  
  
    -   TimeBlocked = durée d'attente réelle pour que l'abonnement soit satisfait  
  
    -   EstimatedTime = durée d'inactivité estimée pour cette orchestration (par ex., le délai d'attente restant pour l'écoute)  
  
 La décision de mise en attente dépend du résultat de la condition booléenne suivante (true = mise en attente) :  
  
-   Mise en attente = (EstimatedTime > TestThreshold OU TimeBlocked > (2* TestThreshold))  
  
> [!NOTE]
>  La durée estimée correspond à la durée restante avant l'expiration du délai (si l'attente est de 5 minutes et si deux minutes se sont déjà écoulées, TimeBlocked=120 secondes, EstimatedTime=180 secondes).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés par défaut de mise en attente](../core/dehydration-default-properties.md)   
 [Fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md)