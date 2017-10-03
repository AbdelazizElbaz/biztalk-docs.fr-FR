---
title: Erreur de gestion des erreurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 602be8a5-1f28-457d-8e12-ba06cff65491
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafc64afb24ce8bb7995e7852a778b17a556f018
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-handling-errors"></a>Erreur en relation avec la gestion des erreurs
Informations sur le diagnostic et résolution des erreurs de gestion des erreurs de WCF.  

## <a name="error-handling-options-disable-location-on-failure-and-suspend-request-message-on-failure-should-not-both-be-set-to-false"></a>Les options de gestion des erreurs « Désactiver l'emplacement en cas d'échec » « Suspendre le message de requête en cas d'échec » ne doivent pas être toutes deux définies sur False    
||Détails|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Les options de gestion des erreurs « Désactiver l'emplacement en cas d'échec » « Suspendre le message de requête en cas d'échec » ne doivent pas être toutes deux définies sur False, faute de quoi des messages pourraient être perdus. Définissez l'une d'elles ou les deux sur True.|  
  
## <a name="explanation"></a>Explication  
 Dans l’adaptateur WCF-NetMsmq, les options **désactiver l’emplacement en cas d’échec** et **suspendre le message de demande en cas d’échec** doivent pas être toutes deux sélectionnées. Une perte de messages peut se produire si l'emplacement de réception continue à recevoir des messages non valides alors que ceux-ci n'ont pas été suspendus ni stockés dans la base de données MessageBox.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer les paramètres de l'adaptateur.    

1. Ouvrez **Administration de BizTalk Server.**  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Sélectionnez **propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Sélectionnez **Configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, sélectionnez le **Messages** onglet.  
  
9. Dans le **gestion des erreurs** section, assurez-vous soit **désactiver l’emplacement en cas d’échec** ou **suspendre le message de demande en cas d’échec** est activée.