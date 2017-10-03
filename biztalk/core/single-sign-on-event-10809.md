---
title: "Single Sign-On : Événement 10809 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7331d12b-1000-4a60-83b3-f092968e0e51
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e010c6ee391e72ec270ddbdc767bed861836cb8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10809"></a>Single Sign-On : Événement 10809
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10809|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_HISSO_APP_NOT_ENABLED|  
|Texte du message|L'application n'est pas activée pour l'authentification unique initiée par l'hôte.|  
  
## <a name="explanation"></a>Explication  
 L'application n'est pas activée pour l'authentification unique initiée par l'hôte.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez les outils d'administration pour configurer l'authentification unique initiée par l'hôte. Cette action permet de définir l'indicateur  
  
 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS sur l'application.