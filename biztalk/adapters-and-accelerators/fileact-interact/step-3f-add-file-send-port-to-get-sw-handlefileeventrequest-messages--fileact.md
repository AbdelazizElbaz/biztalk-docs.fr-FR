---
title: "Étape 3 : ajouter un Port d’envoi de fichier pour le scénario en temps réel FileAct capturer les Messages Sw-HandleFileEventRequest | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b7594b0-0443-41b7-ae04-55b2cc8bf90e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1d70c338696f1c4455161a88c8d2988e0ea0ccb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3f-add-a-file-send-port-for-the-fileact-real-time-scenario-to-capture-sw-handlefileeventrequest-messages"></a>Étape 3 : ajouter un Port d’envoi de fichier pour le scénario en temps réel FileAct capturer les Messages Sw-HandleFileEventRequest
Avant de commencer cette étape, vous devez effectuer [étape 3E : ajouter un Port d’envoi FILE à capturer le Message Sw:ExchangeFileResponse pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)  
  
### <a name="to-add-a-file-send-port-to-capture-status-events"></a>Pour ajouter un port d’envoi FILE pour capturer les événements d’état :  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_ GetStatusReports.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, puis cliquez sur **OK**.  
  
7.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Propriété**|Sélectionnez BTS. MessageType|  
    |**Opérateur**|Sélectionnez ==|  
    |**Valeur**|Type Sw-HandleFileEventRequest|  
    |**Grouper**|Ou|  
    |**Propriété**|Sélectionnez BTS. MessageType|  
    |**Opérateur**|Sélectionnez ==|  
    |**Valeur**|Type Sw-ExchangeSnFResponse|