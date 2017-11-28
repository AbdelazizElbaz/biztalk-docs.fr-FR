---
title: "Composants de Pipeline désassembleur les champs distinctifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, distinquished fields
- Flat File Disassembler [pipeline component], distinquished fields
- BizTalk Framework Disassembler [pipeline component], distinquished fields
- XML Disassembler [pipeline component], distinquished fields
ms.assetid: 7e51d2fe-0004-4a7b-9055-bd41e8a4b7ab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64e4c8f15d167f5343089c11b92b0f373aa45576
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="distinguished-fields-in-disassembler-pipeline-components"></a><span data-ttu-id="ca902-102">Composants de Pipeline désassembleur les champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="ca902-102">Distinguished Fields in Disassembler Pipeline Components</span></span>
<span data-ttu-id="ca902-103">Les champs distinctifs définis dans un schéma sont consignés selon le format suivant dans le contexte de message par les composants de pipeline Désassembleur XML, Désassembleur BizTalk Framework ou Désassembleur de fichier plat :</span><span class="sxs-lookup"><span data-stu-id="ca902-103">Distinguished fields defined in a schema are written to the message context by the XML Disassembler, BizTalk Framework Disassembler, or Flat File Disassembler pipeline components in the following format:</span></span>  
  
 <span data-ttu-id="ca902-104">*nom utilisé* est le champ distinctif dans XPath</span><span class="sxs-lookup"><span data-stu-id="ca902-104">*name used* is the distinguished field in XPath</span></span>  
  
 <span data-ttu-id="ca902-105">*URI de l’espace de noms* est « http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields »</span><span class="sxs-lookup"><span data-stu-id="ca902-105">*namespace URI* is "http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields"</span></span>  
  
 <span data-ttu-id="ca902-106">La valeur de la propriété est la **System.String** valeur extraite du document XML à l’aide de XPath spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca902-106">The value of the property is the **System.String** value extracted from the XML document using specified XPath.</span></span>  
  
 <span data-ttu-id="ca902-107">Le schéma d'exemple suivant comporte un champ distinctif Price.</span><span class="sxs-lookup"><span data-stu-id="ca902-107">The following example schema has a distinguished field Price.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://SendHtmlMessage.PO" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://SendHtmlMessage.PO xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="PO">  
      <xs:annotation>  
         <xs:appinfo>  
            <b:properties>  
               <b:property distinguished="true" xpath="/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/*[local-  
               name()='Price' and namespace-uri()='']" />   
            </b:properties>  
         </xs:appinfo>  
      </xs:annotation>  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="Item" type="xs:string" />   
            <xs:element name="Price" type="xs:string" />   
         </xs:sequence>  
      </xs:complexType>  
   </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="ca902-108">Pour l'instance de document</span><span class="sxs-lookup"><span data-stu-id="ca902-108">For the document instance</span></span>  
  
```  
<PO>  
            <Item>Bolt</Item>  
            <Price>10</Price>  
<PO>  
```  
  
 <span data-ttu-id="ca902-109">le Désassembleur XML consigne un champ distinctif dans un contexte de message de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ca902-109">the XML Disassembler writes a distinguished field on a message context as follows:</span></span>  
  
 <span data-ttu-id="ca902-110">Nom de la propriété du contexte : «/*[local-name()='PO'et namespace-uri()='http://SendHtmlMessage.PO']/\*[local-name()=«Price»et namespace-uri()='']»</span><span class="sxs-lookup"><span data-stu-id="ca902-110">Name of the property on the context: "/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/\*[local-name()='Price' and namespace-uri()='']"</span></span>  
  
 <span data-ttu-id="ca902-111">Namespace de la propriété : http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields</span><span class="sxs-lookup"><span data-stu-id="ca902-111">Namespace of the property: http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields</span></span>  
  
 <span data-ttu-id="ca902-112">Valeur de la propriété : 10</span><span class="sxs-lookup"><span data-stu-id="ca902-112">Value of the property: 10</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca902-113">Si la taille de l'une des valeurs des éléments des documents XML dépasse 85 Ko, les performances de traitement de ces documents risquent de se dégrader.</span><span class="sxs-lookup"><span data-stu-id="ca902-113">If the size of any XML document element values exceeds 85KB, a degradation in the performance of processing those documents may occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca902-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca902-114">See Also</span></span>  
 <span data-ttu-id="ca902-115">[Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="ca902-115">[Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="ca902-116">Comment configurer le composant de Pipeline de désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="ca902-116">How to Configure the Flat File Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)