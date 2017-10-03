---
title: "Extension de l’Éditeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77c93ab2-0a9b-4c9d-81e5-3871fc8e6e13
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8e4f574e652420ae11410e52268a199639cf6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-biztalk-editor"></a><span data-ttu-id="8ebd0-102">Extension de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8ebd0-102">Extending BizTalk Editor</span></span>
<span data-ttu-id="8ebd0-103">L'Éditeur BizTalk est conçu pour autoriser les extensions prenant en charge les formats de message d'instance alternatifs.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-103">BizTalk Editor is designed to allow extensions that support alternative instance message formats.</span></span> <span data-ttu-id="8ebd0-104">En fait, le format XML est le seul format intégré à l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-104">In fact, the XML format is the only format that is built into BizTalk Editor.</span></span> <span data-ttu-id="8ebd0-105">Même la prise en charge des formats de fichier plat, incluse dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], est implémentée en tant qu'extension de l'Éditeur BizTalk, ce qui est un bon exemple du type de fonctionnalités qui peuvent être ajoutées par de telles extensions.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-105">Even support for flat file formats, which is included in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], is implemented as a BizTalk Editor extension, thereby serving as a good example of the type of functionality that can be added by such extensions.</span></span>  
  
 <span data-ttu-id="8ebd0-106">En général, les extensions de l'Éditeur BizTalk conservent leurs données personnalisées sous forme d'annotations de langage XSD (XML Schema Definition) associées avec les éléments XSD correspondant aux nœuds de l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-106">In general, BizTalk Editor extensions persist their custom data as XML Schema definition (XSD) language annotations associated with the XSD elements that correspond to the nodes in the schema tree.</span></span> <span data-ttu-id="8ebd0-107">Là encore, le large éventail d'annotations ajoutées par l'extension de fichier plat à l'Éditeur BizTalk illustre bien la manière dont les extensions de l'Éditeur BizTalk peuvent conserver leurs données personnalisées dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-107">Again, the extensive set of annotations added by the Flat File Extension to BizTalk Editor serves as a good example of the way in which BizTalk Editor extensions can persist their custom data in the schema.</span></span>  
  
 <span data-ttu-id="8ebd0-108">Les extensions de l'Éditeur BizTalk sont des assemblys .NET qui étendent la fonctionnalité de l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-108">BizTalk Editor extensions are .NET assemblies that extend the functionality of BizTalk Editor.</span></span> <span data-ttu-id="8ebd0-109">Pour être identifié en tant qu’extension, un assembly doit avoir une classe qui implémente le **IExtension** d’interface et doit se trouver sous le dossier Developer Tools\Schema Editor Extensions dans le répertoire d’installation de produit.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-109">To be identified as an extension, an assembly must have one class that implements the **IExtension** interface, and must be located under the Developer Tools\Schema Editor Extensions folder in the product installation directory.</span></span>  
  
 <span data-ttu-id="8ebd0-110">Le développeur d'une extension doit faire en sorte que son assembly fasse référence au fichier Microsoft.BizTalk.SchemaEditor.Extensibility.dll, qui contient la définition de toutes les interfaces nécessaires à la présentation de la fonctionnalité étendue à l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-110">The developer of an extension must have its assembly reference the Microsoft.BizTalk.SchemaEditor.Extensibility.dll, which contains the definition of all the interfaces needed for exposing extended functionality to BizTalk Editor.</span></span> <span data-ttu-id="8ebd0-111">Ces interfaces sont définies sous la **Microsoft.BizTalk.SchemaEditor.Extensibility** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-111">Those interfaces are defined under the **Microsoft.BizTalk.SchemaEditor.Extensibility** namespace.</span></span>  
  
 <span data-ttu-id="8ebd0-112">Le **IExtension** interface est le point d’entrée pour l’extension, à partir de laquelle l’Éditeur BizTalk accède à la fonctionnalité étendue, telles que les gestionnaires de propriétés, des vues personnalisées, la validation de schéma, génération d’instances natives et native validation de l’instance.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-112">The **IExtension** interface is the entry point for the extension, from which BizTalk Editor accesses the extended functionality, such as property managers, custom views, schema validation, native instance generation, and native instance validation.</span></span>  
  
 <span data-ttu-id="8ebd0-113">Un schéma donné peut avoir plusieurs extensions associées, mais une seule peut être définie comme norme à un moment donné ; Ce paramètre est défini dans le **Standard** propriété de la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-113">A given schema can have multiple extensions associated with it, but only one can be set as the standard at a given time; this is set in the **Standard** property of the **Schema** node.</span></span> <span data-ttu-id="8ebd0-114">L'extension actuellement définie comme norme est celle utilisée pour la validation et la génération d'instances natives ainsi que pour la validation de schémas.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-114">The extension currently set as the standard is the one used for native instance generation and validation, and for schema validation.</span></span>  
  
 <span data-ttu-id="8ebd0-115">Extensions peuvent être associées à un schéma donné en modifiant le **Extensions de l’éditeur de schéma** propriété de la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-115">Extensions can be associated with a given schema by editing the **Schema Editor Extensions** property of the **Schema** node.</span></span> <span data-ttu-id="8ebd0-116">Les informations sur les extensions associées avec un schéma sont stockées dans le schéma lui-même, dans le **annotation** élément de la **schéma** élément, comme illustré dans le fragment XSD suivant.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-116">The information about the extensions associated with a schema is stored in the schema itself, within the **annotation** element of the **schema** element, as illustrated in the following XSD fragment.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema11"  
        xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
        targetNamespace="http://BizTalk_Server_Project1.Schema11"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <schemaEditorExtension:schemaInfo namespaceAlias="b"  
                extensionClass="Microsoft.BizTalk.FlatFileExtension.FlatFileExtension"  
                standardName="Flat File"  
                xmlns:schemaEditorExtension="http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions" />  
            <b:schemaInfo schema_type="document" root_reference="Root"  
                is_receipt="no" schema_name="abc"  
                standard="Flat File"  
                count_positions_by_byte="false" />   
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="Root">  
        ...  
  
```  
  
 <span data-ttu-id="8ebd0-117">Après avoir instancié l’objet d’extension, le framework appelle la **initialiser** méthode de la **IExtension** interface, en passant un **ITree** objet afin que l’extension peut accéder à plus d’informations sur l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-117">After instantiating the extension object, the framework invokes the **Initialize** method of the **IExtension** interface, passing an **ITree** object so that the extension can access information about the schema tree.</span></span> <span data-ttu-id="8ebd0-118">Par exemple, l’extension peut parcourir tous les nœuds enfants en accédant à la **ITree.RootNode** propriété.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-118">For example, the extension could traverse all child nodes by accessing the **ITree.RootNode** property.</span></span>  
  
 <span data-ttu-id="8ebd0-119">Cette section explique de quelles manières une extension de l'Éditeur BizTalk peut s'intégrer à l'environnement de l'Éditeur BizTalk et se raccorder aux commandes existantes de l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ebd0-119">This section describes the ways in which a BizTalk Editor extension can integrate into the BizTalk Editor environment and hook itself into existing BizTalk Editor commands.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ebd0-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8ebd0-120">In This Section</span></span>  
  
-   [<span data-ttu-id="8ebd0-121">Gestionnaires de propriétés</span><span class="sxs-lookup"><span data-stu-id="8ebd0-121">Property Managers</span></span>](../core/property-managers.md)  
  
-   [<span data-ttu-id="8ebd0-122">Vues personnalisées</span><span class="sxs-lookup"><span data-stu-id="8ebd0-122">Custom Views</span></span>](../core/custom-views.md)  
  
-   [<span data-ttu-id="8ebd0-123">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="8ebd0-123">Schema Validation</span></span>](../core/schema-validation1.md)  
  
-   [<span data-ttu-id="8ebd0-124">Validation de l’instance</span><span class="sxs-lookup"><span data-stu-id="8ebd0-124">Instance Validation</span></span>](../core/instance-validation.md)  
  
-   [<span data-ttu-id="8ebd0-125">Génération d’instance</span><span class="sxs-lookup"><span data-stu-id="8ebd0-125">Instance Generation</span></span>](../core/instance-generation.md)