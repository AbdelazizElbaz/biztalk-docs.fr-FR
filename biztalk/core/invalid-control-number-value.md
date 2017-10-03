---
title: "Valeur de numéro de contrôle non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ac762e2-2d48-45e8-b4c4-2df246b7568c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ce9df9724d85a3b4a2d6ebf28f94e4b9c05db05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-control-number-value"></a>Valeur du numéro de contrôle non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidControlNumberValueDescription|  
|Texte du message|Valeur du numéro de contrôle non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car la valeur d'un numéro de contrôle (échange, groupe ou document informatisé) dans l'échange n'est pas conforme au type de données ou ne possède pas le nombre correct de chiffres spécifié par le schéma. Le schéma est X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le numéro de contrôle est conforme au type de données et au nombre de chiffres spécifiés par le schéma, puis renvoyez l'échange.