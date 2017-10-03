---
title: "Étape 8 : configurer les informations de tiers pour le System_hl7_main ADT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 693fda8b-9a99-4a6e-89b7-294f84676350
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9285b926edb5ca4f1dccf18ed2d5f76b3af14ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8a-configure-party-information-for-the-adt-systemhl7main"></a>Étape 8 : configurer les informations de tiers pour le System_hl7_main ADT
Dans cette étape, vous configurez les informations de tiers pour le système ADT.  
  
### <a name="to-configure-the-adt-system-party-information"></a>Pour configurer les informations de tiers ADT système  
  
1.  Dans la Console Administration de BizTalk, développez **Administration de BizTalk Server**, puis développez **groupe BizTalk**. Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **ADT**. (La valeur que vous tapez dans cette zone doit correspondre à l’instance de message HL7 d’origine, QRY^Q01.txt MSH3).  
  
3.  Dans l’arborescence de la Console, cliquez sur **Ports d’envoi**.  
  
4.  Dans le **Port d’envoi** volet, pour **nom** dans la première ligne, sélectionnez **ADT_Send**, puis cliquez sur **OK**.  
  
5.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
6.  Dans l’Explorateur de Configuration BTAHL7, cliquez sur le **accusé de réception** onglet. Pour **Type d’accusé de réception**, sélectionnez **EnhancedMode**.  
  
7.  Dans les propriétés de l’accusé de réception dans le volet Inboiund Message, pour **MSH15 - accepter le Type d’accusé de réception**, sélectionnez **AL**.  
  
8.  Dans le volet des propriétés de l’accusé de réception pour **MSH16 - Type d’accusé de réception Application**, sélectionnez **Because**.  
  
9. Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration de BTAHL7.  
  
 Passez à [étape 8 : configurer les informations de tiers pour le système HI](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md).