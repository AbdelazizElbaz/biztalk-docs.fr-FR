---
title: "Exécution de l’exemple d’opérations BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e91d4e57-ba94-4730-8c5a-4c96902f313f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57480e6020b2ab262d7d9db522b9dd2f79aa49cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-biztalk-operations-sample"></a>Exécution de l’exemple d’opérations BizTalk
L’exemple de Microsoft BizTalk Operations utilise une application de client de test de Windows Forms pour exécuter des méthodes du service Web d’opérations BizTalk et afficher les résultats. Vous pouvez ouvrir le projet de client de test pour l’exécuter et d’examiner le code pour voir comment vous pouvez utiliser le service Web d’opérations BizTalk dans votre propre architecture orientée services (SOA) et les applications d’ESB.  
  
 Dans l’Explorateur Windows, ouvrez le dossier nommé \Samples\BizTalkOperations\bin\Debug et puis exécutez l’application Microsoft.Practices.ESB.BizTalkOperations.Test.Client.exe.  
  
 Figure 1 montre l’application cliente de test pour le service Web d’opérations BizTalk. Vous pouvez exécuter toutes les fonctions du service Web d’opérations BizTalk à l’aide de cette application. L’application affiche les résultats dans un format d’arborescence et affiche le message retourné par le service.  
  
 ![Web Service Test](../esb-toolkit/media/ch6-webservicetest.gif "§ 6-WebServiceTest")  
  
 **Figure 1**  
  
 **Le Client de Test BizTalk opérations Web Service**  
  
 Pour exécuter une méthode du service Web d’opérations BizTalk qui ne requiert pas de tous les paramètres, cliquez simplement sur le bouton approprié dans la partie gauche de la fenêtre d’application. Pour les méthodes qui ne nécessitent pas les paramètres d’entrée, sélectionnez la méthode dans la liste déroulante en haut de la fenêtre, entrez les valeurs de paramètre que vous avez besoin et puis cliquez sur le **appeler le Service** bouton.  
  
## <a name="how-the-sample-works"></a>Fonctionne de l’exemple  
 L’exemple d’application instancie le service Web d’Operations ESB BizTalk et appelle la méthode appropriée en fonction des paramètres que vous sélectionnez dans l’application. Il transmet les valeurs que vous entrez dans les contrôles de l’application en tant que paramètres à la méthode de service sélectionné, et il récupère la sortie à partir de la méthode de service à afficher dans la fenêtre d’application.