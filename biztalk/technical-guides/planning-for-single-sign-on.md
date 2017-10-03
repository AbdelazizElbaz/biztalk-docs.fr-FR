---
title: "Planification de l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d1bc220-4087-4603-ac15-6bb0c62c59d4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bc35c53193ac8e48c9169131b637dc1d7a581fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-single-sign-on"></a>Planification de l’authentification unique
Enterprise Single Sign-On (SSO) est un composant essentiel de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moment de l’exécution ne peut pas fonctionner sans le service de l’authentification unique, car tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les informations de configuration de l’adaptateur sont chiffrées et stockées dans la base de données SSO et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accède à ces informations via le service d’authentification unique. Informations de configuration de cette carte ne sont pas accessibles si le service d’authentification unique ne fonctionne pas sur le serveur BizTalk server ou si le service d’authentification unique n’a pas accès au serveur de secret principal SSO.  
  
 Votre implémentation de l’authentification unique doit inclure les plans suivants.  
  
## <a name="backing-up-the-master-secret"></a>Sauvegarde du Secret principal  
 Si le serveur de secret principal SSO échoue et que vous perdez la clé, ou si celle-ci est endommagée, vous ne serez pas en mesure de récupérer les données stockées dans la base de données SSO. Vous devez sauvegarder le secret principal, sans quoi vous risquez de perdre les données figurant dans la base de données SSO. Par conséquent, il est absolument essentiel que le secret principal SSO est sauvegardé et stocké dans un emplacement sécurisé. Pour plus d’informations sur la sauvegarde du secret de l’authentification unique, consultez [comment revenir Up the Master Secret](http://go.microsoft.com/fwlink/?LinkId=151395) (http://go.microsoft.com/fwlink/?LinkId=151395).  
  
## <a name="configuring-sso-for-high-availability"></a>Configuration de l’authentification unique pour la haute disponibilité  
 Étant donné que l’authentification unique est ce type d’un composant essentiel d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, le serveur de secret principal SSO doit être configuré pour la haute disponibilité. Si possible, le service Enterprise Single Sign-On sur le serveur de secret principal doit être mis en cluster en suivant les étapes dans [Clustering du serveur de secret principal](../technical-guides/clustering-the-master-secret-server.md). Si vous n’avez pas l’accès à un cluster Windows Server, vous pouvez toujours fournir une haute disponibilité pour le service Enterprise Single Sign-On sur le serveur de secret principal en suivant les étapes décrites dans la rubrique [désignant un nouveau masque Serveur de secret principal manuellement](../technical-guides/designating-a-new-master-secret-server-manually.md).  
  
## <a name="following-established-sso-security-recommendations"></a>Recommandations de sécurité suivantes établie de l’authentification unique  
 Suivez les recommandations de sécurité pour l’authentification unique décrites dans la rubrique [recommandations de sécurité pour l’authentification unique](http://go.microsoft.com/fwlink/?LinkId=155753) (http://go.microsoft.com/fwlink/?LinkId=155753).