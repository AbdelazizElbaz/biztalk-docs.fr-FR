---
title: "Une erreur BTS MIME a été rencontrée lors d’une tentative de décodage d’un message AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65cb5ece-78e4-4b83-b126-4d8c588b2c61
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 660a9e3a6ca5834448dd64815b031e00a0b2942a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-bts-mime-error-was-encountered-when-attempting-to-decode-an-as2-message"></a>Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2.  AS2-à partir de : {0}, AS2-pour : {1}, MessageId : {2}, erreur : {3}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lors de l'utilisation du composant BizTalk MIME pour gérer une partie du traitement MIME.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Le message d’erreur complet fournit les informations sur les problèmes rencontrés par le composant MIME. Consultez les informations d’erreur BTS MIME pour diagnostiquer le problème (c’est parce que les composants AS2 utilisent les composants BizTalk MIME pour une partie du traitement MIME).