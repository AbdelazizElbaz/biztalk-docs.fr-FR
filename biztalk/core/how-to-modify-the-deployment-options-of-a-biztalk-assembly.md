---
title: "Comment modifier les Options de déploiement d’un Assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, deploying
- managing [assemblies], modifying
- deploying, assemblies
- managing [assemblies], deploying
- assemblies, deploying
ms.assetid: d25e2f71-08bd-4786-ab6c-35ae4e88b8cc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 416fc38c8768e7391659d133877b2ae59e704463
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-the-deployment-options-of-a-biztalk-assembly"></a>Modification des options de déploiement d'un assembly BizTalk
Cette rubrique explique comment modifier les options de déploiement d'un assembly BizTalk à l'aide de la console Administration de BizTalk Server.  
  
 Vous pouvez spécifier les options de déploiement suivantes :  
  
-   **Ajouter au global assembly cache sur Ajouter une ressource (gacutil).** si vous sélectionnez cette option, l'assembly est ajouté dans le GAC sur l'ordinateur local lors de son ajout dans l'application. En outre, si vous mettez ensuite à jour l’assembly (faites un clic droit et cliquez sur **Actualiser**), l’assembly est ajouté au GAC. La désactivation de cette option ne supprime pas l'assembly du GAC.  
  
-   **Ajouter au global assembly cache lors de l’importation du fichier MSI (gacutil).** installe l'assembly dans le GAC de l'ordinateur local lors de l'importation du fichier .msi de l'application.  
  
-   **Ajoutez dans le global assembly cache lors de l’installation du fichier MSI (gacutil).** installe l'assembly dans le GAC de l'ordinateur local lorsque l'application est installée à partir du fichier .msi.  
  
-   **Emplacement de destination :** chemin d’accès auquel le fichier d’assembly sera copié lorsque l’application est installée. Si aucun chemin d'accès n'est fourni, le fichier de l'assembly n'est pas copié dans le système de fichiers local lors de l'installation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Vous devez en outre être membre du groupe des administrateurs locaux pour sélectionner une option qui ajoute immédiatement l'assembly au GAC. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-modify-the-deployment-options-of-a-biztalk-assembly"></a>Pour modifier les options de déploiement d'un assembly BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement Administration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], le groupe BizTalk contenant l'assembly BizTalk pour lequel modifier les options de déploiement, puis l'application contenant l'assembly BizTalk.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur l’assembly BizTalk, puis cliquez sur **modifier**.  
  
4.  Dans **Options**, activez les cases à cocher des options de déploiement que vous souhaitez.  
  
5.  Si nécessaire, dans **l’emplacement de Destination** modifier le chemin d’accès dans lequel l’assembly sera copié lorsque l’application est installée, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys BizTalk](../core/managing-biztalk-assemblies.md)