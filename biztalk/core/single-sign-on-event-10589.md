---
title: "Single Sign-On : Événement 10589 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe962bb-e9bb-4107-a5fb-21c180d54e21
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56bb848711a627ceaea70085d770db7b0c759e9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10589"></a>Single Sign-On : Événement 10589
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10589|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_BACKUP_SECRET_REQUIRED|  
|Texte du message|Le secret principal n'a pas été sauvegardé. Si vous perdez le secret principal, toutes les informations stockées dans le système d'authentification unique seront définitivement perdues et il se peut que vos systèmes ne fonctionnent pas correctement. Utilisez les outils d'administration de l'authentification unique pour sauvegarder votre secret principal.|  
  
## <a name="explanation"></a>Explication  
 Le secret principal n'a pas été sauvegardé. Si vous perdez le secret principal, toutes les informations stockées dans le système d'authentification unique seront définitivement perdues et il se peut que vos systèmes ne fonctionnent pas correctement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour plus d’informations sur la sauvegarde du secret, consultez [gestion du Secret](../core/managing-the-master-secret.md).