---
title: "Présentation de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- Windows Integrated Single Sign-On
- Extranet Single Sign-On (Web SSO)
- Server-Based Intranet Single Sign-On
ms.assetid: 03f78a7b-4880-408f-9733-d07e19775d21
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736fee720f2abf0dd051b1f754dd0fd6b8c42ab6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-sso"></a>Présentation de l’authentification unique
Pour comprendre Enterprise Single Sign-On, il est judicieux d’examiner les trois types d’authentification unique sur les services disponibles aujourd'hui : Windows intégrée, extranet et intranet. Ceux-ci sont décrits ci-dessous, l'authentification unique de l'entreprise appartenant à la troisième catégorie.  
  
## <a name="windows-integrated-single-sign-on"></a>Authentification unique Windows intégrée  
 Ces services permettent de se connecter à plusieurs applications de votre réseau qui utilisent une méthode d'authentification commune. Lorsque vous êtes connecté au réseau, ils vérifient vos informations d'identification et utilisent celles-ci pour déterminer les actions que vous pouvez exécuter en fonction de vos droits d'utilisateur. Par exemple, si les applications sont intégrées à l'aide de Kerberos, une fois vos informations d'identification authentifiées par le système, vous pouvez accéder à toutes les ressources du réseau intégré à Kerberos.  
  
## <a name="extranet-single-sign-on-web-sso"></a>Authentification unique extranet (via le Web)  
 Ces services permettent d'accéder à des ressources via Internet à l'aide d'un ensemble unique d'informations d'identification. L'utilisateur fournit des informations d'identification qui permettent d'ouvrir une session sur différents sites Web appartenant à différentes organisations. C'est le cas par exemple de Windows Live ID pour les applications destinées aux consommateurs. Dans le cadre des scénarios fédérés, les services AFDS (Active Directory Federation Services) activent l'authentification unique via le Web.  
  
## <a name="server-based-intranet-single-sign-on"></a>Authentification unique via un serveur intranet  
 Ces services permettent d'intégrer plusieurs applications et systèmes hétérogènes au sein de l'environnement de l'entreprise. Ceux-ci peuvent ne pas utiliser l'authentification commune. Chaque application possède son propre magasin d'annuaires d'utilisateurs. Par exemple, pour authentifier les utilisateurs d'une organisation, Windows utilise le service d'annuaire Active Directory et les macroordinateurs utilisent RACF (Resource Access Control Facility) d'IBM. Au sein de l'entreprise, les applications intermédiaires intègrent les applications principales et frontales. L'authentification unique de l'entreprise permet aux utilisateurs de l'entreprise de se connecter aux deux types d'applications à l'aide d'un seul ensemble d'informations d'identification. Ainsi, aussi bien l'authentification unique initiée par Windows (demande initiale effectuée à partir de l'environnement du domaine Windows) que l'authentification unique initiée par l'hôte (demande initiale effectuée à partir de l'environnement d'un domaine non-Windows) sont en mesure d'accéder à une ressource dans le domaine Windows.  
  
 En outre, **synchronisation de mot de passe** simplifie l’administration de la base de données SSO et synchronise les mots de passe sein des annuaires d’utilisateurs. Pour ce faire, il est nécessaire d'utiliser les adaptateurs de synchronisation de mots de passe, que vous pouvez configurer et gérer à l'aide des outils de synchronisation de mots de passe.  
  
## <a name="the-enterprise-single-sign-on-system"></a>Système d'authentification unique de l'entreprise  
 Enterprise Single Sign-On (SSO) fournit des services pour stocker et transmettre chiffrée des informations d’identification de l’utilisateur entre les locaux et les limites du réseau, y compris les limites de domaine. Les informations d'identification sont stockées dans la base de données de l'authentification unique. Dans la mesure où l'authentification unique fournit une solution générique, les applications intermédiaires et les adaptateurs personnalisés peuvent s'appuyer sur l'authentification unique pour sécuriser le stockage et la transmission des informations d'identification de l'utilisateur dans l'intégralité de l'environnement. Les utilisateurs finaux peuvent accéder aux différentes applications sans avoir à se souvenir de plusieurs informations d'identification.  
  
 Le système d'authentification unique est constitué d'une base de données de l'authentification unique, d'un serveur de secret principal ainsi que d'un ou de plusieurs serveurs de l'authentification unique.  
  
 Le système d'authentification unique contient des applications associées définies par l'administrateur. Une application associée constitue une entité logique représentant un système ou un sous-système tel qu'un hôte, un système principal ou une application sectorielle à laquelle vous êtes connecté via l'authentification unique de l'entreprise. Chaque application associée est dotée de plusieurs mappages d'utilisateurs. Elle dispose, par exemple, des mappages entre les informations d'identification d'un utilisateur utilisées par Active Directory et par RACF.  
  
 La base de données SSO correspond à la base de données SQL Server qui stocke les informations relatives aux applications associées, ainsi que les informations d'identification chiffrées de l'utilisateur destinées à toutes les applications associées.  
  
 Le serveur de secret principal correspond au serveur d'authentification unique de l'entreprise qui stocke le secret principal. Tous les autres serveurs d'authentification unique présents dans le système extraient le secret principal à partir de ce serveur.  
  
 Le système d'authentification unique contient également un ou plusieurs serveurs d'authentification unique. Ces derniers effectuent le mappage entre les informations d'identification Windows et celles de systèmes principaux, recherchent ces informations d'identification dans la base de données SSO et sont utilisés par les administrateurs dans le cadre de la gestion du système d'authentification unique.  
  
> [!NOTE]
>  Votre système d'authentification unique peut inclure uniquement un serveur de secret principal et une base de données SSO. Celle-ci peut être distante du serveur de secret principal.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)  
  
-   [Composants de l’authentification unique](../core/sso-components.md)  
  
-   [Serveur d’authentification unique](../core/sso-server.md)  
  
-   [Serveur de secret principal](../core/master-secret-server.md)  
  
-   [Applications associées SSO](../core/sso-affiliate-applications.md)  
  
-   [Mappages SSO](../core/sso-mappings.md)  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Configuration de l’authentification unique](../core/configuring-sso.md)