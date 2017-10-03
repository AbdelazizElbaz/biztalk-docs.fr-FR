---
title: "Single Sign-On : Événement 10565 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d279491-dc0d-44c4-a77e-a67498a3481d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9567421210689d8615cf88e7fbd6493ef5749d02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10565"></a>Single Sign-On : Événement 10565
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10565|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_SECRET_VALIDATE_FAILED|  
|Texte du message|Le secret n'a pas pu être chargé à partir du Registre. Il se peut que le compte du service d'authentification unique ait été modifié ou que le secret soit endommagé. Restaurez le secret à partir d'un fichier de sauvegarde.%r<br /><br /> MSID : %1|  
  
## <a name="explanation"></a>Explication  
 Un administrateur du système a probablement modifié le compte du service d'authentification unique, ce qui rend le déchiffrement impossible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Recherchez la personne qui a modifié le compte du service d'authentification unique, puis restaurez le secret à partir d'un fichier de sauvegarde. Pour plus d’informations sur la restauration de la clé secrète, consultez [gestion du Secret](../core/managing-the-master-secret.md).