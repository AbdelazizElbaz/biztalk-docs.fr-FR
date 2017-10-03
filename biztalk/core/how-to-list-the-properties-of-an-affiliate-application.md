---
title: "Comment afficher les propriétés d’une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], listing properties
- managing [SSO applications], listing properties
ms.assetid: a120acd7-2f0b-4c72-8a8a-f8e500a773c8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 651c629a0290fef9af20dce3771d87dbb9eeb82d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a>Comment afficher les propriétés d’une Application associée
Cette commande affiche les informations suivantes sur l'application associée. Pour plus d’informations sur les propriétés d’une application associée, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).  
  
 Le système d'authentification unique tire ces informations du fichier xml que vous avez utilisé pour mettre à jour l'application affiliée. Pour plus d’informations, consultez [comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md).  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a>Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-displayapp  *\<nom de l’application >***, où  *\<nom de l’application >* est le nom de l’Application associée vous souhaitez afficher les propriétés.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a>Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur d’installation*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – displayapp  *\<nom de l’application >***, où  *\<nom de l’application >* est le nom de l’Application associée vous souhaitez afficher les propriétés.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)