---
title: "Contrôle d’accès et sécurité des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access control, BizTalk Server Operator role
- databases, SQL roles
- access control, about access control
- BizTalk Server Administrator role
- databases, access control
- access control
- access control, BizTalk Server Administrator role
- access control, SQL roles
- user accounts, access control
- BizTalk Server Operator role
ms.assetid: f04fd4a3-0f8c-4170-934a-9cc77edd7f34
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11cb00eabf6110de78e2d194e0a25bfac6a3b6b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="access-control-and-data-security"></a>Contrôle d’accès et sécurité des données
BizTalk Server restreint l'accès à ses processus et bases de données en attribuant des droits d'utilisateur minimaux. Vous pouvez ainsi sécuriser certaines données stratégiques du système à l'aide de fonctionnalités de Microsoft Windows Server. Pour des raisons de sécurité, les administrateurs de BizTalk Server et les hôtes BizTalk ne doivent pas disposer de plus de droits d'utilisateur qu'il n'en faut pour exécuter leur travail.  
  
 BizTalk contrôle l'accès administratif aux données à l'aide des rôles SQL, par l'intermédiaire d'outils et directement dans la base de données. Le contrôle de l'accès des hôtes BizTalk aux données s'effectue à l'aide des groupes d'utilisateurs d'hôtes et des comptes.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il existe deux rôles d’administration : l’administrateur du serveur BizTalk et l’opérateur de BizTalk Server. Chaque fois que vous créez une base de données BizTalk Server dans le cadre d'une installation ou via la console Administration de BizTalk Server, BizTalk Server crée automatiquement des rôles SQL pour ces deux rôles d'administration dans cette base de données. BizTalk Server attribue à chaque rôle et à tout compte de connexion SQL Server qui lui est associé les droits d'utilisateur minimaux sur les objets SQL Server (tables, vues, procédures stockées, etc.) dont les administrateurs ont besoin pour effectuer des tâches administratives sur cette base de données.  
  
 Le rôle administrateur de BizTalk Server dispose de privilèges élevés lui donnant accès à des données de configuration et de suivi. Le rôle opérateur de BizTalk Server dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage. Ce deuxième rôle peut visualiser l'état du service et le flux de message, démarrer ou arrêter des applications et terminer et rétablir des instances de service. Il ne permet pas de modifier la configuration ou d'afficher les propriétés de message ou le contenu.  
  
 De même, BizTalk Server crée, dans chaque base de données, un rôle SQL pour le groupe d'utilisateurs pour chaque hôte, et attribue à ce rôle les droits d'utilisateur minimaux nécessaires pour que le groupe d'utilisateurs puisse effectuer des tâches pour cet hôte.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Groupes et comptes d’utilisateur Windows dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)  
  
-   [Contrôle d’accès pour les groupes et comptes de Service](../core/access-control-for-groups-and-service-accounts.md)  
  
-   [Contrôle d’accès pour les rôles d’administration](../core/access-control-for-administrative-roles.md)  
  
-   [Contrôle d’accès aux informations de l’entreprise](../core/access-control-to-business-information.md)  
  
-   [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)