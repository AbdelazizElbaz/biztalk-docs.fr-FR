---
title: "Message ne peut pas être sérialisé car le schéma n’a pas pu être localisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37897c04-650d-4695-846d-b8ba61365647
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b887d4a07d7a461278d3858289882a9ce441e9e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-cannot-be-serialized-as-the-schema-could-not-be-located"></a>Le message ne peut pas être sérialisé car le schéma n'a pu être localisé.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|MessageSerializationFailureDueToMissingSchema|  
|Texte du message|Le message ne peut pas être sérialisé car le schéma {0} n'a pu être localisé. Soit le schéma n'est pas déployé, soit plusieurs copies sont déployées.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu sérialiser l'échange sortant, car il n'est pas parvenu à déterminer le schéma qu'il devait utiliser pour ce faire. Le schéma n'était pas déployé ou plusieurs copies du schéma étaient déployées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
1.  Si le schéma associé à l'échange n'a pas été déployé, ouvrez Visual Studio, ajoutez le schéma à un projet BizTalk, puis créez et déployez le projet.  
  
2.  Si plusieurs copies du schéma ont été déployées, ouvrez Visual Studio et annulez le déploiement de toutes les copies du schéma associé à l'échange, à l'exception d'une.