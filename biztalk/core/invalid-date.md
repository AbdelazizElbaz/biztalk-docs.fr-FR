---
title: Date non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41da9c5-9dcf-44cd-be5b-922e6c267ec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 259456e781f5f5255f9fed8a51c8eb0569dd57b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-date"></a>Date non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12DeInvalidDateDescription|  
|Texte du message|Date non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car une valeur de date de l'élément de données n'est pas conforme au type de données spécifié par le schéma EDI, ou la valeur de date de l'en-tête de champ GS04 d'un échange X12 n'est pas conforme au schéma de service (X12ServiceSchema dans le fichier BaseArtifacts.dll). Pour X12, le schéma de service définit une date dans le champ GS04 du type de données X12_DT et d'une longueur comprise entre 6 et 8 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que la valeur d'heure contenue dans un élément de données est conforme au type de données spécifié par le schéma EDI, ou que la valeur de date dans l'en-tête GS04 d'un échange X12 est conforme au schéma de service, puis demandez à l'expéditeur de renvoyer l'échange.