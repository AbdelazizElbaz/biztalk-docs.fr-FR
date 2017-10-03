---
title: "Emplacement de réception pour la réception de l’Application Back-End-création de la FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: 78bd8084-ddec-4066-a474-ab5b1a0a849f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46895ff64e6585c8b80979c09874dffb510cf049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-location-for-receiving-from-the-back-end-application"></a>Création de la FRR emplacement de réception pour la réception de l’Application Back-End
Pour effectuer le rapprochement de réponse de FIN, vous devez créer un emplacement de réception qui reçoit un message à partir de l’application principale dans [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  
  
 **Résumé**  
  
 Créer un emplacement de réception avec les propriétés suivantes et les composants :  
  
|Propriété/composant|Paramètre|  
|-------------------------|-------------|  
|Port de réception|Port unidirectionnel|  
|Type de transport |Le type de transport utilisé par l’application principale|  
|Adresse URI|Selon les besoins pour le type de transport|  
|Gestionnaire de réception|BizTalkServerApplication|  
|Pipeline de réception|Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline que vous avez créé pour FRR de réception|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-the-back-end-application"></a>Pour ajouter un FRR emplacement de réception pour la réception de l’application principale  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1** nœuds.  
  
2.  Avec le bouton droit **Pipelines**, puis cliquez sur **Actualiser**.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception, par exemple FRRBackEndReceivePort.  
  
5.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.  
  
6.  Dans la Console d’Administration, cliquez sur **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
7.  Dans la boîte de dialogue un Port de réception, sélectionnez, sélectionnez le port de réception que vous venez créé, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception.  
  
9. Dans le **Transport** section, pour le **Type** zone de texte, sélectionnez le type de transport utilisé par l’application principale.  
  
10. Cliquez sur **configurer**.  
  
11. Dans la boîte de dialogue Propriétés du Transport FILE, renseignez les propriétés requises pour le type de transport, puis cliquez sur **OK**.  
  
12. Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Gestionnaire de réception**, sélectionnez **BizTalkServerApplication**.  
  
13. Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Pipeline de réception**, sélectionnez le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline que vous avez créé pour FRR de réception.  
  
14. Cliquez sur **appliquer**, puis cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.  
  
15. Dans l’Explorateur BizTalk, cliquez sur l’emplacement de réception que vous venez créé, puis cliquez sur **activer**.