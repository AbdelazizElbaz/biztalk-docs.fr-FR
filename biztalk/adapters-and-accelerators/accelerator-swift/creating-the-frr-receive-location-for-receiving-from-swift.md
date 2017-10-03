---
title: "Création de la FRR emplacement de réception pour recevoir des SWIFT | Documents Microsoft"
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
ms.assetid: e10857f4-21cb-4c09-8eed-cb6e9b0a0aa9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43ac2ac0fab9b2a29a44784032f9d3369833ae2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-location-for-receiving-from-swift"></a>Création de la FRR emplacement de réception pour recevoir des SWIFT
Pour effectuer le rapprochement de réponse de FIN, vous devez créer un emplacement de réception qui reçoit un message à partir du réseau SWIFT dans A4SWIFT.  
  
> [!NOTE]
>  Il est recommandé de configurer deux emplacements de réception pour recevoir des messages de SAA : un pour la réception de panoramique/valeurs NaN et l’autre pour recevoir tous les autres messages. Pour configurer les deux emplacements de réception, vous devez recevoir des messages de deux les files d’attente MQSeries à SAA : un pour panoramique/valeurs NaN et un pour tous les autres types de messages.  
  
 **Résumé**  
  
 Créer un emplacement de réception avec les propriétés suivantes et les composants :  
  
|Propriété/composant|Paramètre|  
|-------------------------|-------------|  
|Port de réception|Port unidirectionnel|  
|Type de transport |MQSeries|  
|Définition de la file d’attente (MQSeries)|MQSeries server<br />Gestionnaire de file d’attente<br />File d'attente|  
|Gestionnaire de réception|BizTalkServerApplication|  
|Pipeline de réception|Le A4SWIFT pipeline de réception qui vous avez créé pour FRR|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-swift"></a>Pour ajouter un FRR provenant de l’emplacement de réception SWIFT  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1** nœuds.  
  
2.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
3.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception, par exemple FRRSWIFTReceivePort.  
  
4.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.  
  
5.  Dans la Console d’Administration, cliquez sur **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
6.  Dans la boîte de dialogue un Port de réception, sélectionnez, sélectionnez le port de réception que vous venez créé, puis cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception, par exemple FRRSWIFTReceiveLocation.  
  
8.  Dans le **Transport** section, pour le **Type** zone de texte, sélectionnez **MQSeries**.  
  
9. Cliquez sur **configurer**.  
  
10. Dans la boîte de dialogue Propriétés du Transport MQSeries, cliquez sur **définition file d’attente**, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
11. Dans le **définition file d’attente** boîte de dialogue, entrez le serveur MQSeries, Gestionnaire de file d’attente et la file d’attente. Cliquez sur **OK**.  
  
12. Dans le **propriétés du Transport MQSeries** boîte de dialogue, vérifiez que les propriétés sont en fonction des besoins. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les propriétés du transport MQSeries, consultez la documentation de MQSeries.  
  
13. Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Gestionnaire de réception**, sélectionnez **BizTalkServerApplication**.  
  
14. Pour **Pipeline de réception** section, sélectionnez le A4SWIFT pipeline de réception qui vous avez créé pour FRR.  
  
15. Cliquez sur **appliquer**, puis cliquez sur **OK**  
  
16. Dans l’Explorateur BizTalk, cliquez sur l’emplacement de réception que vous venez créé, puis cliquez sur **activer**.