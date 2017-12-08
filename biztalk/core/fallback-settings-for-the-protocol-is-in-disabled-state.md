---
title: "Paramètres de secours pour le protocole est dans un état désactivé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f14a5e46-1028-4250-af7b-8137fa927d7e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9060dbe2bf3644310d862d4949d2cf944269105d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fallback-settings-for-the-protocol-is-in-disabled-state"></a>Les paramètres de secours du protocole sont désactivés
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|AgreementResolutionFallbackSettingsDisabled|  
|Texte du message|Les paramètres de secours du protocole {0} sont désactivés.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server a réussi à trouver une correspondance pour un accord et a été redirigé vers les paramètres de secours, mais que ceux-ci ont été désactivés pour le protocole spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, activez les paramètres de secours pour le protocole spécifié.