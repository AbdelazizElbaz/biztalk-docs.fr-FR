---
title: "Paramètres de secours pour le protocole introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d93e5db1-16a3-4796-8fa2-fef934508034
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5b3f8ea35f4f29859f5156ff254137ea7a8f8db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# Les paramètres de secours pour le protocole sont introuvables
## Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|AgreementResolutionFallbackSettingsNotFound|  
|Texte du message|Les paramètres de secours pour le protocole {0} sont introuvables.|  
  
## Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server a réussi à trouver une correspondance pour un accord et a été redirigé vers les paramètres de secours. Toutefois, les paramètres de secours n'étaient pas présents pour le protocole spécifié.  
  
## Action de l'utilisateur  
 Pour résoudre cette erreur, configurez les paramètres de secours pour le protocole spécifié.