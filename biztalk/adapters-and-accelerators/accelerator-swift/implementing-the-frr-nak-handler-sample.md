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
ms.openlocfilehash: a91c0303c9abdf6b1d8c434869445f3c84348935
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="implementing-the-frr-nak-handler-sample"></a>Implémentation de l’exemple de gestionnaire FRR NAK
Pour implémenter l’exemple de gestionnaire personnalisé FRR NAK, ajoutez l’exemple de projet à votre solution, générer et déployer le projet, lier et démarrer l’orchestration et puis arrêtez et redémarrez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-implement-the-frr-nak-custom-handler"></a>Pour implémenter le gestionnaire personnalisé de NAK FRR  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], ouvrez votre solution. Dans l’Explorateur de solutions, cliquez sur la solution, pointez sur **ajouter**, puis cliquez sur **projet existant**.  
  
2.  Dans le **ajouter un projet existant** boîte de dialogue, accédez à  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Samples\FrrHandler. Sélectionnez **RepairSWIFTRejectedMessage.btproj**, puis cliquez sur **ouvrir**.  
  
3.  Générer une clé et attribuez la clé au projet.  
  
4.  Générez et déployez le projet RepairSWIFTRejectedMessage.btproj.  
  
5.  Dans l’Explorateur BizTalk, développez **bases de données de Configuration BizTalk**,  **\< *nom du serveur*\>, BizTalkMgmtDb.dbo**, et  **Orchestrations**, avec le bouton droit **RepairSWIFTRejectedMessage.Orchestration_1**, puis cliquez sur **lier**.  
  
6.  Dans le **propriétés de liaison de Port** boîte de dialogue, sélectionnez votre hôte, telles que BizTalkServerApplication, puis **OK**.  
  
7.  Dans l’Explorateur BizTalk, cliquez sur **RepairSWIFTRejectedMessage.Orchestration_1**, puis cliquez sur **Démarrer**.  
  
8.  Dans le **démarrage rapide** boîte de dialogue, cliquez sur **OK**.  
  
9. Cliquez sur **Démarrer**, puis sur **Exécuter**. Entrez **services.msc**, puis cliquez sur **OK**. Avec le bouton droit **BizTalk Service**, puis cliquez sur **redémarrer**.