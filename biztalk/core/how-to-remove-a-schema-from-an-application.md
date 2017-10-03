---
title: "Comment supprimer un schéma à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, schemas
- applications, schemas
- schemas, deleting
- managing [schemas], deleting
- managing [schemas], applications
- schemas, applications
ms.assetid: 17dd5869-b56c-4166-9f02-03e04e691eda
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6535764af00156325c006388a88803207329e5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-schema-from-an-application"></a>Suppression d'un schéma d'une application
Cette rubrique décrit comment supprimer un schéma dans une application à l'aide de la console Administration de BizTalk Server. Cette procédure supprime également le schéma de la base de données de gestion BizTalk du groupe. Il peut être utile de supprimer un schéma après avoir déployé une nouvelle version du schéma. Pour plus d’informations et des considérations importantes pour la mise à jour des artefacts de l’application, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).  
  
 Lorsque vous supprimez un schéma et une version précédente du schéma ayant le même espace de noms racine dans l'application, la version précédente devient active.  
  
 Lorsque vous supprimez un schéma, voici ce qui se produit :  
  
-   Le schéma est supprimé de la base de données de gestion BizTalk.  
  
-   L'assembly BizTalk qui contient le schéma est supprimé de la base de données de gestion BizTalk, mais pas du système de fichiers local ou du Global Assembly Cache (GAC), s'il existe dans ces emplacements.  
  
-   par conséquent, tous les artefacts contenus dans l'assembly sont également supprimés de la base de données de gestion BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-remove-a-schema"></a>Pour supprimer un schéma  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le schéma à supprimer, puis l’application contenant le schéma.  
  
3.  Cliquez sur **schémas**, cliquez sur le schéma, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas](../core/managing-schemas.md)