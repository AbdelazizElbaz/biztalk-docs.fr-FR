---
title: "Single Sign-On : Événement 10850 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e2af52-d35b-491a-a983-d80442dd6aef
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e9bef6d104b8da3c41d295005a7a274a1d2610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10850"></a>Single Sign-On : Événement 10850
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10850|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE|  
|Texte du message|Une application ne peut pas être créée avec l'indicateur « enabled » spécifié.|  
  
## <a name="explanation"></a>Explication  
 Avant d'activer une application, il est nécessaire de créer l'application et d'entrer des informations dans ses champs (UserID et Password). Il n'est pas possible de créer une application avec le champ « enabled » déjà activé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Créez à nouveau l'application (à l'aide de l'API Création d'une application ou de l'Assistant Création d'une application associée). Lorsque cette application est terminée et les champs renseignés, activez l'application.