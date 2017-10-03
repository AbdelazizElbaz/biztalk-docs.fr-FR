---
title: "L’ajout d’un Port d’envoi à un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send port groups], adding send ports
- managing [send ports], adding to send port groups
- send port groups, send ports
- send ports, send port groups
- adding, send ports
ms.assetid: a61b3b32-c05e-40b9-abf1-09b7065fb6a2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61329a5489379f6b8840b15672e40195e3c58328
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-send-port-to-a-send-port-group"></a>Ajout d'un port d'envoi à un groupe de ports d'envoi
La présente rubrique explique comment ajouter un ou plusieurs ports d'envoi à un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server. Vous pouvez uniquement ajouter des ports d’envoi statiques unidirectionnels à un groupe de ports d’envoi.  
  
 Vous pouvez ajouter un port d'envoi existant dans une application différente. Dans ce cas, vous devez ajouter une référence de l'application contenant le groupe de ports d'envoi dans l'application contenant le port d'envoi. Pour obtenir des instructions, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-add-a-send-port-to-a-send-port-group"></a>Pour ajouter un port d'envoi à un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dans laquelle ajouter un port d'envoi à un groupe de ports d'envoi.  
  
3.  Cliquez sur **groupes de ports d’envoi**, cliquez sur le groupe de ports d’envoi, puis cliquez sur **propriétés**.  
  
4.  Dans **ports d’envoi**, cliquez sur la liste déroulante sous **nom**, puis cliquez sur le port d’envoi à ajouter au groupe de ports d’envoi. Répétez cette opération pour chaque port d'envoi que vous souhaitez ajouter au groupe. Pour créer un port d’envoi et l’ajouter, cliquez sur  **\<nouveau port d’envoi >** , puis suivez les instructions de [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
5.  Une fois terminé d’ajouter des ports d’envoi pour le groupe de ports d’envoi, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md)   
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)