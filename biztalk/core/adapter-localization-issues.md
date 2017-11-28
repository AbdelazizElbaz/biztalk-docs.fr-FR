---
title: "Problèmes de localisation de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d200ce9-1a60-455b-88b0-6ec86092a786
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8862318547f2a7b8b4fa5dc7291e1673f1b9ba29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-localization-issues"></a><span data-ttu-id="a26a0-102">Problèmes de localisation de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="a26a0-102">Adapter Localization Issues</span></span>
<span data-ttu-id="a26a0-103">Les rubriques suivantes abordent les problèmes de localisation que vous pouvez rencontrer lors du développement d'adaptateurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a26a0-103">The following topics cover localization issues that you may encounter when developing custom adapters.</span></span>  
  
## <a name="xsd-issues"></a><span data-ttu-id="a26a0-104">Problèmes XSD</span><span class="sxs-lookup"><span data-stu-id="a26a0-104">XSD Issues</span></span>  
 <span data-ttu-id="a26a0-105">En utilisant l'infrastructure d'adaptateurs, les développeurs peuvent implémenter les pages de propriétés d'adaptateurs avec les schémas XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="a26a0-105">By using the Adapter Framework, adapter developers can implement adapter property pages with XML Schema Definition (XSD) schemas.</span></span>  
  
 <span data-ttu-id="a26a0-106">Si votre adaptateur ne possède aucune exigence de globalisation et de localisation, vous pouvez coder en dur la chaîne de schéma XSD à l’intérieur de la **IDynamicAdapterConfig : Getconfigschema** (fonction).</span><span class="sxs-lookup"><span data-stu-id="a26a0-106">If your adapter has no globalization or localization requirements, then you can hard code the XSD schema string inside the **IDynamicAdapterConfig:GetConfigSchema** function.</span></span>  
  
 <span data-ttu-id="a26a0-107">S'il comporte des contraintes de globalisation ou de localisation, vous pouvez implémenter le schéma XSD de l'une des deux manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="a26a0-107">If your adapter has globalization or localization requirements, you can implement the XSD schema in one of two ways.</span></span>  
  
-   <span data-ttu-id="a26a0-108">Utiliser des fichiers XSD distincts hors de la représentation binaire de conception.</span><span class="sxs-lookup"><span data-stu-id="a26a0-108">Use separate XSD files outside the design-time binary.</span></span> <span data-ttu-id="a26a0-109">Faire du texte entier du schéma une ressource de manifeste.</span><span class="sxs-lookup"><span data-stu-id="a26a0-109">Make the whole text of the schema a manifest resource.</span></span>  
  
-   <span data-ttu-id="a26a0-110">Remplacer dynamiquement la description et le nom des propriétés de la ressource :</span><span class="sxs-lookup"><span data-stu-id="a26a0-110">Dynamically replace the Property Names and Description from the resource:</span></span>  
  
    -   <span data-ttu-id="a26a0-111">Ajoutez un _locID à chaque élément à localiser.</span><span class="sxs-lookup"><span data-stu-id="a26a0-111">Add a _locID to each element that you want to localize.</span></span>  
  
    -   <span data-ttu-id="a26a0-112">Utilisez un xpath pour extraire tous les nœuds du schéma dotés d'un attribut _locID.</span><span class="sxs-lookup"><span data-stu-id="a26a0-112">Use an xpath to pull back all the nodes in the schema that have a _locID attribute.</span></span>  
  
    -   <span data-ttu-id="a26a0-113">Recherchez les ressources d'une chaîne indexée avec la valeur de _locID.</span><span class="sxs-lookup"><span data-stu-id="a26a0-113">Look up the resources for a string indexed by the value of the _locID.</span></span>  
  
    -   <span data-ttu-id="a26a0-114">Remplacez le texte du nœud par le résultat.</span><span class="sxs-lookup"><span data-stu-id="a26a0-114">Replace the node text with the result.</span></span>  
  
 <span data-ttu-id="a26a0-115">Voici un exemple de code pour la deuxième option :</span><span class="sxs-lookup"><span data-stu-id="a26a0-115">The following is sample code for the second option:</span></span>  
  
```  
string mySchema = GetSchemaFromResource(“mySchema”);  
string myLocalizedSchema = LocalizeSchemaDOM (mySchema, resourceManager);  
//  where…  
protected string GetSchemaFromResource (string name)  
{  
Assembly assem = this.GetType().Assembly;  
Stream stream = assem.GetManifestResourceStream(name);  
StreamReader reader = new StreamReader(stream);  
string schema = reader.ReadToEnd();  
return schema;  
}  
  
protected XmlDocument LocalizeSchemaDOM (string schema, ResourceManager resourceManager)  
{  
XmlDocument document = new XmlDocument();  
document.LoadXml(schema);  
XmlNodeList nodes = document.SelectNodes  
("/descendant::*[@_locID]");  
foreach (XmlNode node in nodes)  
{  
string locID = node.Attributes["_locID"].Value;  
node.InnerText = resourceManager.GetString(locID);  
}  
return document;  
}  
```