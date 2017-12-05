---
title: "Comment désactiver les alertes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, disabling
- managing [BAM definitions], disabling alerts
- Disable-Alerts command [BAM]
ms.assetid: c5938bc2-1043-4633-8cad-02caf442f2e8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4279030b9c3bcc7913bf64cc870b0d82d618dff8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-alerts"></a>Désactivation des alertes
Les administrateurs utilisent la **disable-alerts** commande pour désactiver toutes les alertes dans la vue spécifiée.  
  
### <a name="to-disable-an-alert"></a>Pour désactiver une alerte  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité. Appuyez sur **Entrée**.  
  
3.  Type **bm disable-alerts-View :\<nom de la vue\>**.  
  
    > [!NOTE]
    >  Si vous avez exporté une configuration BAM en tant que fichier XML, ne modifiez pas le fichier XML liés aux alertes. Si vous modifiez le fichier XML liés aux alertes et déployez les modifications, bm.exe détectera les modifications et activera les alertes BAM.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Comment activer les alertes](../core/how-to-enable-alerts.md)