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
ms.openlocfilehash: 6307f9d9e4ff9907bab22efcde0755dbdfdc228b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-biztalk-operations-sample"></a><span data-ttu-id="6bcdc-102">Installation de l’exemple d’opérations BizTalk</span><span class="sxs-lookup"><span data-stu-id="6bcdc-102">Installing the BizTalk Operations Sample</span></span>
<span data-ttu-id="6bcdc-103">L’exemple de BizTalk de Microsoft Operations nécessite le service d’opérations de BizTalk ESB installé et configuré.</span><span class="sxs-lookup"><span data-stu-id="6bcdc-103">The Microsoft BizTalk Operations sample requires the ESB BizTalk Operations service installed and configured.</span></span> <span data-ttu-id="6bcdc-104">Service d’opérations de BizTalk ESB est un des services Web principaux qui peuvent être installés et configurés à l’aide de l’outil de Configuration ESB.</span><span class="sxs-lookup"><span data-stu-id="6bcdc-104">ESB BizTalk Operations service is one of the core Web services that can be installed and configured using the ESB Configuration Tool.</span></span> <span data-ttu-id="6bcdc-105">Pour plus d’informations sur l’utilisation de l’outil de Configuration ESB, consultez [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).</span><span class="sxs-lookup"><span data-stu-id="6bcdc-105">For more information about using the ESB Configuration Tool, see [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).</span></span> <span data-ttu-id="6bcdc-106">L’emplacement par défaut du service Web d’opérations BizTalk est http://localhost/ESB.BizTalkOperationsService/Operations.asmx; Toutefois, vous pouvez y remédier dans le fichier de configuration d’application si vous déployez le service dans un autre emplacement ou un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="6bcdc-106">The default location of the BizTalk Operations Web service is http://localhost/ESB.BizTalkOperationsService/Operations.asmx; however, you can change this in the application configuration file if you deploy the service in a different location or a remote server.</span></span>  
  
 <span data-ttu-id="6bcdc-107">Vous devez installer les exemples d’opérations BizTalk à partir du projet de la solution.</span><span class="sxs-lookup"><span data-stu-id="6bcdc-107">You must install BizTalk Operations sample from the solution project.</span></span>  
  
 <span data-ttu-id="6bcdc-108">**Pour installer l’exemple d’opérations BizTalk**</span><span class="sxs-lookup"><span data-stu-id="6bcdc-108">**To install the BizTalk Operations sample**</span></span>  
  
1.  <span data-ttu-id="6bcdc-109">Ouvrez la solution nommée ESB.BizTalkOperations.Test.Client.csproj à partir du dossier \Source\Samples\BizTalkOperations où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples dans [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6bcdc-109">Open the solution named ESB.BizTalkOperations.Test.Client.csproj from the \Source\Samples\BizTalkOperations folder where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples into [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6bcdc-110">Utilisez les commandes dans le **générer** menu pour compiler la solution.</span><span class="sxs-lookup"><span data-stu-id="6bcdc-110">Use the commands on the **Build** menu to compile the solution.</span></span>