---
title: "Que se passe-t-il pour les artefacts pendant l’Installation et la désinstallation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- uninstalling, artifacts
- artifacts, uninstalling
- installing, artifacts
- artifacts, installing
- uninstalling
ms.assetid: f7b5bd8b-bfdf-4536-ae64-fa98c4885be6
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6274c32656ddece5a0afd81317538126d48b2f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-to-artifacts-during-installation-and-uninstallation"></a>Effets de l'installation et de la désinstallation sur les artefacts
Cette rubrique décrit la façon dont BizTalk Server traite les artefacts basés sur un fichier inclus dans une application BizTalk lorsque vous installez ou désinstallez l’application.  
  
> [!NOTE]
>  Ports d’envoi, groupes de ports d‘envoi, emplacements de réception et ports de réception ne sont pas des artefacts basés sur un fichier et ne sont pas affectés par l’installation et la désinstallation. Les orchestrations, schémas, mappages et pipelines sont tous déployés et gérés dans le cadre des assemblages dont ils font partie.  
  
-   **Assembly BizTalk.** Au cours de l’installation, le fichier de l’assembly BizTalk est copié vers le chemin de destination, s'il en a été spécifié un lors de l'ajout de l'assembly à l'application. L’assembly est également installé dans le global assembly cache (GAC) si cette option a été spécifiée lors de l’ajout de l’assembly. Lors de la désinstallation de l’application, le fichier de l’assembly est supprimé du système de fichiers (si c'est là qu'il se trouve), mais il n'est pas désinstallé du GAC, à moins que le développeur n’ait ajouté un script de post-traitement consacré à l’exécution de cette opération dans l’application. Au besoin, vous pouvez désinstaller manuellement des assemblys BizTalk du GAC. Pour plus d’informations, consultez [comment désinstaller un Assembly du GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).  
  
-   **Assembly .NET.** Au cours de l’installation, le fichier de l’assembly .NET est copié vers le chemin de destination, s'il en a été spécifié un lors de l'ajout de l'assembly à l'application. L’assembly est également installé dans le global assembly cache (GAC) dans le registre Windows si cette option a été spécifiée lors de l’ajout de l’assembly. Lors de la désinstallation de l’application, le fichier de l'assembly est supprimé du système de fichiers, si c'est là qu'il se trouve, mais ne l'est pas dans le registre Windows. L’assembly n’est pas supprimé du GAC ou du registre Windows, sauf si le développeur a prévu un script de post-traitement consacré à l'exécution de cette opération dans l'application. Au besoin, vous pouvez supprimer manuellement des assemblys du GAC ou du registre Windows. Pour plus d’informations, consultez [comment désinstaller un Assembly du GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4) et [comment supprimer d’autres fichiers et les paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **Fichier.** Au cours de l’installation, le fichier est copié dans le système de fichiers local, si un chemin de destination a été spécifié lors de l'ajout du fichier à l'application. Lorsque l’application est désinstallée, le fichier est supprimé du système de fichiers.  
  
-   **Certificat.** Lorsque vous installez l'application, le certificat est ajouté au magasin de certificats Autres personnes de l'ordinateur local. Lorsque l’application est désinstallée, le certificat n'est pas supprimé, sauf si le développeur a prévu un script de post-traitement consacré à l'exécution de cette opération dans l'application. Si nécessaire, vous pouvez supprimer manuellement les certificats. Pour plus d’informations, consultez [comment supprimer d’autres fichiers et les paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **Répertoire virtuel.** Si Internet Information Services (IIS) existe sur l’ordinateur à l'emplacement où l'application est installée, le répertoire virtuel est créé. Si un répertoire virtuel portant le même nom existe déjà et utilise le port spécifié, les ressources du répertoire virtuel présentes dans le fichier d'application .msi sont inscrites dans le répertoire virtuel et les paramètres de sécurité du répertoire virtuel existant ne sont pas modifiés. Vérifiez que ces paramètres de sécurité sont suffisants. Si le pool d’applications auquel le répertoire virtuel est lié n’existe pas dans l’ordinateur local lorsque vous installez l’application, le répertoire virtuel est lié au pool d’applications par défaut.  
  
     Lorsque l’application est désinstallée, le répertoire virtuel et ses fichiers sont supprimés, sauf si le répertoire virtuel existait avant l’installation, ou les fichiers ont été ajoutés au répertoire virtuel après l’installation. Dans ce cas, seuls les fichiers qui ont été installés à partir du fichier d’application .msi sont supprimés. Ainsi, le répertoire virtuel et les fichiers qui lui ont été ajoutés après l'installation de l'application ne sont pas supprimés. Le répertoire virtuel est supprimé uniquement s'il est vide.  
  
-   **Composant COM.** Au cours de l'installation, le composant COM est ajouté au registre Windows si l’option n’a pas été spécifié lors de l'ajout du composant à l'application. De plus, le fichier est copié dans le système de fichiers local, si un emplacement de destination a été spécifié lors de l'ajout du composant à l'application. Lorsque l’application est désinstallée, le composant COM n’est pas supprimé du registre Windows ou du système de fichiers à moins que le développeur n'ait ajouté un script de post-traitement consacré à l'exécution de cette fonction dans l'application. Au besoin, vous pouvez supprimer manuellement des composants COM du registre Windows et du système de fichiers. Pour plus d’informations, consultez [comment supprimer d’autres fichiers et les paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **Scripts de pré-traitement et de post-traitement.** Au cours de l’installation, les fichiers de script sont copiés dans le système de fichiers local, si un chemin de destination a été spécifié lors de l'ajout du fichier à l'application. Les scripts de pré-traitement s'exécutent avant l'importation ou la suppression de l'application et après la désinstallation. Les scripts de post-traitement s'exécutent après l'importation ou la suppression de l'application et avant l’installation. Les fichiers de script sont supprimés du système de fichier lorsque l’application est désinstallée. Toutefois, si un script de pre-traitement ou post-traitement a ajouté des fichiers au système de fichiers, ils ne sont pas supprimés. Si nécessaire, vous pouvez supprimer manuellement des fichiers. Pour plus d’informations, consultez [comment supprimer d’autres fichiers et les paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **Artefacts BAM.** Au cours de l’installation, les fichiers de l’artefact BAM sont copiés vers le chemin de destination spécifié lors de l'ajout de l’artefact à l'application. Les artefacts BAM ne sont pas déployés lors de l’installation de l’application. Lorsque l'application est désinstallée, les fichiers de l'artefact BAM sont supprimés.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md)   
 [Comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md)   
 [Que se passe-t-il pour les artefacts au cours du déploiement](../core/what-happens-to-artifacts-during-application-deployment.md)