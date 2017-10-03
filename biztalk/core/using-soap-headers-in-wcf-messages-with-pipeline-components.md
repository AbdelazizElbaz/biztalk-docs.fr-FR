---
title: "Utilisation des en-têtes SOAP des Messages WCF avec les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, SOAP headers
- SOAP headers, pipeline components
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: b02f2913-4948-4de9-bc59-73bab40aa1a0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf40cf5a81188dae0174199f16229daf61115796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-pipeline-components"></a>Utilisation des en-têtes SOAP des messages WCF à l'aide des composants de pipeline
Vous pouvez définir les en-têtes SOAP personnalisés avec les adaptateurs WCF dans les composants de pipeline. Vous utilisez une combinaison du nom de la propriété de contexte, **OutboundCustomHeaders**et l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**. Lorsque vous utilisez la **OutboundCustomHeaders** propriété, la propriété doit avoir la \< **en-têtes**> élément comme élément racine. Tous les en-têtes SOAP personnalisés doivent être placés dans le \< **en-têtes**> élément. Si la valeur d’en-tête SOAP personnalisée est une chaîne vide, vous devez affecter \< **en-têtes**>\</**en-têtes**> ou \< **en-têtes**/ > pour le **OutboundCustomHeaders** propriété. Pour plus d’informations sur l’utilisation des en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).  
  
 L’exemple de code suivant définit les en-têtes SOAP personnalisés dans un composant de pipeline d’envoi pour une propriété nommée **OutboundCustomHeaders**:  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<headers>  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </headers>";  
inmsg.Context.Write("OutboundCustomHeaders","http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties", stringVar);  
      }  
   catch (Exception ex)  
      {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
      }  
return inmsg;  
}  
```  
  
 Pour plus d’informations sur les composants de pipeline, consultez [développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md).  
  
> [!NOTE]
>  Vous ne devez pas définir les en-têtes SOAP standard utilisés par l'infrastructure WCF pour les normes des services Web, telles que WS-Addressing, WS-Security et WS-AtomicTransaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des en-têtes SOAP des Messages WCF avec les Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)   
 [En-têtes SOAP avec les Services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md)   
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [En-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md)