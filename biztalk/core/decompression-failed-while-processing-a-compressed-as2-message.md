---
title: "Échec de la décompression lors du traitement d'un message AS2 compressé. | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5246ee97-cc60-4878-9447-de870c0f4c34
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4121fc3598913f4c3edab52655866c02b5a4fe86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="decompression-failed-while-processing-a-compressed-as2-message"></a>Échec de la décompression lors du traitement d'un message AS2 compressé.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Échec de la décompression lors du traitement d'un message AS2 compressé. Erreur : {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu décompresser le message AS2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Vérifier que le wrapper de compression dans le message AS2 est valide.  
  
-   Vérifier que la décompression est activée pour BizTalk Server en vérifiant que la propriété « Le message doit être compressé » est activée dans la page Tiers considéré comme expéditeur des messages AS2 de la boîte de dialogue Propriétés AS2 (si la propriété Remplacer les propriétés du message entrant est activée).  
  
-   Consultez la description de l'erreur fournie dans le texte du message d'erreur pour identifier le problème.