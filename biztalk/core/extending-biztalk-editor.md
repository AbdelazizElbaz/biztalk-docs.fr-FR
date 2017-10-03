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
# <a name="extending-biztalk-editor"></a>Extension de l’Éditeur BizTalk
L'Éditeur BizTalk est conçu pour autoriser les extensions prenant en charge les formats de message d'instance alternatifs. En fait, le format XML est le seul format intégré à l'Éditeur BizTalk. Même la prise en charge des formats de fichier plat, incluse dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], est implémentée en tant qu'extension de l'Éditeur BizTalk, ce qui est un bon exemple du type de fonctionnalités qui peuvent être ajoutées par de telles extensions.  
  
 En général, les extensions de l'Éditeur BizTalk conservent leurs données personnalisées sous forme d'annotations de langage XSD (XML Schema Definition) associées avec les éléments XSD correspondant aux nœuds de l'arborescence de schéma. Là encore, le large éventail d'annotations ajoutées par l'extension de fichier plat à l'Éditeur BizTalk illustre bien la manière dont les extensions de l'Éditeur BizTalk peuvent conserver leurs données personnalisées dans le schéma.  
  
 Les extensions de l'Éditeur BizTalk sont des assemblys .NET qui étendent la fonctionnalité de l'Éditeur BizTalk. Pour être identifié en tant qu’extension, un assembly doit avoir une classe qui implémente le **IExtension** d’interface et doit se trouver sous le dossier Developer Tools\Schema Editor Extensions dans le répertoire d’installation de produit.  
  
 Le développeur d'une extension doit faire en sorte que son assembly fasse référence au fichier Microsoft.BizTalk.SchemaEditor.Extensibility.dll, qui contient la définition de toutes les interfaces nécessaires à la présentation de la fonctionnalité étendue à l'Éditeur BizTalk. Ces interfaces sont définies sous la **Microsoft.BizTalk.SchemaEditor.Extensibility** espace de noms.  
  
 Le **IExtension** interface est le point d’entrée pour l’extension, à partir de laquelle l’Éditeur BizTalk accède à la fonctionnalité étendue, telles que les gestionnaires de propriétés, des vues personnalisées, la validation de schéma, génération d’instances natives et native validation de l’instance.  
  
 Un schéma donné peut avoir plusieurs extensions associées, mais une seule peut être définie comme norme à un moment donné ; Ce paramètre est défini dans le **Standard** propriété de la **schéma** nœud. L'extension actuellement définie comme norme est celle utilisée pour la validation et la génération d'instances natives ainsi que pour la validation de schémas.  
  
 Extensions peuvent être associées à un schéma donné en modifiant le **Extensions de l’éditeur de schéma** propriété de la **schéma** nœud. Les informations sur les extensions associées avec un schéma sont stockées dans le schéma lui-même, dans le **annotation** élément de la **schéma** élément, comme illustré dans le fragment XSD suivant.  
  
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
  
 Après avoir instancié l’objet d’extension, le framework appelle la **initialiser** méthode de la **IExtension** interface, en passant un **ITree** objet afin que l’extension peut accéder à plus d’informations sur l’arborescence du schéma. Par exemple, l’extension peut parcourir tous les nœuds enfants en accédant à la **ITree.RootNode** propriété.  
  
 Cette section explique de quelles manières une extension de l'Éditeur BizTalk peut s'intégrer à l'environnement de l'Éditeur BizTalk et se raccorder aux commandes existantes de l'Éditeur BizTalk.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Gestionnaires de propriétés](../core/property-managers.md)  
  
-   [Vues personnalisées](../core/custom-views.md)  
  
-   [Validation de schéma](../core/schema-validation1.md)  
  
-   [Validation de l’instance](../core/instance-validation.md)  
  
-   [Génération d’instance](../core/instance-generation.md)