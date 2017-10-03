---
title: "Configuration requise pour l’authentification unique-le3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, requirements
- SSO, enabling
- Single Sign-On, enabling
- SSO requirements
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 005f095ae09b3018b9c8fe796520205103c7961a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a>Configuration requise pour l'authentification unique
Pour utiliser l'authentification unique (SSO), vous devez disposer des éléments suivants :  
  
-   Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   Enterprise Single Sign-On  
  
-   Un système de serveur qui prend en charge l’authentification unique  
  
-   L’hôte isolé doit être configuré comme approuvé par authentification.  
  
### <a name="to-enable-sso"></a>Pour activer SSO  
  
1.  Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.  
  
2.  Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.  
  
 Pour plus d’informations, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).  
  
> [!NOTE]
>  Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**. Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on5.md)