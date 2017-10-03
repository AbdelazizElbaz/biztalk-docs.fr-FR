---
title: "Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f4bae51-6869-4334-a3a1-ef7e662197ca
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2027878771249ceb2dcb45683a71b4475a75cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-store-and-forward-scenario"></a>Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et d’un scénario avant
Complète [étape 2 : ajouter une Configuration pour le Paramfile pour le magasin d’interagir et le scénario par progression SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) avant de commencer cette étape.
  
## <a name="add-a-file-receive-location"></a>Ajouter l’emplacement de réception de fichier  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
4.  Dans le **propriétés du Port de réception** fenêtre, nom du port de réception, Tutorial_IA_InputRequest_SnF.  
  
5.  Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue, tapez C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF, puis cliquez sur **OK**.  
  
8.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
9. Cliquez sur **OK**.  
  
## <a name="complete-steps"></a>Étapes à suivre
 [Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)