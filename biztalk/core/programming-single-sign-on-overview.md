---
title: "Présentation de l’authentification unique de programmation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a0a3978-cdbf-4703-9d1d-23e0f4923c9c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5f8ffa7463e4c1fbdd7231cf87abea751fea3d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="programming-single-sign-on-overview"></a>Présentation de l’authentification unique de programmation
Un processus d'entreprise qui repose sur diverses applications est en général confronté au défi que représentent plusieurs domaines de sécurité différents. L'accès à une application sous un système d'exploitation Microsoft Windows peut requérir un ensemble particulier d'informations d'identification destinées à garantir la sécurité, tandis que l'accès à une application située sur un macroordinateur IBM est susceptible d'être dépendant d'autres informations d'identification. Cette profusion d’informations d’identification est difficile pour les utilisateurs, et il peut présenter un défi supérieur pour automatiser les processus. Pour résoudre ce problème, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut Enterprise Single Sign-On (SSO). Cette fonction d'authentification unique de l'entreprise permet de mapper un ID utilisateur Windows avec les informations d'identification d'un utilisateur non-Windows. Ce service peut simplifier les processus d'entreprise qui utilisent des applications installées sur des systèmes différents.  
  
 Pour employer l'authentification unique de l'entreprise, un administrateur doit définir des applications associées représentant chacune un système ou une application non-Windows. Il peut s'agir d'une application CICS (Customer Information Control System) exécutée sur un macroordinateur IBM, d'un système ERP SAP fonctionnant sous UNIX ou de tout autre type de logiciel. Chacune de ces applications possède son propre mécanisme d'authentification et nécessite donc des informations d'identification uniques et personnalisées.  
  
 La fonction d'authentification unique de l'entreprise stocke un mappage chiffré entre l'ID utilisateur Windows d'un utilisateur et les informations d'identification correspondantes d'une ou plusieurs applications associées. Ces paires reliées sont stockées dans une base de données d'authentification unique. La fonction d'authentification unique utilise la base de données d'authentification unique de deux manières. La première méthode, appelée *initiée par Windows Single Sign-On*, utilise l’ID d’utilisateur pour déterminer à quelles applications associées, l’utilisateur a accès. Par exemple, un compte d'utilisateur Windows peut être lié à des informations d'identification donnant accès à une base de données DB2 exécutée sur un serveur AS/400 distant. La deuxième méthode, appelée *initiée par l’hôte Single Sign-On*, agit dans le sens inverse : déterminer quelles applications distantes ont accès à un ID d’utilisateur spécifié et les privilèges associés à ce compte. Par exemple, une application distante peut être liée à des informations d'identification donnant accès à un compte d'utilisateur ayant des privilèges d'administration sur un réseau Windows.  
  
 Notez que l'authentification unique inclut en outre des outils d'administration grâce auxquels vous pouvez effectuer diverses opérations. Toutes les opérations exécutées sur la base de données d'authentification unique sont auditées. Par exemple, des outils sont fournis afin de permettre à un administrateur de surveiller ces opérations et de définir divers niveaux d'audit. D'autres outils permettent à un administrateur de désactiver une application associée en particulier, d'activer ou de désactiver un mappage spécifique pour un utilisateur et d'effectuer d'autres fonctions. Un programme client permet également aux utilisateurs finaux de définir leurs propres informations d'identification et mappages.  
  
 L'une des conditions administratives requises pour l'authentification unique de l'entreprise est que votre système local doit connaître les informations d'identification nécessaires à la connexion à un système distant. De même, le système distant doit connaître les informations d'identification de votre système local. Par conséquent, lorsque vous avez mis à jour vos informations d'identification, par exemple lorsque vous avez modifié votre mot de passe sur votre ordinateur local, vous devez également informer les systèmes distants que vous avez procédé de la sorte. Le composant de conception qui synchronise les mots de passe dans l’entreprise est appelé un *adaptateur de synchronisation de mot de passe*.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Interface de l’authentification unique](../core/single-sign-on-interface.md)  
  
 [Applications à authentification uniques](../core/single-sign-on-applications.md)  
  
 [Éléments à connaître avant de programmer l’authentification unique](../core/what-you-should-know-before-programming-single-sign-on.md)  
  
 [Plateformes prises en charge pour l’authentification unique](../core/supported-platforms-for-single-sign-on.md)