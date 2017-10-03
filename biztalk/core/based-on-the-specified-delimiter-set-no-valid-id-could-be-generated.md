---
title: "En fonction de l’ensemble de délimiteurs spécifié, aucun ID valide pu être généré. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ab5f018-b56f-4e3c-97e4-f9ea4258f6d9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d70c4210ce57f4af9fb318caaf8274a0c6effc7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="based-on-the-specified-delimiter-set-no-valid-id-could-be-generated"></a>Sur la base de l'ensemble de délimiteurs spécifié, aucun ID valide n'a pu être créé.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|En fonction de l’ensemble de délimiteurs spécifié, aucun ID valide pu être généré. Utilisez un autre ensemble de délimiteurs.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu générer une valeur d'ID valide, car un caractère utilisé dans un champ d'identificateur de l'échange sortant était identique à un caractère de séparation.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, modifiez les valeurs de séparateur utilisées par le pipeline d'envoi EDI pour créer un message afin qu'aucun caractère de séparation ne soit identique à celui utilisé dans un champ d'identificateur de l'échange sortant. Procédez de l'une des manières suivantes :  
  
-   Pour un échange X12 envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers en tant que récepteur d'échanges.  
  
-   Pour un échange X12 envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments ISA.  
  
-   Pour un échange EDIFACT envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers considéré comme récepteur des échanges.  
  
-   Pour un échange EDIFACT envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments UNA.