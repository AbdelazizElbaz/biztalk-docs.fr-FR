---
title: "À l’aide de l’Explorateur de faits | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, Facts Explorer
- business rules, vocabularies
- business rules, schemas
- business rules, databases
- business rules, .NET classes
- Facts Explorer [Business Rule Composer]
ms.assetid: ee125eb1-d5b9-4121-8a25-fcb7a640570e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4c84b01625bb1566d02c1679bfadd0100b7b406
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-facts-explorer"></a>À l’aide de l’Explorateur de faits
L’Explorateur de faits contient quatre onglets : **vocabulaires**, **schémas XML**, **bases de données**, et **Classes .NET**.  
  
## <a name="vocabularies-tab"></a>Onglet Vocabulaires  
 Utilisez le **vocabulaires** onglet dans l’Explorateur de faits pour gérer les définitions et les versions de vocabulaire.  
  
 Utilisez le menu contextuel pour accéder aux options ci-dessous.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Ajouter un nouveau vocabulaire**|Créer un vocabulaire.|  
|**Ajouter une nouvelle Version**|Créer une version vide du vocabulaire sélectionné. Vous pouvez copier des définitions provenant d'autres versions et les coller dans la nouvelle version.|  
|**Coller une Version de vocabulaire**|Dans le vocabulaire sélectionné, coller, en tant que nouvelle version, le contenu d'une version de vocabulaire préalablement copiée.|  
|**Delete**|Supprimer le vocabulaire sélectionné ainsi que toutes ses versions.|  
|**Ajouter une nouvelle définition**|Lancer l'Assistant Définition de vocabulaire pour créer une définition dans la version de vocabulaire sélectionnée.|  
|**Enregistrer**|Enregistrer toutes les modifications effectuées dans la version sélectionnée et dans ses définitions.|  
|**Publier**|Publier la version de vocabulaire sélectionnée. Notez que vous ne pouvez pas directement modifier une version publiée. Vous pouvez copier et coller dans une nouvelle version du vocabulaire.|  
|**Recharger**|Recharger la version de vocabulaire sélectionnée et ses définitions, en choisissant d'ignorer ou non les modifications effectuées dans cette version et de rétablir le contenu à partir du magasin de règles.|  
|**Modifier**|Lancer l'Assistant Définition de vocabulaire pour modifier la définition sélectionnée. Notez que vous ne pouvez pas modifier une définition qui fait partie d'une version publiée.|  
|**Atteindre le fait source**|À partir d'un assembly .NET, d'un schéma XML ou d'une table de base de données, accéder au fait source correspondant à la définition sélectionnée.|  
  
## <a name="xml-schemas-tab"></a>Onglet Schémas XML  
 Cet onglet permet de rechercher les définitions d'éléments et attributs XML dans des schémas XSD. Vous pouvez faire glisser des éléments vers des versions de vocabulaire non publiées sur le **vocabulaire** onglet pour créer des définitions, ou vous pouvez faire glisser des éléments à l’éditeur de Conditions ou d’Actions pour définir des prédicats, des actions et des arguments.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Sélectionnez le nœud racine**|Sélectionner un nœud racine à télécharger à partir d'un schéma XML qui contient plusieurs nœuds racines.|  
  
## <a name="databases-tab"></a>Onglet Bases de données  
 Cet onglet permet de rechercher les définitions de base de données et de table dans les serveurs de base de données. Vous pouvez faire glisser des éléments vers des versions de vocabulaire non publiées sur le **vocabulaire** onglet pour créer des définitions, ou vous pouvez faire glisser des éléments à l’éditeur de Conditions ou d’Actions pour définir des prédicats, des actions et des arguments.  
  
## <a name="net-classes-tab"></a>Onglet Classes .NET  
 Cet onglet permet de rechercher des définitions de classes .NET publiques dans des assemblys .NET. Vous pouvez faire glisser des éléments vers des versions de vocabulaire non publiées sur le **vocabulaire** onglet pour créer des définitions, ou vous pouvez faire glisser des éléments à l’éditeur de Conditions ou d’Actions pour définir des prédicats, des actions et des arguments.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Parcourir**|Charger un assembly .NET à partir du global assembly cache|  
|**Supprimer**|Supprimer un assembly .NET.|