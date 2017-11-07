---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 318b9977-ce24-48d6-971b-49a059a1bdbc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd2a1fb342911c904044c8099901c5056f17ac9f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a>Configuration requise pour l'authentification unique
Pour utiliser l’authentification unique (SSO), vous devez :  
  
-   Microsoft BizTalk Server 
  
-   Visual Studio  
  
-   Enterprise Single Sign-On  
  
-   Un système de serveur prenant en charge SSO  
  
 L’hôte isolé doit être configuré comme approuvé par authentification.  
  
## <a name="enable-sso"></a>Activer l’authentification unique  
  
1.  Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.  
  
2.  Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.  
  
     Pour plus d’informations sur la création d’applications associées, consultez [création d’Applications associées](../core/creating-affiliate-applications3.md).  
  
    > [!NOTE]
    >  Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser les **partage Web** dossier **ne partagent pas**. La mise à jour ou la désinstallation d'applications utilisant ce dossier ne pourra pas s'effectuer correctement car, s'il est partagé, il est considéré comme en cours d'utilisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de la carte](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)