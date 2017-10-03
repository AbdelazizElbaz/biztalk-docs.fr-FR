---
title: "Contrôle d’accès pour les rôles d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roles, administrative
- administrator accounts, administrative roles
- administrative roles
- access control, administrative roles
ms.assetid: 328e049b-921d-4057-85f0-7d008ec308bb
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfc7b1891cd266457af97c18f2ad6220145e00ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="access-control-for-administrative-roles"></a>Contrôle d’accès pour les rôles d’administration
Quand un utilisateur ouvre un outil de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] nécessitant un accès aux bases de données ou à des ressources Windows, il doit disposer des droits d'utilisateur SQL Server et Windows appropriés pour l'exécution des différentes tâches que cet outil prend en charge.  
  
 Certains outils de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accèdent aux bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Par conséquent, BizTalk Server doit attribuer aux administrateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] un certain niveau d'accès dans chaque base de données. Par ailleurs, pour de raisons de sécurité, les administrateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne doivent pas disposer de plus de droits d'utilisateur qu'il n'en faut pour exécuter leur travail. Grâce aux rôles de base de données SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut répondre à ces deux exigences. Chaque fois que vous créez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données via l’installation ou la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée automatiquement des rôles de base de données SQL Server pour ces deux rôles d’administration dans cette base de données. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]accorde à chaque rôle et toute connexion SQL Server affecté au rôle, les droits d’utilisateur minimaux requis par les administrateurs sur les objets SQL Server (tables, vues, procédures stockées, etc.) pour effectuer des tâches administratives sur cette base de données.  
  
> [!NOTE]
>  Certaines tâches administratives, telles que la création d'instances de l'hôte, exigent que les administrateurs de BizTalk disposent de plus d'autorisations que celles qui leur sont attribuées via les rôles SQL Server. Pour plus d’informations sur ces autorisations supplémentaires, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il existe deux rôles d’administration : le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrateur et le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] opérateur. Le rôle administrateur de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dispose de privilèges élevés lui donnant accès à des données de configuration et de suivi. Le rôle opérateur de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage. Le groupe Opérateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   est un rôle administratif disposant de privilèges restreints, sans accès aux données de message ;  
  
-   permet à ses membres de surveiller [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour identifier des erreurs, interroger des messages ou instances suspendus, et consulter la configuration ;  
  
-   empêche ses membres de modifier la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Par exemple, les opérateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peuvent pas modifier des ports d'envoi, des emplacements de réception ou des filtres sur des ports, ni déployer de nouveaux artefacts.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée le rôle administrateur de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par défaut lorsque vous installez le produit pour la première fois. Par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] appelle ce rôle Administrateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], mais vous pouvez choisir un autre nom.  
  
 De même, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée, dans chaque base de données, un rôle de base de données SQL Server pour le groupe d'utilisateurs pour chaque hôte, et attribue à ce rôle les droits d'utilisateur minimaux nécessaires pour que le groupe d'utilisateurs puisse effectuer des tâches pour cet hôte. Vous devez ajouter le rôle Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au groupe d'administrateurs d'applications associées à authentification unique. Pour plus d’informations sur Enterprise Single Sign-On, consultez [à l’aide de l’authentification unique](../core/using-sso.md).  
  
> [!CAUTION]
>  Les administrateurs de BizTalk doivent veiller à approuver la source de l'assembly qu'ils comptent déployer dans le système. S’ils déploient des assemblys avec le code que vous ne faites pas confiance, ils risquent d’exposer l’environnement BizTalk à des attaques potentielles. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]n’applique pas les restrictions sur les actions que les composants de code personnalisé peuvent effectuer lorsque le moteur BizTalk les appelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md)   
 [Groupes et comptes d’utilisateur Windows dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)