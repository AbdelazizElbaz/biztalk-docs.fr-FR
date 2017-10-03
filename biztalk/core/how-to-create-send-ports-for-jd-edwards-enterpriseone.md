---
title: "Comment créer des Ports d’envoi pour JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, send ports
- send ports, creating [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], send ports
- send ports, JD Edwards EnterpriseOne adapters
- creating, send ports [JD Edwards EnterpriseOne adapters]
ms.assetid: 687f9207-ad3e-41ea-8640-5b9b6efbc14e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36a3e8d2d3e8e1db230a03d9c4a0351d3a0f8394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-enterpriseone"></a>Création de ports d'envoi pour JD Edwards EnterpriseOne
À l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un port d'envoi.  
  
### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi** et cliquez sur **nouveau**, puis cliquez sur **Port statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    -   Dans le **nom** , tapez le nom du port d’envoi (par exemple, `SendToJDE`).  
  
    -   À partir de la **Type** la liste déroulante, sélectionnez **JDEdwards**.  
  
    -   À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’adresse du Gestionnaire d’envoi.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi de EnterpriseOne JD Edwards](../core/creating-jd-edwards-enterpriseone-send-handlers.md)