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
# <a name="modifying-2xml-schemas-to-work-with-biztalk-editor"></a><span data-ttu-id="08d65-102">Modification de schémas XML de 2 pour travailler avec l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="08d65-102">Modifying 2.XML Schemas to Work with BizTalk Editor</span></span>
<span data-ttu-id="08d65-103">Schémas XML de 2 HL7 nécessitent une modification pour fonctionner correctement avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="08d65-103">HL7 2.XML schemas require modification to work properly with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span> <span data-ttu-id="08d65-104">La liste suivante décrit comment modifier HL7 V2. Schémas XML pour vous permettre de les utiliser avec l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="08d65-104">The following describes how to modify HL7 V2.XML schemas to enable you to use them with BizTalk Editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08d65-105">L’outil Update2XMLSchema exécute ces étapes automatiquement.</span><span class="sxs-lookup"><span data-stu-id="08d65-105">The Update2XMLSchema tool performs these steps automatically.</span></span> <span data-ttu-id="08d65-106">Consultez [Update2XMLSchema outil](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="08d65-106">See [Update2XMLSchema Tool](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md) for more information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08d65-107">Le **nillable** attribut peut se produire dans un schéma sur un élément.</span><span class="sxs-lookup"><span data-stu-id="08d65-107">The **nillable** attribute can occur in a schema on an element.</span></span> <span data-ttu-id="08d65-108">Si la valeur **true**, il indique que l’instance de l’élément parent peut avoir un **xsi : nil = « true »** attribut.</span><span class="sxs-lookup"><span data-stu-id="08d65-108">If set to **true**, it indicates that the instance of the parent element can have an **xsi:nil="true"** attribute.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="08d65-109">ignore cet attribut lors de la compilation et pendant l’analyse/sérialisation.</span><span class="sxs-lookup"><span data-stu-id="08d65-109"> ignores this attribute during compilation and during parsing/serialization.</span></span>  
  
### <a name="to-modify-2xml-schemas"></a><span data-ttu-id="08d65-110">Pour modifier des schémas XML de 2.</span><span class="sxs-lookup"><span data-stu-id="08d65-110">To modify 2.XML schemas</span></span>  
  
1.  <span data-ttu-id="08d65-111">Dans le fichier fields.xsd, vous devez supprimer les instances de **importer** et remplacez-les par **incluent**.</span><span class="sxs-lookup"><span data-stu-id="08d65-111">In the fields.xsd file, you must remove instances of **import** and replace them with **include**.</span></span> <span data-ttu-id="08d65-112">Par exemple, recherchez dans le fichier fields.xsd pour le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="08d65-112">For example, search the fields.xsd file for the following text:</span></span>  
  
    ```  
    <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
    ```  
  
     <span data-ttu-id="08d65-113">Et modifiez le texte comme suit :</span><span class="sxs-lookup"><span data-stu-id="08d65-113">And change the text to the following:</span></span>  
  
    ```  
    <xsd:include schemaLocation="datatypes.xsd"/>   
    ```  
  
2.  <span data-ttu-id="08d65-114">Dans le fichier segments.xsd, vous devez supprimer toutes les instances des lignes qui contiennent le texte processContents = « lax ».</span><span class="sxs-lookup"><span data-stu-id="08d65-114">In the segments.xsd file, you must remove all instances of the lines that contain the text processContents="lax".</span></span> <span data-ttu-id="08d65-115">Par exemple, recherchez dans le fichier segments.xsd pour le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="08d65-115">For example, search the segments.xsd file for the following text:</span></span>  
  
    ```  
    <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
    ```  
  
     <span data-ttu-id="08d65-116">And</span><span class="sxs-lookup"><span data-stu-id="08d65-116">And</span></span>  
  
    ```  
    <xsd:any processContents="lax" namespace="##any"/>   
    ```  
  
     <span data-ttu-id="08d65-117">Et supprimer des lignes.</span><span class="sxs-lookup"><span data-stu-id="08d65-117">And remove those lines.</span></span>  
  
3.  <span data-ttu-id="08d65-118">Pour tous les schémas sous la balise XSD, vous devez ajouter la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="08d65-118">For all schemas, under the tag xsd:schema, you must add the following line:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="08d65-119">N’ajoutez pas cette ligne si vous avez ajouté le schéma à l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] car [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] fait automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="08d65-119">Do not add this line if you have added the schema using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] because [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does this for you automatically.</span></span>  
  
    ```  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    ```  
  
     <span data-ttu-id="08d65-120">Par exemple, dans le fichier ADT_A01.xsd, recherchez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="08d65-120">For example, in the file ADT_A01.xsd, search for the following text:</span></span>  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns="urn:hl7-org:v2xml"   
     targetNamespace="urn:hl7-org:v2xml">   
    ```  
  
     <span data-ttu-id="08d65-121">Et modifiez le texte comme suit :</span><span class="sxs-lookup"><span data-stu-id="08d65-121">And change the text to the following:</span></span>  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="urn:hl7-org:v2xml"  
     targetNamespace="urn:hl7-org:v2xml"  
     xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
    ```  
  
4.  <span data-ttu-id="08d65-122">Pour tous les schémas, vous devez ajouter une référence de racine.</span><span class="sxs-lookup"><span data-stu-id="08d65-122">For all schemas, you must add a root reference.</span></span> <span data-ttu-id="08d65-123">Par exemple, dans le fichier ADT_A01.xsd, recherchez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="08d65-123">For example, in the ADT_A01.xsd file, search for the following text:</span></span>  
  
    ```  
    <xsd:include schemaLocation="segments.xsd" />   
    ```  
  
     <span data-ttu-id="08d65-124">Et remplacez le texte par :</span><span class="sxs-lookup"><span data-stu-id="08d65-124">And change the text to:</span></span>  
  
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
    >  <span data-ttu-id="08d65-125">Si vous utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous pouvez ajouter cette root_reference à l’aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="08d65-125">If you are using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can add this root_reference by using the following procedure.</span></span>  
  
### <a name="to-add-the-root-reference"></a><span data-ttu-id="08d65-126">Pour ajouter la référence de racine</span><span class="sxs-lookup"><span data-stu-id="08d65-126">To add the root reference</span></span>  
  
1.  <span data-ttu-id="08d65-127">Dans l’Explorateur de solutions, double-cliquez sur le schéma que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="08d65-127">In Solution Explorer, double-click the schema you want to edit.</span></span>  
  
2.  <span data-ttu-id="08d65-128">Dans le volet Propriétés, faites défiler jusqu'à la propriété **root_reference**, dans la liste déroulante, cliquez sur la propriété portant le même nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="08d65-128">In the Properties pane, scroll down to the property **root_reference**, and from the drop-down list, click the property with the same schema name.</span></span>  
  
3.  <span data-ttu-id="08d65-129">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="08d65-129">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d65-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08d65-130">See Also</span></span>  
 [<span data-ttu-id="08d65-131">Utilisation de schémas XML de 2 HL7</span><span class="sxs-lookup"><span data-stu-id="08d65-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)