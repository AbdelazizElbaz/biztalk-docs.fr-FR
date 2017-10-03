---
title: "Pipeline d’envoi envoyer un lot conservé avec un document XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6765576a-134f-4856-911c-2f603b6479bd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14bd61538398bb11967cbbe750a4fadc016a5168
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-a-preserved-batch-with-an-xml-send-pipeline"></a>Envoi d'un lot conservé à l'aide d'un pipeline d'envoi XML
Normalement, un lot conservé est envoyé via un pipeline d'envoi EDI. Toutefois, vous pouvez également envoyer un lot conservé au moyen d'un pipeline d'envoi XML. Comme le lot conservé qui a été généré puis déposé dans la base de données MessageBox par le pipeline de réception EDI est au format XML, le pipeline d'envoi XML le transmet au format XML.  
  
 Pour envoyer un lot conservé à l'aide du pipeline d'envoi XML, vous devez déployer un projet avec le schéma de lot applicable et les schémas de document pour chaque type de message au sein de l'échange. Vous devez également modifier l'espace de noms du schéma de lot que vous déployez dans le projet. Si vous ne procédez pas de cette manière, l'espace de noms dans le fichier XML de lot conservé risque de différer de l'espace de noms dans le schéma de lot. Vous devez modifier l'espace de noms dans le schéma de lot comme indiqué dans le tableau suivant :  
  
|Pour ce type de codage :|Modifiez cet espace de noms dans le schéma de lot :|Sur l'espace de noms suivant :|  
|-----------------------------|------------------------------------------------|---------------------------------|  
|EDIFACT|`http://schemas.microsoft.com/Edi/Edifact`|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML`|  
|X12|`http://schemas.microsoft.com/Edi/X12_BatchSchema`|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`|  
  
 Ce problème ne concerne pas l'Assembleur EDI.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des lots EDI](../core/configuring-edi-batches.md)