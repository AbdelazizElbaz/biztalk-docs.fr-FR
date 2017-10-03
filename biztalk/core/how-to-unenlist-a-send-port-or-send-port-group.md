---
title: "Comment désinscrire un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unenlisting, send port groups
- send port groups, unenlisting
- managing [send ports], unenlisting
- managing [send port groups], unenlisting
- unenlisting, send ports
- send ports, unenlisting
ms.assetid: 3185adad-2efa-4abd-a532-77ae6c7b4c1d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac2599ae3d06a75506de244a4f996a9e77cef6ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-unenlist-a-send-port-or-send-port-group"></a>Désinscription d'un port d'envoi ou d'un groupe de ports d'envoi
La présente rubrique explique comment désinscrire un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server. Désinscrire un port d'envoi ou un groupe de ports d'envoi permet de supprimer tous les abonnements associés à ces éléments. Vous pouvez désinscrire les ports d'envoi ou les groupes de ports d'envoi en cours d'exécution ou arrêtés. La désinscription d'un port d'envoi ou d'un groupe de ports d'envoi arrête automatiquement ce dernier.  
  
 Vous pouvez par exemple vouloir désinscrire un port d'envoi ou un groupe de ports d'envoi pour modifier ses liaisons, ou encore pour les supprimer de l'environnement BizTalk Server.  
  
 Vous ne pouvez pas désinscrire le dernier port d'envoi inscrit d'un groupe de ports d'envoi inscrit ou en cours d'exécution. Le fait de désinscrire un groupe de ports d'envoi ne modifie pas l'état des ports d'envoi qu'il contient.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-unenlist-a-send-port-or-send-port-group"></a>Pour désinscrire un port d'envoi ou un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez Annuler l’inscription.  
  
3.  Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un groupe de ports d’envoi, puis cliquez sur **désinscrire**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md)