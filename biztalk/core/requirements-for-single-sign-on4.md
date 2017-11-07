---
title: "Configuration requise de l’authentification unique pour l’adaptateur TIBCO EMS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 805d14e056da665f8828ce0244f28ed9adc40ff4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a>Configuration requise pour l'authentification unique

## <a name="overview"></a>Vue d'ensemble
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) prend en charge l'authentification unique (SSO). Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente un système serveur tel que TIBCO EMS.  
  
 Pour utiliser l'authentification unique, vous devez disposer des éléments suivants :  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   Enterprise Single Sign-On  
  
-   Un système de serveur qui prend en charge l’authentification unique  
  
 L’hôte isolé doit être configuré comme approuvé par authentification.
  
## <a name="enable-sso"></a>Activer l’authentification unique  
  
1.  Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.  
  
2.  Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.  
  
     Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).  
  
    > [!NOTE]
    >  Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**. Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-tibco-ems.md)