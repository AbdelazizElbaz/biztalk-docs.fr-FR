---
title: "DOCTYPE n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67233aae-65c0-4689-a4b3-60a48132343a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fec7dc4f2dfed0c8e8b8fcde13593d4e29997f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="doctype-is-invalid"></a>Doctype non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|DocTypeInvalidFormat|  
|Texte du message|Le type de document {0} n'est pas valide. Il est impossible de déterminer un ou plusieurs identificateurs d'espace de noms, de version ou de document informatisé.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas réussi à traiter l'échange entrant, car le schéma n'a pas été détecté correctement.  
  
 Pour X12, l'espace de noms cible est déterminé dans la grille « Activer les définitions des documents informatisés personnalisés » de la page Propriétés du processus d'échange X12 de la boîte de dialogue Propriétés EDI. Pour que l'espace de noms cible soit correctement identifié, les valeurs GS02 et ST01 du message doivent correspondre à celles d'une ligne de la grille. La création du nom du schéma à utiliser pour le document informatisé s'effectue en ajoutant la version (les cinq premiers caractères de GS08) et le type de document (ST01) du document informatisé entrant dans l'espace de noms cible identifié.  
  
 Pour EDIFACT, l'espace de noms cible est déterminé dans la grille « Activer les définitions des documents informatisés personnalisés » de la page Propriétés du processus d'échange EDIFACT de la boîte de dialogue Propriétés EDI. Pour que l'espace de noms cible soit correctement identifié, les valeurs UNH2.1, UNH2.2, UNH2.3, UNH2.5, UNG2.1 et UNG2.2 du message doivent correspondre à celles d'une ligne de la grille. La création du nom du schéma à utiliser pour le document informatisé s'effectue en ajoutant le numéro de version (UNH2.2), le numéro de version finale du message (UNH2.3) et le type du message (UNH2.1) du document informatisé entrant dans l'espace de noms cible identifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
1.  Dans la boîte de dialogue Propriétés EDI, dans la page Propriétés du traitement de l'échange, assurez-vous que l'espace de noms cible du schéma du document informatisé est correctement identifié par une ligne dans la grille « Activer les définitions des documents informatisés personnalisés ». Dans le cas contraire, modifiez les valeurs dans la grille.  
  
2.  Si l'espace de noms a été correctement identifié, déterminez si les valeurs utilisées pour identifier le schéma sont correctes. Pour X12, il s'agit de la version (c'est-à-dire les cinq premiers caractères de GS08) et du type de document (ST01) dans le document informatisé entrant. Pour EDIFACT, il s'agit du numéro de version (UNH2.2), du numéro de version finale du message (UNH2.3) et du type de message (UNH2.1) dans le document informatisé entrant. Si les valeurs sont erronées, demandez à l'expéditeur du document informatisé de modifier les valeurs de ces champs, puis renvoyez le message.