---
title: "Configuration requise de l’authentification unique pour l’adaptateur TIBCO Rendevous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40cf27a3b96534239fa871bd04b90febee9beafe
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a>Configuration requise pour l'authentification unique

## <a name="prerequisites"></a>Conditions préalables
Pour utiliser l'authentification unique (SSO), vous devez disposer des éléments suivants :  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   Enterprise Single Sign-On  
  
-   Un système de serveur qui prend en charge l’authentification unique  
  
-   L’hôte isolé doit être configuré comme approuvé par authentification.  
  
## <a name="enable-sso"></a>Activer l’authentification unique  
  
1.  Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.  
  
2.  Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.  
  
 Pour plus d’informations, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).  
  
> [!NOTE]
>  Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**. Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
[Sécurité](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)