---
title: "Envoi de Messages via emplacements de réception et des formulaires InfoPath | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, receive locations
- receive locations, messages
- messages, InfoPath forms
- InfoPath forms, messages
ms.assetid: e8676830-3fbc-423f-82f6-03e6a532075f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6cddeca2eb80fbeb7c9fb5742e2838a860079d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="submitting-messages-through-receive-locations-and-infopath-forms"></a>Envoi de Messages via emplacements de réception et des formulaires InfoPath
Recevoir des emplacements de recevoir des messages à envoyer dans [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] applications. Vous pouvez définir des emplacements de réception en tant que points de terminaison physiques configurés pour recevoir des messages à l’aide d’un protocole de transport spécifié. Par exemple, un emplacement de réception peut être configuré pour des fichiers de réception déplacées vers un dossier de système de fichier particulier en utilisant le transport de fichier.  
  
 Vous créez des emplacements de réception pour les ports de réception qui logiquement regroupement et gérer les emplacements de réception. Pour chaque emplacement de réception, vous spécifiez un pipeline de réception, qui effectue le traitement (le décodage, le code machine, validation et ainsi de suite) des messages reçus à cet emplacement de réception particulier. Emplacements de réception de réception A4SWIFT lie les ports qui logiquement regroupement et gérer les emplacements de réception.  
  
 Pour envoyer un message SWIFT dans une application A4SWIFT via un emplacement de réception, le message doit supprimé à un emplacement de réception configuré, traité par un pipeline de réception à l’aide du désassembleur SWIFT, analyser et de valider par le désassembleur SWIFT, et publié dans la base de données MessageBox. Une fois que les messages sont publiés dans la base de données MessageBox, autres composants de votre application A4SWIFT de récupérer les messages (à l’aide d’abonnements) pour un traitement supplémentaire. Par exemple, vous pouvez utiliser des ports d’envoi pour le routage finale.  
  
 Pour plus d’informations sur la création et configuration des ports de réception et emplacements de réception, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Vous pouvez également envoyer un message via un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran, à l’aide de la fonctionnalité de Message Repair et New Submission. Pour ce faire, vous ouvrez le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour ce message à partir d’un dossier sur le site MRSR. Vous fournissez les données dans le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forment, se connecter à l’aide de votre certificat, puis l’envoyer. L’orchestration Message Repair et New Submission traite le message.  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator pour SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)