---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae4b5c1f-1718-4628-9159-2fb877498913
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 472893a2a65d762f17747dac78b67b373165c0cf
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a>Configuration requise pour l'authentification unique
Pour utiliser l’authentification unique (SSO), vous devez :  
  
-   BizTalk Server
  
-   Visual Studio  
  
-   Enterprise Single Sign-On  
  
-   Un système de serveur prenant en charge SSO  
  
 L’hôte isolé doit être configuré comme approuvé par authentification.  
  
## <a name="enable-sso"></a>Activer l’authentification unique  
  
1.  Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.  
  
2.  Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.  
  
 Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications2.md).  
  
> [!NOTE]
>  Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**. Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets SSO](../core/running-sso-projects1.md)   
 [Utilisation de l’authentification unique](../core/using-single-sign-on2.md)