---
title: "Conventions d’affectation de noms de schéma SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- naming conventions [schemas]
- schemas, naming conventions
ms.assetid: 3c1f2519-2575-4178-89c1-e97333c1e6bd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: beb792fe66e5806a186b0ffb946aa99f86a6a10c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-schema-naming-conventions"></a>Conventions d’affectation de noms de schéma SWIFT
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] inclut des schémas pour la société pour les messages FIN de télécommunication financières Interbank (SWIFT) dans le monde entier ont été créés à l’aide de l’Éditeur BizTalk. Ces schémas sont conformes aux conventions suivantes dans l’ensemble de :  
  
> [!NOTE]
>  Tous les schémas sont gérées. Pour afficher la version, ouvrez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur le schéma dans l’Explorateur de solutions. Avec la \<schéma > nœud sélectionné dans l’Éditeur BizTalk, dans le volet Propriétés défiler la propriété Version Standard.  
  
-   Le nom de chaque fichier de schéma d’échange est  **MT*xxx*.xsd **, où *xxx* est le type de message FIN.  
  
-   Le nom du fichier de stratégie principal associé pour chaque message est  **MT*xxx*_Master_Policy.xml**, et le nom correspondant dans le moteur de règles d’entreprise (BRE) est   **MT*xxx*_Master_Policy**, avec un nom de la liste de  **MT*xxx*_PolicyList **.  
  
-   Le nom du fichier de stratégie de validation associés pour chaque message est  **MT*xxx*_Validation_Policy.xml**, et le nom correspondant dans le moteur BRE est  **MT* xxx*_Validation_Policy**.  
  
-   Dans chaque schéma de message, le nom de la racine est  **SWIFT_CATEGORY*z*_MT*zxx*_Interchange **, où *z* est la catégorie du message (premier chiffre de type de message) et *zxx* est le type de message.  
  
-   L’espace de noms cible pour chaque schéma de message est  **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx***, où *z* est la catégorie de message (premier chiffre de type de message) et *zxx* est le type de message.  
  
-   Le type de document est  **MT*zxx***, où *zxx* est le type de message.  
  
-   Les noms des champs qui ne sont pas numérotées et sous-champs incluent les noms descriptifs. La première lettre de chaque mot en majuscules et les noms n’incluent pas un espace intermédiaire ou ponctuation entre les mots (par exemple, le nom serait **ServiceIdentifier**, et non **identificateur Service**) .  
  
-   Les étiquettes de séquences dans les messages sont conformes à la *Guide de référence SWIFT* (par exemple, **SequenceA**).  
  
-   Les étiquettes de numérotées SWIFT champs inclure un titre descriptif, suivi de la séquence (le cas échéant), suivi par le code numérique et le format de lettre facultative (par exemple, **Reference_A_20C**).  
  
-   S’il existe un choix de plusieurs formats pour un champ, l’étiquette du nœud est  **\<* choix*> **, puis chaque option est un champ numéroté (par exemple, **Date_A_98A** et **DateTime_A_98C**).  
  
-   Le nom de la définition d’élément de niveau le plus bas d’un champ se compose du nom du champ secondaire suivi **Type** (par exemple, **accountType** compte).  
  
 Autres espaces de noms dans le schéma de message sont les suivantes :  
  
-   prend = « http://www.w3.org/2001/XMLSchema ». Il s’agit de l’espace de noms du schéma XML de W3C par défaut.  
  
-   xmlns : b = « http://schemas.microsoft.com/BizTalk/2003 ». Il s’agit de l’espace de noms BizTalk par défaut.  
  
 Chaque schéma de message fait référence directement le type de base et des schémas de type de données courants.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)