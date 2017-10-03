---
title: "Scénario : Distribution d’artefacts sur plusieurs ordinateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [artifacts], multiple computers
- examples, distributing
- examples, artifacts
- artifacts, distributing
- artifacts, examples
- deploying [artifacts], examples
- examples, deploying
ms.assetid: 7000cded-1fda-4276-b7f3-3f427f686f64
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abedc60ad13c7e8b2be3ce4caa7b8d34262b4e5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-distributing-artifacts-among-multiple-computers"></a>Scénario : Distribution d’artefacts sur plusieurs ordinateurs
Cette rubrique décrit le scénario de déploiement d'une application lorsque les artefacts sont installés de manière sélective sur différents ordinateurs. Vous pouvez adopter cette méthode si vous souhaitez que certains assemblys ou d'autres types d'artefacts d'une application soient installés uniquement sur certains ordinateurs d'un groupe BizTalk. Pour ce faire, vous pouvez exporter les artefacts inclus dans l'application dans plusieurs fichiers .msi, en regroupant dans un même fichier les artefacts que vous voulez installez sur un même ordinateur physique.  
  
 Le diagramme suivant montre un fichier .msi est importé dans la base de données de gestion BizTalk pour BizTalk groupe 1. Cela crée l’application de traitement des commandes et tous ses artefacts dans ce groupe. Les artefacts de l'application sont alors exportés dans deux fichiers .msi différents. Le premier fichier .msi contient Assembly1, Certificat1 et Script1. Le second contient Assembly2, Script2 et VirtualDirectory1.  
  
 Les deux fichiers .msi sont importés dans BizTalk groupe 2. Étant donné que les deux appartiennent à l’application de traitement des commandes, tous les artefacts dans les deux fichiers .msi sont importés dans la même application nommée traitement des commandes dans le nouveau groupe.  
  
 En outre, les artefacts de l'application sont installés à partir des fichiers .msi sur les ordinateurs du groupe qui les exécuteront. Notez que le fichier .msi contenant le répertoire virtuel est installé sur BizTalk Serveur B et BizTalk Serveur C, qui exécutent tous deux les services IIS.  
  
 ![Artefacts installés sur différents ordinateurs](../core/media/distributionofartifacts.gif "DistributionOfArtifacts")  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md)   
 [Comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md)   
 [Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)   
 [Comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md)