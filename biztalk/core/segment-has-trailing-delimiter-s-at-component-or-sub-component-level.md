---
title: "Segment possède un ou plusieurs délimiteurs fin au composant ou sous-composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 517f1cfc-66c1-47e6-be94-2c76c1f89230
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eede2923da1ed206a897b879b7b6be589800e4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-has-trailing-delimiters-at-component-or-sub-component-level"></a>Un segment possède un ou plusieurs délimiteurs de fin au niveau du composant ou du sous-composant
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12SeSegmentHasTrailingDelimiterDescription|  
|Texte du message|Un segment possède un ou plusieurs délimiteurs de fin au niveau du composant ou du sous-composant|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car celui-ci contenait des délimiteurs de fin, mais ces derniers n'étaient pas activés pour le tiers jouant le rôle d'expéditeur des échanges.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, activez les séparateurs de fin de la façon suivante :  
  
1.  Ouvrez la console Administration de BizTalk Server, déplacez le dossier Tiers et ouvrez les propriétés EDI du tiers.  
  
2.  Déplacez la page Génération d'accusés de réception et paramètres de validation pour X12 ou EDIFACT, selon les besoins.  
  
3.  Cliquez sur Autoriser les séparateurs de fin.