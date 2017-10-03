---
title: "Les Formats de Date et d’heure personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5efbec4-3138-44d7-bc76-f9c21547e1d5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1496f1f506df06a4d5569c065cba3bf4f8cbdad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-date-time-formats"></a>Formats de Date et d’heure personnalisés

## <a name="overview"></a>Vue d'ensemble
En raison de leurs origines héritées, les formats de fichier plat pour lesquels vous créez des schémas de fichier plat sont tenus d'utiliser des formats de date et d'heure qui ne sont pas conformes aux formats ISO 8601. Par conséquent, lorsque vous créez un schéma de fichier plat et que vous définissez la **Type de données** propriété d’un **élément de champ** ou **attribut de champ** nœud à un de le (définition de schéma XML Types de données primitifs du langage XSD), **xs : DateTime**, **xs : Time**, ou **xs : date**, vous pouvez utiliser la **Format de Date/heure personnalisé**propriété pour spécifier un autre format pour les valeurs de date ou d’heure.  
  
> [!NOTE]
>  Stockage dans la boîte de message tronque les valeurs d’heure dans **xs : DateTime** et **xs : Time** éléments sous le niveau de la milliseconde. Une perte similaire de précision peut survenir en cas de conversion vers les types de données de date/heure .NET.  
  
 Lorsque le désassembleur de fichier plat traduit un tel champ en son équivalent XML de format, la valeur de la **Format Date/heure personnalisé** propriété sera utilisée pour autoriser le format de date/heure de fichier plat être converti en son conforme ISO 8601 équivalent. De même, lorsque l’assembleur de fichier plat traduit une valeur de date/heure conforme ISO 8601 en son équivalent de fichier plat, la chaîne de format spécifié dans le **Format Date/heure personnalisé** propriété sera utilisée construire la date appropriée / format d’heure attendu dans le fichier plat.  
  
> [!NOTE]
>  Par défaut, les valeurs qui correspondent aux types de données de date et d'heure XSD, qui sont plusieurs, doivent respecter les formats ISO 8601. En bref, les dates sont exprimées en tant que **AAAA-MM-jj** et heures sont exprimées en tant que **hh : mm :** à l’aide de la notation de 24 heures. Lorsqu’elles apparaissent ensemble, les valeurs de date et heure sont séparées par le caractère « T » : **YYYY:MM:DDThh:mm:ss**.  
  
 Vous pouvez configurer le **Format Date/heure personnalisé** propriété avec presque n’importe quel format de date et l’heure, à l’exception des dates du calendrier julien. La liste déroulante offre plusieurs choix, mais vous avez aussi la possibilité de taper un format de votre choix. Les formats de date et d’heure utilisent le Common Language Runtime (CLR) **DateTime** installations. Excepté qu'un caractère unique j, m ou M est automatiquement précédé d'un signe de pourcentage (%) afin de donner lieu à l'élément unique correspondant de la valeur DateTime. Les séparateurs autorisés pour les formats de date et d'heure personnalisés sont le tiret (-), la barre oblique (/) et le point (.). Pour plus d’informations sur **DateTime** formats, recherchez « DateTimeFormatInfo » dans la collection de documents de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations relatives aux champs](../core/field-considerations.md)   
-  **Type de données (propriété de nœud de tous les schémas)** et **Format de Date et d’heure personnalisé (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]