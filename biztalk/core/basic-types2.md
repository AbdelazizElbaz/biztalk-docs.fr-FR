---
title: Base Types2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, data types
- adapters [JD Edwards EnterpriseOne adapters], data types
- data types, JD Edwards EnterpriseOne adapters
ms.assetid: 96a70f0d-f7f8-4e3b-9511-59b330910ead
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7e5c47d8760e9743ec11a62598581d9d20b3e53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-types"></a>Types de base
L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne permet d'accéder uniquement aux fonctions commerciales de JD Edwards EnterpriseOne. Les métadonnées des fonctions commerciales sont lues à l'aide d'une interface de fonction commerciale et sont utilisées pour rechercher une liste des fonctions commerciales et des structures de données associées. Dans tous les cas, les métadonnées sont fortement typées pour toutes les méthodes de fonctions commerciales.  
  
 Toutes les méthodes de fonctions commerciales ont la même convention d’appel : trois paramètres dérivés du système et un pointeur vers une structure de données. Le tableau suivant présente la représentation des types de données d’entreprise (fonction).  
  
|Type de données JD Edwards EnterpriseOne| Description|Conversion WDSL|  
|----------------------------------------|-----------------|---------------------|  
|char|Chaîne de caractères.|xsd:string de 1|  
|int|Entier court.|xsd:short|  
|long|Entier long.|xsd:short|  
|Chaîne|Consultez [la gestion des valeurs de chaîne](../core/handling-string-values2.md).|xsd:string|  
|JDEDATE|Implémentation spéciale de dates.|xsd:date|  
|MATH_NUMERIC|Implémentation spéciale de nombres à virgule flottante, y compris les valeurs de devises.|XSD : String de 32|  
|Byte|Caractère non signé unique.|xsd:string de 1|  
|JDEUTIME|Inclut les composants de date et heure.<br /><br /> Le type de données enregistre toutes les dates/heures et effectue tous les calculs de date/heure en temps universel coordonné (UTC).|xsd:dateTime|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Type MATH_NUMERIC](../core/using-the-math-numeric-type1.md)   
 [Gestion des valeurs de chaîne](../core/handling-string-values2.md)   
 [Annexe b : les Types de données](../core/appendix-b-data-types.md)