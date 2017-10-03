---
title: "Un ou plusieurs segments erronés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ee86667-e72a-4f1b-8d5c-15ca710dbe5d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 340c722bc96ec8efdf2f48e6b40260aa5323e675
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="one-or-more-segments-in-error"></a>Un ou plusieurs segments erronés
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12TsOneOrMoreSegmentsInErrorDescription|  
|Texte du message|Un ou plusieurs segments erronés|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique qu'un ou plusieurs segments de l'échange n'étaient pas conformes au schéma qui les gouverne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, identifiez le segment qui pose problème, ouvrez le schéma qui le gouverne puis, à partir de ce dernier, déterminez la cause de l'erreur.