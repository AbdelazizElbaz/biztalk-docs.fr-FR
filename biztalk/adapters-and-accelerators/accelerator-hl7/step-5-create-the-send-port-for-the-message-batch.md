---
title: "Étape 5 : Créer le Port d’envoi pour le lot de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5db815df-5b76-4ba4-99ab-c7766b0c301a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5749166c8a9b34d5e5a04849c4179ac4427201c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-5-create-the-send-port-for-the-message-batch"></a>Étape 5 : Créer le Port d’envoi pour le lot de messages
Dans cette étape, vous créez un port d’envoi pour remettre le lot de messages que vous créez au tiers de destination. Il s’agit d’un port statique unidirectionnel avec un type d’adaptateur FILE. Vous désignez un dossier de fichiers pour la destination (\Tutorial_BatchMsgDrop) où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprimera le fichier de commandes de message. Vous définissez un filtre pour le port qui indique le type de lots de messages envoie les ports. Le filtre spécifie la destination des Tutorial_BatchDest et le type de message de OutboundBatch.  
  
> [!NOTE]
>  Lors de l’exécution de cette partie du didacticiel, vous pouvez simplifier les résultats en arrêtant le port d’envoi utilisé dans la partie 2 du didacticiel : le **Tutorial_BTAHL7Drop** port d’envoi.  
  
### <a name="to-create-the-send-port-for-the-message-batch"></a>Pour créer le port d’envoi pour le lot de messages  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_BatchDest**.|  
    |**Type**|Sélectionnez **fichier** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir la boîte de dialogue Propriétés du Transport FILE.|  
  
3.  Dans le **propriétés du Transport FILE** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Accédez à  **\< *lecteur*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BatchMsgDrop**. Il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier contenant le lot de messages.|  
    |**Nom de fichier**|Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).|  
    |**Mode de copie**|Sélectionnez **créer de nouveaux**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
6.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Cliquez sur le champ sous **propriété**, puis sélectionnez **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** dans la liste déroulante.|  
    |**Opérateur**|Laissez  **==**  comme l’opérateur.|  
    |**Value**|Type **Tutorial_BatchDest**.|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété**|Select **BTAHL7Schemas.BTAHL7MessageType**.|  
    |**Opérateur**|Laissez  **==**  comme l’opérateur.|  
    |**Value**|Type **OutboundBatch**.|  
  
7.  Appuyez sur **Entrée**. Dans le volet du bas de la boîte de dialogue, vérifiez que vous avez correctement entré l’expression de filtre, puis cliquez sur **OK**.  
  
8.  Dans la Console Administration de BizTalk, sélectionnez **Ports d’envoi**, avec le bouton droit **Tutorial_BatchDest**, puis cliquez sur **Démarrer**.  
  
### <a name="to-associate-the-send-port-with-the-destination-party"></a>Pour associer le port d’envoi de tiers de destination  
  
1.  Dans la Console Administration de BizTalk Server, développez **Parties**, cliquez sur **Tutorial_BatchDest**, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers, cliquez sur **Ports d’envoi** dans l’arborescence de la console.  Sélectionnez **Tutorial_BatchDest** dans la liste déroulante, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si une violation d’accès concurrentiel se produit pendant la **Tutorial_DestBatch** tiers a été mis à jour, cliquez sur **OK** et fermer la boîte de dialogue. Dans la Console d’Administration, cliquez sur **groupe BizTalk**, cliquez sur **Actualiser**, puis répétez les étapes 1 et 2.  
  
 Passez à [étape 6 : créer le Port d’envoi pour le traitement de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md).