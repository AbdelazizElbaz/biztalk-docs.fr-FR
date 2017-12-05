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
ms.openlocfilehash: 041bd8c6e6fa9c3969be18f0804460c00de5f11a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-pipeline-components"></a>Déploiement des composants de Pipeline
Tous les les pipeline composant assemblys .NET (natifs et personnalisés) doivent se trouver dans le \< *répertoire d’installation*\>dossier \Pipeline Components doit être exécuté par le serveur. Si le pipeline avec un composant personnalisé est déployé sur plusieurs serveurs, les composants du binaire doivent se trouver dans le dossier spécifié de chaque serveur.  
  
 Il n'est pas nécessaire d'ajouter un composant de pipeline personnalisé que le moteur d'exécution de BizTalk utilisera dans le Global Assembly Cache (GAC).  
  
 Les composants des services COM personnalisés du pipeline apparaîtront dans la boîte à outils, à condition d'être enregistrés sur l'ordinateur en tant que composant des services COM. Les composants de pipeline .NET personnalisés doivent être placés dans le \< *répertoire d’installation*\>dossier \Pipeline Components.  
  
 Après avoir installé les fichiers binaires dans l'emplacement approprié, ajoutez le composant à la boîte à outils. Pour obtenir des instructions sur l’ajout du composant de pipeline à la boîte à outils, consultez [l’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement des composants de pipeline personnalisés](../core/developing-custom-pipeline-components.md)