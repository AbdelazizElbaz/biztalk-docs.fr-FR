---
title: "Cette instance est en dehors de la fenêtre de Service de traitement par lot pour le partenaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e420d75-11fd-4221-9d97-814ca6e48c81
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e93e7e769a8f0e30b3753af690a69c5e6eaa9786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="this-instance-is-outside-the-batching-service-window-for-the-partner"></a>Cette instance est en dehors de la fenêtre de service de traitement par lot pour le partenaire
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|OutsideBatchingServiceWindow|  
|Texte du message|Cette instance est en dehors de la fenêtre de service de traitement par lot pour le partenaire|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique qu'une instance de l'orchestration de traitement par lot n'a pas pu démarrer car l'instance était en dehors des limites d'activation pour le tiers.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, ouvrez la page Paramètres de création de lots d'échange des propriétés EDI pour le tiers et vérifiez que l'instance d'orchestration est incluse dans les limites d'activation. Dans le cas contraire, modifiez la propriété d’heure de début, puis **Démarrer**.