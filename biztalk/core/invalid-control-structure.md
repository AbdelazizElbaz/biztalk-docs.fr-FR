---
title: "Structure de contrôle non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9bb104-7ea1-429a-8540-49f4d598fd46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa21ceae70798242a153978adeaf5b75478b3b49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-control-structure"></a>Structure de contrôle non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidControlStructureDescription|  
|Texte du message|Structure de contrôle non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu valider la structure de l'accusé de réception TA1 par rapport à TA1Schema.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, identifiez la raison pour laquelle l'accusé de réception TA1 n'est pas conforme à TA1Schema.