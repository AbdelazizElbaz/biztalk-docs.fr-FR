---
title: "Comment créer des Ports d’envoi pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- ports, send
- send ports, creating
ms.assetid: 0c8d9fdc-b273-4876-9f93-b5a85539a3c1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b6e7dbb1a3b32979c94ec1af9483bd9fcb7cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-tibco-rendezvous"></a>Création de ports d'envoi pour TIBCO Rendezvous
Les étapes suivantes permettent de créer un port d'envoi à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Cliquez sur **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport TIBCO Rendezvous** boîte de dialogue zone, procédez comme suit :  
  
    1.  Saisissez les propriétés.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application SSO associée que vous avez créée pour représenter le système TIBCO Rendezvous.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Cliquez sur **OK**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)