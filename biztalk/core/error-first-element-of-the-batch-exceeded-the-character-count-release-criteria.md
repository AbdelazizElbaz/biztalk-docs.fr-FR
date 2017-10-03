---
title: "Le premier élément du lot dépasse l’ensemble de critères de mise en production de nombre caractère | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b06f8f-247d-4e93-8c4e-5e86e4ad70c9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 746fbfabb2fe411310735f66c6d8a8398a94a5dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-first-element-of-the-batch-exceeded-the-character-count-release-criteria-set"></a>Le premier élément du lot dépasse l'ensemble de critères de diffusion « nombre de caractères »
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|FirstElementExceededCharCount|  
|Texte du message|Le premier élément du lot dépasse l'ensemble de critères de diffusion « nombre de caractères ». Modifiez le critère de diffusion « nombre de caractères » pour pouvoir traiter ce message. Ce message devra être renvoyé au système de traitement par lot après modification des paramètres.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu générer l'échange traité par lot, car le nombre de caractères du premier élément de lot récupéré par l'orchestration de traitement par lot dépasse le nombre de caractères spécifié par la propriété « Nombre maximal de caractères dans un échange » des critères de déclenchement du lot. Notez que le nombre de caractères par rapport au maximum n'inclut pas le nombre de caractères dans l'enveloppe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
1.  Dans la boîte de dialogue Propriétés EDI pour le tiers en tant que récepteur d'échanges, dans la page Paramètres de création de lots d'échange, augmentez la valeur de la propriété Nombre maximal de caractères dans un échange. Pour ce faire, vous devez arrêter l'instance d'orchestration, augmenter le nombre maximal de caractères de la propriété, puis redémarrer l'instance d'orchestration. Demandez à l'expéditeur de renvoyer le message.  
  
2.  Demandez à l'expéditeur d'envoyer des documents informatisés possédant un nombre de caractères inférieur au nombre maximal autorisé.