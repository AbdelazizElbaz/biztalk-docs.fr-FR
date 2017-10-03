---
title: Compteurs de Performance des adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, WCF adapters
- performance, performance counters
- WCF adapters, performance
ms.assetid: 9feb052f-5674-419f-84ab-9b5d312a04a5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 236eaed7401c79540274e0419b99d14d0f128332
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapters-performance-counters"></a>Compteurs de performance des adaptateurs WCF
Les compteurs de performance permettent d’analyser des aspects spécifiques du travail effectué sur un système de site ou par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur. Les adaptateurs WCF ne possèdent pas leurs propres compteurs de performance. Vous pouvez toutefois surveiller les compteurs de performance de Windows Communication Foundation (WCF) pour évaluer les performances des emplacements de réception WCF. Avant d'utiliser les compteurs de performance WCF pour les emplacements de réception WCF, vous devez les activer pour les instances d'hôte qui exécutent ces derniers.  
  
> [!NOTE]
>  Les compteurs de performance WCF ne sont pas disponibles pour les ports d'envoi WCF.  
  
 Pour les adaptateurs WCF In-process, vous pouvez activer les compteurs de performance via le fichier BTSNTSvc.exe.config. Pour les adaptateurs WCF isolés, vous pouvez modifier le fichier Web.config pour activer les compteurs de performance. Pour plus d’informations sur les compteurs de performance WCF, consultez « Compteurs de Performance WCF » à [http://go.microsoft.com/fwlink/?LinkID=87245](http://go.microsoft.com/fwlink/?LinkID=87245).  
  
## <a name="enabling-the-wcf-performance-counters-for-the-wcf-receive-locations"></a>Activation des compteurs de performance WCF pour les emplacements de réception WCF  
 Pour les adaptateurs WCF In-process, vous pouvez activer les compteurs de performance via le fichier BTSNTSvc.exe.config.  
  
 Pour les adaptateurs WCF isolés, vous pouvez activer le suivi WCF en modifiant le fichier Web.config que l'Assistant Publication de services WCF BizTalk crée dans le dossier de l'application Web  
  
 Pour modifier le fichier de configuration BTSNtSvc.exe.config ou Web.config, ouvrez-le, puis configurez le suivi WCF, comme décrit dans l'exemple de configuration suivant :  
  
> [!NOTE]
>  Le fichier BTSNTSvc.exe.config est toujours situé dans le même répertoire que le fichier BTSNTSvc.exe (généralement, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
```  
<configuration>  
 <system.serviceModel>  
 <diagnostics performanceCounters="All" />  
 </system.serviceModel>  
 </configuration>  
```  
  
 Le **performanceCounters** attribut peut être défini pour activer un type spécifique de compteurs de performance. Les valeurs valides sont :  
  
-   **Tous les**: tous les compteurs de catégorie (**ServiceModelService**, **ServiceModelEndpoint**, et **ServiceModelOperation**) sont activés.  
  
-   **ServiceOnly**: uniquement **ServiceModelService** compteurs de catégorie sont activés.  
  
-   **Désactiver**: les compteurs de performance ServiceModel * sont désactivés. Ceci est la valeur par défaut.  
  
 Une fois le fichier BTSNTSvc.exe.config modifié, vous devez redémarrer les instances d'hôte exécutant les emplacements de réception WCF In-process.  
  
## <a name="types-of-performance-counters"></a>Types de compteurs de performance  
 Compteurs de performance WCF sont limités à trois niveaux différents : service, point de terminaison et opération.  
  
 **Compteurs de performance de service**  
  
 Les compteurs de performance de service mesurent le comportement de l'intégralité du service et permettent de diagnostiquer les performances de celui-ci. Ils sont trouvent sous le **ServiceModelService 3.0.0.0** objet de performance lors de l’affichage avec l’Analyseur de performances. Les instances sont nommées selon le modèle suivant :  
  
```  
biztalkserviceinstance@<URI of a receive location>  
```  
  
 Comme les adaptateurs WCF créent un hôte de service distinct pour chaque emplacement de réception, une instance de compteur de performance est créée pour chaque emplacement de réception. Pour plus d’informations sur la classe de service WCF de mise en œuvre des contrats de service, consultez le **classe BizTalkServiceInstance** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
 **Compteurs de performance de point de terminaison**  
  
 Les compteurs de performance de point de terminaison permettent de consulter les données indiquant la manière dont un point de terminaison accepte les messages. Ils sont trouvent sous le **ServiceModelEndpoint 3.0.0.0** objet de performance lors de l’affichage avec l’Analyseur de performances. Les instances sont nommées selon le modèle suivant :  
  
```  
biztalkserviceinstance.<WCF service contract>@<URI of a receive location>  
```  
  
 Une instance de compteur de performance est créée pour chaque emplacement de réception. Dans le modèle précédent, le nom du contrat de service WCF représente le contrat de service que les adaptateurs WCF choisissent pour recevoir les messages via l'emplacement de réception. Pour plus d’informations sur la façon dont les adaptateurs WCF choisissent un contrat de service WCF disponible à partir de contrats de service, consultez **référence de contrat de Service WCF adaptateurs** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 **Compteurs de performance d’opération**  
  
 Compteurs de performance d’opération sont trouvent sous le **ServiceModelOperation 3.0.0.0** objet de performance lors de l’affichage avec l’Analyseur de performances. Deux instances de compteur de performance sont créées pour chaque emplacement de réception. L'une des instances d'objet est nommée selon le modèle suivant :  
  
```  
biztalkserviceinstance.<WCF service contract>biztalksubmit@<URI of a receive location>  
```  
  
 Dans le modèle précédent, le nom du contrat de service WCF représente le contrat de service que les adaptateurs WCF choisissent pour recevoir les messages via l'emplacement de réception. **biztalksubmit** est un nom d’opération déclaré dans le contrat de service et provoque l’exécution de la création d’opérations WSDL dans les métadonnées.  
  
> [!NOTE]
>  Pour plus d’informations sur la façon dont les adaptateurs WCF choisissent un contrat de service WCF disponible à partir de contrats de service, consultez **référence de contrat de Service WCF adaptateurs** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 L'autre instance d'objet est nommée selon le modèle suivant :  
  
```  
biztalkserviceinstance.<WCF service contract><twowaymethod|onewaymethod>@<URI of a receive location>  
```  
  
 Cette instance de compteur de performance représente l'opération qui traite de manière asynchrone les messages entrant via l'emplacement de réception. La partie nom de l’opération de cette instance peut être **twowaymethod** ou **onewaymethod** selon le type d’adaptateur WCF utilisé dans l’emplacement de réception. Si vous utilisez l’adaptateur WCF-NetMsmq, une instance portant le **onewaymethod** nom de l’opération est créé. Pour les autres adaptateurs, **twowaymethod** est utilisé pour la partie nom de l’opération.