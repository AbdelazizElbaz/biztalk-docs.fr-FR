---
title: "Comment activer SSL pour l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, SSL
- managing [SSO], enabling SSL
- SSL
ms.assetid: 0d75962a-a0b0-4e69-8001-54e7df617006
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ae2f3840cd2620f9c03a5b207b32d8bbd4feee9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-ssl-for-sso"></a>Comment activer SSL pour l’authentification unique
Cette commande permet d'activer le protocole SSL (Secure Sockets Layer) entre les serveurs d'authentification unique de l'entreprise et la base de données SSO.  
  
### <a name="to-enable-ssl-for-enterprise-single-sign-on"></a>Pour activer le protocole SSL pour l'authentification unique de l'entreprise  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoconfig – setSSL \<Oui/non >**, où \< **Oui/non**> indique si vous souhaitez activer le protocole SSL dans le système d’authentification unique.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-sso.md)