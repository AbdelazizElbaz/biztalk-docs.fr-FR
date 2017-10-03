---
title: "Étape 3E : ajouter un Port d’envoi de fichier pour l’et de transférer le scénario afin de capturer les messages Sw-ExchangeSnFResponse FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04bad2ab-1ea4-4602-9dee-5b9af9be3b93
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cf320f22f5acc2511d6327c36c54cda8f0dd1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-a-file-send-port-for-the-fileact-store-and-forward-scenario-to-capture-sw-exchangesnfresponse-messages"></a>Étape 3E : ajouter un Port d’envoi de fichier pour l’et de transférer le scénario afin de capturer les messages Sw-ExchangeSnFResponse FileAct
Avant de commencer cette étape, vous devez effectuer [étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md).  
  
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