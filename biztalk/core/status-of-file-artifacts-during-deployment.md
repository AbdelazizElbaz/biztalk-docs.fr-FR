---
title: "État des artefacts de fichier au cours du déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, status
- deploying [artifacts], status
ms.assetid: 6d0f7336-c2cb-4aa4-9f1d-55fb85fe78bf
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1f57716741bb61c7a9f6f012aed14ec04c8e250
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="status-of-file-artifacts-during-deployment"></a>État des artefacts de fichier lors du déploiement
Vous pouvez avoir besoin de savoir quels artefacts basés sur des fichiers existent sur le système de fichiers lors de l'exécution d'un script de pré-traitement ou de post-traitement. Par exemple, vous pouvez vouloir l'exécution d'un script de post-traitement lors de la désinstallation et la suppression d'un certain fichier d'artefact du système de fichiers. Les artefacts basés sur des fichiers sont des artefacts qui peuvent exister en tant que fichiers dans le système de fichiers local, en plus de leur représentation dans les bases de données BizTalk. Parmi les artefacts basés sur des fichiers, il y a les composants COM, les assemblys .NET, les assemblys BizTalk, les artefacts BAM, les fichiers ad hoc, les scripts et les fichiers de liaison.  
  
 Le tableau suivant récapitule l'état des fichiers d'artefact à chaque étape du processus de déploiement.  
  
|Étape du processus de déploiement|État des fichiers d'artefact de l'application|  
|-------------------------------------|------------------------------------------|  
|Avant installation|Seuls les fichiers du type System.BizTalk.File existent sur le système de fichiers local.*|  
|Après installation|Tous les fichiers existent sur le système de fichiers local.*|  
|Avant désinstallation|Tous les fichiers existent sur le système de fichiers local.*|  
|Après désinstallation|Tous les fichiers ont été supprimés du système de fichiers local.|  
|Avant importation|Aucun fichier n'existe sur le système de fichiers local, à moins que l'application n'ait été installée sur l'ordinateur local.|  
|Après importation|Aucun fichier n'existe sur le système de fichiers local, à moins que l'application n'ait été installée sur l'ordinateur local.|  
  
 \*Fichiers existent sur le système de fichiers local uniquement si un emplacement de destination valide a été spécifié lorsque le fichier a été ajouté à l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)