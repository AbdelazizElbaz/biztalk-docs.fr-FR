---
title: "Implémentation de l’exemple de gestionnaire FRR NAK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80fa5fb7-6864-4923-b641-e76d2b95d923
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4233bf7f81cf7e645440e18a54479c8aa81094e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-the-frr-nak-handler-sample"></a>Implémentation de l’exemple de gestionnaire FRR NAK
Pour implémenter l’exemple de gestionnaire personnalisé FRR NAK, ajoutez l’exemple de projet à votre solution, générer et déployer le projet, lier et démarrer l’orchestration et puis arrêtez et redémarrez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-implement-the-frr-nak-custom-handler"></a>Pour implémenter le gestionnaire personnalisé de NAK FRR  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], ouvrez votre solution. Dans l’Explorateur de solutions, cliquez sur la solution, pointez sur **ajouter**, puis cliquez sur **projet existant**.  
  
2.  Dans le **ajouter un projet existant** boîte de dialogue, accédez à  *\<lecteur >*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Samples\FrrHandler. Sélectionnez **RepairSWIFTRejectedMessage.btproj**, puis cliquez sur **ouvrir**.  
  
3.  Générer une clé et attribuez la clé au projet.  
  
4.  Générez et déployez le projet RepairSWIFTRejectedMessage.btproj.  
  
5.  Dans l’Explorateur BizTalk, développez **bases de données de Configuration BizTalk**,  **\<* nom du serveur*>, BizTalkMgmtDb.dbo**, et  **Orchestrations**, avec le bouton droit **RepairSWIFTRejectedMessage.Orchestration_1**, puis cliquez sur **lier**.  
  
6.  Dans le **propriétés de liaison de Port** boîte de dialogue, sélectionnez votre hôte, telles que BizTalkServerApplication, puis **OK**.  
  
7.  Dans l’Explorateur BizTalk, cliquez sur **RepairSWIFTRejectedMessage.Orchestration_1**, puis cliquez sur **Démarrer**.  
  
8.  Dans le **démarrage rapide** boîte de dialogue, cliquez sur **OK**.  
  
9. Cliquez sur **Démarrer**, puis sur **Exécuter**. Entrez **services.msc**, puis cliquez sur **OK**. Avec le bouton droit **BizTalk Service**, puis cliquez sur **redémarrer**.