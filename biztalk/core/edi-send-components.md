---
title: "Composants d’envoi EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce270db-a573-48b3-be15-0178a5b7785b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5520a0c1dd0a6ef7e42818314a9f87733aebcb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-send-components"></a>Composants d'envoi EDI
Le pipeline et les composants de pipeline décrits dans cette rubrique traitent les messages EDI de type autre que EDI/AS2. Pour plus d’informations sur l’envoi d’EDI/AS2 ou les messages EDI/AS2, consultez [composants d’envoi AS2](../core/as2-send-components.md). Notez que les composants d'envoi AS2 exécutent le traitement EDI en plus du traitement AS2.  
  
## <a name="edi-send-pipeline"></a>Pipeline d'envoi EDI  
 Le traitement d'envoi EDI est effectué dans le pipeline EDISend suivant. Ce pipeline est installé dans `Microsoft.BizTalk.Edi.EdiPipelines.dll` dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
 **Pipeline EDISend**  
  
 Ce pipeline génère et envoie des messages EDI. En revanche, il ne traite pas les messages EDI de type AS2 reçus via HTTP Le traitement des messages EDI codés AS2 est effectué par un pipeline AS2. Les pipelines d'envoi AS2 utilisent les mêmes composants que le pipeline EDI pour traiter les messages EDI.  
  
> [!NOTE]
>  L'exécution du pipeline EDISend à partir d'une orchestration n'est pas prise en charge.  
  
> [!NOTE]
>  Le pipeline AS2EDISend génère et envoie des messages EDI, via le transport AS2. Pour plus d’informations, consultez [composants d’envoi AS2](../core/as2-send-components.md).  
  
 Ce pipeline est formé du composant de pipeline Assembleur EDI :  
  
## <a name="edi-send-pipeline-component"></a>Composant de pipeline d'envoi EDI  
 Le pipeline EDISend utilise le composant de pipeline Assembleur EDI. Ce composant est installé dans `Microsoft.BizTalk.Edi.PipelineComponents.dll` dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]composants de Pipeline\\.  
  
 Le plus souvent, l'assembleur EDI traite les échanges EDI codés dans le pipeline EDISend. Pour plus d’informations sur la façon dont l’assembleur EDI traite les messages EDI, consultez [EDI assembleur fonctionnement](../core/how-the-edi-assembler-works.md).