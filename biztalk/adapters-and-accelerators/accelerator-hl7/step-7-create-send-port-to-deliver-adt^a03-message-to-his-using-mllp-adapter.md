---
title: "Étape 7 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: d9e7f281-3d25-4675-a13e-0e2057f5e69a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc122ab37ee0d618c3bd75792a5b88571dd49162
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-a-send-port-to-deliver-the-adta03-message-to-his-using-the-mllp-adapter"></a>Étape 7 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP
Dans cette étape, vous créez le port d’envoi pour envoyer le message à l’hôpital informations système HIS () à l’aide de l’adaptateur MLLP.  
  
### <a name="to-create-the-tutorialmllpsend-send-port"></a>Pour créer le port d’envoi Tutorial_MllpSend  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, effectuez les actions suivantes :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_MllpSend**.|  
    |**Type de transport**|Sélectionnez **MLLP** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir le **propriétés du Transport MLLP** boîte de dialogue.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport MLLP, effectuez les actions suivantes, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la connexion**|Type **1WaySend**.|  
    |**Hôte**|Type **localhost**.|  
    |**Port**|Type **14000**.|  
  
4.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
5.  Dans le volet gauche, sélectionnez **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. ReceivePortName** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **Tutorial_1WayReceive**.|  
  
    > [!NOTE]
    >  Le port d’écoute le port spécifié dans 1WayReceive pour tous les messages.  
  
6.  Cliquez sur **appliquer**, puis cliquez sur **OK.**  
  
7.  Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_MllpSend**, puis cliquez sur **Démarrer**.  
  
 Passez à [étape 8 : configurer les informations de tiers](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md).