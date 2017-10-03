---
title: Enterprise Single Sign-On (SSO) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- SSO
ms.assetid: beab96f7-f026-4ae1-8462-a165ad76bbec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6cbc5f514d13cd8457cd9417be5ea5b78408e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enterprise-single-sign-on-sso"></a>Authentification unique de l'entreprise (SSO)
Enterprise Single Sign-On (SSO) fournit des services pour stocker et transmettre chiffrée des informations d’identification de l’utilisateur entre les locaux et les limites du réseau, y compris les limites de domaine. Les informations d'identification sont stockées dans la base de données de l'authentification unique. Dans la mesure où l'authentification unique fournit une solution générique, les applications intermédiaires et les adaptateurs personnalisés peuvent s'appuyer sur l'authentification unique pour sécuriser le stockage et la transmission des informations d'identification de l'utilisateur dans l'intégralité de l'environnement. Les utilisateurs finaux peuvent accéder aux différentes applications sans avoir à se souvenir de plusieurs informations d'identification.  
  
 Le système d'authentification unique est constitué d'une base de données de l'authentification unique, d'un serveur de secret principal ainsi que d'un ou de plusieurs serveurs de l'authentification unique.  
  
 Le système d’authentification unique contient *applications associées* définies par l’administrateur. Un *application associée* est une entité logique représentant un système ou sous-système tel qu’un hôte, un système principal ou une application métier à laquelle vous êtes connecté à l’aide de Enterprise Single Sign-On. Chaque application associée est dotée de plusieurs mappages d'utilisateurs. Elle dispose, par exemple, des mappages entre les informations d'identification d'un utilisateur utilisées par Active Directory et par RACF.  
  
 La base de données de l'authentification unique correspond à la base de données SQL Server qui stocke les informations relatives aux applications associées, ainsi que les informations d'identification chiffrées de l'utilisateur destinées à toutes les applications associées.  
  
 Le *serveur de secret principal* est le serveur Enterprise Single Sign-On qui stocke le secret principal. Tous les autres serveurs d'authentification unique présents dans le système extraient le secret principal à partir de ce serveur.  
  
 Le système d'authentification unique contient également un ou plusieurs serveurs d'authentification unique. Ces derniers effectuent le mappage entre les informations d'identification Microsoft Windows et principales, et ils recherchent ces informations d'identification dans la base de données d'authentification unique. Les administrateurs les utilisent pour assurer la gestion du système d'authentification unique.  
  
 Pour plus d’une étude complète à Enterprise Single Sign-On, consultez [présentation SSO](../core/understanding-sso.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’exécution](../core/runtime-architecture.md)