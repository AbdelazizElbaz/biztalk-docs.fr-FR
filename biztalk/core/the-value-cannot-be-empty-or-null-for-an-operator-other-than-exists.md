---
title: "La valeur ne peut pas être vide ou null pour un opérateur autre qu’Exists. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44de42c8-eab7-4b13-b55a-d33eabe75c52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e257b78df8bf872764542d711637d33714349
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-value-cannot-be-empty-or-null-for-an-operator-other-than-exists"></a>Cette valeur ne peut pas être vide ou null pour un opérateur autre qu'Exists.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|ValueCannotBeNullOrEmpty|  
|Texte du message|Cette valeur ne peut pas être vide ou null pour un opérateur autre qu'Exists.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique qu'une valeur entrée pour une propriété sur une ligne de la boîte de dialogue Filtre par lot n'était pas valide, car l'opérateur n'était pas Exists, mais la valeur entrée était vide ou nulle.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot. Si l'opérateur d'une ligne n'est pas Exists, faites en sorte que la valeur entrée ne soit ni vide ni nulle.