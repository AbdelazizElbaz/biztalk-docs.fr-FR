---
title: "Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05e4d20-4cf2-402f-aaea-66987cb6515a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0c8c8721d9f7de7b1cd1e57537aa02d2ed8fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-add-a-file-send-port-to-capture-the-swhandleresponse-message-for-the-interact-real-time-scenario"></a>Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour l’interaction du scénario en temps réel
Complète [étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) avant de commencer cette étape.
  
## <a name="add-a-file-send-port-to-capture-swhandleresponse-message"></a>Ajouter un fichier de port d’envoi pour capturer les messages Sw:HandleResponse  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendResponseToSender**.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **Transporttype** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** , tapez **C:\SWIFTAdapterTutorial\Interact\Response**, puis cliquez sur **OK**.  
  
7.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |Tout d’abord la ligne : **propriété**|Dans la liste déroulante, sélectionnez **BTS. SPName**.|  
    |Tout d’abord la ligne : **(opérateur)**|Dans la liste déroulante, sélectionnez  **==** .|  
    |Tout d’abord la ligne : **valeur**|Type **Tutorial_IA_HandleRequest_RealTime**.|  
    |Tout d’abord la ligne : **regrouper par**|Dans la liste déroulante, sélectionnez **ou**.|  
    |Deuxième ligne : **propriété**|Dans la liste déroulante, sélectionnez **BTS. MessageType**.|  
    |Deuxième ligne : **(opérateur)**|Dans la liste déroulante, sélectionnez  **==** .|  
    |Deuxième ligne : **valeur**|Type **SwInt-ExchangeResponse**.|  
    |Deuxième ligne : **regrouper par**|Laissez la valeur par défaut.|  
  
9. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)