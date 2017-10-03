---
title: "Comment définir les informations d’identification de l’Application associée à l’aide de l’utilitaire Client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], configuring credentials
- SSOClient [SSO], configuring credentials
- applications [SSO], credentials
ms.assetid: 454b6257-3538-40be-840c-00172a2c1dce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31ba167bc35d01907166bb6610720e03be654c4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a>Comment définir les informations d’identification de l’Application associée à l’aide de l’utilitaire Client
Cette commande permet de définir les informations d'identification d'un utilisateur pour que celui-ci puisse accéder à une application spécifique. Par ailleurs, elle active automatiquement le mappage.  
  
 Cette commande n'affiche pas le mot de passe durant sa saisie.  
  
 Si le mappage utilisateur existe déjà, cette commande définit les informations d'identification pour le mappage existant. Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.  
  
### <a name="to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a>Pour définir les informations d'identification de l'application associée à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – setcredentials \<nom de l’application >**, où  **\<nom de l’application >** est l’application spécifique pour lequel vous souhaitez définir les informations d’identification.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Lorsque vous êtes invité à indiquer les informations d'identification de l'utilisateur, entrez le mot de passe pour cette application.  
  
5.  Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)