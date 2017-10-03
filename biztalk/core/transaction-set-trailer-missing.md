---
title: Code de fin manquante du jeu de transactions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07753300-fe47-47a6-a947-6abec10c1c90
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7f1c153aa0bb62b6c62f4eeebf9d1fb9bea004b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-trailer-missing"></a>Code de fin de document informatisé manquant
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12TsTrailerMissingDescription|  
|Texte du message|Code de fin de document informatisé manquant|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter le document informatisé entrant ou que le pipeline d'envoi n'a pas pu traiter le document informatisé sortant, car celui-ci n'incluait pas le code de fin de document informatisé SE (pour les documents informatisés X12) ou le code de fin de message UNT (pour les documents informatisés EDIFACT).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que l'expéditeur du document informatisé ajoute à celui-ci un code de fin de document informatisé SE (pour les documents informatisés X12) ou le code de fin de message UNT (pour les documents informatisés EDIFACT), puis renvoyez le document informatisé.