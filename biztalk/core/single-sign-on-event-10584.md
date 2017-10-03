---
title: "Single Sign-On : Événement 10584 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8af9377d-b4fd-48a6-961a-3629b3db644a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d08be0100d53f081eb7d8f4faa27d1e7f46f6f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10584"></a>Single Sign-On : Événement 10584
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10584|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NO_IMPERSONATION|  
|Texte du message|Impossible d'emprunter l'identité du client.%r<br /><br /> Code d’erreur : %1|  
  
## <a name="explanation"></a>Explication  
 Le système d'authentification unique de l'entreprise emprunte l'identité du client pour la vérifier. Diverses causes peuvent expliquer le fait que le système ne parvienne pas à effectuer cette opération. Il se peut que le client tente d'effectuer une activité inhabituelle ou d'infiltrer la sécurité du système, ou que l'application cliente ait été conçue pour bloquer l'emprunt d'identité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Localisez l'application cliente, puis déterminez ce qu'elle tente de faire et si elle bloque ou non l'emprunt d'identité.