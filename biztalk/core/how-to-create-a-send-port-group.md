---
title: "Comment créer un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send port groups
- send port groups, creating
- managing [send port groups], creating
ms.assetid: de3e72aa-83f4-4760-9f39-a488f904f1d3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f308c950d56569c06403df1394580302089a453e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-send-port-group"></a>Création d'un groupe de ports d'envoi
Cette rubrique explique comment utiliser la console Administration de BizTalk Server pour créer un groupe de ports d'envoi dans une application BizTalk et pour ajouter des ports d'envoi à cette application. Vous ne pouvez ajouter que des ports d'envoi statiques unidirectionnels à un groupe de ports d'envoi. Un groupe de ports d'envoi doit contenir au moins un port d'envoi permettant d'acheminer les messages.  
  
 Vous pouvez ajouter un port d'envoi existant dans une application différente. Dans ce cas, vous devez ajouter une référence de l'application contenant le groupe de ports d'envoi dans l'application contenant le port d'envoi. Pour obtenir des instructions, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-create-a-send-port-group"></a>Pour créer un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dans laquelle créer un groupe de ports d'envoi.  
  
3.  Avec le bouton droit **groupes de ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **groupe de ports d’envoi**.  
  
4.  Dans le **nom** , tapez un nom pour le groupe de ports d’envoi.  
  
5.  Dans **ports d’envoi**, cliquez sur la liste déroulante sous **nom**, puis cliquez sur le port d’envoi à ajouter au groupe de ports d’envoi. Répétez cette opération pour chaque port d'envoi que vous souhaitez ajouter au groupe. Pour créer un port d’envoi et l’ajouter, cliquez sur  **\<nouveau port d’envoi >** , puis suivez les instructions de [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
6.  Une fois terminé d’ajouter des ports d’envoi pour le groupe de ports d’envoi, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md)