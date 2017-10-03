---
title: "Numéro de contrôle de groupe ne respecte pas la syntaxe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e173c914-cb5c-4369-ac2f-8f9abee420cb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c9364260d9c90b9935f894eb3a0ada882057ea5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="group-control-number-violates-syntax"></a>Ce numéro de contrôle de groupe ne respecte pas la syntaxe
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12FaInvalidControlNumberDescription|  
|Texte du message|Ce numéro de contrôle de groupe ne respecte pas la syntaxe|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant car le numéro de contrôle du groupe des champs GS06 et GE02 de l'échange n'est pas conforme au type de données et à la longueur spécifiés dans le schéma de service. Le schéma du service est X12ServiceSchema dans BaseArtifacts.dll.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que les numéros de contrôle du groupe contenus dans les champs GS06 et GE02 de l'échange sont conformes au type de données (X12_N0) et à la longueur (entre un et neuf chiffres) spécifiés dans le schéma de service, puis demandez à l'expéditeur de renvoyer l'échange.