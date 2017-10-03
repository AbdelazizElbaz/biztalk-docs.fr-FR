---
title: ID de version non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 563af6e8-f496-46c9-8b5f-7b941b2d08a5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5edd2dddc5df19d99c434ec60cad46664ba378e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-versionid"></a>ID de version non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidVersionIdDescription|  
|Texte du message|ID de version non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car l'identificateur de version de l'échange (le champ GS08 dans un échange X12 ou le champ UNG7 dans un échange EDIFACT) n'était pas conforme au type de données et au nombre de chiffres définis par le schéma de service (X12ServiceSchema ou le EdifactServiceSchema dans BaseArtifacts.dll). Les données du champ GS08 doivent être de type X12_AN. Ce champ peut contenir de 1 à 12 chiffres. La version d'origine dans UNG7.1 doit être spécifiée via le type de données EDIFACT_AN. Ce champ peut contenir de 1 à 3 chiffres. La version finale dans UNG7.2 doit être spécifiée via le type de données EDIFACT_AN. Ce champ peut contenir de 1 à 3 chiffres. Le code d'association assigné dans UNG7.3 doit être spécifié via le type de données EDIFACT_AN. Ce champ peut contenir de 1 à 6 chiffres.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que la version du champ GS08 ou UNG7 est spécifiée via le type de données et conformément au nombre de chiffres indiqués par le schéma de service, puis faites renvoyer l'échange.