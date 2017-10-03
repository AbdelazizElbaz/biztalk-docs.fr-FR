---
title: "Les paramètres de lot pour le tiers ont expiré et l’orchestration de traitement par lot est terminée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f272b6-4da2-4736-8d61-ce48359f36dd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d56e06766a980c1ce293b211d2956a86c093726
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-settings-for-party-have-expired-and-the-batching-orchestration-is-being-terminated"></a>Les paramètres de traitement par lot pour le tiers ont expiré et l'orchestration de traitement par lots est terminée
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|BatchSettingsExpired|  
|Texte du message|Les paramètres de traitement par lot pour le tiers {0} ont expiré et l'orchestration de traitement par lots est terminée. Aucun nouveau lot ne sera créé tant que le traitement par lot ne sera pas activé pour ce tiers|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que l'instance d'orchestration de traitement par lot a été désactivée car la fin des limites de l'activation a été atteinte.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, redémarrez le processus de traitement par lot en effectuant l'une des opérations suivantes :  
  
1.  Ouvrez la console Administration de BizTalk Server, puis accédez à la page Paramètres de création de lots d'échange de la boîte de dialogue Propriétés EDI.  
  
2.  Réinitialiser les critères de fin et redémarrez l’orchestration en cliquant sur **Démarrer**.  
  
3.  Si la valeur datetime de début est antérieure à l’heure lorsque vous avez cliqué sur **Démarrer**, cliquez sur **Oui** pour mettre à jour la valeur datetime de début à la date/heure actuelle.