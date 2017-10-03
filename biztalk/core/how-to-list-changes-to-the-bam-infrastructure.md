---
title: "Comment répertorier les modifications apportées à l’Infrastructure BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], listing infrastructure changes
- managing [BAM definitions], listing infrastructure changes
- Get-Changes command [BAM]
- infrastructure, listing changes [BAM]
ms.assetid: 3feacd7d-6f42-4626-835b-0dc3befc9fd6
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d0ed240f156d853c18f28a52022eea585af513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-changes-to-the-bam-infrastructure"></a>Affichage des modifications apportées à l'infrastructure BAM
Les administrateurs utilisent la **get-changes** commande de l’utilitaire de gestion BAM pour afficher des informations en cours sur une définition BAM déployée. Cette commande vous permet également de répertorier les artefacts de déploiement en cours d'utilisation dans la base de données d'importation principale BAM.  
  
 Les informations répertoriées indiquent la réussite des déploiements et des annulations de déploiement, le nom du fichier de la définition BAM, celui du fichier de configuration du composant BAM, les noms des activités et des vues associées au fichier de définition ainsi que le compte de l'utilisateur ayant appliqué ces modifications. La liste générée par la commande get-changes affiche les déploiements et les suppressions de définition accompagnés de leur numéro d'identification.  
  
### <a name="to-list-changes-to-the-bam-definition"></a>Répertorier les modifications à la définition BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type **bm get-changes.**  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)