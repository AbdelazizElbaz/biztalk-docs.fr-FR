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
ms.openlocfilehash: 8cd617fd955100930b513bc6c364626e4912eb81
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-ssl-for-sso"></a>Comment activer SSL pour l’authentification unique
Cette commande permet d'activer le protocole SSL (Secure Sockets Layer) entre les serveurs d'authentification unique de l'entreprise et la base de données SSO.  
  
### <a name="to-enable-ssl-for-enterprise-single-sign-on"></a>Pour activer le protocole SSL pour l'authentification unique de l'entreprise  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoconfig – setSSL \<Oui/non\>**, où \< **Oui/non** \> indique si vous souhaitez activer le protocole SSL dans le système d’authentification unique.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’authentification unique](../core/using-sso.md)