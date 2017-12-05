---
title: "Installation de l’exemple d’opérations BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57c982c2-f796-4c63-9bca-7e8965779850
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8fb289e5bb7950f9ad8bca3dac98035bada176
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-the-biztalk-operations-sample"></a><span data-ttu-id="f6e4c-102">Installation de l’exemple d’opérations BizTalk</span><span class="sxs-lookup"><span data-stu-id="f6e4c-102">Installing the BizTalk Operations Sample</span></span>
<span data-ttu-id="f6e4c-103">L’exemple de BizTalk de Microsoft Operations nécessite le service d’opérations de BizTalk ESB installé et configuré.</span><span class="sxs-lookup"><span data-stu-id="f6e4c-103">The Microsoft BizTalk Operations sample requires the ESB BizTalk Operations service installed and configured.</span></span> <span data-ttu-id="f6e4c-104">Service d’opérations de BizTalk ESB est un des services Web principaux qui peuvent être installés et configurés à l’aide de l’outil de Configuration ESB.</span><span class="sxs-lookup"><span data-stu-id="f6e4c-104">ESB BizTalk Operations service is one of the core Web services that can be installed and configured using the ESB Configuration Tool.</span></span> <span data-ttu-id="f6e4c-105">Pour plus d’informations sur l’utilisation de l’outil de Configuration ESB, consultez [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).</span><span class="sxs-lookup"><span data-stu-id="f6e4c-105">For more information about using the ESB Configuration Tool, see [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).</span></span> <span data-ttu-id="f6e4c-106">L’emplacement par défaut du service Web d’opérations BizTalk est http://localhost/ESB.BizTalkOperationsService/Operations.asmx; Toutefois, vous pouvez y remédier dans le fichier de configuration d’application si vous déployez le service dans un autre emplacement ou un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="f6e4c-106">The default location of the BizTalk Operations Web service is http://localhost/ESB.BizTalkOperationsService/Operations.asmx; however, you can change this in the application configuration file if you deploy the service in a different location or a remote server.</span></span>  
  
 <span data-ttu-id="f6e4c-107">Vous devez installer les exemples d’opérations BizTalk à partir du projet de la solution.</span><span class="sxs-lookup"><span data-stu-id="f6e4c-107">You must install BizTalk Operations sample from the solution project.</span></span>  
  
 <span data-ttu-id="f6e4c-108">**Pour installer l’exemple d’opérations BizTalk**</span><span class="sxs-lookup"><span data-stu-id="f6e4c-108">**To install the BizTalk Operations sample**</span></span>  
  
1.  <span data-ttu-id="f6e4c-109">Ouvrez la solution nommée ESB.BizTalkOperations.Test.Client.csproj à partir du dossier \Source\Samples\BizTalkOperations où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6e4c-109">Open the solution named ESB.BizTalkOperations.Test.Client.csproj from the \Source\Samples\BizTalkOperations folder where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples into Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f6e4c-110">Utilisez les commandes dans le **générer** menu pour compiler la solution.</span><span class="sxs-lookup"><span data-stu-id="f6e4c-110">Use the commands on the **Build** menu to compile the solution.</span></span>