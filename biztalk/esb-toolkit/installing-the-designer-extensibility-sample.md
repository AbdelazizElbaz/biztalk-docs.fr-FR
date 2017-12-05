---
title: "Installation de l’exemple de l’extensibilité du Concepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eba13a4a-1b87-4268-af91-29af3a5bc5ef
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea0cd71c22fdd614d2e49c996939b785ecadf8bd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-the-designer-extensibility-sample"></a>Installation de l’exemple de l’extensibilité du Concepteur
Cette section décrit le processus d’installation de l’exemple de l’extensibilité du concepteur. Vous devez installer les exemples de [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) et [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) avant d’installer et utiliser cet exemple.  
  
 **Pour installer l’exemple de l’extensibilité du Concepteur**  
  
1.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample, où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et ouvrez le fichier de solution Microsoft Visual Studio nommé Extenders.Itinerary.OrchestrationSample.sln.  
  
2.  Dans Visual Studio, cliquez sur **générer la Solution** sur la **générer** menu.  
  
3.  Fermez Visual Studio.  
  
4.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample, où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et ouvrez le fichier de solution Visual Studio nommé Extenders.Resolvers.ResolverSample.sln.  
  
5.  Dans Visual Studio, cliquez sur **générer la Solution** sur la **générer** menu.  
  
6.  Fermez Visual Studio.  
  
7.  Dans l’Explorateur Windows, ouvrez le dossier \Lib sous le chemin d’installation de concepteur d’itinéraire.  
  
8.  Parmi les dossiers \bin\Debug des solutions Visual Studio créées à l’étape précédente, copiez les fichiers Extenders.Resolvers.ResolverSample.dll et Extenders.Itinerary.OrchestrationSample.dll dans le répertoire \Lib.