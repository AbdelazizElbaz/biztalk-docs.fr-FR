---
title: "Étape 8C : configurer les informations de tiers pour le système HI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ac5c113-7ee7-4009-8ca3-d263f74c7a8d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f0b9e1538ea667eab2299a1a02021c1237bc985
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8c-configure-party-information-for-the-hi-system"></a>Étape 8C : configurer les informations de tiers pour le système HI
Dans cette étape, vous configurez les informations de tiers pour le système HI.  
  
### <a name="to-configure-the-hi-system-party-information"></a>Pour configurer les informations de tiers HI système  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_HISystem**.  
  
3.  Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.  
  
4.  Dans le volet Ports d’envoi, cliquez sur le champ vide dans le **nom** colonne, sélectionnez **Tutorial_MllpSend**, puis cliquez sur **OK**.  
  
5.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
6.  Dans l’Explorateur de Configuration BTAHL7, sélectionnez le **MSH carte** onglet, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**MSH3**|Type **BTAHL7**, **IE**, et **UUID** dans la première, deuxième et troisième messages, respectivement.|  
    |**MSH5**|Type **HI**, **système**, et **GUID** dans la première, deuxième et troisième messages, respectivement.|  
    |**MSH9**|Type **ADT** et **A04** dans les zones de message de premier et deuxième, respectivement.|  
    |**MSH12**|Type **2.4**.|  
    |**MSH15**|Sélectionnez **SU** pour envoyer des accusés de réception après la transmission réussie d’un message.|  
    |**MSH16**|Sélectionnez **Because** pour ne jamais envoyer les accusés de réception.|  
  
7.  Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration BTAHL7.  
  
    > [!NOTE]
    >  Il est inutile de créer des informations de tiers pour le système de moteur Interface BTAHL7, car les informations de configuration ne sont pas nécessaires pour ce scénario.  
  
 Passez à [étape 9 : redémarrez BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md).