---
title: "Single Sign-On : Événement 10615 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5dd0041-2dfd-4fd1-97ec-f9fc719a6fcc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9570290f82821a80d22826f41d4ed669e29f5b4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10615"></a>Single Sign-On : Événement 10615
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10615|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NO_UPDATE_TICKET_TIMEOUT|  
|Texte du message|L'utilisateur client doit être membre du compte Administrateurs SSO pour pouvoir modifier le délai d'attente du ticket relatif à une application.%r<br /><br /> L’utilisateur client : %1 %r<br /><br /> Les administrateurs SSO : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur client doit être membre du compte Administrateurs SSO pour pouvoir modifier le délai d'attente du ticket relatif à une application.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour pouvoir procéder à cette modification, demandez à votre administrateur système de vous indiquer un membre du compte Administrateurs SSO.