---
title: "Promotion des propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, promoting
- promoting properties
- promoting properties, about promoting properties
ms.assetid: e1825028-7dd9-4eae-a383-4db12a83a402
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1c5ac3e6e9aeadccc4eaefcb1457821ef36a93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="promoting-properties"></a>Promotion des propriétés
La promotion de propriétés implique la promotion **élément de champ** ou **attribut de champ** nœuds dans un schéma d’être **champs distinctifs** ou **propriété Champs**. Vous pouvez également promouvoir **enregistrement** nœuds en tant que **champs de propriété** s’ils ont un contenu simple (**Content Type** propriété de la **enregistrement** nœud la valeur **SimpleContent**). Cette section fournit des instructions détaillées pour la promotion des nœuds en tant que **champs distinctifs** ou en tant que **champs de propriété**.  
  
 Pour promouvoir un **enregistrement** (avec contenu simple), **élément de champ**, ou **attribut de champ** nœud en tant qu’un **champ de propriété**, vous deviez d’abord définissez un type spécial de schéma appelé schéma de propriété. Schémas de propriété définissent un ensemble non structuré de **Fieldelement** nœuds dans lequel vous promouvez **enregistrement** (avec contenu simple), **élément de champ**, ou  **Attribut de champ** nœuds. Pour obtenir des instructions pour la création d’un schéma de propriété, consultez [comment créer des schémas de propriété](../core/how-to-create-property-schemas.md).  
  
 Vous pouvez également utiliser le **Promotion rapide** fonctionnalité, qui sera automatiquement créer et mettre à jour un schéma de propriété unique chaque fois que vous promouvez un nouveau **Fieldelement**, **attribut de champ** , ou **enregistrement** (avec contenu simple) nœud.  
  
> [!NOTE]
>  Vous pouvez promouvoir un champ à la fois comme un **champ distinctif** et un **champ de propriété**.  
  
> [!NOTE]
>  Le **Promotion rapide** fonctionnalité modifie le schéma de propriété en insérant une nouvelle propriété avec le nom du nœud promu.  
  
> [!IMPORTANT]
>  Ne déplacez pas et ne renommez pas un champ dans le schéma une fois que vous l'avez promu. Lorsque vous déplacez ou renommez un champ de schéma, l'Éditeur BizTalk ne met pas à jour le XPath définissant l'emplacement du champ promu.  
  
## <a name="xsd-and-clr-data-types"></a>Types de données XSD et CLR  
 Dans certaines phases comme celle de la promotion de propriété, les types de données XSD sont promues vers des types de données Common Language Runtime (CLR). Le tableau suivant répertorie les types de données XSD qui peuvent être promus et les types de données CLR correspondants.  
  
|Type de données XSD|Type de données CLR|  
|-------------------|-------------------|  
|anyURI|Chaîne|  
|Booléen|Booléen|  
|Byte|sbyte|  
|Date|DateTime|  
|dateTime|DateTime|  
|Décimal|Décimal|  
|Double|Double|  
|ENTITY|Chaîne|  
|Float|Unique|  
|gDay|DateTime|  
|gMonth|DateTime|  
|gMonthDay|DateTime|  
|gYear|DateTime|  
|gYearMonth|DateTime|  
|ID|Chaîne|  
|IDREF|Chaîne|  
|int|Int32|  
|Entier|Décimal|  
|Langage|Chaîne|  
|Nom|Chaîne|  
|NCName|Chaîne|  
|negativeInteger|Décimal|  
|NMTOKEN|Chaîne|  
|nonNegativeInteger|Décimal|  
|nonPositiveInteger|Décimal|  
|normalizedString|Chaîne|  
|NOTATION|Chaîne|  
|positiveInteger|Décimal|  
|QName|Chaîne|  
|Short|Int16|  
|Chaîne|Chaîne|  
|Time|DateTime|  
|Jeton|Chaîne|  
|unsignedByte|Byte|  
|UnsignedInt|UInt32|  
|unsignedShort|UInt16|  
  
> [!NOTE]
>  Les types de données XSD base64Binary, duration, ENTITES, hexBinary, IDREFS, long, NMTOKENS et unsignedLong ne permettent pas la promotion.  
  
## <a name="limitations-for-promoting-properties"></a>Restrictions liées à la promotion des propriétés  
 Lorsque vous promouvez des propriétés, prenez en compte les éléments suivants :  
  
-   Les propriétés promues sont limitées à 256 caractères alors que les propriétés écrites n'ont aucune limitation de longueur.  
  
-   Les propriétés promues sont utilisées dans le routage des messages et sont limitées en taille pour des raisons d'efficacité des tâches de comparaison et de stockage. Si les propriétés écrites n'ont aucune limite de taille, l'utilisation de valeurs excessivement grandes dans le contexte a un impact sur les performances car ces valeurs doivent quand même être traitées et transmises avec le message. Les champs distinctifs sont des exemples de propriétés écrites.  
  
-   Nœuds d’enregistrement ne peuvent jamais être promus en tant que **champs distinctifs**.  
  
-   Les propriétés promues sont limitées à des éléments/attributs non répétés.  
  
-   N'effectuez pas la promotion de champs appartenant au même nœud racine vers la même propriété. Ce type de promotion génère des erreurs de compilation ou de déploiement.  
  
-   Au sein d'un contexte de message, certaines propriétés ne sont pas disponibles car elles ne sont pas promues  (par exemple, la propriété BTS.ReceiveLocationName). Si vous pouvez ajouter un nouveau schéma de propriété ou projet BizTalk Server à votre développement, il est possible d'accéder à cette propriété à partir d'une orchestration.  
  
     Les valeurs de propriété sont identifiées par l'espace de noms cible et le nom de la propriété.  L'exemple suivant illustre l'accès à l'emplacement de réception dans le code.  
  
     `string receiveLocationName =       pInMsg.Context.Read("ReceiveLocationName", sysNamespace);`  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment ouvrir la boîte de dialogue Propriétés de promouvoir](../core/how-to-open-the-promote-properties-dialog-box.md)  
  
-   [Comment copier des données dans le contexte du Message en tant que champs distinctifs](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)  
  
-   [Comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)