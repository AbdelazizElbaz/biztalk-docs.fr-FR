---
title: "Exécution de l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c933839f-13e6-4b49-9838-2773e3f99b64
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e613934c44db03cf29edbf3fff4ef34d6b946577
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-dynamic-resolution-sample"></a>Exécution de l’exemple de résolution dynamique
Pour exécuter un des exemples de cas d’utilisation, vous importez le fichier de liaison de Microsoft BizTalk approprié dans l’application BizTalk de GlobalBank.ESB puis déposez un message approprié dans le dossier d’exemples d’entrée ou appelez l’exemple de service Web. L’exemple de résolution dynamique prend en charge deux scénarios principaux :  
  
-   [Les scénarios de messagerie unidirectionnels pour l’exemple de résolution dynamique](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md). Résolution dynamique exemple prend en charge ce scénario à l’aide d’un dossier de dépôt du fichier en tant que la publication pointent tous dans Microsoft BizTalk.  
  
-   [Les scénarios de messagerie bidirectionnelles pour l’exemple de résolution dynamique](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md). L’exemple de résolution dynamique prend en charge ce scénario en utilisant le service de NorthAmerican Web situé à http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx que la publication point dans BizTalk.  
  
 Pour comprendre comment l’exemple utilise le répartiteur d’ESB et les composants de pipeline désassembleur de répartiteur ESB, consultez [dynamique résolution exemple fonctionnement](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).