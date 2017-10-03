---
title: "Pas de Transaction définie par l’ensemble du segment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 914e333f-96e4-4094-880d-51a5f25915c3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2f0b330110ef08196681e54e543173c3f2bd0f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-not-in-defined-transaction-set"></a>Segment non défini dans le document informatisé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12SegmentNotInDefinedTSDescription|  
|Texte du message|Segment non défini dans le document informatisé|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant car un document informatisé faisant partie de cet échange ne contient pas un segment requis par le schéma de document.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, demandez à l'expéditeur d'ajouter le segment requis au document informatisé dans l'échange, puis de renvoyer l'échange.