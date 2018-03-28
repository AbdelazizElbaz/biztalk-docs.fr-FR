---
title: Comment configurer le serveur d’authentification unique à l’aide de l’utilitaire Client | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], selecting servers
- managing [SSO applications], selecting servers
- SSOClient [SSO], selecting servers
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49b2145320bd8e22b01d312d62246fa282fb534e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a>Comment configurer le serveur d’authentification unique à l’aide de l’utilitaire Client
Chaque fois que vous utilisez ssoclient, vous devez commencer par pointer l'utilisateur sur le serveur d'authentification unique approprié contenant ses informations de configuration.  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a>Pour définir le serveur d'authentification unique pour un utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – serveur *\<serveur d’authentification unique\>***, où \<*serveur d’authentification unique\>*  est le nom du serveur d’authentification unique sur le utilisateur souhaite se connecter à.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Gestion des applications associées](../core/managing-affiliate-applications.md)