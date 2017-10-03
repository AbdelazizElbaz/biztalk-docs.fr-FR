---
title: "Comment inscrire ou désinscrire un tiers pour un rôle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [role links], enlisting
- enlisting, role links
- role links, unenlisting
- role links, enlisting
- managing [role links], unenlisting
ms.assetid: 06fc2a64-3add-400c-9f9d-fab22fdf5366
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af988a001e63ba210e5d5c224eeb486800b7286
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-or-unenlist-a-party-for-a-role"></a>Inscription et désinscription d'un tiers dans un rôle
Cette rubrique explique comment inscrire un tiers dans un rôle, et comment le désinscrire, à l'aide de la console Administration de BizTalk Server. L'inscription d'un tiers dans un rôle est l'action qui permet d'attribuer un tiers à un rôle, et la désinscription est celle qui permet de supprimer le tiers du rôle.  
  
 Quelle que soit l'action effectuée (inscription ou désinscription), gardez les points suivants à l'esprit :  
  
-   Vous devez créer un tiers avant de pouvoir l'inscrire. Pour obtenir des instructions, consultez [la création d’un tiers](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).  
  
-   Vous pouvez inscrire ou désinscrire un tiers dans un rôle sans avoir à redémarrer l'application.  
  
> [!NOTE]
>  Le développeur peut inscrire ou désinscrire un tiers au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-enlist-or-unenlist-a-party-for-a-role"></a>Pour inscrire un tiers dans un rôle ou le désinscrire  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le lien de rôle pour lequel vous souhaitez inscrire ou désinscrire un tiers.  
  
3.  Cliquez sur **des liens de rôle**, cliquez sur le lien de rôle pour lequel vous souhaitez inscrire ou désinscrire un tiers, puis cliquez sur **propriétés**.  
  
4.  Pour inscrire un tiers, procédez de la manière suivante :  
  
    -   Cliquez sur **Enlist** et cliquez sur le tiers à inscrire.  
  
    -   Cliquez sur **lier**, dans le **Port d’envoi** liste déroulante, cliquez sur l’envoi de port à utiliser pour ce tiers, puis cliquez sur **OK** à deux reprises.  
  
5.  Pour désinscrire un tiers, cliquez sur le tiers, cliquez sur **désinscrire**, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des liens de rôle](../core/managing-role-links.md)