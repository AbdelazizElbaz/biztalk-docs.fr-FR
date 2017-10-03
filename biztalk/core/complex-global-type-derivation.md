---
title: "Dérivation de Type Global complexe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbf429d0-64f4-4c43-a5f7-e8af050803b9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee4e6235af62b2c08c08382b897632d15e34e0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complex-global-type-derivation"></a>Dérivation de types globaux complexes
Il existe deux types d’héritages dans XSD : extension et restriction. L’Éditeur BizTalk fournit l’accès à ces fonctionnalités XSD à l’aide de deux suivants **enregistrement** propriétés de nœud :  
  
-   **Type de données de base**. cette propriété fournit la liste de tous les types complexes globaux et types simples disponibles en tant que type de données de base. Les types globaux complexes peuvent se trouver dans un même schéma ou dans n'importe quel schéma importé.  
  
-   **Derived By**. cette propriété sert à faire un choix entre la dérivation par extension et la dérivation par restriction. Cette propriété est automatiquement définie sur **Extension** lorsque vous définissez la **Base Data Type** propriété à n’importe quel type dans la liste. Si vous définissez cette propriété sur **(par défaut)**, tout type dans le **Base Data Type** propriété est supprimée, la désactivation de l’héritage pour le nœud.  
  
> [!NOTE]
>  Le **le Type de contenu** est également définie automatiquement à **ComplexContent** lorsque la dérivation par restriction ou extension est utilisée.  
  
 Cette section explique la dérivation de type complexe en utilisant les mécanismes d'extension et restriction de manière plus détaillée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Dérivation de Type complexe à l’aide du mécanisme d’Extension](../core/complex-type-derivation-using-the-extension-mechanism.md)  
  
-   [Dérivation de Type complexe à l’aide du mécanisme de Restriction](../core/complex-type-derivation-using-the-restriction-mechanism.md)