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
# <a name="adapter-localization-issues"></a>Problèmes de localisation de l’adaptateur
Les rubriques suivantes abordent les problèmes de localisation que vous pouvez rencontrer lors du développement d'adaptateurs personnalisés.  
  
## <a name="xsd-issues"></a>Problèmes XSD  
 En utilisant l'infrastructure d'adaptateurs, les développeurs peuvent implémenter les pages de propriétés d'adaptateurs avec les schémas XSD (XML Schema Definition).  
  
 Si votre adaptateur ne possède aucune exigence de globalisation et de localisation, vous pouvez coder en dur la chaîne de schéma XSD à l’intérieur de la **IDynamicAdapterConfig : Getconfigschema** (fonction).  
  
 S'il comporte des contraintes de globalisation ou de localisation, vous pouvez implémenter le schéma XSD de l'une des deux manières suivantes.  
  
-   Utiliser des fichiers XSD distincts hors de la représentation binaire de conception. Faire du texte entier du schéma une ressource de manifeste.  
  
-   Remplacer dynamiquement la description et le nom des propriétés de la ressource :  
  
    -   Ajoutez un _locID à chaque élément à localiser.  
  
    -   Utilisez un xpath pour extraire tous les nœuds du schéma dotés d'un attribut _locID.  
  
    -   Recherchez les ressources d'une chaîne indexée avec la valeur de _locID.  
  
    -   Remplacez le texte du nœud par le résultat.  
  
 Voici un exemple de code pour la deuxième option :  
  
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