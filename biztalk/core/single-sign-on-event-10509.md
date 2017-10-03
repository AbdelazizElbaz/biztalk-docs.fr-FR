---
title: "Single Sign-On : Événement 10509 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f906823f-db3f-45fc-bf61-cbe6a9566bd7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4d61cbb7af195aa88c36b64149366334c835b80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10509"></a>Single Sign-On : Événement 10509
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10509|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_INFO_SERVICE_REMOVE_FAILED|  
|Texte du message|Impossible de supprimer le service SSO.%r<br /><br /> Code d’erreur : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement indique que la désinstallation du service ENTSSO a échoué. Cet événement peut uniquement survenir lors d'une installation manuelle de l'authentification unique de l'entreprise.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet événement, procédez comme suit :  
  
-   Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées à ENTSSO ou à d'autres services.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [L’installation de l’authentification unique](../core/installing-sso.md)  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)