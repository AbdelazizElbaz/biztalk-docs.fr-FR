---
title: "Accès aux données dans le moteur de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, data access
- Business Rules Engine, helper classes
- data, data access
ms.assetid: 38da32af-1e0d-43fb-b946-fb49a11f1681
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58de70c2befd13f4995ebd073ebd70a2e7d84ea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-access-in-the-business-rule-engine"></a>Accès aux données dans le moteur des règles d'entreprise
En mode natif, le moteur de règles ne prend en charge que des objets .NET. Pour gérer des données d'une base de données, vous pouvez utiliser directement les objets ADO.NET. Toutefois, le moteur fournit des classes d'assistance afin de simplifier l'utilisation des données de la base de données à partir de règles. Le moteur de règles étend sa prise en charge en exposant trois types de base de données : **TypedDataRow**, **TypedDataTable**, et **DataConnection**. Cette section décrit ces classes d'assistance, fournit des recommandations sur l'utilisation de chaque type et indique quelles sont les conséquences de leur utilisation sur les performances.  
  
 Les classes d'assistance sont les suivantes :  
  
-   **TypedDataRow.** Construit à l’aide d’une référence à un élément ADO.NET **DataRow** instance. Le **TypedDataRow** est un choix évident pour les règles qui ne traitent des données d’une chaîne ou un petit nombre de lignes à partir d’une table particulière.  
  
-   **TypedDataTable.** Littéralement, une collection de **TypedDataRow** objets. Chaque ligne dans la table de base de données est insérée comme un **TypedDataRow** déclarée dans la mémoire de travail par le moteur de règles.  
  
     A **TypedDataTable** requiert un élément ADO.NET en mémoire **DataTable**, ce qui peut être un particulier de surcharge si cette performance **DataTable** contient un très grand nombre de lignes. Si un petit nombre de lignes dans la table de base de données ne s’applique et que vous pouvez déterminer ces lignes avant d’appeler les règles, utilisez un **DataTable**, sinon utilisez **TypedDataRow**. L’hypothèse est qu’un grand nombre de lignes du DataTable est pertinents pour les règles.  
  
-   **DataConnection.** représente une table d'une base de données à laquelle on accède via une connexion de base de données. La différence entre **DataConnection** et **TypedDataTable** qui s’ajoute le nom du jeu de données et le nom de la table, **DataConnection** requiert une base de données utilisable connexion et éventuellement un contexte de transaction de base de données.  
  
     Certains ou tous les prédicats utilisés dans les règles avec la **DataConnection** feront partie des contraintes de requêtes par rapport à la connexion de base de données. Seules les lignes qui répondent aux contraintes de requêtes sont extraites de la base de données et utilisées par le moteur. Ce mécanisme offre de meilleures performances et consomme moins de mémoire que contenant un très grand **DataTable** en mémoire.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Considérations sur l’utilisation de DataConnection](../core/considerations-when-using-dataconnection.md)  
  
-   [À l’aide de TypedDataTable et DataConnection](../core/using-dataconnection-and-typeddatatable.md)