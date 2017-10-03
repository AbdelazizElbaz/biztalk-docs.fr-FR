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
ms.openlocfilehash: 6307f9d9e4ff9907bab22efcde0755dbdfdc228b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-biztalk-operations-sample"></a>Installation de l’exemple d’opérations BizTalk
L’exemple de BizTalk de Microsoft Operations nécessite le service d’opérations de BizTalk ESB installé et configuré. Service d’opérations de BizTalk ESB est un des services Web principaux qui peuvent être installés et configurés à l’aide de l’outil de Configuration ESB. Pour plus d’informations sur l’utilisation de l’outil de Configuration ESB, consultez [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx). L’emplacement par défaut du service Web d’opérations BizTalk est http://localhost/ESB.BizTalkOperationsService/Operations.asmx; Toutefois, vous pouvez y remédier dans le fichier de configuration d’application si vous déployez le service dans un autre emplacement ou un serveur distant.  
  
 Vous devez installer les exemples d’opérations BizTalk à partir du projet de la solution.  
  
 **Pour installer l’exemple d’opérations BizTalk**  
  
1.  Ouvrez la solution nommée ESB.BizTalkOperations.Test.Client.csproj à partir du dossier \Source\Samples\BizTalkOperations où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples dans [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Utilisez les commandes dans le **générer** menu pour compiler la solution.