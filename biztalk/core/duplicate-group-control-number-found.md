---
title: "Numéro de contrôle de groupe trouvé dupliqué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1badc033-42fd-4992-ad36-b53047ba7817
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9165414d1a9a743c77c28b087730745d3dcc4c0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="duplicate-group-control-number-found"></a>Numéro de contrôle de groupe dupliqué trouvé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Numéro de contrôle de groupe dupliqué trouvé|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter un échange entrant, car il présentait le même numéro de contrôle d'échange, de groupe ou de document informatisé qu'un échange reçu précédemment. Cette situation aboutit à un échec tant que les vérifications de numéro de contrôle dupliqué appropriées sont activées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Assurez-vous que l'échange envoyé à BizTalk Server ne présente pas le même numéro de contrôle de groupe qu'un échange précédent, si la vérification de numéro de contrôle dupliqué correspondante est activée.  
  
-   Désactivez la vérification du numéro de contrôle de groupe dupliqué. Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit de la souris sur le tiers approprié, puis ouvrez la boîte de dialogue Propriétés du traitement de l'échange EDIFACT ou Propriétés du processus d'échange X12 correspondant au tiers jouant le rôle d'expéditeur de l'échange. Pour désactiver la vérification d'un échange EDIFACT, désélectionnez la propriété Vérifier qu'aucun doublon n'existe pour UNG5 (numéro de contrôle du groupe) dans l'échange. Pour désactiver la vérification d'un échange X12, désélectionnez la propriété Vérifier qu'aucun doublon n'existe pour GS6 (numéro de contrôle du groupe) dans l'échange.