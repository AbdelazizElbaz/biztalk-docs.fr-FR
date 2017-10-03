---
title: "Comment obtenir la durée d’une fenêtre RTA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- aggregations [BAM], time intervals
- managing [BAM], time intervals
- Get-RTAWindow command [BAM]
ms.assetid: 4e7ad0fd-e7ed-47f7-9435-ef01bbe17afa
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb930c3e9d252a23653f0464e1adaa1e18b4f45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-get-the-duration-on-an-rta-window"></a>Obtention de la durée dans une fenêtre RTA
Les administrateurs utilisent la **get-rtawindow** commande pour obtenir la durée de l’agrégation en temps réel (RTA) spécifiée. Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.  
  
### <a name="to-get-the-duration-on-an-aggregation"></a>Pour obtenir la durée dans une agrégation  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type **bm get-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité > -Rta :\<nom RTA >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Comment définir la durée dans une fenêtre RTA](../core/how-to-set-the-duration-on-an-rta-window.md)