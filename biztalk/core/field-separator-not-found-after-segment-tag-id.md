---
title: "Séparateur de champs introuvable après l’id de balise de segment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f6f0a74-3560-4d6d-9893-85e8426e6b17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 818a061cd723c0d8f8c58570c9e6df94a670942b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-separator-not-found-after-segment-tag-id"></a>Séparateur de champs non trouvé avec l'ID de balise de segment
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12SeFsNotFoundAfterTagIdDescription|  
|Texte du message|Séparateur de champs non trouvé avec l'ID de balise de segment|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange, car ce dernier contient un segment dans lequel un identificateur de segment n'est pas immédiatement suivi d'un séparateur d'éléments de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que tous les identificateurs de segment d'un échange soient immédiatement suivis de séparateurs d'éléments de données, puis demandez à l'expéditeur de renvoyer l'échange.