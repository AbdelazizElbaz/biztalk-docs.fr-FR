---
title: "Étape 7 : Créer un Port d’envoi pour remettre des Messages de réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, send ports
ms.assetid: 5edaefb6-72f2-4317-9477-f3a0d0027e0c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1260772f3b3df5f0dea96b0aa66023e107b9aa6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-a-send-port-to-deliver-response-messages"></a>Étape 7 : Créer un Port d’envoi pour remettre des Messages de réponse
Dans cette étape, vous créez le port d’envoi pour fournir les réponses de requêtes l’admission, rejet, et transférer (ADT) système.  
  
### <a name="to-create-the-adtsend-send-port"></a>Pour créer le port d’envoi ADT_Send  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **ADT_Send**.|  
    |**Type de transport**|Sélectionnez **MLLP**.|  
    |**Configurer**|Cliquez sur le **configurer** bouton à droite de **Type**.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport MLLP, entrez les informations suivantes, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la connexion**|Type **ADT_SendMLLP**.|  
    |**Hôte**|Type **localhost**.|  
    |**Port**|Type **25000**.|  
  
4.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
5.  Dans l’arborescence de la Console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. MessageType**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF**.|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété**|Dans la première propriété, cliquez sur la zone vierge, puis **BTAHL7Schemas.MSH5_1**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **ADT**.|  
  
    > [!NOTE]
    >  Le premier filtre spécifie que le port d’envoi sélectionne uniquement les messages conformes au DSR ^ schéma Q01 créé à l’étape 3 a. Le deuxième filtre spécifie la destination à laquelle le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface moteur envoie ces messages.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **ADT_Send**, puis cliquez sur **Démarrer**.  
  
 Passez à [étape 8 : configurer les informations de tiers](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md).