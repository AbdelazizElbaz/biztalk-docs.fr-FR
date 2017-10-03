---
title: "Exécution de l’exemple de l’extensibilité du Concepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05ac3b50-5bf2-4566-8654-472391476d1f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b26c483568e1ceb05679d7548721c1cce818fde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-designer-extensibility-sample"></a>L’exemple de l’extensibilité du concepteur en cours d’exécution
L’exemple de l’extensibilité du concepteur utilise deux unités d’exemple pour illustrer comment vous pouvez fournir des options de configuration au moment du design pour les programmes de résolution personnalisés et pour les services d’itinéraire.  
  
 **Pour exécuter l’exemple de l’extensibilité du Concepteur**  
  
1.  Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Dans Visual Studio, pointez sur **nouveau** sur la **fichier** menu, puis sur **projet**.  
  
3.  Sélectionnez le modèle de bibliothèque de classes c#, type **ItineraryLibrary** dans les **nom** zone, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le projet ItineraryLibrary, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
5.  Dans le **nom** , tapez **TestItinerary**, puis appuyez sur ENTRÉE.  
  
6.  Dans la boîte à outils, cliquez sur un élément de modèle On rampe d’entrée, puis faites-le glisser vers l’aire de conception.  
  
7.  Dans la boîte à outils, cliquez sur un élément de modèle de Service de l’itinéraire, puis faites-le glisser vers l’aire de conception.  
  
8.  Dans la boîte à outils, cliquez sur un autre élément de modèle de Service de l’itinéraire, puis faites-le glisser vers l’aire de conception.  
  
9. Dans la boîte à outils, cliquez sur un élément de modèle de démarrage de la valeur Off, puis faites-le glisser vers l’aire de conception.  
  
10. Dans la boîte à outils, cliquez sur l’outil de connecteur, puis faites glisser une connexion entre le **OnRamp1** élément de modèle et la **ItineraryService1** élément de modèle.  
  
11. Dans la boîte à outils, cliquez sur l’outil de connecteur, puis faites glisser une connexion entre le **ItineraryService1** élément de modèle et la **ItineraryService2** élément de modèle.  
  
12. Dans la boîte à outils, cliquez sur l’outil de connecteur, puis faites glisser une connexion entre le **ItineraryService2** élément de modèle et la **OffRamp1** élément de modèle.  
  
13. Cliquez sur le **OnRamp1** élément de modèle, puis dans la fenêtre Propriétés, définissez la propriété d’extendeur **Extension du Service ESB rampe d’entrée**.  
  
14. Définir le **Application BizTalk** propriété **Microsoft.Practices.ESB**.  
  
15. Définir le **Port de réception** propriété **OnRamp.Itinerary**.  
  
16. Cliquez sur le **ItinearyService1** élément de modèle et, dans la fenêtre Propriétés, définissez la **extendeur** propriété **exemple d’Extension de Service d’Orchestration itinéraire**.  
  
    > [!NOTE]
    >  Il s’agit de l’extension personnalisée installée en tant que partie de l’exemple de l’extensibilité du concepteur. Il vous permet de vous permet d’ajouter des propriétés pour le jeu de propriétés passé à un service d’orchestration d’itinéraire.  
  
17. Définir le **OtherValue** propriété **1**.  
  
18. Définir le **ServiceName** propriété **Microsoft.Practices.ESB.Services.Routing**.  
  
19. Définir le **SomeValue** propriété **2**.  
  
20. Avec le bouton droit le **résolveur** collection de **ItineraryService1**, puis cliquez sur **ajouter le nouveau programme de résolution**.  
  
21. Cliquez sur **Resolver1**, puis, dans la fenêtre Propriétés, définissez la **implémentation d’un programme de résolution** propriété **exemple d’Extension du programme de résolution**.  
  
22. Définir le **SomeResolverValue** propriété **test**, puis définissez la propriété de version **1.0**.  
  
23. Cliquez sur le **ItineraryService2** élément de modèle et, dans la fenêtre Propriétés, définissez la **d’extension du Service itinéraire** propriété **rampe itinéraire Service Extension**.  
  
24. Définir le **rampe** propriété **OffRamp1 > gestionnaires d’envoi**.  
  
25. Cliquez sur le **OffRamp1** élément de modèle et, dans la fenêtre Propriétés, définissez la **extendeur** propriété **rampe ESB Service Extension**.  
  
26. Définir le **Application BizTalk** propriété **GlobalBank.ESB**.  
  
27. Définir le **Port d’envoi** propriété **DynamicResolutionOneWay**.  
  
28. Cliquez sur l’aire de conception, puis cliquez sur **exporter le modèle**.  
  
29. Examinez le code XML généré.  
  
    > [!NOTE]
    >  Notez le **PropertyBag** élément et les propriétés qu’il contient. Notez également l’exemple de chaîne de connexion de programme de résolution et la façon dont il a été configuré selon les propriétés d’entrée.