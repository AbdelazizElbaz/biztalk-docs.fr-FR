---
title: "Serveurs de traitement pour l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, processing servers
- processing servers [SSO]
ms.assetid: 9e80a456-974a-49b3-bb64-2e4713036cfb
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972e1a3b01394cbf63fb0c8094586d2beda73c3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-servers-for-sso"></a>Serveurs de traitement pour l’authentification unique
Dans un environnement multiserveur, une fois le serveur de secret principal et la base de données SSO créés, vous pouvez installer l'authentification unique de l'entreprise sur les autres ordinateurs. Il s'agit généralement des ordinateurs sur lesquels BizTalk Server ou Host Integration Server est installé.  
  
 Bien que le processus d'installation initial soit identique à celui effectué sur le premier ordinateur, la configuration varie légèrement. Étant donné que le serveur de secret principal et de la base de données SSO sont déjà en place, sélectionnez **joindre** lors de la demande de l’Assistant Configuration, **créer un nouveau système SSO** ou **joindre un système existant**.  
  
 Lors de la configuration d'un groupe sur un seul ordinateur, notez qu'il est possible de joindre une base de données SSO située sur un autre ordinateur et qui ne correspond pas à la base de données configurée pour ce groupe. Bien que cette opération soit envisageable, elle est déconseillée.  
  
## <a name="see-also"></a>Voir aussi  
 [La mise à niveau à partir d’une Version précédente de l’authentification unique](../core/upgrading-from-a-previous-version-of-sso.md)