---
title: "Comment créer des Ports de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, receive
- receive ports
- creating receive ports
ms.assetid: d390320e-12f1-4ead-b608-60bc1e273477
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ca5727422fd7519443cc290d35d0c2e24d499f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-receive-ports"></a>Comment créer des Ports de réception
Suivez ces étapes pour créer un port de réception en utilisant Visual Studio.  
  
### <a name="to-create-a-receive-port"></a>Pour créer un port de réception  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.  
  
3.  Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :  
  
    1.  Dans le **nom** , tapez `ReceiveFromTIBCORV`.  
  
    2.  Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.  
  
    3.  Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.  
  
4.  Sur le **emplacements de réception** page, procédez comme suit :  
  
    1.  Cliquez sur **Nouveau**.  
  
    2.  Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.  
  
    3.  À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.  
  
    4.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.  
  
    5.  Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.  
  
    6.  Sélectionnez le **activer la fenêtre de service** case à cocher.  
  
    7.  Cliquez sur **OK**.  
  
5.  Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.  
  
6.  Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.  
  
7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaires de réception création TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)