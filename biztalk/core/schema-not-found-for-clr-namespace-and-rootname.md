---
title: "Schéma non trouvé pour CLR Namespace et rootName | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db283d81-1cb0-460d-ace4-49a91ceb4a02
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06db4a89803b8386ccbb45372b72423e83c6ff7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-not-found-for-clr-namespace-and-rootname"></a>Schéma non trouvé pour CLR Namespace et rootName
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|SchemaNotFoundForCLRAndRN|  
|Texte du message|Schéma non trouvé pour CLR Namespace = {0} et rootName = {{1}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu détecter le schéma de document à l'aide du nom racine associé à l'échange et à l'aide de l'espace de noms associé au tiers qui a été résolu pour l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le nom racine issu de l'échange et que l'espace de noms déterminé d'après les propriétés du tiers résolu correspondent tous deux au schéma déployé. BizTalk détermine le nom racine à partir du type et de la version du document de l'échange. Il identifie le schéma à partir du champ Espace de noms cible par défaut (pour les schémas par défaut) ou d'après la grille « Activer les définitions des documents informatisés personnalisés » (pour les schémas personnalisé) des propriétés de traitement de l'échange.