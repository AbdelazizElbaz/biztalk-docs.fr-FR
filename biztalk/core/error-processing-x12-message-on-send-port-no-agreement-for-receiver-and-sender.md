---
title: "Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire et aucun tiers ayant le nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdf445e8-51a3-44fb-aa71-e0b0ab9c428f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acb05b7795c48c161ab50ab5e79d18a225306fd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a>Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire et aucun tiers ayant le nom
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un échec s'est produit lors du traitement du message X12 sur le port d'envoi {0}. Il n’existe aucun accord pour les paires qualificateur/identificateur expéditeur et destinataire pour {{1}, {2}, {3}, {4}. Il n’existe aucun tiers avec {5} de nom.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d’erreur/avertissement/Information indique BizTalk Server n’a pas pu résoudre le tiers pour l’échange EDIFACT, car BizTalk Server n’a pas pu correspondent promu propriétés qualificateur et identificateur de l’expéditeur et promues du qualificateur du récepteur et propriétés de l’identificateur, avec les valeurs correspondantes pour un tiers.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Définition des segments ISA associée au tiers, assurez-vous que le qualificateur et l'identificateur de l'expéditeur (ISA5 et ISA6) et que le qualificateur et l'identificateur du récepteur (ISA7 et ISA8) qui y sont définis correspondent aux propriétés promues dans le contexte de l'échange.