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
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="distinguished-fields-in-disassembler-pipeline-components"></a>Composants de Pipeline désassembleur les champs distinctifs
Les champs distinctifs définis dans un schéma sont consignés selon le format suivant dans le contexte de message par les composants de pipeline Désassembleur XML, Désassembleur BizTalk Framework ou Désassembleur de fichier plat :  
  
 *nom utilisé* est le champ distinctif dans XPath  
  
 *URI de l’espace de noms* est « http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields »  
  
 La valeur de la propriété est la **System.String** valeur extraite du document XML à l’aide de XPath spécifié.  
  
 Le schéma d'exemple suivant comporte un champ distinctif Price.  
  
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
  
 Pour l'instance de document  
  
```  
<PO>  
            <Item>Bolt</Item>  
            <Price>10</Price>  
<PO>  
```  
  
 le Désassembleur XML consigne un champ distinctif dans un contexte de message de la façon suivante :  
  
 Nom de la propriété du contexte : «/*[local-name()='PO'et namespace-uri()='http://SendHtmlMessage.PO']/\*[local-name()=«Price»et namespace-uri()='']»  
  
 Namespace de la propriété : http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields  
  
 Valeur de la propriété : 10  
  
> [!NOTE]
>  Si la taille de l'une des valeurs des éléments des documents XML dépasse 85 Ko, les performances de traitement de ces documents risquent de se dégrader.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)