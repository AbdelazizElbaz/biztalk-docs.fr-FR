---
title: "Utilisation des en-têtes SOAP des Messages WCF avec les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- WCF services, orchestrations
- WCF services, SOAP headers
ms.assetid: 31c01e35-a2a6-4ea9-bdf4-6d4311268dbe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e8248ec62e75a058566eefef1942e1f82061dbb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-orchestrations"></a>Utilisation des en-têtes SOAP des messages WCF à l'aide des orchestrations
Pour envoyer des en-têtes SOAP personnalisés avec des messages WCF sortants dans les orchestrations, vous utilisez la propriété de contexte **WCF. OutboundCustomHeaders**. Les adaptateurs WCF envoient les en-têtes SOAP personnalisés combinés aux en-têtes SOAP standard utilisés par l'infrastructure WCF pour les normes des services Web, telles que WS-Addressing, WS-Security et WS-AtomicTransaction. Lorsque vous utilisez la **OutboundCustomHeaders** propriété, la propriété doit avoir la \< **en-têtes** \> élément comme élément racine. Tous les en-têtes SOAP personnalisés doivent être placés dans le \< **en-têtes** \> élément. Si la valeur d’en-tête SOAP personnalisée est une chaîne vide, vous devez affecter \< **en-têtes**\>\</**en-têtes** \> ou \< **en-têtes** / \> à la **OutboundCustomHeaders** propriété.  
  
 Pour les orchestrations, les propriétés de contexte d'en-tête SOAP sont définies sur les chaînes qui contiennent des données XML. Vous pouvez définir celles-ci en utilisant l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** forme. Pour plus d’informations sur l’utilisation des en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).  
  
 L'exemple suivant (d'une forme Assignation du message ou Expression) montre la chaîne définissant la propriété de contexte :  
  
```  
outboundMessageInstance(WCF.OutboundCustomHeaders) = "<headers><Origination>Home</Origination><Destination>Work</Destination></headers>"  
```  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a>Création d'un élément XmlDocument pour définir des propriétés de contexte  
 Vous pouvez définir le **WCF. OutboundCustomHeaders** propriété de contexte en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte. Vous déclarez une variable de type **XMLDocument** et affecter les données XML.  
  
 L’exemple suivant illustre la déclaration d’une variable de type **XMLDocument** et affectation des données XML :  
  
```  
xmlDoc.LoadXml("<headers><Origination>Home</Origination><Destination>Work</Destination></headers>");  
```  
  
 L'exemple suivant illustre la configuration de la propriété de contexte :  
  
```  
RequestMessageInstance(WCF.OutboundCustomHeaders) = xmlDoc.OuterXml;  
```  
  
 Pour plus d’informations sur l’utilisation de l’éditeur d’Expression BizTalk, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md). Pour plus d’informations sur l’appel [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] des classes, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [En-têtes SOAP avec les Services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md)   
 [En-têtes SOAP avec les services WCF publiés](../core/soap-headers-with-published-wcf-services.md)