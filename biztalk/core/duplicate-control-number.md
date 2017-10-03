---
title: "Numéro de contrôle dupliqué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 331ad173-29b3-427c-8104-60d80c580a5a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e83f685242f4c69e6a142f3abb027017657611f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="duplicate-control-number"></a>Numéro de contrôle dupliqué
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Numéro de contrôle dupliqué|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter un échange entrant, car il présentait le même numéro de contrôle d'échange, de groupe ou de document informatisé qu'un échange reçu précédemment. Cette situation aboutit à un échec tant que les vérifications de numéro de contrôle dupliqué appropriées sont activées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Assurez-vous que l'échange envoyé à BizTalk Server ne présente pas le même numéro de contrôle d'échange, de groupe ou de document informatisé qu'un échange précédent, si la vérification de numéro de contrôle dupliqué correspondante est activée.  
  
-   Désactivez la vérification du numéro de contrôle dupliqué. Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit de la souris sur le tiers approprié, puis ouvrez la boîte de dialogue Propriétés du traitement de l'échange EDIFACT ou Propriétés du processus d'échange X12 correspondant au tiers jouant le rôle d'expéditeur de l'échange. Pour désactiver la vérification d'un échange EDIFACT, désélectionnez la propriété Vérifier qu'aucun doublon n'existe pour UNB5 (Numéro de contrôle de l'échange), Vérifier qu'aucun doublon n'existe pour UNG5 (Numéro de contrôle de l'échange) dans l'échange ou Vérifier qu'aucun doublon n'existe pour UNH1 (Numéro de référence du document informatisé) dans le groupe. Pour désactiver la vérification d'un échange X12, désélectionnez la propriété Vérifier qu'aucun doublon n'existe pour ISA13 (Numéro de contrôle de l'échange), Vérifier qu'aucun doublon n'existe pour GS6 (Numéro de contrôle de l'échange) dans l'échange ou Vérifier qu'aucun doublon n'existe pour ST2 (Numéro de contrôle du document informatisé) dans le groupe.