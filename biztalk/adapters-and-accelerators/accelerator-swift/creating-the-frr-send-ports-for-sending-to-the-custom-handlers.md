---
title: "Création de Ports d’envoi pour envoyer aux gestionnaires personnalisés FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 036f1f97-17a2-4e02-a85a-a52739a48528
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a6326ae6e82e819d3cdf76ecc4d81e2a377ea65
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-the-frr-send-ports-for-sending-to-the-custom-handlers"></a>Création de Ports d’envoi pour envoyer aux gestionnaires personnalisés FRR
Pour effectuer le rapprochement de réponse de FIN, vous devez créer une série de ports d’envoi, chacun d’eux envoie un message (message d’origine ou réponse) à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] aux gestionnaires personnalisés qui traitent les messages corrélés.  
  
 **Résumé**  
  
 Créer une série de ports d’envoi avec les propriétés suivantes et les composants, chacun d’eux différencié par la valeur de BizTalk Server. Opération dans le filtre :  
  
|Propriété/composant|Paramètre|  
|-------------------------|-------------|  
|Port d'envoi|Port statique unidirectionnel|  
|Type de transport |FILE|  
|Dossier de destination (adresse URI)|Le dossier que vous souhaitez envoyer le message|  
|Nom de fichier (adresse URI)|%MessageID%.txt|  
|Pipeline d’envoi|[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. BizTalk.DefaultPipelines. PassThruTransmit|  
|Filtres|Comme indiqué dans les tableaux ci-dessous|  
  
 Les ports d’envoi pour les différents messages sont distinguent par la valeur de BizTalk Server. Opération dans les filtre du port d’envoi.  
  
### <a name="to-add-frr-send-ports-for-sending-to-the-custom-handlers"></a>Pour ajouter des ports d’envoi FRR pour l’envoi aux gestionnaires personnalisés  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Static-waySend un Port**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez un nom pour le port d’envoi, par exemple FRRCustomHandlersSendPort.  
  
3.  Pour **Type**, sélectionnez **fichier**.  
  
4.  Cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.  
  
6.  Dans la boîte de dialogue Rechercher un dossier, déplacer vers le dossier que vous souhaitez envoyer des messages à partir de. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.  
  
7.  Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Vous pouvez créer un dossier différent pour chaque type de message.  
  
8.  Dans la boîte de dialogue Propriétés de Port d’envoi pour le Gestionnaire d’envoi, vérifiez que **BizTalkServerApplication** est sélectionnée.  
  
9. Pour **Pipeline d’envoi**, sélectionnez **PassThruTransmit**.  
  
10. Cliquez sur **filtres** dans le volet gauche, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **A4SWIFT_FrrService**.|  
    |**Grouper**|**And**|  
    |**Propriété**|Sélectionnez **BTS. Opération**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Tapez le BTS. Valeurs d’opération dans le tableau ci-dessous.|  
  
     Pour BizTalk Server. Opération, entrez une des valeurs suivantes :  
  
    |type de message|BIZTALK SERVER. Valeur de l’opération|  
    |------------------|-------------------------|  
    |Tous les types de messages SWIFT FIN catégorie 0 à 9|**A4SWIFT_FrrSendMTMsg**|  
    |MQ Series panoramique/NAN (au niveau du transport MQSeries l’accusé de réception/NON-RÉCEPTION)|**A4SWIFT_FrrSendTransport**|  
    |MT010 (avertissement de non-remise)|**A4SWIFT_FrrSend010NDW**|  
    |MT011 (accusé de réception)|**A4SWIFT_FrrSend011Delivered**|  
    |MT012 (Notification de l’expéditeur)|**A4SWIFT_FrrSend012SenderACK**|  
    |MT015 (DNK ou NAK retardé)|**A4SWIFT_FrrSend015DNK**|  
    |MT019 (abandon de Notification)|**A4SWIFT_FrrSend019Abort**|  
    |MTS21_FIN_ACKNAK (accusé de réception d’un message FIN envoyé par un LT (accusé de réception)|**A4SWIFT_FrrSendS21ACK**|  
    |MTS21_FIN_ACKNAK (valeur négative d’accusé de réception d’un message FIN envoyé par un LT (NAK)|**A4SWIFT_FrrSendS21NAK**|  
  
11. Pour les messages de catégorie de 0 à 9 SWIFT FIN qui ne sont pas envoyés avec succès, procédez comme suit le **filtres** volet :  
  
    > [!NOTE]
    >  Le **A4SWIFT_FRRFailedReason** propriétés dans le filtre suivant doivent être regroupées.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **A4SWIFT_FrrService**.|  
    |**Grouper**|**And**|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **True**.|  
    |**Grouper**|**And**|  
    |**Propriété**|Sélectionnez **BTS. Opération**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **A4SWIFT_FrrSendMTMsg**.|  
    |**Grouper**|**And**|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type  *\<NAKErrorCode\>*, tels que « Y01 ».|  
    |**Grouper**|**Or**|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **TimedOut**.|  
    |**Grouper**|**Or**|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **TransportError**.|  
    |**Grouper**|**Or**|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **DelayedNAK**.|  
    |**Grouper**|**Or**|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **AbortMessage**.|  
  
12. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
13. Cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
14. Répétez les étapes 2 à 13 pour créer un port d’envoi pour chaque type de message requis.