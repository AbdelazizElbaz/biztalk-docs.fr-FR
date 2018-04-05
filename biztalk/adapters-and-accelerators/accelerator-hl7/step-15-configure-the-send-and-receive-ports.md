---
title: 'Étape 15 : Configurer l’envoi et Ports de réception | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, ports
ms.assetid: d532b196-473e-4c8f-b4ed-acef674fc698
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 020d83db1db86f9ff9ce116578cf58f19ba08241
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-15-configure-the-send-and-receive-ports"></a>Étape 15 : Configurer l’envoi et Ports de réception
Dans les étapes précédentes, vous créé un envoi logique à l’aide du Concepteur d’Orchestration de port de réception et définissez la liaison de port pour « Spécifier plus tard ». Dans cette étape, vous utilisez l’Explorateur BizTalk pour finaliser la configuration du port en définissant les emplacements source et destination physiques et de liaison des ports physiques aux ports logiques que vous avez créé dans l’orchestration.  
  
## <a name="configure-the-send-and-receive-ports"></a>Configurer l’envoi et de ports de réception  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur Nouveau, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez **MLLPSendPort**.  
  
4.  Pour **Type**, sélectionnez **MLLP**.  
  
5.  Cliquez sur le **configurer** bouton à droite de la **Type** champ.  
  
6.  Dans la boîte de dialogue Propriétés du Transport MLLP pour **nom de la connexion** entrez **MLLPConnection**. Pour **hôte** entrez **localhost**. Cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**, puis cliquez sur **OK**.  
  
8.  Dans la Console d’Administration, cliquez sur **MLLPSendPort** de port, puis cliquez sur **Démarrer**.  
  
9. Développez **paramètres de plateforme**, cliquez sur **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **Démarrer**. Si l’hôte est déjà en cours d’exécution, cliquez sur **redémarrer**.  
  
10. Cliquez sur **Orchestrations**, avec le bouton droit **BTAHL7_Project.Doorbell_Orchestration**, puis cliquez sur **propriétés**.  
  
11. Dans la boîte de dialogue Propriétés d’Orchestration dans l’arborescence de la console, cliquez sur **liaisons**.  
  
12. Dans le **liaisons** volet, pour **hôte**, sélectionnez **BizTalkServerApplication**.  
  
13. Pour **SOAPReceivePort**, sélectionnez **WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** dans les **Ports de réception** colonne.  
  
14. Pour **MLLPSendPort**, sélectionnez **MLLPSendPort** dans les **groupes de ports d’envoi d’envoi** colonne.  
  
15. Cliquez sur **OK** pour enregistrer les modifications.  
  
## <a name="msh-5-and-msh-6"></a>MSH 5 et 6 de MSH  
 Les champs d’en-tête MSH 5 et 6 de MSH contiennent l’application de destination, des installations, respectivement. Dans l’Explorateur de Configuration, vous pouvez spécifier les valeurs pour chacun des trois composants de MSH 5 et 6 de MSH, dans les cas où vous souhaitez que les informations de destination dans le message doit être modifié. Il s’agit d’un scénario probable lorsque le message d’origine n’inclut pas les informations spécifiques aux tiers. Cette étape s’applique dans le modèle déclaratif (serveur de publication/abonné). Vous effectuez cette étape si elle est applicable dans votre environnement. Pour plus d’informations sur la définition de ces valeurs, consultez [Parties - Explorateur de Configuration de BTAHL7](parties-tab.md).  
  
 Passez à [étape 16 : démarrer l’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)