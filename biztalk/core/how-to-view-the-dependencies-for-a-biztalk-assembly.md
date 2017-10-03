---
title: "Comment afficher les dépendances d’un Assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing, dependencies
- assemblies, dependencies
- managing [assemblies], dependencies
- assemblies, viewing
- viewing, assemblies
- managing [assemblies], viewing
ms.assetid: 872abc99-8248-4397-9fcb-24a0ba6f4757
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99fbc09a5adb59691a4914a8ddc341c8034c8bb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-the-dependencies-for-a-biztalk-assembly"></a>Affichage des dépendances d'un assembly BizTalk
Cette rubrique explique comment afficher la liste des artefacts dépendants d'un assembly BizTalk à l'aide de la console Administration de BizTalk Server. Pour plus d’informations générales sur les dépendances et comment ils affectent le déploiement d’application, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk ou du groupe d'administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-view-the-dependencies-of-a-biztalk-assembly"></a>Pour afficher les dépendances d'un assembly BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant l'assembly BizTalk dont vous souhaitez afficher les dépendances, puis l'application le contenant.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur l’assembly BizTalk, puis cliquez sur **modifier**.  
  
4.  Cliquez sur le **dépendances** onglet.  
  
     Le nom et l'état des artefacts dépendants de cet assembly BizTalk s'affichent dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys BizTalk](../core/managing-biztalk-assemblies.md)