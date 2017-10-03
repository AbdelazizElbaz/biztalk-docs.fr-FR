---
title: "Composants de réception EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d3b82e8-1168-4c2c-bf1a-886b43ff8108
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc53f4c592b767c8061fb1ed8134636322b35b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-receive-components"></a>Composants de réception EDI
Le pipeline et les composants de pipeline décrits dans cette rubrique traitent les messages EDI de type autre que EDI/AS2. Pour plus d’informations sur le traitement de réception EDI/AS2 ou les messages EDI/AS2, consultez [les composants de réception AS2](../core/as2-receive-components.md). Notez que les composants de réception AS2 exécutent le traitement EDI en plus du traitement AS2.  
  
## <a name="edi-receive-pipeline"></a>Pipeline de réception EDI  
 Le traitement de réception EDI est effectué dans le pipeline de réception EDI. Ce pipeline est installé dans le fichier Microsoft.BizTalk.Edi.EdiPipelines.dll situé dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]. Ce pipeline traite les messages EDI reçus via un protocole de transport quelconque. En revanche, il ne traite pas les messages EDI de type AS2 reçus via HTTP (traités par les pipelines AS2). Les pipelines de réception AS2 utilisent les mêmes composants que le pipeline EDI pour traiter les messages EDI.  
  
> [!NOTE]
>  Un problème de sécurité peut survenir si vous créez un emplacement de réception utilisant le pipeline EDIReceive et le type de transport HTTP. Le pipeline EdiReceive ne génèrera aucun accusé de réception HTTP "200 OK". Si aucun accusé de réception EDI n'est renvoyé, la connexion n'est pas interrompue correctement et reste ouverte. La connexion se termine à l'expiration du délai d'attente.  
  
 Le pipeline EDIReceive inclut les composants de pipeline suivants :  
  
-   Désassembleur EDI  
  
-   BatchMarker.  
  
## <a name="edi-receive-pipeline-components"></a>Composants du pipeline de réception EDI  
 Le pipeline EDIReceive utilise les composants de pipeline suivants Ces composants sont installés dans le fichier Microsoft.BizTalk.EDI.pipelinecomponents.dll situé dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]composants de Pipeline\\.  
  
### <a name="edi-disassembler"></a>Désassembleur EDI  
 Le Désassembleur EDI effectue la plus grande partie du traitement des échanges EDI reçus dans le pipeline EDIReceive. Pour plus d’informations sur la façon dont le désassembleur EDI traite les messages EDI, consultez [EDI désassembleur fonctionnement](../core/how-the-edi-disassembler-works.md).  
  
### <a name="batchmarker"></a>BatchMarker  
 Le composant de pipeline BatchMarker prépare un échange pour son traitement par lot via la promotion des propriétés de contexte BatchId, ToBeBatched et ToBeRouted nécessaires au traitement d'un échange par lot. La manière dont le composant BatchMarker définit ces propriétés dépend du nombre d'accords de partenariat commercial abonnés à l'élément de lot.  
  
-   Si un seul accord est abonné à un élément de lot, le composant BatchMarker définit la propriété de contexte ToBeBatched sur True pour permettre à l'orchestration de traitement par lot de récupérer l'élément de lot.  
  
-   Si plusieurs accords sont abonnés à un élément de lot, le composant BatchMarker définit la propriété de contexte ToBeRouted sur True pour permettre à l'orchestration de routage de récupérer l'élément de lot. Il définit également la propriété de contexte BatchIds sur une liste d'ID de lot délimités par des espaces. L'orchestration de routage effectue ensuite une copie de l'élément de lot pour chaque ID de lot, puis définit la propriété ToBeBatched de chacune de ces copies sur True pour permettre à l'orchestration de traitement par lot de récupérer toutes les copies.  
  
 Le composant BatchMarker est inclus dans la dernière étape (résolution de l'accord de partenariat commercial) du pipeline EDIReceive. Tous les pipelines chargés du traitement des messages EDI doivent inclure le composant de pipeline BatchMarker.  
  
> [!NOTE]
>  Ce composant peut faire partie d'un pipeline de réception n'incluant pas le Désassembleur EDI, pour résoudre l'accord de partenariat commercial sans analyser le message EDI.  
  
 Vous pouvez utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le composant BatchMarker pour traiter les messages non-EDI par lot. Pour plus d’informations, consultez la section « Traitement de Non-EDI Messages dans le composant de BatchMarker » de [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages EDI dans BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)