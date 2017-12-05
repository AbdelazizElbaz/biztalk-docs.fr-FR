---
title: "Promotion des propriétés dans les composants de Pipeline désassembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, promoting properties
- XML Disassembler [pipeline component], properties
- pipeline components, properties
- promoting properties, disassembler pipeline components
- BizTalk Framework Assembler [pipeline component], properties
- Flat File Disassembler [pipeline component], properties
ms.assetid: aa37b308-8aa2-45f4-9383-aca4f2c925ce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c95c58dafe1f7f875232c5b65962e731334f16
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="property-promotion-in-disassembler-pipeline-components"></a><span data-ttu-id="1c4d2-102">Promotion des propriétés dans les composants de Pipeline désassembleur</span><span class="sxs-lookup"><span data-stu-id="1c4d2-102">Property Promotion in Disassembler Pipeline Components</span></span>
<span data-ttu-id="1c4d2-103">La promotion de propriétés est un processus par lequel une valeur de propriété est extraite d'un document XML à l'aide d'une expression XPath et placée dans le contexte du message afin de pouvoir être utilisée pour le routage des messages.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-103">Property promotion is a process by which a property value is extracted from an XML document by using an XPath expression and placed on the message context so that it can be used for message routing.</span></span>  
  
 <span data-ttu-id="1c4d2-104">Si une propriété promue n’a pas de valeur par défaut ou valeur fixe, le champ XML de cette propriété est manquant, et la propriété valider la Structure du Document est **False**, la propriété n’est pas promue.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-104">If a promoted property does not have a default or fixed value, the XML field for that property is missing, and the Validate Document Structure property is **False**, the property is not promoted.</span></span>  
  
 <span data-ttu-id="1c4d2-105">Un composant de pipeline personnalisé peut promouvoir des propriétés à valeurs multiples.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-105">A custom pipeline component can promote multivalued (that is, arrayed) properties.</span></span> <span data-ttu-id="1c4d2-106">Les messages qui contiennent des propriétés à valeurs multiples ne sont pris en charge que dans les scénarios de routage basé sur le contenu ; ils ne peuvent pas être acheminés vers des orchestrations ni être utilisés aux fins de suivi.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-106">Messages that contain multivalued properties are only supported in content-based routing (CBR) scenarios; they cannot be routed to orchestrations or be used for tracking purposes.</span></span>  
  
 <span data-ttu-id="1c4d2-107">Le Désassembleur XML ne promeut pas de valeurs par défaut ou fixes pour un élément vide qui possède une balise de fermeture.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-107">The XML Disassembler does not promote default or fixed values for an empty element if it has a closing tag.</span></span> <span data-ttu-id="1c4d2-108">Par exemple, \<field1\> n’est pas promue dans le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-108">For example, \<field1\> is not promoted in the following XML.</span></span>  
  
```  
<document>  
   <field1></field1>  
</document>  
```  
  
 <span data-ttu-id="1c4d2-109">Cependant, un élément vide sans balise de fermeture (comme dans l'exemple suivant) est promu.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-109">However, an empty element without a closing tag (as shown in the following example) is promoted.</span></span>  
  
```  
<document>  
   <field1/>  
</document>  
```  
  
 <span data-ttu-id="1c4d2-110">Lors de la lecture de données de date et d'heure au format UTC dans un document et de leur transfert dans la propriété de contexte, ce format est préservé.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-110">When reading datetime data from a document and placing it into the context property, if the data is in UTC format, that format is preserved.</span></span> <span data-ttu-id="1c4d2-111">Si les données de date et d'heure sont dans un format local+décalage, BizTalk Server convertit le format date/heure au format UTC résultant de l'ajout du décalage à l'heure locale.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-111">If the datetime data is in local+offset format, BizTalk Server converts the datetime format to the UTC format that results from adding the offset to the local time.</span></span> <span data-ttu-id="1c4d2-112">Si le format date/heure ne spécifie pas de fuseau horaire ni de format UTC, l'heure est supposée locale et convertie au format UTC sur la base du fuseau horaire actuel.</span><span class="sxs-lookup"><span data-stu-id="1c4d2-112">If the datetime format does not specify time zone or UTC format, the time is assumed to be local and is converted to UTC based on the current time zone.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4d2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c4d2-113">See Also</span></span>  
 <span data-ttu-id="1c4d2-114">[Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="1c4d2-114">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="1c4d2-115">Comment configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="1c4d2-115">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)