---
title: "Création de liens | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, links
- BizTalk Mapper, links
ms.assetid: e8596c50-62e9-40a7-ad61-29cbdb4f4fc9
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87570b82dc63a02c629e0fc024c2e44d57df1401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-links"></a>Création de liens
Le Mappeur BizTalk permet d’automatiser certains éléments participant à la création des liens. La création de liens simple s’apparente aux types de données simples. Il existe des formes plus sophistiquées de création de liens qui ressemblent davantage à l’attribution de structure dans un langage de programmation. Une création de liens simple spécifie, par exemple, combien d’éléments de données multiples doivent être déplacés de messages d’instance d’entrée vers les messages d’instance de sortie correspondants.  
  
 Vous pouvez créer des liens à l’aide des méthodes suivantes :  
  
-   **Création de liens simple.** dans la création de liens simple, vous produisez un lien par déplacement. Le déplacement par glissement d’un champ du schéma source vers un champ du schéma de destination entraîne la création d’un élément ou d’un attribut dans un message d’instance de sortie et insère la valeur de l’élément ou de l’attribut dans le message. Ces liens peuvent être créés directement entre **enregistrement** et **champ** nœuds dans le schéma source et de destination, ou ils peuvent inclure un ou plusieurs fonctoids dans un chemin d’accès du lien entre **enregistrement**et **champ** nœuds dans les schémas source et de destination.  
  
-   **Liens de type structure.** Lors de la création de liens de type structure, vous produisez plusieurs liens simples en même temps entre **enregistrement** et **champ** nœuds dans les schémas source et de destination qui ont la même structure relative. Pour utiliser la création de liens de type structure, la structure des parties pertinentes des deux schémas doit être identique. Pour plus d’informations sur la configuration des liens de type structure, consultez [comment lier des enregistrements automatiquement](../core/how-to-link-records-automatically.md).  
  
-   **Liens de mise en correspondance de nom.** Lorsque vous utilisez cette méthode, vous créez plusieurs liens simples en même temps entre **enregistrement** et **champ** nœuds dans les schémas source et de destination selon les noms de la **enregistrements** et **champ** nœuds. Pour utiliser la création de liens de type correspondance des noms, la structure des schémas source et de destination doit être très similaire mais pas rigoureusement identique. Pour plus d’informations sur la configuration des liaisons de correspondance de noms, consultez [comment lier des enregistrements automatiquement](../core/how-to-link-records-automatically.md).  
  
    > [!NOTE]
    >  Vous pouvez également voir [comment gérer des liens existants](../core/how-to-manage-existing-links.md) pour plus d’informations sur la modification les liaisons existantes.  
  
## <a name="preserving-whitespace-in-a-link"></a>Conservation des espaces dans un lien  
 Vous devez écrire un script personnalisé si vous souhaitez conserver les espaces figurant dans un élément source lorsque vous effectuez un mappage sur un fonctoid ou un élément cible.  
  
 Les espaces ne sont pas conservés que ce soit dans le mappeur ou dans le système runtime. Le Mappeur et le système runtime utilisent l'objet BTSXslTransform.Transform qui gère la transformation de messages volumineux et s'appuie sur XmlReader pour naviguer à l'aide du modèle de données XPath.  
  
 Afin de conserver les espaces, vous pouvez écrire un script personnalisé qui renvoie le nombre d'espaces requis. Par exemple, le code ci-après renvoie toujours une chaîne comprenant 5 espaces :  
  
```  
public string Whitespace(string param1)  
{  
  return "     ";  
}  
```  
  
 Si vous liez un élément source à l'entrée de ce script et un élément cible en tant qu'élément sortant, l'élément sortant comprendra 5 caractères une fois le mappage exécuté.  
  
> [!NOTE]
>  Si vous affichez la sortie à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l’élément apparaîtra vide. En effet, la visionneuse XML considère les éléments contenant des espaces comme des éléments vides. Pour afficher l’espace blanc, avec le bouton droit de la vue XML et sélectionnez **afficher la Source**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : modifier les propriétés de lien](../core/how-to-edit-link-properties.md)