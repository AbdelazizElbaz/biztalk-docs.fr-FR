---
title: "Gérer les ressources | Documents Microsoft"
description: Utilisez btstask ou la console Administration de BizTalk pour travailler avec les assemblys, les scripts, les certificats, les fichiers de liaison et plus dans BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b478ef2e-1363-4c2c-a4b7-6a582a6b33a5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07248c1689adf6b6474fd8e1f3e01f2d660becdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-resources"></a>Gérer les ressources

## <a name="overview"></a>Vue d'ensemble
Cette rubrique fournit des instructions sur l'utilisation de la console Administration de BizTalk Server ou de l'outil de ligne de commande BTSTask afin de gérer les ressources BizTalk Server une fois celles-ci déployées dans un groupe. Les ressources incluent des artefacts de types suivants :  
  
-   Assemblys BizTalk  
  
-   Scripts de pré-traitement et de post-traitement  
  
-   assemblys .NET  
  
-   composants des services COM  
  
-   Certificats  
  
-   Fichiers ad hoc  
  
-   définitions BAM  
  
-   Fichiers de liaison  
  
-   Répertoires virtuels  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
> [!NOTE]
>  N'ajoutez jamais plusieurs ressources portant le même nom à un groupe BizTalk, quel que soit le cas. La gestion de ressources multiples portant le même nom dans un groupe BizTalk Server n'est pas prise en charge, même lorsque la base de données de gestion BizTalk est hébergée sur un serveur SQL configuré pour utiliser les classements binaires et prenant en charge le respect de la casse.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Gestion des assemblys BizTalk](../core/managing-biztalk-assemblies.md)  
  
-   [Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md)  
  
-   [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)  
  
-   [Actualisation d’une ressource](../core/how-to-refresh-a-resource.md)