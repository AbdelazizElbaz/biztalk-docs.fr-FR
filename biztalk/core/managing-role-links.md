---
title: "Gestion des liens de rôle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8860e11-3d2c-450f-a7d2-cc116478999c
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07f85bfe0d16b3963b0ba18585220f508f679346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-role-links"></a>Gérer les liens de rôle

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur la gestion des liens de rôle dans une application BizTalk à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Un lien de rôle définit la relation entre les tiers impliqués dans une transaction commerciale et spécifie les types de messages et de ports utilisés dans l'interaction dans les deux sens. Pour plus d’informations sur les liens de rôle, consultez [à l’aide des liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md).  

## <a name="added-to-application"></a>Ajouté à l’application  
 Les liens de rôle sont créés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilés dans les assemblys BizTalk. Vous ne pouvez pas ajouter un lien de rôle de manière individuelle à une application. Son ajout s'effectue dans les cas suivants :  
  
-   Lorsque vous ajoutez un assembly BizTalk contenant un lien de rôle à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
-   Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un lien de rôle, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
-   Lorsqu’un développeur déploie dans une application d’un assembly contenant un lien de rôle à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  

## <a name="deploy-to-production"></a>Déployer en production  
 Le développeur BizTalk crée des liens de rôle pour implémenter des communications entre deux ou plusieurs tiers impliqués dans une transaction commerciale, tels que votre organisation et un fournisseur. Il ne spécifie pas nécessairement les tiers impliqués, seulement leurs rôles. Pour déployer une application comportant un lien de rôle dans un environnement de production et permettre aux tiers de communiquer, vous devez effectuer la configuration suivante :  
  
-   Si cela n'a pas été fait au cours du processus de développement, vous devez attribuer un tiers à chaque rôle défini dans le lien de rôle. Cette opération s'appelle « inscrire » un tiers dans un rôle. Si cette inscription devait ne plus être nécessaire par la suite, vous avez la possibilité de l'annuler.  
  
-   Vous devez lier les ports logiques de chaque tiers défini dans le lien de rôle aux ports physiques sur les instances d'hôte BizTalk qui hébergeront l'application.  
  
 Pour plus d’informations sur le développement des liens de rôle, consultez [à l’aide des liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md).  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## <a name="next-step"></a>Étape suivante
  
-   [Comment inscrire ou désinscrire un tiers pour un rôle](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)