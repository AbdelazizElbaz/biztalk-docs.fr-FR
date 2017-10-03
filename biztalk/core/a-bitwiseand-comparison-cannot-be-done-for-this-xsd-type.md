---
title: "Ne peut pas être effectuée une comparaison BitwiseAnd pour ce type XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bc2351-c002-458a-9d35-5fdcc91c6a0e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0f3aa2b3ae7c60f3c104daaa885ab7ae8cc7ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-bitwiseand-comparison-cannot-be-done-for-this-xsd-type"></a>Impossible d'effectuer une comparaison BitwiseAnd pour ce type  XSD
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|Err_InvalidBitwiseComparision|  
|Texte du message|Impossible d'effectuer une comparaison BitwiseAnd pour ce type XSD.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d’erreur/avertissement/Information indique que BizTalk Server n’a pas pu comparer une propriété de contexte lors de la tentative de décider à un message du lot.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas de propriété de contexte dont le type CSD ne peut pas faire l'objet d'une comparaison au niveau du bit.