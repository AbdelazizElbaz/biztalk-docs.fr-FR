---
title: "Scénario : Déploiement de deux Versions d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, multiple assemblies
- assemblies, multiple assemblies
- receive locations, examples
- assemblies, deploying
- assemblies, examples
ms.assetid: 3e79a7df-bf77-4a0b-86ec-359fcf3489b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1bb4f04e8b00dd171de89bbed6f01d2a2d1e2e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-two-versions-of-an-application"></a>Scénario : Déploiement de deux Versions d’une Application
Cette rubrique décrit le déploiement de deux versions d'une application au sein d'un groupe BizTalk, de sorte qu'elles puissent s'exécuter simultanément. Dans ce scénario, vous devez déployer une nouvelle version principale de l'application. Les partenaires doivent modifier leur interaction avec le système du fait des modifications apportées au schéma ou au protocole, ce qui revient globalement à utiliser une nouvelle version de l'application. Le changement de ce système a été testé, mais pas à l'échelle d'un système de production entier. Vous souhaitez gérer le nouveau système avec 20 % des partenaires, avant d'augmenter progressivement ce pourcentage jusqu'à 100 % des partenaires.  
  
 Les deux applications recevant les messages sur deux emplacements de réception différents, vous devez demander aux partenaires qui doivent utiliser la nouvelle version de l'application d'envoyer des messages vers la nouvelle URL, de sorte qu'ils puissent être traités par la nouvelle version.  
  
 Le schéma suivant montre un déploiement d'application côte à côte type.  
  
 ![Deux Versions d’assemblys déployées ensemble](../core/media/sidebysideassemblyversions.gif "SideBySideAssemblyVersions")  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md)