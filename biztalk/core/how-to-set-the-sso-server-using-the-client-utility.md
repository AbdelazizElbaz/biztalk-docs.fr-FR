---
title: "Comment configurer le serveur d’authentification unique à l’aide de l’utilitaire Client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], selecting servers
- managing [SSO applications], selecting servers
- SSOClient [SSO], selecting servers
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d917114d21ceed37eb68ee4bb9503aac97735ffa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a>Comment configurer le serveur d’authentification unique à l’aide de l’utilitaire Client
Chaque fois que vous utilisez ssoclient, vous devez commencer par pointer l'utilisateur sur le serveur d'authentification unique approprié contenant ses informations de configuration.  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a>Pour définir le serveur d'authentification unique pour un utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – serveur  *\<serveur d’authentification unique >***, où \< *serveur d’authentification unique >* est le nom de l’authentification unique serveur de l’utilisateur veut se connecter.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)