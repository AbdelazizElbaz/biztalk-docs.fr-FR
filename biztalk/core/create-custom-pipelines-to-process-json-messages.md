---
title: "Créer des pipelines personnalisés pour traiter les messages JSON | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b04faad1-b14b-4146-82c7-88a38d2a46a5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c85f1a45dceb812fc805a66701653642d0ccb6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-custom-pipelines-to-process-json-messages"></a>Créer des pipelines personnalisés pour traiter les messages JSON
> [!NOTE]
>  Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit des composants de pipeline pouvant être utilisés pour traiter les messages JSON dans une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans cette étape, nous utilisons ces composants de pipeline pour créer des pipelines personnalisés pouvant être utilisés lors de la configuration d'une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="create-a-custom-receive-pipeline"></a>Créer un pipeline de réception personnalisé  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, à partir de l’Explorateur de solutions, cliquez sur le projet, puis pointez sur **ajouter** > **un nouvel élément** > **Pipeline de réception**. Indiquez le nom du pipeline en tant que `JSONToXmlReceivePipeline.btp`, puis cliquez sur **ajouter**.  
  
2.  Dans le **Decode** étape Ajouter les nouveaux **décodeur JSON**. Dans les autres étapes et autres composants de pipeline, comme indiqué dans la capture d'écran, enregistrer les modifications.  
  
     ![Pipeline de réception personnalisé](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")  
  
## <a name="create-a-custom-send-pipeline"></a>Création d'un pipeline d'envoi personnalisé  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, à partir de l’Explorateur de solutions, cliquez sur le projet, puis pointez sur **ajouter** > **un nouvel élément** > **le Pipeline d’envoi**. Indiquez le nom du pipeline en tant que `XmlToJSONSendPipeline.btp`, puis cliquez sur **ajouter**.  
  
2.  Dans le **Encode** étape Ajouter les nouveaux **encodeur JSON**. Dans les autres étapes et autres composants de pipeline, comme indiqué dans la capture d'écran, enregistrer les modifications.  
  
     ![Pipeline d’envoi personnalisé](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)