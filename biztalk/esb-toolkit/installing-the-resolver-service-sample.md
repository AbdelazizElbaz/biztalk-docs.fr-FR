---
title: "Installation de l’exemple de Service de programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce9bbeb-9377-41af-8ca7-740ce4d1f617
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b06c7383dee805612a3f599148f1d631891ace79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-resolver-service-sample"></a>Installation de l’exemple de Service de programme de résolution
Cette section décrit le processus d’installation de l’exemple de Service de résolution. Le Service de résolution varie selon le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] solution de base. L’installation de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core copie automatiquement et installe les principaux assemblys requis par cet exemple, les emplacements corrects.  
  
 **Pour installer l’exemple de Service de résolution à partir du projet de la solution**  
  
1.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ResolverService\Install\Scripts.  
  
2.  Double-cliquez sur le fichier Setup_bin.cmd.  
  
3.  Pour confirmer la réussite de l’installation de l’exemple, ou si vous rencontrez des problèmes lorsque vous exécutez des applications, vous pouvez utiliser la liste fournie dans le tableau suivant pour vérifier la présence d’assemblys requis et d’autres artefacts.  
  
|Emplacement|Catégorie|Nom et la version du composant|  
|--------------|--------------|---------------------------------------|  
|Application BizTalk GlobalBank.ESB|Orchestrations|(aucun)|  
|Application BizTalk GlobalBank.ESB|Ports d'envoi|(aucun)|  
|Application BizTalk GlobalBank.ESB|Ports de réception|(aucun)|  
|Application BizTalk GlobalBank.ESB|Emplacements de réception|(aucun)|  
|Application BizTalk GlobalBank.ESB|Schémas|(aucun)|  
|Application BizTalk GlobalBank.ESB|Pipelines|(aucun)|  
|Application BizTalk GlobalBank.ESB|Ressources|(aucun)|  
|Application BizTalk GlobalBank.ESB|Stratégies|ResolveEndpoint|  
|||ResolveMap|  
|Application BizTalk GlobalBank.ESB|Cartes|(aucun)|  
|Cache d’assembly global|Assemblys|(aucun)|  
|%Program Files%\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline composants|Composants de pipeline|(aucun)|