---
title: "Comment répertorier les Applications associées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], listing applications
- applications [SSO], listing applications
ms.assetid: b51ff597-824e-4488-a47f-3a9b3d4437c6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6c4d4e4118bfe5f5cab7a9c44e770dd12656c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-affiliate-applications"></a>Comment répertorier les Applications associées
Cette commande permet de répertorier toutes les applications associées. Si l'utilisateur est membre du compte Administrateurs d’application, cette commande affiche uniquement l'application dont il est administrateur.  
  
### <a name="to-list-affiliate-applications-using-the-administration-utility"></a>Pour répertorier les applications associées à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage - listapps [all]** où **tous les** est un paramètre optionnel qui affiche également des applications à l’aide de la fonctionnalité de magasin de Configuration. Si l'utilisateur exécutant cette commande est un administrateur d'applications, la commande répertorie uniquement les applications dont il est administrateur. Si l’utilisateur qui exécute cette commande est un administrateur d’applications associées ou un administrateur SSO, il répertorie toutes les applications associées.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-list-affiliate-applications-using-the-client-utility"></a>Pour répertorier les applications associées à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – listapps** pour répertorier les applications associées. Cela a pour effet de répertorier uniquement les applications associées dont l'utilisateur exécutant cette tâche est membre. Par exemple, l'utilisateur doit appartenir au compte du groupe d'utilisateurs de l'application pour cette application associée.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Comment créer une Application associée](../core/how-to-create-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des applications associées](../core/managing-affiliate-applications.md)