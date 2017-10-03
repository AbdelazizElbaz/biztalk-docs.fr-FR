---
title: Heure non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6942eb77-3ef1-460c-ac4f-8f1339c25d1b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aae508a945cc6934e83408b2a9b78c324947e0e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-time"></a>Heure non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidTimeDescription|  
|Texte du message|Heure non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car une valeur d'heure d'un élément de données n'est pas conforme au type de données spécifié par le schéma EDI, ou une valeur d'heure de l'en-tête de champ GS05 d'un échange X12 n'est pas conforme au schéma de service (X12ServiceSchema dans le fichier BaseArtifacts.dll). Pour X12, le schéma de service définit une heure dans le champ GS05 du type de données X12_TM et d'une longueur comprise entre 4 et 8 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous qu'une valeur d'heure contenue dans un élément de données est conforme au type de données spécifié par le schéma EDI ou que la valeur d'heure dans l'en-tête GS05 d'un échange X12 est conforme au schéma de service, puis demandez à l'expéditeur de renvoyer l'échange.