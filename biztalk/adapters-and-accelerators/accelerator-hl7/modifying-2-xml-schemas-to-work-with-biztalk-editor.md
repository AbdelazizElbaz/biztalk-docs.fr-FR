---
title: "Modification de schémas XML de 2 pour une utilisation avec l’Éditeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, modifying
- modifying, 2.XML schemas
ms.assetid: 07316826-84b6-494e-81b9-f64a3d46ffb0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf68f39e4e4c36587b889490b28541e5a690ed05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="modifying-2xml-schemas-to-work-with-biztalk-editor"></a>Modification de schémas XML de 2 pour travailler avec l’Éditeur BizTalk
Schémas XML de 2 HL7 nécessitent une modification pour fonctionner correctement avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]). La liste suivante décrit comment modifier HL7 V2. Schémas XML pour vous permettre de les utiliser avec l’Éditeur BizTalk.  
  
> [!IMPORTANT]
>  L’outil Update2XMLSchema exécute ces étapes automatiquement. Consultez [Update2XMLSchema outil](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md) pour plus d’informations.  
  
> [!NOTE]
>  Le **nillable** attribut peut se produire dans un schéma sur un élément. Si la valeur **true**, il indique que l’instance de l’élément parent peut avoir un **xsi : nil = « true »** attribut. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ignore cet attribut lors de la compilation et pendant l’analyse/sérialisation.  
  
### <a name="to-modify-2xml-schemas"></a>Pour modifier des schémas XML de 2.  
  
1.  Dans le fichier fields.xsd, vous devez supprimer les instances de **importer** et remplacez-les par **incluent**. Par exemple, recherchez dans le fichier fields.xsd pour le texte suivant :  
  
    ```  
    <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
    ```  
  
     Et modifiez le texte comme suit :  
  
    ```  
    <xsd:include schemaLocation="datatypes.xsd"/>   
    ```  
  
2.  Dans le fichier segments.xsd, vous devez supprimer toutes les instances des lignes qui contiennent le texte processContents = « lax ». Par exemple, recherchez dans le fichier segments.xsd pour le texte suivant :  
  
    ```  
    <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
    ```  
  
     And  
  
    ```  
    <xsd:any processContents="lax" namespace="##any"/>   
    ```  
  
     Et supprimer des lignes.  
  
3.  Pour tous les schémas sous la balise XSD, vous devez ajouter la ligne suivante :  
  
    > [!NOTE]
    >  N’ajoutez pas cette ligne si vous avez ajouté le schéma à l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] car [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] fait automatiquement pour vous.  
  
    ```  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    ```  
  
     Par exemple, dans le fichier ADT_A01.xsd, recherchez le texte suivant :  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns="urn:hl7-org:v2xml"   
     targetNamespace="urn:hl7-org:v2xml">   
    ```  
  
     Et modifiez le texte comme suit :  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="urn:hl7-org:v2xml"  
     targetNamespace="urn:hl7-org:v2xml"  
     xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
    ```  
  
4.  Pour tous les schémas, vous devez ajouter une référence de racine. Par exemple, dans le fichier ADT_A01.xsd, recherchez le texte suivant :  
  
    ```  
    <xsd:include schemaLocation="segments.xsd" />   
    ```  
  
     Et remplacez le texte par :  
  
    ```  
    <xsd:include schemaLocation="segments.xsd" />  
    <xsd:annotation>   
      <xsd:appinfo>   
        <schemaInfo root_reference="ADT_A01"  
     xmlns="http://schemas.microsoft.com/BizTalk/2003" />   
      </xsd:appinfo>   
    </xsd:annotation>   
    ```  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous pouvez ajouter cette root_reference à l’aide de la procédure suivante.  
  
### <a name="to-add-the-root-reference"></a>Pour ajouter la référence de racine  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le schéma que vous souhaitez modifier.  
  
2.  Dans le volet Propriétés, faites défiler jusqu'à la propriété **root_reference**, dans la liste déroulante, cliquez sur la propriété portant le même nom de schéma.  
  
3.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)