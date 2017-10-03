---
title: "Single Sign-On : Événement 11049 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 031ec1a6-4b2b-46b2-9dbb-5525d758651f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45ac6095950e02e7e73ab287b180bc22d88b4191
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11049"></a>Single Sign-On : Événement 11049
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11049|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_DTC_FAILED|  
|Texte du message|Impossible de détecter MSDTC. L'authentification unique requiert MSDTC pour fonctionner correctement.|  
  
## <a name="explanation"></a>Explication  
 Le système d'authentification unique de l'entreprise n'a pas pu se connecter à Microsoft Distributed Transaction Coordinator (MSDTC).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez si MSDTC est actuellement opérationnel.  
  
 Pour obtenir de l’aide sur les problèmes MSDTC, consultez [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).