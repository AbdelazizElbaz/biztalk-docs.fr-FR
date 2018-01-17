---
title: "Étape 6 : Créer le Port d’envoi pour le traitement de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a0f1ee-e060-4fb9-923e-ebe8168777d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 958746634776e9b01c32ff2425122312bc7a841c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-6-create-the-send-port-for-the-acknowledgment-batch"></a>Étape 6 : Créer le Port d’envoi pour le traitement de l’accusé de réception
Dans cette étape, vous créez un port d’envoi pour fournir le traitement de l’accusé de réception que vous créez à la partie de la source. Il s’agit d’un port statique unidirectionnel avec un type d’adaptateur FILE. Vous désignez un dossier de fichiers pour la source (\Tutorial_BatchACKDrop), où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprimera le fichier de commandes d’accusé de réception. Vous définissez un filtre pour le port qui indique le type de lots d’accusé de réception envoie les ports. Le filtre spécifie la source de Tutorial_BatchSource et le type de message de OutboundBatch.  
  
### <a name="to-create-the-send-port-for-the-acknowledgment-batch"></a>Pour créer le port d’envoi pour le traitement de l’accusé de réception  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_BatchSource**.|  
    |**Type**|Sélectionnez **fichier** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir la boîte de dialogue Propriétés du Transport FILE.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Accédez à  **\< *lecteur*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BatchACKDrop**. Il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier contenant le lot d’accusé de réception.|  
    |**Nom de fichier**|Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).|  
    |**Mode de copie**|Sélectionnez **créer de nouveaux**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
6.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Cliquez sur le champ sous **propriété**, puis sélectionnez **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** dans la liste déroulante.|  
    |**Opérateur**|Laissez  **==**  comme l’opérateur.|  
    |**Value**|Type **Tutorial_BatchSource**.|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété**|Select **BTAHL7Schemas.BTAHL7MessageType**.|  
    |**Opérateur**|Laissez  **==**  comme l’opérateur.|  
    |**Value**|Type **OutboundBatch**.|  
  
7.  Appuyez sur **Entrée**. Dans le volet du bas de la boîte de dialogue, vérifiez que vous avez correctement entré l’expression de filtre, puis cliquez sur **OK**.  
  
8.  Dans la Console Administration de BizTalk, sélectionnez **Ports d’envoi**, avec le bouton droit **Tutorial_BatchSource**, puis cliquez sur **Démarrer**.  
  
### <a name="to-associate-the-send-port-with-the-source-party"></a>Pour associer le port d’envoi du tiers source  
  
1.  Dans la Console Administration de BizTalk, cliquez sur **Parties**. Avec le bouton droit **Tutorial_BatchSource**, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers, cliquez sur **Ports d’envoi** dans l’arborescence de la console. Pour **Ports d’envoi**, sélectionnez **Tutorial_BatchSource** dans la liste déroulante, puis cliquez sur **OK**.  
  
 Passez à [étape 7 : démarrer l’Orchestration et redémarrez le serveur BizTalk](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md).