---
title: Comment exporter une Application vers un fichier .msi | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7179e86-aa55-426b-a0db-19229ca5625a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600118718585401d9ba6c3158b6510af55c53e74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-an-application-to-an-msi-file"></a>Comment exporter une Application vers un fichier .msi
Vous pouvez utiliser l’Assistant Exportation de fichier MSI ou BTSTask pour exporter les artefacts de l’application dans un fichier .msi que vous utiliserez pour importer l’application dans un groupe BizTalk. Ce processus sera également installer l’application sur les ordinateurs qui l’exécuteront.  
  
## <a name="exporting-application-bindings-in-an-msi-file"></a>Exportation des liaisons dans un fichier .msi de l’Application  
 Lorsque vous exportez une application dans un fichier .msi, vous sélectionnez les ressources à exporter. Ces ressources peuvent inclure tout ou partie des assemblys déployés ou exporter des liaisons qui sont disponibles pour.  
  
 Pour faciliter la réimporter les applications dans votre environnement de développement ultérieurement pour apporter des modifications ou ajouts, vous souhaiterez exporter les liaisons pour chaque application, puis les ajouter dans les applications. Lorsque vous définissez le type de ressource pour « Liaison BizTalk », vous pouvez ajouter des fichiers de liaison supplémentaires à un fichier .msi. Pour chaque fichier de liaison que vous ajoutez, vous devez spécifier le nom d’environnement (champ de texte) pour les liaisons doivent être appliquées à. Puis lors de l’importation, vous devez sélectionner le nom de l’environnement sur lequel vous importez actuellement. Si elles correspondent, le fichier de liaison est appliqué au groupe cible. Vous ne pouvez également spécifier aucun nom d’environnement pour le fichier de liaison ajoutés, ce qui provoque l’ensemble des liaisons à appliquer à tous les environnements de manière inconditionnelle.  
  
 À l’aide d’un fichier .msi automatise peut sinon être un substantiel ensemble des tâches manuelles. Dans un environnement de production, vous pouvez rendre plus facile de déployer un assembly dans plusieurs groupes BizTalk par le transport les liaisons pour l’assembly et l’assembly. Si votre application contient un nombre important d’artefacts, vous pouvez exporter des artefacts dans un package de programme d’installation de Windows et d’autres dans un ou plusieurs packages Windows Installer.  
  
 Lors de l’exportation de l’application, vous devez envisager les points importants. Par exemple, vous pouvez soit exporter tous les artefacts de l’application ou uniquement les artefacts que vous souhaitez ajouter ou mettre à jour. Si vous exportez un artefact de fichier, assurez-vous qu'il s'agit de la version que vous voulez utiliser dans l'application. Pour plus de ces points et pour plus d’informations sur l’exportation d’une application BizTalk dans un fichier .msi, consultez [comment exporter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).