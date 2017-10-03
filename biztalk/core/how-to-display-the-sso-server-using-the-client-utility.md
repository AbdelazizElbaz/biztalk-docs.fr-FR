---
title: "Comment afficher le serveur d’authentification unique à l’aide de l’utilitaire Client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], viewing servers
- managing [SSO applications], viewing servers
- SSOClient [SSO], viewing servers
ms.assetid: af79ad96-6d94-48e0-9c80-6f0e38a3b8ac
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11d6845711c03209085803134fbfdef1fa32ca55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-the-sso-server-using-the-client-utility"></a>Comment afficher le serveur d’authentification unique à l’aide de l’utilitaire Client
Cette commande permet d'afficher le serveur d'authentification unique sur lequel l'utilisateur pointe actuellement.  
  
### <a name="to-display-the-sso-server-using-the-client-utility"></a>Pour afficher le serveur d'authentification unique à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – showserver**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)