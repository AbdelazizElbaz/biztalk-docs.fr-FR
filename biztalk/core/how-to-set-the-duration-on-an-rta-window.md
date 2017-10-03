---
title: "Comment définir la durée dans une fenêtre RTA | Documents Microsoft"
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
- Set-RTAWindow command [BAM]
- managing [BAM], time intervals
ms.assetid: 3042c3f5-be0f-48fb-9831-daa4868b90fe
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09a1b9e0514a2c83d927a956bb890c1a89864a07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-duration-on-an-rta-window"></a>Définition de la durée dans une fenêtre RTA
Les administrateurs utilisent la **set-rtawindow** commande pour définir la durée de l’agrégation en temps réel (RTA) spécifiée.  
  
### <a name="to-set-the-duration-on-an-aggregation"></a>Pour définir la durée dans une agrégation  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité. Appuyez sur **Entrée**.  
  
3.  Type **bm set-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité >-nom :\<nom RTA > - TimeLength :\<nombre entier > - TimeUnit : jour &#124; Heure &#124; Minute**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Comment obtenir la durée d’une fenêtre RTA](../core/how-to-get-the-duration-on-an-rta-window.md)