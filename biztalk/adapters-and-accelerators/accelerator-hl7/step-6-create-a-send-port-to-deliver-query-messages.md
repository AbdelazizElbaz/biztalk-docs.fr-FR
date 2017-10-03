---
title: "Étape 6 : Créer un Port d’envoi pour remettre des Messages de requête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, send ports
ms.assetid: a3cfa2aa-888d-4a82-9eb3-2e9cc29ee582
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c373940d8ab1e847b66527d83ef24e952d84d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-a-send-port-to-deliver-query-messages"></a>Étape 6 : Créer un Port d’envoi pour remettre des Messages de requête
Dans cette étape, vous créez le port d’envoi pour remettre les requêtes entrantes (Req ^ Q01 messages) à l’hôpital informations système (HIS).  
  
### <a name="to-create-the-hissend-send-port"></a>Pour créer le port d’envoi HIS_Send  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **HIS_Send**.|  
    |**Type de transport**|Sélectionnez **MLLP**.|  
    |**Configurer**|Cliquez sur le **configurer** bouton à droite de **Type**.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport MLLP, entrez les informations suivantes, puis **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la connexion**|Type **HIS_SendMLLP**.|  
    |**Hôte**|Type **localhost**.|  
    |**Port**|Type **24000**.|  
  
4.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
5.  Dans l’arborescence de la Console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Pour **propriété**, sélectionnez **BTS. MessageType**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF**.|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété**|Pour **propriété** sur la deuxième ligne, sélectionnez **BTAHL7Schemas.MSH5_1**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **HIS**.|  
  
    > [!NOTE]
    >  Le premier filtre spécifie que le port d’envoi sélectionne uniquement les messages qui se conforment à la req ^ schéma Q01 créé à l’étape 3 a. Le deuxième filtre spécifie la destination à laquelle le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface moteur envoie ces messages.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans la console d’Administration, sélectionnez **Ports d’envoi**, avec le bouton droit **HIS_Send**, puis cliquez sur **Démarrer**.  
  
 Passez à [étape 7 : créer un Port d’envoi pour remettre des Messages de réponse](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md).