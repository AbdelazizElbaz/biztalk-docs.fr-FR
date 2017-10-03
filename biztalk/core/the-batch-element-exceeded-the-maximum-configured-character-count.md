---
title: "L’élément de lot a dépassé le nombre maximal de caractères configuré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ad12733-295a-43ba-8147-34c8716c2d37
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dac259db250a88e434efb649a2baf2e75b805a40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-element-exceeded-the-maximum-configured-character-count"></a>L'élément par lot a dépassé le nombre maximal de caractères configuré
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|MessageExceededCharacterCount|  
|Texte du message|L'élément par lot a dépassé le nombre maximal de caractères configuré|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu générer l'échange traité par lot, car le nombre de caractères d'un élément de lot récupéré par l'orchestration de traitement par lot dépasse le nombre de caractères spécifié par la propriété « Nombre maximal de caractères dans un échange » des critères de déclenchement du lot. L'élément de lot à l'origine de ce message d'erreur ne sera pas le premier élément de lot à être récupéré pour un lot, mais un élément de lot suivant le premier élément a déjà été traité par lot. Notez que le nombre de caractères par rapport au maximum n'inclut pas le nombre de caractères dans l'enveloppe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
1.  Dans la boîte de dialogue Propriétés EDI pour le tiers en tant que récepteur d'échanges, dans la page Paramètres de création de lots d'échange, augmentez la valeur de la propriété Nombre maximal de caractères dans un échange. Pour ce faire, vous devez arrêter l'instance d'orchestration, augmenter le nombre maximal de caractères de la propriété, puis redémarrer l'instance d'orchestration.  
  
2.  Demandez à l'expéditeur d'envoyer des documents informatisés possédant un nombre de caractères inférieur au nombre maximal autorisé.