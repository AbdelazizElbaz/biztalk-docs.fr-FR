---
title: "Exécuter un scénario d’itinéraire personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fd69e29-e853-4b16-9966-29ab98dd5bea
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8659c5b37cba0520fb4a4c0f4c63c8d6ecff37be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="execute-a-custom-itinerary-scenario"></a>Exécuter un scénario d’itinéraire personnalisé
Vous pouvez utiliser le Client de Test itinéraire application exécuter des scénarios d’itinéraire personnalisées.  
  
### <a name="to-execute-a-custom-itinerary-scenario-using-the-itinerary-test-client-application"></a>Pour exécuter un scénario d’itinéraire personnalisé à l’aide de l’application cliente de Test d’itinéraire  
  
1.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test\bin\Debug où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] échantillonne et démarrer l’application nommée Esb.Itinerary.Test.exe.  
  
2.  Sélectionnez un type de service dans le **ServiceType** la liste déroulante, spécifiez un nom pour la demande, puis sélectionnez le **IsRequestResponse** case à cocher s’il s’agit d’une opération de demande/réponse. Vous pouvez spécifier une opération bidirectionnelle et choisir d’utiliser la version WCF du service Web de l’itinéraire ; Pour ce faire, activez les cases à cocher dans la **Options du Service Web** section en haut de la fenêtre d’application.  
  
3.  Pour spécifier la résolution à utiliser avec le service sélectionné dans le **AddResolversfortheService** section de la fenêtre, sélectionnez un programme de résolution de type dans la liste déroulante, puis cliquez sur **AddResolver**. Vous pouvez ajouter plus d’un programme de résolution si nécessaire. Après avoir ajouté tous les programmes de résolution requis, cliquez sur le **AddService** pour ajouter cet appel de service à l’itinéraire.  
  
4.  Si vous souhaitez ajouter plus d’appels de service pour l’itinéraire, répétez les étapes 2 et 3. Vous pouvez également utiliser le **RemoveService** et **ClearServices** boutons pour modifier la liste des services dans l’itinéraire.  
  
5.  Si vous souhaitez répéter l’itinéraire actuel à un autre moment, enregistrez la feuille de route en cours terminée sur le disque en cliquant sur le **SaveItinerary** bouton. Vous pouvez le charger à nouveau en cliquant sur le **LoadItinerary** bouton. Cela signifie que vous n’avez pas à spécifier les services et les programmes de résolution dans l’itinéraire, chaque fois que vous exécutez ce scénario avec différents messages ou les paramètres du service Web de l’itinéraire.  
  
6.  Charger un message approprié. Pour ce faire, tapez le chemin d’accès et le nom du message dans le **LoadMessage** texte zone ou cliquez sur le bouton de sélection (...), puis sélectionnez le fichier de message requis.  
  
7.  Cliquez sur le **SubmitRequest** pour envoyer le message pour le traitement avec les paramètres d’itinéraire spécifiés. Si le traitement retourne un résultat, il apparaît dans le **résultat** zone de texte.