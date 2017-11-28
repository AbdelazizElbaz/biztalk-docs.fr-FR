---
title: "Exemple de Service de gestion des exceptions en cours d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d69e720c-89e4-42c2-b4d0-31f0b865ab7f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a224c985591801bc9622000c35587b7137f933
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-exception-handling-service-sample"></a><span data-ttu-id="7b02b-102">Exemple de Service de gestion des exceptions en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="7b02b-102">Running the Exception Handling Service Sample</span></span>
<span data-ttu-id="7b02b-103">L’exemple de Service de gestion des exceptions montre comment consommer le Service Web de gestion des exceptions afin d’envoyer une erreur dans l’infrastructure de gestion d’Exception ESB à partir d’une application externe.</span><span class="sxs-lookup"><span data-stu-id="7b02b-103">The Exception Handling Service sample demonstrates how to consume the Exception Handling Web Service in order to submit a fault into the ESB Exception Handling Framework from an external application.</span></span> <span data-ttu-id="7b02b-104">La procédure suivante pour exécuter cet exemple nécessite [installant les exemples de gestion des exceptions](../esb-toolkit/installing-the-exception-management-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b02b-104">The following procedure for running this sample requires [Installing the Exception Management Samples](../esb-toolkit/installing-the-exception-management-samples.md).</span></span>  
  
 <span data-ttu-id="7b02b-105">**Pour exécuter l’exemple de Service de gestion des exceptions**</span><span class="sxs-lookup"><span data-stu-id="7b02b-105">**To run the Exception Handling Service sample**</span></span>  
  
1.  <span data-ttu-id="7b02b-106">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ExceptionHandlingService, où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et ouvrez le fichier de solution Visual Studio nommé ExceptionHandlingService.sln.</span><span class="sxs-lookup"><span data-stu-id="7b02b-106">In Windows Explorer, open the folder \Source\Samples\ExceptionHandlingService, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Visual Studio solution file named ExceptionHandlingService.sln.</span></span>  
  
2.  <span data-ttu-id="7b02b-107">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], cliquez sur **démarrer le débogage** sur la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="7b02b-107">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], click **Start Debugging** on the Toolbar.</span></span>  
  
3.  <span data-ttu-id="7b02b-108">Dans le formulaire qui charge, cliquez sur le **générer une Exception** bouton.</span><span class="sxs-lookup"><span data-stu-id="7b02b-108">On the form that loads, click the **Generate Exception** button.</span></span>  
  
4.  <span data-ttu-id="7b02b-109">Dans l’Explorateur Windows, ouvrez le dossier \Samples\Exception Handling\Test\Filedrop\All_Exceptions et ouvrez le fichier le plus récent Exceptions_ {GUID} .xml.</span><span class="sxs-lookup"><span data-stu-id="7b02b-109">In Windows Explorer, open the folder \Samples\Exception Handling\Test\Filedrop\All_Exceptions, and then open the most recent Exceptions_{GUID}.xml file.</span></span>  
  
5.  <span data-ttu-id="7b02b-110">Examinez le contenu de l’exception générée.</span><span class="sxs-lookup"><span data-stu-id="7b02b-110">Examine the contents of the generated exception.</span></span>  
  
 <span data-ttu-id="7b02b-111">Pour plus d’informations sur la façon dont l’exemple de Service de gestion des exceptions utilise le service de gestion des exceptions, consultez [Exception gestion Service exemple fonctionnement](../esb-toolkit/how-the-exception-handling-service-sample-works.md).</span><span class="sxs-lookup"><span data-stu-id="7b02b-111">For more information about how the Exception Handling Service sample uses the Exception Management service, see [How the Exception Handling Service Sample Works](../esb-toolkit/how-the-exception-handling-service-sample-works.md).</span></span>