---
title: "Comment activer une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], enabling
- managing [SSO applications], enabling
- enabling, applications [SSO]
ms.assetid: 81c94e1b-cd3d-482e-9a78-9b1476af9e5f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a0e4776b60b81256552552c60aa1abb8abdcde8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-an-affiliate-application"></a>Comment activer une Application associée
Le composant logiciel enfichable MMC ou la ligne de commande permet d'activer l'application associée spécifiée.  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a>Pour activer une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur l’application associée, puis cliquez sur **activer**.  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a>Pour activer une application associée à l'aide d'une ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-enableapp  *\<nom de l’application\>***, où \< *nom de l’application* \> est le nom de l’application associée que vous souhaitez activer.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Comment créer une Application associée](../core/how-to-create-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des applications associées](../core/managing-affiliate-applications.md)