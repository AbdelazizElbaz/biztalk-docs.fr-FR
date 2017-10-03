---
title: "Qualificateur de sécurité non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dce36f4b-ab59-41c0-8b92-3020f6393db9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f4d16b4295bd8d01f93db964d4e45e8363205ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-security-qualifier"></a>Qualificateur de sécurité non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidSecurityQualifierDescription|  
|Texte du message|Qualificateur de sécurité non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le qualificateur de sécurité dans le champ ISA03 ou le qualificateur du mot de passe du destinataire dans le champ UNB6.2 ne correspond à aucune valeur de l'énumération établie par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le champ ISA03 ou UNB6.2 correspond à l'une des valeurs de l'énumération établie par le schéma de service. Demandez à l'expéditeur de renvoyer l'échange.