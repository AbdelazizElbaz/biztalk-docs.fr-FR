---
title: "Comment désactiver une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, applications
- managing [SSO applications], disabling
- applications [SSO], disabling
ms.assetid: febf1687-f0d0-4f87-b462-23535bbddf6d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe1a19ee34a98be4130be2ac72e9ad27e83b0c13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-disable-an-affiliate-application"></a>Comment désactiver une Application associée
Le composant logiciel enfichable MMC ou la ligne de commande permet de désactiver l'application associée spécifiée.  
  
### <a name="to-disable-an-affiliate-application-using-the-mmc-snap-in"></a>Pour désactiver une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur l’application associée, puis cliquez sur **désactiver**.  
  
### <a name="to-disable-an-affiliate-application-using-the-command-line"></a>Pour désactiver une application associée à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-disableapp  *\<nom de l’application >***, où \< *nom de l’application*> est le nom de l’application associée vous souhaitez désactiver.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)