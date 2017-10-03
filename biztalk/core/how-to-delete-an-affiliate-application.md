---
title: "Comment supprimer une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], deleting
- managing [SSO applications], deleting
- deleting, applications [SSO]
ms.assetid: c7ec065e-ef10-49ff-a350-105dd08dc4a9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ddb40109ff402f1c1794a90e591a43e11407fba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-an-affiliate-application"></a>Comment supprimer une Application associée
Le composant logiciel enfichable MMC ou la ligne de commande permet de supprimer une application associée de la base de données SSO.  
  
> [!IMPORTANT]
>  Lorsque vous supprimez une application associée, le système SSO supprime automatiquement tous les mappages qui y sont associés.  
  
> [!IMPORTANT]
>  Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a>Pour supprimer une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d’étendue du composant logiciel enfichable MMC, développez le **Enterprise Single Sign-On** nœud.  
  
3.  Cliquez sur l’application associée, puis cliquez sur **supprimer**.  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a>Pour supprimer une application associée à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-deleteapp  *\<nom de l’application >***, où  *\<nom de l’application >* est le nom de l’application associée vous vous souhaitez supprimer de la base de données SSO.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)