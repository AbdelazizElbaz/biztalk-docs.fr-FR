---
title: "Comment modifier les Options de déploiement d’un Assembly .NET, un composant COM, un fichier ou un artefact BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [.NET assemblies], deploying
- deploying, virtual directories
- managing [applications], deploying
- managing [applications], modifying
- definition files [BAM], modifying
- modifying, artifacts
- deploying, artifacts
- managing [certificates], deploying
- deploying, .NET assemblies
- COM components, deploying
- definition files [BAM], deploying
- virtual directories, deploying
- deploying, certificates
- modifying, deployment options
- virtual directories, modifying
- deploying, COM components
ms.assetid: 4955d420-d9ff-4d5a-82f4-fb16477a828c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6469f06b7b42ae1f8b45419fa0214682bd9fa67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-the-deployment-options-of-a-net-assembly-com-component-file-or-bam-artifact"></a>Modification des options de déploiement d'un assembly .NET, d'un composant COM, d'un fichier ou d'un artefact BAM
Cette rubrique explique comment modifier les options de déploiement des artefacts de ressource suivants dans la console Administration de BizTalk Server :  
  
-   assemblys .NET  
  
-   composants des services COM  
  
-   Fichiers ad hoc  
  
-   Artefacts BAM  
  
 La modification des propriétés de déploiement peut vous permettre de modifier l'emplacement de destination dans lequel est copié le fichier d'artefact lorsque l'application est installée sur l'ordinateur local. Le fichier n'est pas copié sur l'ordinateur local lors de l'installation si vous n'indiquez pas de chemin d'accès.  
  
 En outre, vous pouvez souhaiter modifier les options suivantes d'un assembly .NET :  
  
-   **Ajouter au global assembly cache sur Ajouter une ressource (gacutil).** si vous sélectionnez cette option, l'assembly est ajouté dans le GAC sur l'ordinateur local lors de son ajout dans l'application. En outre, si vous mettez ensuite à jour l’assembly (faites un clic droit et cliquez sur **Actualiser**), l’assembly est ajouté au GAC. La désactivation de cette option ne supprime pas l'assembly du GAC.  
  
-   **Ajouter au global assembly cache lors de l’importation du fichier MSI (gacutil).** Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que le fichier .msi est importé dans un groupe BizTalk, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'importation.  
  
-   **Ajoutez dans le global assembly cache lors de l’installation du fichier MSI (gacutil).** Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'installation.  
  
-   **Rendre visible pour les composants COM (regasm).** lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, un assembly COM géré est ajouté au Registre Windows sur l'ordinateur local au cours de la procédure d'installation. Si vous spécifiez cette option, vous devez également préciser un emplacement pour le fichier dans Destination.  
  
-   **Inscrire les composants traités (regsvcs).** lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, un assembly COM+ géré est ajouté au Registre Windows sur l'ordinateur local au cours de la procédure d'installation. Si vous spécifiez cette option, vous devez également préciser un emplacement pour le fichier dans Destination.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Vous devez en outre être membre du groupe des administrateurs locaux pour sélectionner une option qui ajoute immédiatement l'assembly au GAC. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-modify-the-deployment-properties-of-a-resource-artifact"></a>Pour modifier les propriétés de déploiement d'un artefact de ressource  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant l'artefact pour lequel modifier les options de déploiement, puis l'application contenant l'artefact.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur l’artefact, puis cliquez sur **modifier**.  
  
4.  Sur le **Options** onglet, modifier les options de déploiement si nécessaire, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)