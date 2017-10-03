---
title: "Single Sign-On : Événement 10808 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b4efc1d-f163-4440-a78e-53065c6af36c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b891a8cb076c332eca8918ece713385c1bbccc3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10808"></a>Single Sign-On : Événement 10808
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10808|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED|  
|Texte du message|L'authentification unique initiée par l'hôte n'est pas activée pour le système d'authentification unique.|  
  
## <a name="explanation"></a>Explication  
 L'authentification unique initiée par l'hôte n'est pas activée pour le système d'authentification unique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez les outils d'administration pour configurer l'authentification unique initiée par l'hôte. Cette action permet de définir l'indicateur  
  
 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS sur les informations globales.