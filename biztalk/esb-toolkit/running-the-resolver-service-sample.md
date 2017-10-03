---
title: "Exécution de l’exemple de Service de programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4bf0b21-6aa0-4524-9e63-93a172845d4a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb9d7e3e4d4bce4e46653f7b650004928368eced
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-resolver-service-sample"></a>L’exemple de Service de programme de résolution en cours d’exécution
L’exemple de Service de résolution illustre les scénarios suivants :  
  
-   Résoudre un URI à partir de UDDI3 à l’aide d’une clé de liaison le point de terminaison de service  
  
-   Résoudre un URI à partir de UDDI3 à l’aide d’une recherche de catégorisation le point de terminaison de service  
  
-   Résoudre une transformation (type de mappage BizTalk) à l’aide d’un programme de résolution statique  
  
-   Résoudre un URI à l’aide d’un programme de résolution statique le point de terminaison de service  
  
-   Résoudre un URI à l’aide d’une expression XPath le point de terminaison de service  
  
-   Résoudre un itinéraire à l’aide d’un programme de résolution d’itinéraire statique  
  
-   Résoudre un itinéraire à l’aide du programme de résolution d’un itinéraire statique (Unity)  
  
-   Résoudre un itinéraire à l’aide du moteur BRE (résolution BRI)  
  
-   Résoudre un itinéraire avec le Message à l’aide de BRE (résolution BRI)  
  
-   Résoudre un URI le point de terminaison de service à l’aide du moteur BRE  
  
-   Résoudre une transformation à l’aide du moteur BRE  
  
 **Pour exécuter tous les scénarios de résolution à l’aide de l’implémentation ASMX du service de programme de résolution**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ResolverService, puis double-cliquez sur le fichier RunTestClient_ASMX.cmd.  
  
3.  Ouvrez le dossier \Source\Samples\ResolverService\Output et ouvrez les fichiers de résultats qui correspondent aux requêtes de résolution répertoriées plus haut.  
  
 **Pour exécuter tous les scénarios de résolution à l’aide de l’implémentation de WCF du service de programme de résolution**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ResolverService, puis double-cliquez sur le fichier RunTestClient_WCF.cmd.  
  
3.  Ouvrez le dossier \Source\Samples\ResolverService\Output et ouvrez les fichiers de résultats qui correspondent aux requêtes de résolution répertoriées plus haut.