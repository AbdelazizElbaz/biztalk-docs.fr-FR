---
title: "Comment créer des Ports d’envoi pour TIBCO Enterprise Message Service | Documents Microsoft"
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
ms.assetid: 6e569244-494e-4db4-8030-eda3b390d073
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfadeb3306687bfcbea27c0df41973b12b003563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-tibco-enterprise-message-service"></a>Création de ports d'envoi pour TIBCO Enterprise Message Service
Les étapes suivantes permettent de créer un port d'envoi.  
  
## <a name="creating-a-send-port"></a>Création d'un port d'envoi  
  
#### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Cliquez sur **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport TIBCO EMS** boîte de dialogue zone, procédez comme suit :  
  
    1.  Entrez **la gestion des messages**, **définition de la connexion serveur**, **prise en charge des transactions**, **nom d’utilisateur**et le  **mot de passe**.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application associée que vous avez créée pour représenter le système TIBCO EMS.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Cliquez sur **OK**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des propriétés du Transport TIBCO Enterprise Message Service pour le Port d’envoi](../core/setting-tibco-enterprise-message-service-transport-properties-for-the-send-port.md)   
 [Création de gestionnaires d’envoi TIBCO Enterprise Message Service](../core/creating-tibco-enterprise-message-service-send-handlers.md)