---
title: Comment activer les alertes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Enable-Alerts command [BAM]
- managing [BAM definitions], enabling alerts
- alerts, enabling
ms.assetid: 18f494b7-54fb-4aaf-89d1-7e3fe91f35c6
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22bb3610d489f02aa535b562057b4bb09e208983
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-alerts"></a>Activation des alertes
Les administrateurs utilisent la **enable-alerts** commande pour activer toutes les alertes dans la vue spécifiée.  
  
### <a name="to-enable-an-alert"></a>Pour activer une alerte  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité. Appuyez sur **Entrée**.  
  
3.  Type **bm enable-alerts-View :\<nom de la vue >**.  
  
    > [!NOTE]
    >  Si vous avez exporté une configuration BAM en tant que fichier XML, ne modifiez pas le fichier XML liés aux alertes. Si vous modifiez le fichier XML liés aux alertes et déployez les modifications, bm.exe détectera les modifications et activera les alertes BAM.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [entrer la description de l’image ici](../core/how-to-disable-alerts.md)