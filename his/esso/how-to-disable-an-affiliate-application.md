---
title: Comment désactiver une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7df6e78-6d18-443d-82dc-4351c20a8c4e
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 6bae89d2a05ec34095e0fa2ac3feafc7b88b894e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-disable-an-affiliate-application"></a>Comment désactiver une Application associée
Utilisez le composant logiciel enfichable MMC ou la **disableapp** commande pour désactiver l’application associée spécifiée.  
  
### <a name="to-disable-an-affiliate-application-using-the-mmc-snap-in"></a>Pour désactiver une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur l’application associée, puis cliquez sur **désactiver**.  
  
### <a name="to-disable-an-affiliate-application-using-the-command-line"></a>Pour désactiver une application associée à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –disableapp <application name>`, où \< *nom de l’application*> est le nom de l’application associée que vous souhaitez désactiver.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../esso/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)   
 [Gestion des applications associées](../esso/managing-affiliate-applications.md)