---
title: "Installation de l’exemple d’opérations BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57c982c2-f796-4c63-9bca-7e8965779850
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8fb289e5bb7950f9ad8bca3dac98035bada176
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-the-biztalk-operations-sample"></a>Installation de l’exemple d’opérations BizTalk
L’exemple de BizTalk de Microsoft Operations nécessite le service d’opérations de BizTalk ESB installé et configuré. Service d’opérations de BizTalk ESB est un des services Web principaux qui peuvent être installés et configurés à l’aide de l’outil de Configuration ESB. Pour plus d’informations sur l’utilisation de l’outil de Configuration ESB, consultez [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx). L’emplacement par défaut du service Web d’opérations BizTalk est http://localhost/ESB.BizTalkOperationsService/Operations.asmx; Toutefois, vous pouvez y remédier dans le fichier de configuration d’application si vous déployez le service dans un autre emplacement ou un serveur distant.  
  
 Vous devez installer les exemples d’opérations BizTalk à partir du projet de la solution.  
  
 **Pour installer l’exemple d’opérations BizTalk**  
  
1.  Ouvrez la solution nommée ESB.BizTalkOperations.Test.Client.csproj à partir du dossier \Source\Samples\BizTalkOperations où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples dans Visual Studio.  
  
2.  Utilisez les commandes dans le **générer** menu pour compiler la solution.