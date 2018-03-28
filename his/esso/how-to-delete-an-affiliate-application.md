---
title: Comment supprimer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec290d38-0220-4bf2-b596-2d6453e51c8d
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: d0632f7e4217cb9bbccd2ee604688f22eb6de348
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-delete-an-affiliate-application"></a>Comment supprimer une Application associée
Utilisez le composant logiciel enfichable MMC ou la **deleteapps** commande pour supprimer l’application associée spécifiée à partir de la base de données d’informations d’identification.  
  
> [!IMPORTANT]
>  Lorsque vous supprimez une application associée, le système SSO supprime automatiquement tous les mappages qui y sont associés.  
  
> [!IMPORTANT]
>  Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a>Pour supprimer une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d’étendue du composant logiciel enfichable MMC, développez le **Enterprise Single Sign-On** nœud.  
  
3.  Cliquez sur l’application associée, puis cliquez sur **supprimer**.  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a>Pour supprimer une application associée à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –deleteapp <application name>`, où  *\<nom de l’application >* est le nom de l’application associée que vous souhaitez supprimer de la base de données d’informations d’identification.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../esso/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)   
 [Gestion des applications associées](../esso/managing-affiliate-applications.md)