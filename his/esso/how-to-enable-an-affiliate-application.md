---
title: Comment activer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 051bc35f-55e6-4811-9559-b1bb66a570ce
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 53dcd9886bc808f84b112146971a6f9519c404e2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-enable-an-affiliate-application"></a>Comment activer une Application associée
Vous pouvez utiliser le composant logiciel enfichable MMC ou la **enableapp** commande pour activer l’application associée spécifiée.  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a>Pour activer une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur l’application associée, puis cliquez sur **activer**.  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a>Pour activer une application associée à l'aide d'une ligne de commande  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –enableapp <application name>`, où \< *nom de l’application*> est le nom de l’application associée que vous souhaitez activer.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../esso/sso-affiliate-applications.md)   
 [Comment créer une Application associée](../esso/how-to-create-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)   
 [Gestion des applications associées](../esso/managing-affiliate-applications.md)