---
title: "Les artefacts qui doivent être uniques dans une Application ou le groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, artifacts
- artifacts, requirements
- applications, artifacts
ms.assetid: a758cd74-a962-4e75-aea2-47752ab72a64
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe9ff033621ed491b7f1deae9e3f2e467e54f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="artifacts-that-must-be-unique-in-an-application-or-group"></a>Artefacts devant être uniques au sein d'une application ou d'un groupe
Certains types d'artefact d'une application ou d'un groupe BizTalk doivent être uniques :  
  
-   Les assemblys BizTalk et les assemblys .NET non-BizTalk doivent avoir un nom complet unique dans le groupe. Leur nom complet se compose d'un nom de fichier, d'un jeton de clé publique, de la culture et de la version.  
  
-   Les règles et stratégies doivent avoir un nom et un numéro de version uniques dans le groupe.  
  
-   Les ports d'envoi, groupes de ports d'envoi, ports de réception et emplacements de réception doivent avoir un nom unique dans le groupe.  
  
-   Les sites Web doivent avoir un nom de répertoire unique dans le groupe.  
  
-   Les ressources BAM doivent avoir un nom de fichier unique dans le groupe.  
  
-   Les certificats doivent avoir une empreinte unique dans le groupe.  
  
-   Les composants COM doivent avoir un nom de fichier unique dans le groupe.  
  
-   Les artefacts basés sur des fichiers, tes que les scripts ou autres fichiers plats, doivent avoir des noms de fichier uniques dans l'application, mais pas dans le groupe.  
  
 Vous pouvez spécifier l'option de remplacement afin d'importer ou d'ajouter un artefact à une application s'il existe déjà dans celle-ci et que son type doit être unique dans une application. Si l'artefact existe déjà dans une autre application du groupe, et que son type doit être unique dans ce groupe, vous ne pouvez pas l'ajouter ou l'importer.  
  
 Si vous devez utiliser un artefact dans une application et qu'il existe déjà dans une autre du groupe, vous pouvez créer une référence à celle-ci. Pour plus d’informations, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
> [!NOTE]
>  Vous pouvez afficher le nom complet de la plupart des types d’artefacts dans une application à l’aide de la commande ListApp de BTSTask, comme décrit dans [commande ListApp](../core/listapp-command.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)