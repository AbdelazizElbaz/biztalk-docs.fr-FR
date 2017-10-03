---
title: "Valeur d’indicateur de Test non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d81d501-4020-4ff9-955c-5674a99d250b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 166ab446831243c58b1c12881393be1466399e0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-test-indicator-value"></a>Valeur de l'indicateur de test non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidTestIndicatorValueDescription|  
|Texte du message|Valeur de l'indicateur de test non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car l'indicateur de test dans le champ UNB11 n'est pas conforme au type de données et au nombre de chiffres qui ont été définis par le schéma de service (X12ServiceSchema ou le EdifactServiceSchema dans le fichier BaseArtifacts.dll).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le champ UNB11 est du type de données EDIFACT_N et que sa longueur est de 1 caractère. Demandez à l'expéditeur de renvoyer l'échange.