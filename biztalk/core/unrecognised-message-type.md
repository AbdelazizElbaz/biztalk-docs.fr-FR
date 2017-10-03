---
title: "Type de message n’est pas reconnu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4094bf-af00-4d5c-9661-7c8abcb1b722
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd58907b61e68140ccf68d8256882b81e46bd863
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognised-message-type"></a>Type de message non reconnu
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|UnRecognizedMessageType|  
|Texte du message|Type de message non reconnu. Impossible de poursuivre.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car aucun schéma de document n'a été déployé pour le type de document d'un document informatisé dans cet échange, ou BizTalk Server ne peut pas déterminer le type de document à partir du code identificateur, de la version et de l'espace de noms du document informatisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Déployez un schéma de document pour le type de document d'un document informatisé dans l'échange, puis renvoyez l'échange.  
  
-   Vérifiez que les valeurs suivantes définissent un schéma valide : X12, l’espace de noms cible, version/publication et au document, tapez ; pour EDIFACT, l’espace de noms cible, le numéro de version de message, le numéro de version du message et le message type. Pour plus d'informations, consultez la section « Détection du schéma » de la rubrique « Résolution de tiers, détection du schéma et autorisation des messages EDI reçus » de l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].