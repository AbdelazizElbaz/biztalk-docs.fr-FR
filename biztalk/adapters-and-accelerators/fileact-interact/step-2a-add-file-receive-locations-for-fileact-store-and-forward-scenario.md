---
title: "Étape 2 a - ajouter des emplacements de réception FILE | Documents Microsoft"
description: "Étape 2 a - ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (Pull) dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13720ebb-fbe4-4fe1-a095-9ae14c62def1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e297a85f309445c3caf569d2d752be58997e9754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2a-add-file-receive-locations-for-the-fileact-store-and-forward-pull-scenario"></a>Étape 2 a : ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)
Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour et le scénario de (extraits) avant de FileAct](step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario.md).  
  
## <a name="add-a-file-receive-location"></a>Ajouter un emplacement de réception de fichier  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
4.  Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_FA_InputRequest_SnF**.  
  
5.  Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**, puis cliquez sur **OK**.  
  
8.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
9. Cliquez sur **OK**.  
  
10. Répétez les étapes 1 et 2.  
  
11. Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
12. Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_ FA_InputRequest_PullMode**.  
  
13. Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
14. Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.  
  
15. Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\SWIFTAdapterTutorial\Interact\PullRequest**, puis cliquez sur **OK**.  
  
16. Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
17. Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes
-  [Étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et scénario Sw:HandleSnFRequest des Messages pour le magasin de FileAct et le transfert (Pull)](step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)   
-  [Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct](step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)