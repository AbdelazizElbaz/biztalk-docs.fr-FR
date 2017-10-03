---
title: "À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- customizing, applications
- applications, customizing
- scripts, applications
- scripts, customizing
ms.assetid: 47627394-d594-491b-9098-38c5d028a378
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dc0afd7ed042f475a9a008125c968f401e6df92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-pre--and-post-processing-scripts-to-customize-application-deployment"></a>Utilisation des scripts de pré-traitement et de post-traitement pour personnaliser le déploiement de l'application
Les rubriques de cette section expliquent comment créer des scripts de pré-traitement et post-traitement pour réaliser un certain nombre de tâches lors de l'importation, l'installation ou la désinstallation d'une application. Les scripts de pré-traitement permettent de réaliser ces tâches avant l'importation ou l'installation d'une application et à la fin de la désinstallation, tandis que les scripts de post-traitement permettent de les réaliser après l'importation ou l'installation d'une application et avant la désinstallation.  
  
 Un script de pré-traitement peut ainsi vous permettre de sauvegarder des fichiers de ressources avant qu'ils ne soient écrasés au cours de l'installation, et un script de post-traitement d'ajouter un certificat au magasin de certificats après l'installation d'une application.  
  
> [!NOTE]
>  BizTalk Server inclut des exemples de ces deux types de scripts. Pour plus d’informations sur les exemples de scripts, consultez [(exemple de déploiement d’Application) de modèle](../core/template-application-deployment-sample.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d’un Script de pré-traitement ou post-traitement](../core/creating-a-pre-or-post-processing-script.md)  
  
-   [Comment les Variables d’environnement indiquent état du déploiement](../core/how-environment-variables-indicate-deployment-state.md)  
  
-   [État des artefacts de fichier au cours du déploiement](../core/status-of-file-artifacts-during-deployment.md)  
  
-   [Variables d’environnement de Script de pré-traitement et de post-traitement](../core/pre-and-post-processing-script-environment-variables.md)