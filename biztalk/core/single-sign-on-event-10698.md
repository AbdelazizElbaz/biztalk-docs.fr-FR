---
title: "Single Sign-On : Événement 10698 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f467934d-fef5-4962-a341-18f272d84108
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ca4d65927e7e9d01f7c73eb64a19bc613496f5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10698"></a>Single Sign-On : Événement 10698
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10698|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_INFO_REPLAY_FILE_DELETED|  
|Texte du message|Le fichier de reprise ou de progression a été supprimé.%r<br /><br /> Nom du fichier : %1|  
  
## <a name="explanation"></a>Explication  
 Cette information indique que le système SSO a supprimé un fichier de reprise et/ou de progression.  
  
 Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO. Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Aucune action utilisateur n’est nécessaire.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)