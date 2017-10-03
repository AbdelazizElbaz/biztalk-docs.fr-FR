---
title: Affichage des mappages utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO maps], listing maps
- maps [SSO], listing maps
ms.assetid: f9b73785-3a59-45c8-9e88-d2d16b5a46aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6041b40c2b6a3fa468462478754079d41881bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-user-mappings"></a>Affichage des mappages utilisateur
Cette commande permet de répertorier tous les mappages existants pour l'utilisateur spécifié.  
  
 Pour effectuer cette tâche, vous devez être un administrateur SSO, un administrateur d'applications, un administrateur d'applications associées à SSO ou un utilisateur.  
  
 Mappages utilisateur activés apparaissent sous la forme (E) \< *domaine*>\\*\<nom d’utilisateur >*, alors que désactivé mappages utilisateur apparaissent en tant que (D) \< *domaine*>\\*\<nom d’utilisateur >*.  
  
### <a name="to-list-user-mappings-using-the-administration-utility"></a>Pour répertorier des mappages utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Procédez de l'une des manières suivantes :  
  
    -   Type **ssomanage – listmappings  *\<domaine >\\< nom d’utilisateur\>***  pour répertorier tous les mappages d’un utilisateur donné possède dans les applications associées auxquelles il appartient vers l’emplacement où  *\<domaine >* est le domaine Microsoft Windows pour le compte d’utilisateur, et  *\<nom d’utilisateur >* est le nom d’utilisateur Windows pour lequel vous souhaitez répertorier les Mappages utilisateur. Si l'utilisateur est un administrateur d'applications associées ou un administrateur SSO, cette commande répertorie tous les mappages pour cet utilisateur dans toutes les applications associées.  
  
         Ou  
  
    -   Type **ssomanage – listmappings  *\<nom de l’application >***  pour répertorier tous les mappages utilisateur pour une application donnée.  
  
         Ou  
  
    -   Si vous êtes un administrateur d’application, tapez **ssomanage – listmappings  *\<domaine >\\< nom d’utilisateur\>*   *\<nom de l’application >***  pour répertorier tous les mappages d’un utilisateur donné possède dans les applications associées dont vous êtes un administrateur.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-list-user-mappings-using-the-client-utility"></a>Pour répertorier des mappages utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – listmappings** pour répertorier tous les mappages que vous avez.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md)   
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)