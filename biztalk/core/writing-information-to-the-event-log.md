---
title: "Écrire des informations dans le journal des événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d7398dc-29d8-4a7a-bab4-c8f128b47dca
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f848cafd6ee9247511db3b9a6dad7dc5da91236b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="writing-information-to-the-event-log"></a><span data-ttu-id="dda0f-102">Écriture d'informations dans le journal des événements</span><span class="sxs-lookup"><span data-stu-id="dda0f-102">Writing Information to the Event Log</span></span>
<span data-ttu-id="dda0f-103">Il est possible de contrôler la progression des divers processus d'entreprise de votre application BizTalk en écrivant des informations dans le journal de l'application ou un journal des événements personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dda0f-103">You may want to monitor the progress of the different business processes within your BizTalk application by writing information to the default Application log or to a custom event log.</span></span> <span data-ttu-id="dda0f-104">L'écriture d'informations dans le journal des événements peut s'avérer utile dans les situations suivantes  :</span><span class="sxs-lookup"><span data-stu-id="dda0f-104">Writing to the event log can be useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="dda0f-105">vous voulez accéder aux messages de l'application de manière standard à l'aide des outils fournis par Windows ;</span><span class="sxs-lookup"><span data-stu-id="dda0f-105">You want to access application messages in a standard way using tools supplied by Windows.</span></span>  
  
-   <span data-ttu-id="dda0f-106">vous voulez archiver des informations ainsi que d'autres messages de l'environnement serveur afin d'obtenir un historique plus complet ;</span><span class="sxs-lookup"><span data-stu-id="dda0f-106">You want to archive information with other messages from the server environment for a more complete history.</span></span>  
  
-   <span data-ttu-id="dda0f-107">vous voulez pouvoir contrôler votre application à l'aide d'outils qui interagissent avec le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="dda0f-107">You want the ability to monitor your application using tools that interact with the event log.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dda0f-108">La taille de la méthode System.Diagnostics.EventLog.WriteEntry est limitée sur la chaîne de message.</span><span class="sxs-lookup"><span data-stu-id="dda0f-108">The System.Diagnostics.EventLog.WriteEntry method has a size limitation on the message string.</span></span> <span data-ttu-id="dda0f-109">Si cette chaîne dépasse 32 766 octets, un message d'exception s'affiche.</span><span class="sxs-lookup"><span data-stu-id="dda0f-109">You will receive exception if the message string exceeds 32766 bytes.</span></span>  
  
## <a name="writing-to-the-application-log"></a><span data-ttu-id="dda0f-110">Écriture dans le journal de l'application</span><span class="sxs-lookup"><span data-stu-id="dda0f-110">Writing to the Application Log</span></span>  
 <span data-ttu-id="dda0f-111">Vous pouvez écrire le journal des applications ou de tout autre journal à partir de votre code à l’aide de **System.Diagnostics.EventLog** comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dda0f-111">You can write to the Application log or any other log from your code by using **System.Diagnostics.EventLog** as shown in the following:</span></span>  
  
```  
System.Diagnostics.EventLog.WriteEntry("Orchestration Debug", System.String.Format("The Value = {0}", iResult));  
```  
  
 <span data-ttu-id="dda0f-112">De la même manière, vous pouvez utiliser :</span><span class="sxs-lookup"><span data-stu-id="dda0f-112">Similar, you can also do,</span></span>  
  
```  
EventLog appLog = new EventLog();   
appLog.Source = "This Application's Name";  
appLog.WriteEntry("An entry to the Application event log.");  
```  
  
 <span data-ttu-id="dda0f-113">Si vous utilisez un journal personnalisé, vous devez utiliser le **SourceExists** méthode pour garantir qu’il existe avant d’écrire sur elle.</span><span class="sxs-lookup"><span data-stu-id="dda0f-113">If you are using a custom log, you should use the **SourceExists** method to ensure it exists before you write to it.</span></span>  
  
## <a name="writing-to-a-custom-log"></a><span data-ttu-id="dda0f-114">Écriture dans un journal personnalisé</span><span class="sxs-lookup"><span data-stu-id="dda0f-114">Writing to a Custom Log</span></span>  
 <span data-ttu-id="dda0f-115">L'écriture dans un journal personnalisé est similaire à l'écriture dans le journal de l'application, à ceci près que vous devez d'abord créer le journal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dda0f-115">Writing to a custom log is similar to writing to the Application log with the exception that you must first create the custom log.</span></span> <span data-ttu-id="dda0f-116">Voici le code à utiliser pour créer un journal personnalisé :</span><span class="sxs-lookup"><span data-stu-id="dda0f-116">The code to create a custom log is straightforward:</span></span>  
  
```  
// Create the source, if it does not already exist. if(!EventLog.SourceExists("MySource"))   
{   
  //An event log source should not be created and immediately used.  
  //There is a latency time to enable the source, it should be created  
  //prior to executing the application that uses the source.  
  EventLog.CreateEventSource("MySource", "MyNewLog");  
}  
```  
  
 <span data-ttu-id="dda0f-117">Cependant, votre code ne pourra être exécuté par un compte qui dispose des privilèges de sécurité suffisants pour la création d'un nouveau journal des événements.</span><span class="sxs-lookup"><span data-stu-id="dda0f-117">However, you should not assume that your code will be run under an account that has the security privileges to create a new event log.</span></span> <span data-ttu-id="dda0f-118">En effet, la création d'un journal des événements requiert également des privilèges d'administrateur et doit être effectuée dans un utilitaire distinct ou, idéalement, dans le cadre d'une installation .msi.</span><span class="sxs-lookup"><span data-stu-id="dda0f-118">Creating an event log takes administrator privileges and should be done in a separate utility program or, ideally, as part of an .msi installation.</span></span> <span data-ttu-id="dda0f-119">Pour plus d’informations sur l’utilisation de script personnalisé avec une installation .msi exportée, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="dda0f-119">For more information about using custom script with an exported .msi installation, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>