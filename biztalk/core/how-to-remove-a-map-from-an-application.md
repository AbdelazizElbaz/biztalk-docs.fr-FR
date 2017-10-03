---
title: "Comment supprimer un mappage à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, maps
- deleting, maps
- managing [maps], deleting
- managing [maps], applications
ms.assetid: 27d9bb08-36f0-46ff-ae9a-2247be6e3f96
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8b264809306e2cda40cc44be1287b6c2426fb43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-map-from-an-application"></a>Suppression d'un mappage d'une application
Cette rubrique décrit comment supprimer un mappage d'une application BizTalk à l'aide de la console Administration de BizTalk Server. Il peut être utile de supprimer un mappage après avoir déployé une nouvelle version du mappage. Pour plus d’informations et des considérations importantes pour la mise à jour des artefacts de l’application, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).  
  
 Lorsque vous supprimez un mappage, voici ce qui se produit :  
  
-   le mappage est supprimé de la base de données de gestion BizTalk ;  
  
-   l'assembly BizTalk qui contient le mappage est supprimé de la base de données de gestion BizTalk, mais pas du système de fichiers local ou du Global Assembly Cache (GAC), s'il existe dans ces emplacements ;  
  
-   par conséquent, tous les artefacts contenus dans l'assembly sont également supprimés de la base de données de gestion BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-remove-a-map"></a>Pour supprimer un mappage  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le mappage à supprimer, puis développez l’application contenant le mappage.  
  
3.  Cliquez sur le **cartes** dossier, avec le bouton droit de la carte, puis cliquez sur **supprimer**.  
  
> [!NOTE]
>  Pour supprimer plusieurs mappages, maintenez la touche MAJ enfoncée, cliquez sur chaque carte à supprimer, cliquez sur un des mappages, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des mappages](../core/managing-maps.md)   
 [Comment supprimer un Assembly BizTalk à partir d’une Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)   
 [Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md)