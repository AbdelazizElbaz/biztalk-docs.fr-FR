---
title: Comment activer l’authentification unique | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], creating
- SSO, enabling
- maps [SSO], creating
- managing [SSO], enabling
- SSO, maps
- SSO, applications
- creating, applications [SSO]
- managing [SSO], creating affiliate applications
ms.assetid: dda89d15-6b70-4c40-b658-2f6cbdd545c8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a843c0f6cdea32ba5218140069163058fcd42442
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-enable-sso"></a>Comment activer l’authentification unique
Vous pouvez activer le système d'authentification unique à l'aide du composant logiciel enfichable MMC ou de la ligne de commande.  
  
 Après avoir exécuté la commande d'activation, il y a un court délai avant l'activation de tous les serveurs d'authentification unique, le temps que chaque serveur interroge la base de données SSO pour obtenir les dernières informations globales.  
  
 Si vous souhaitez configurer les applications associées et les mappages du système SSO, vous devez également créer une application associée. Après la création d'une application associée par un administrateur SSO, un administrateur d'application peut y apporter des modifications, et les utilisateurs d'application (utilisateurs finaux) peuvent créer leurs propres mappages. Pour plus d’informations, consultez [la gestion des Applications associées](../core/managing-affiliate-applications.md) et [gestion des mappages d’utilisateur](../core/managing-user-mappings.md).  
  
### <a name="to-enable-the-sso-system-using-the-mmc-snap-in"></a>Pour activer le système SSO à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **activer**.  
  
### <a name="to-enable-the-sso-system-using-the-command-line"></a>Pour activer le système SSO à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – enablesso**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-enable-sso-to-create-affiliate-applications-and-mappings"></a>Pour activer SSO en vue de créer des applications associées et des mappages  
  
1.  Connectez-vous en tant qu'administrateur SSO ou administrateur d'applications associées à SSO au serveur SSO, ou sur un ordinateur hébergeant des sous-services d'administration SSO.  
  
2.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
3.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - enablesso** pour activer le service Enterprise Single Sign-On.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Connectez-vous en tant qu'administrateur d'applications associées à SSO.  
  
6.  Type **ssomanage - createapps *\<fichier de l’application\>***  pour créer une application associée, où \<fichier de l’application\> est le fichier XML qui contient des définitions pour les applications associées.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le serveur d’authentification unique](../core/how-to-set-the-sso-server.md)   
 [Comment désactiver l’authentification unique](../core/how-to-disable-sso.md)   
 [Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md)   
 [Utilisation de l’authentification unique](../core/using-sso.md)