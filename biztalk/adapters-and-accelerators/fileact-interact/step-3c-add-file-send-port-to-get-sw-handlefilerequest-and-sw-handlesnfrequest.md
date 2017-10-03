---
title: "Étape 3c : ajouter un Port d’envoi FILE pour capturer les Messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc41e352-acc5-47eb-bb87-38990f0e76a7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6858164ee82f935c607246e7e93ffd86908f93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-a-file-send-port-to-capture-the-swhandlefilerequest-and-swhandlesnfrequest-messages-for-the-fileact-store-and-forward-scenario"></a>Étape 3c : ajouter un Port d’envoi FILE pour capturer les Messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour et le scénario de transfert de FileAct
Avant de commencer cette étape, vous devez effectuer [étape 3 b : ajouter un emplacement de réception FILEACT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md).  
  
### <a name="to-add-a-file-send-port-to-capture-swresponseserver-message"></a>Pour ajouter un fichier de port d’envoi pour capturer les messages Sw:ResponseServer  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_FA_SendResponseToReceiver.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Fileact\ResponseServer, puis cliquez sur **OK**.  
  
7.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Tout d’abord de ligne : propriété**|Dans la liste déroulante, sélectionnez **BTS. MessageType**.|  
    |**Tout d’abord de ligne : (opérateur)**|Dans la liste déroulante, sélectionnez  **==** .|  
    |**Tout d’abord de ligne : valeur**|Type **Sw-HandleFileRequest**.|  
    |**Tout d’abord de ligne : regrouper par**|Dans la liste déroulante, sélectionnez **ou**.|  
    |**Deuxième ligne : propriété**|Dans la liste déroulante, sélectionnez **BTS. MessageType**.|  
    |**Deuxième ligne : (opérateur)**|Dans la liste déroulante, sélectionnez  **==** .|  
    |**Deuxième ligne : valeur**|Type **Sw-HandleSnFRequest**.|  
    |**Deuxième ligne : regrouper par**|Laissez la valeur par défaut.|  
  
9. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md)   
 [Étape 3 b : ajouter un FILEACT emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md)   
 [Étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)