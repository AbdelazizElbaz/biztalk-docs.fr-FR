---
title: "Déploiement des composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, pipeline components [custom]
- pipeline components [custom], deploying
ms.assetid: 98b47fbf-62c0-4012-a406-58c4d56b305a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84ee3255c38e26c5f5d6d19797cba03ba549668b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-pipeline-components"></a>Déploiement des composants de Pipeline
Tous les les pipeline composant assemblys .NET (natifs et personnalisés) doivent se trouver dans le \< *répertoire d’installation*> dossier \Pipeline Components doit être exécuté par le serveur. Si le pipeline avec un composant personnalisé est déployé sur plusieurs serveurs, les composants du binaire doivent se trouver dans le dossier spécifié de chaque serveur.  
  
 Il n'est pas nécessaire d'ajouter un composant de pipeline personnalisé que le moteur d'exécution de BizTalk utilisera dans le Global Assembly Cache (GAC).  
  
 Les composants des services COM personnalisés du pipeline apparaîtront dans la boîte à outils, à condition d'être enregistrés sur l'ordinateur en tant que composant des services COM. Les composants de pipeline .NET personnalisés doivent être placés dans le \< *répertoire d’installation*> dossier \Pipeline Components.  
  
 Après avoir installé les fichiers binaires dans l'emplacement approprié, ajoutez le composant à la boîte à outils. Pour obtenir des instructions sur l’ajout du composant de pipeline à la boîte à outils, consultez [l’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md)