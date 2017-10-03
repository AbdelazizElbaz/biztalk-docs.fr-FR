---
title: "Accès aux en-têtes SOAP dans les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, pipelines
- SOAP headers, properties
- pipelines, SOAP headers
ms.assetid: a2fb074e-0fde-487e-a6ec-7e2b543b7c8b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e484b221df54f00b02f20ef89466fed6b99cd69d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-soap-headers-in-pipeline-components"></a>Accès aux en-têtes SOAP dans les composants de Pipeline
Vous pouvez accéder aux propriétés de contexte d'en-tête SOAP dans les composants de pipeline. Vous utilisez une combinaison de nom de la propriété de contexte et de l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.  
  
 L’exemple de code suivant obtient l’en-tête SOAP de demande dans un composant de pipeline de réception pour la propriété **OrigDest**:  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
   {  
   string stringVar = inmsg.Context.Read("OrigDest",    "http://schemas.microsoft.com/BizTalk/2003/SOAPHeader").ToString();  
   }  
   catch (Exception ex)  
   {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
   }  
return inmsg;  
}  
```  
  
 Pour plus d’informations sur les composants de pipeline, consultez [développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes SOAP avec les Services Web publiés](../core/soap-headers-with-published-web-services.md)