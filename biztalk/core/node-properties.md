---
title: "Propriétés du nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 366080f0-c21a-467d-8051-fd280264c5c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d41f0f3b0fe0b302a763629b8777669b54f6cc86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="node-properties"></a>Propriétés de nœud

## <a name="overview"></a>Vue d'ensemble
Dans l’Éditeur BizTalk, vous examinez et définissez les propriétés de nœud dans la fenêtre Propriétés de Visual Studio. À mesure que vous sélectionnez différents types de nœuds dans la vue de l'arborescence de schéma, différents ensembles de propriétés s'affichent dans la fenêtre Propriétés. Comme c'est la norme dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ces propriétés peuvent être affichées soit par catégories, soit par ordre alphabétique, sans indication de la catégorie. Les boutons standard situés vers le haut de la fenêtre Propriétés vous permettent de passer de l’un de ces paramètres à l’autre.  
  
 Les propriétés de nœud, en particulier lorsqu’elles affichent des valeurs autres que leurs valeurs par défaut, sont généralement représentées en langage XSD (XML Schema definition) comme des attributs et valeurs d'attributs associés à l'élément correspondant. Par exemple, lorsque les propriétés sont définies pour le **Min Occurs** et **Max Occurs** propriétés, qui sont disponibles pour plusieurs types de nœud différents, les valeurs qui sont définies sont utilisées comme valeurs de la **minOccurs** et **maxOccurs** attributs, respectivement, associé à l’élément qui représente le nœud pour lequel la **Min Occurs** et **Max Se produit** propriétés sont définies.  

## <a name="property-types"></a>Types de propriétés
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] référence du développeur contient une section de référence pour les propriétés de différents types de nœuds, organisés par catégorie et par ordre alphabétique. Les éléments suivants récapitulent les propriétés associées à chaque type de nœud :  
  
-   Propriétés de nœud de schéma
  
-   Propriétés d’un nœud Enregistrement
  
-   Propriétés d’un nœud Élément de champ
  
-   Propriétés d’un nœud Attribut de champ
  
-   Propriétés d’un nœud Groupe Séquence
  
-   Propriétés d’un nœud Groupe Choix 
  
-   Propriétés d’un nœud Groupe Tous
  
-   Propriétés d’un nœud Groupe Attribut
  
-   Propriétés d’un nœud Tout élément
  
-   Propriétés d’un nœud Tout attribut
  
-   Propriétés d’un nœud Équivalent
  
-   Propriétés d’un nœud enfant Équivalent

Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 **Propriétés de nœud-Liste alphabétique** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] contient toutes les rubriques de référence pour chaque propriété de nœud, certains d'entre eux s’appliquent à différents types de nœuds. Les rubriques de référence individuelles sont classées selon qu’il s’agit de propriétés de base s’appliquant à tous les types de schémas, ou de propriétés spécialisées associées à une extension de l’éditeur de schéma, telle que l’extension de fichier plat. Au sein de ces catégories, elles sont répertoriées par ordre alphabétique.  
  
 L'Éditeur BizTalk utilise la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour vous permettre d'examiner et de définir les propriétés des nœuds dans l'arborescence de schéma. Cette section décrit certaines caractéristiques de l’utilisation des propriétés dans la fenêtre Propriétés, y compris des considérations spéciales pour le **nom de nœud** propriété, une explication des interdépendances entre les propriétés, et Pour plus d’informations sur les longueurs maximales autorisées pour certaines propriétés ou les types de propriétés.  
  
 Le reste de cette section propose des informations supplémentaires sur des propriétés de nœuds particulières et d’autres informations s’appliquant à des propriétés de nœud de manière générale.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Propriété de nom de nœud](../core/node-name-property.md)  
  
-   [Interdépendances des propriétés](../core/property-interdependencies.md)  
  
-   [Propriétés de fichier plat supplémentaires](../core/additional-flat-file-properties.md)