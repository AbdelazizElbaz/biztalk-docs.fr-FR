---
title: "Emplacements de réception et événements Rendezvous TIBCO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive locations, life cycle
ms.assetid: 3576af82-4723-4efc-961e-40b1150cf13d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9278687ff212fc2368eca138780417d7c052824
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-events-and-receive-locations"></a>Emplacements de réception et événements Rendezvous TIBCO
Un système TIBCO Rendezvous peut envoyer des messages vers le nom d'objet de son choix. Le concept de *événement* est la génération de messages par d’autres programmes TIBCO Rendezvous.  
  
 Les étapes suivantes décrivent le cycle de vie d'un emplacement de réception :  
  
1.  création d'un emplacement de réception ;  
  
2.  association de l'emplacement de réception à un hôte ;  
  
3.  liaison de l'emplacement de réception à une orchestration ;  
  
4.  activation de l'emplacement de réception ;  
  
5.  réception de messages sur l'emplacement de réception.  
  
> [!IMPORTANT]
>  Le nom de chaque emplacement de réception doit être unique. Deux emplacements de réception ne peuvent pas avoir le même nom au sein d'un même déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!IMPORTANT]
>  Il est recommandé de définir des listes de contrôle d'accès renforcées dans l'emplacement de dépôt des emplacements de réception. Par exemple, vous devez définir des listes de contrôle d'accès renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaires de réception création TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)