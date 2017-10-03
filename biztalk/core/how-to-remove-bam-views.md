---
title: Comment supprimer des vues BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, views
- managing [BAM definitions], deleting views
- Remove-View command [BAM]
ms.assetid: 1a43ec81-20b1-41f7-941f-753132ac9ed2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04d8930fb4e3f2014945b743b15da4dbdfff3451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-views"></a>Suppression des vues BAM
Les administrateurs utilisent la **remove-view** commande pour supprimer une vue à partir de la base de données d’importation principale BAM.  
  
> [!NOTE]
>  La suppression d'une vue entraîne automatiquement la suppression des alertes ayant été définies pour cette vue.  
  
### <a name="to-remove-bam-views"></a>Pour supprimer des vues BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant **C:\Program Files\Microsoft BizTalk Server 2009\Tracking** à l’invite de commandes. Appuyez sur **Entrée**.  
  
3.  Type **bm remove-view-nom :\<nom de la vue >**.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Comment supprimer des alertes BAM](../core/how-to-remove-bam-alerts.md)