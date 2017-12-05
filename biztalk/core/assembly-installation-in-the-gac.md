---
title: "Installation de l’assembly dans le GAC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b12d00c-8750-4c6d-8244-e613f955a478
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25af22c85602c323b87340cce8b740fe5b68accb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="assembly-installation-in-the-gac"></a>Installation de l’assembly dans le GAC
Chaque ordinateur dispose d'un GAC (Global Assembly Cache), qui contient les assemblys qu'une ou plusieurs applications de cet ordinateur partagent. Pour que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] puisse traiter les messages lors de l'exécution, les assemblys inclus dans une application BizTalk doivent figurer dans les GAC des ordinateurs exécutant l'application.  
  
 Si votre application est présente sur un seul serveur, les assemblys ne doivent figurer que dans le GAC de ce serveur. En revanche, si elle est hébergée par plusieurs serveurs, les assemblys de cette application doivent exister dans le GAC de chacun des ordinateurs nécessitant un accès aux artefacts contenus dans les assemblys. Par exemple, si vous déployez Assembly_A sur Server_1, puis inscrivez Assembly_A dans un hôte de Server_2, Assembly_A doit être installé dans le GAC de Server_2. Dans le cas contraire, Server_2 ne sera pas en mesure d’accéder à Assembly_A pendant l’exécution.  
  
 Plus précisément, les assemblys contenant des orchestrations et tout assembly associé doivent toujours être installés dans le GAC des serveurs sur lesquels sont exécutées les instances de l'hôte auquel est liée l'orchestration. En outre, les assemblys contenant les mappages et pipelines utilisés par un port doivent figurer sur les serveurs exécutant les instances de l'hôte faisant office de gestionnaire d'adaptateur pour ce port.  
  
 Vous avez la possibilité de spécifier une option de déploiement pour chaque assembly afin que ce dernier soit installé dans le GAC lors du déploiement de l'assembly depuis [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous pouvez également installer un assembly manuellement. En outre, vous pouvez spécifier que l'assembly soit installé dans le GAC après son déploiement dans une application BizTalk.  
  
 Voici un récapitulatif des outils et méthodes permettant d'installer un assembly dans le GAC :  
  
-   **Microsoft Visual Studio.** Comme mentionné précédemment, vous pouvez définir des propriétés de projet pour installer des assemblys dans le GAC automatiquement lorsque vous déployez les, comme décrit dans [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Vous pouvez également installer manuellement les assemblys dans le GAC à l’aide de l’outil de ligne de commande Gacutil inclus dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [comment installer un Assembly dans le GAC](../core/how-to-install-an-assembly-in-the-gac.md).  
  
-   **Outil de ligne de commande BTSTask.** lorsque vous ajoutez un assembly à une application BizTalk à l'aide de l'outil BTSTask, vous pouvez spécifier que l'assembly soit installé dans le GAC lors de l'importation ou de l'installation de l'application le contenant. Pour plus d’informations, consultez [commande AddResource : BizTalk Assembly](../core/addresource-command-biztalk-assembly.md). Consultez également [commande AddResource : Assembly .NET](../core/addresource-command-net-assembly.md).  
  
-   **Console d’Administration de BizTalk Server.** à l'instar de l'outil BTSTask, lorsque vous ajoutez un assembly à une application à l'aide de la console Administration, vous pouvez spécifier que l'assembly soit installé dans le GAC lors de l'importation ou de l'installation de l'application le contenant. Pour plus d’informations, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md). Consultez également [l’ajout d’un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md).  
  
     En outre, vous pouvez configurer des options de déploiement à tout moment une fois un assembly a été déployé ou ajouté à une application, comme décrit dans [comment modifier les Options de déploiement d’un BizTalk Assembly](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md). Lorsque les assemblys sont déployés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour la première fois, les options de déploiement dans la console d’Administration sont définies comme suit : GAC lors de l’installation est activé et GAC lors de l’importation est désactivé. Si vous apportez des modifications à ces paramètres, vos modifications seront toujours en vigueur si l’assembly est redéployé à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
-   **Glisser -déplacer.** À l’aide de l’Explorateur Windows, vous pouvez glisser -déplacer le fichier d’assembly dans le \< *dossier Windows*\>\assembly.  
  
-   **Autres méthodes.** il existe d'autres méthodes et outils permettant d'installer un assembly dans le GAC, notamment le programme d'installation Windows ou les outils créés par des fournisseurs tiers.  
  
> [!IMPORTANT]
>  Afin de garantir un bon fonctionnement de votre application, assurez-vous que les versions des assemblys contenues dans la base de données de gestion BizTalk sont les mêmes que celles du GAC. Si un assembly ne fait pas l'objet d'une installation systématique dans le GAC lors de son déploiement, il se peut que les versions contenues dans le GAC et dans la base de données de gestion BizTalk diffèrent, avec comme conséquence la génération d'erreurs lors de l'exécution.  
  
> [!IMPORTANT]
>  Pour plus d'informations sur la numérotation des versions, consultez la section « Versioning des assemblys » dans l'aide de .NET Framework disponible dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Notez que l'utilisation des fichiers de stratégie .NET n'est pas prise en charge dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)   
 [Présentation de la gestion et du déploiement d’une application BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)