---
title: "Erreur lors de la sérialisation. Le groupe fonctionnel Edifact comporte les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed81bc79-d99c-4305-805f-ab38eae91ea0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a8166e5a66038d4cbda3a6fcb9597c7827d1eeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-functional-group-had-the-following-errors"></a>Erreur lors de la sérialisation. Le groupe fonctionnel Edifact comporte les erreurs suivantes
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactFunctionalGroupSendError|  
|Texte du message|Erreur lors de la sérialisation. Le groupe fonctionnel Edifact avec l’id '{0}' dans l’échange possédant l’id « {{1}', id d’expéditeur « {{2} », id de destinataire '{3}' comporte les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un groupe fonctionnel au sein de l'échange EDIFACT sortant en raison des erreurs mentionnées pour le groupe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le groupe fonctionnel et déterminer une méthode de résolution dans la documentation.