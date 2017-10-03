---
title: "Sur les itinéraires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d34632f-8652-49dd-97b7-2513aacc1bd7
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66a9a759a6afdd55c3c1646d02c480aa193261aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-itineraries"></a>À propos des itinéraires
Un itinéraire est une représentation d’une stratégie de médiation ESB pour l’exécution d’une séquence d’instructions en fonction de traitement le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] format extensible. Un itinéraire peut être considéré comme un langage de haut niveau de médiation qui décrit une série de services d’itinéraire déclaratives qui sont associés à des composants de médiation par la configuration de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] moteur de base. Vous pouvez concevoir des flux de médiation pour décrire la manière dont les messages doivent être traités, et vous pouvez organiser le flux entier comme un dessin visuel. Au moment de l’exécution, le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] moteur principal exécute l’itinéraire produit par le Concepteur d’itinéraire.  
  
## <a name="the-itinerary-designer-surface"></a>L’aire du Concepteur d’itinéraire  
 La surface du Concepteur d’itinéraire est un concepteur visuel qui permet de créer [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinéraires et exporter ces itinéraires dans le format de l’exécution. Il s’agit d’une zone de dessin à laquelle vous pouvez faire glisser des éléments à partir de la boîte à outils, comme illustré dans la Figure 1.  
  
 ![Concepteur d’itinéraire](../esb-toolkit/media/ch5-itinerarydesigner.gif "Ch5-ItineraryDesigner")  
  
 **Figure 1**  
  
 **Aire du Concepteur d’itinéraire**  
  
 Le nom de l’itinéraire s’affiche sous l’onglet supérieur du Concepteur d’itinéraire et dans la barre de titre de Microsoft Visual Studio. L’aire de conception elle-même est une zone et contienne les éléments de modèle qui décrivent le flux de message réel de l’itinéraire. Le ItineraryDSL vous permet de modifier les propriétés d’élément de modèle à l’aide de la fenêtre Propriétés de Visual Studio.  
  
## <a name="itinerary-designer-toolbox"></a>Boîte à outils du Concepteur d’itinéraire  
 La boîte à outils Visual Studio contient des onglets, qui représentent les ensembles d’outils. Lorsque vous ouvrez un projet Visual Studio qui utilise le Concepteur d’itinéraire, la boîte à outils contient deux onglets : le **général** onglet et la **ItineraryDsl** onglets. Le **ItineraryDsl** onglet contient les outils suivants :  
  
-   **Outil d’itinéraire du Service**. Cet élément de modèle correspond à la médiation d’itinéraire et représente une instruction de traitement.  
  
-   **Outil de connecteur**. Cet élément de modèle définit la relation entre les éléments de modèle individuel sur l’aire du Concepteur d’itinéraire.  
  
-   **Outil de rampe**. Cet élément de modèle correspond à la rampe qui envoie un message. Le Concepteur d’itinéraire permet plusieurs écarter par modèle.  
  
-   **Outil de rampe d’entrée**. Cet élément de modèle correspond à une rampe d’entrée qui reçoit un message. Le Concepteur d’itinéraire permet uniquement d’une rampe d’entrée par le modèle.  
  
-   **Outil de Service Broker d’itinéraire**. Cet élément de modèle correspond à la médiation d’itinéraire qui autorise le flux de message défini avec plusieurs entrées et plusieurs sorties.  
  
-   **Port de sortie de service Broker d’itinéraire**. Cet élément de modèle correspond au port de sortie de la feuille de route de Service Broker. L’élément de modèle d’itinéraire de Service Broker permet à plusieurs ports de sortie.  
  
## <a name="steps-in-itinerary-development"></a>Étapes de développement d’itinéraire  
 Pour développer un itinéraire, qui représente le flux de médiation ESB, vous devez généralement effectuer les actions suivantes :  
  
-   Ajouter des éléments de modèle pour représenter le traitement des étapes de votre feuille de route des messages. Le Concepteur d’itinéraire fournit une boîte à outils qui contient des formes utilisées pour représenter diverses actions et des abstractions de clé.  
  
-   Spécifiez les propriétés du modèle d’itinéraire, qui incluent une chaîne de connexion à la configuration de l’exportateur Microsoft BizTalk Server Administration de base de données et le modèle.  
  
-   Lier des éléments de modèle rampe d’entrée et rampe à BizTalk physique des emplacements de réception et ports d’envoi en associant ces éléments de modèle correspondant extendeurs de technologie.  
  
-   Associer des éléments de modèle d’itinéraire services extendeurs et définir les propriétés spécifiques à la technologie requises par un extendeur. Ces propriétés peuvent varier d’un type particulier de l’extendeur ; ils peuvent représenter des propriétés du service de médiation d’itinéraire et les propriétés spécifiques à BizTalk associées à ses composants d’exécution et les artefacts.  
  
-   Identifier les composants personnalisés que vous pouvez faire référence en tant que services de médiation d’itinéraire. Par exemple, vous pouvez développer une orchestration en tant que le service d’itinéraire.  
  
-   Vérifiez les paramètres d’élément de modèle de résolution par rapport à [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration d’exécution en appelant le service de résolution de l’aire du concepteur.  
  
-   Valider et exporter la stratégie d’exécution d’itinéraire à l’aide d’un exportateur. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit deux exportateurs avec le Concepteur d’itinéraire : fichier exportateur et l’exportateur de base de données. Vous pouvez également implémenter un exportateur personnalisé.  
  
-   Test de votre feuille de route à l’aide de tester les applications client ou BizUnit framework.  
  
## <a name="security-considerations-for-developing-itineraries"></a>Considérations sur la sécurité pour le développement d’itinéraires  
 Lorsque vous concevez des itinéraires, vous devez envisager les problèmes potentiels de sécurité :  
  
-   Évitez de spécifier des informations d’identification de l’utilisateur sans utiliser un certificat à partir des propriétés de modèle.  
  
-   Ne font pas référence à BizTalk ports de réception avec les emplacements de réception qui autorisent l’accès anonyme.  
  
-   Protéger le canal de transport ou message si le message d’itinéraire contient des données sensibles.  
  
-   Protéger les messages dans la boîte de Message avec un composant de pipeline si les messages contiennent des données sensibles qui doivent être protégées en cours de transit.