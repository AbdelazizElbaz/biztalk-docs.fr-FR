---
title: "Comment modifier le nom d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- naming conventions, renaming
- naming conventions, applications
- applications, renaming
ms.assetid: ae59c792-44bd-43e0-a4ae-e67bcad2e128
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4826688935bf18cd5288924d4544f484b3dcf0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-name-of-an-application"></a>Changement du nom d'une application
Cette rubrique explique comment changer le nom d'une application à l'aide de la console Administration de BizTalk Server. Le nom d'application que vous utilisez ne doit pas déjà exister dans le groupe.  
  
> [!NOTE]
>  Si vous avez exporté un fichier .msi pour une application qui a une référence à l'application renommée, cette référence ne fonctionnera plus lorsque vous importerez le fichier. Vous devrez mettre la référence à jour avec le nouveau nom d'application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-change-the-name-of-an-application"></a>Pour changer le nom d'une application  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, cliquez sur l’application dont vous souhaitez modifier, puis cliquez sur le nom **propriétés**.  
  
3.  Dans le **nom** zone, tapez un nouveau nom pour l’application, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)