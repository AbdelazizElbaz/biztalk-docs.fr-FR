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
# <a name="running-the-biztalk-operations-sample"></a><span data-ttu-id="74e44-102">Exécution de l’exemple d’opérations BizTalk</span><span class="sxs-lookup"><span data-stu-id="74e44-102">Running the BizTalk Operations Sample</span></span>
<span data-ttu-id="74e44-103">L’exemple de Microsoft BizTalk Operations utilise une application de client de test de Windows Forms pour exécuter des méthodes du service Web d’opérations BizTalk et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="74e44-103">The Microsoft BizTalk Operations sample uses a Windows Forms test client application to execute methods of the BizTalk Operations Web service and display the results.</span></span> <span data-ttu-id="74e44-104">Vous pouvez ouvrir le projet de client de test pour l’exécuter et d’examiner le code pour voir comment vous pouvez utiliser le service Web d’opérations BizTalk dans votre propre architecture orientée services (SOA) et les applications d’ESB.</span><span class="sxs-lookup"><span data-stu-id="74e44-104">You can open the test client project to run it and to examine the code to see how you can use the BizTalk Operations Web service in your own service-oriented architecture (SOA) and ESB applications.</span></span>  
  
 <span data-ttu-id="74e44-105">Dans l’Explorateur Windows, ouvrez le dossier nommé \Samples\BizTalkOperations\bin\Debug et puis exécutez l’application Microsoft.Practices.ESB.BizTalkOperations.Test.Client.exe.</span><span class="sxs-lookup"><span data-stu-id="74e44-105">In Windows Explorer, open the folder named \Samples\BizTalkOperations\bin\Debug, and then execute the application Microsoft.Practices.ESB.BizTalkOperations.Test.Client.exe.</span></span>  
  
 <span data-ttu-id="74e44-106">Figure 1 montre l’application cliente de test pour le service Web d’opérations BizTalk.</span><span class="sxs-lookup"><span data-stu-id="74e44-106">Figure 1 shows the test client application for the BizTalk Operations Web service.</span></span> <span data-ttu-id="74e44-107">Vous pouvez exécuter toutes les fonctions du service Web d’opérations BizTalk à l’aide de cette application.</span><span class="sxs-lookup"><span data-stu-id="74e44-107">You can execute all the functions of the BizTalk Operations Web service using this application.</span></span> <span data-ttu-id="74e44-108">L’application affiche les résultats dans un format d’arborescence et affiche le message retourné par le service.</span><span class="sxs-lookup"><span data-stu-id="74e44-108">The application displays the results in a tree-view format and shows the message returned by the service.</span></span>  
  
 <span data-ttu-id="74e44-109">![Web Service Test](../esb-toolkit/media/ch6-webservicetest.gif "§ 6-WebServiceTest")</span><span class="sxs-lookup"><span data-stu-id="74e44-109">![Web Service Test](../esb-toolkit/media/ch6-webservicetest.gif "Ch6-WebServiceTest")</span></span>  
  
 <span data-ttu-id="74e44-110">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="74e44-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="74e44-111">**Le Client de Test BizTalk opérations Web Service**</span><span class="sxs-lookup"><span data-stu-id="74e44-111">**The BizTalk Operations Web Service Test Client**</span></span>  
  
 <span data-ttu-id="74e44-112">Pour exécuter une méthode du service Web d’opérations BizTalk qui ne requiert pas de tous les paramètres, cliquez simplement sur le bouton approprié dans la partie gauche de la fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="74e44-112">To execute a method of the BizTalk Operations Web service that does not require any parameters, simply click the appropriate button in the left side of the application window.</span></span> <span data-ttu-id="74e44-113">Pour les méthodes qui ne nécessitent pas les paramètres d’entrée, sélectionnez la méthode dans la liste déroulante en haut de la fenêtre, entrez les valeurs de paramètre que vous avez besoin et puis cliquez sur le **appeler le Service** bouton.</span><span class="sxs-lookup"><span data-stu-id="74e44-113">For methods that do require input parameters, select the method in the drop-down list at the top of the window, enter the parameter values you require, and then click the **Invoke Service** button.</span></span>  
  
## <a name="how-the-sample-works"></a><span data-ttu-id="74e44-114">Fonctionne de l’exemple</span><span class="sxs-lookup"><span data-stu-id="74e44-114">How the Sample Works</span></span>  
 <span data-ttu-id="74e44-115">L’exemple d’application instancie le service Web d’Operations ESB BizTalk et appelle la méthode appropriée en fonction des paramètres que vous sélectionnez dans l’application.</span><span class="sxs-lookup"><span data-stu-id="74e44-115">The sample application instantiates the ESB BizTalk Operations Web service and calls the appropriate method depending on the settings you select in the application.</span></span> <span data-ttu-id="74e44-116">Il transmet les valeurs que vous entrez dans les contrôles de l’application en tant que paramètres à la méthode de service sélectionné, et il récupère la sortie à partir de la méthode de service à afficher dans la fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="74e44-116">It passes the value(s) you enter in the application controls as parameters to the selected service method, and it collects the output from the service method to display in the application window.</span></span>