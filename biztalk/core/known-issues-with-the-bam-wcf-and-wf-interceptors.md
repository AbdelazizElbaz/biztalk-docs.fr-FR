---
title: "Problèmes connus avec l’analyse BAM intercepteurs WCF et WF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2407809-1f71-41a9-b305-722a7f86af5b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42078eb2b1272072016ded9a117e88ddf4fda038
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-bam-wcf-and-wf-interceptors"></a><span data-ttu-id="9c9d2-102">Problèmes connus avec les intercepteurs WCF et WF BAM</span><span class="sxs-lookup"><span data-stu-id="9c9d2-102">Known Issues with the BAM WCF and WF Interceptors</span></span>
<span data-ttu-id="9c9d2-103">Cette section fournit des informations sur certains problèmes connus que vous pouvez rencontrer lors de l'utilisation des intercepteurs BAM pour Windows Workflow Foundation ou Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-103">This section provides information about known issues that you may experience when using the BAM interceptors for Windows Workflow Foundation or Windows Communication Foundation.</span></span>  
  
## <a name="intercepting-a-dynamically-generated-wcf-assembly-hosted-in-iis"></a><span data-ttu-id="9c9d2-104">Interception d'un assembly WCF généré de manière dynamique et hébergé dans IIS</span><span class="sxs-lookup"><span data-stu-id="9c9d2-104">Intercepting a dynamically generated WCF assembly hosted in IIS</span></span>  
 <span data-ttu-id="9c9d2-105">Lorsque vous faites appel à IIS pour héberger une application Windows Communication Foundation intégrée (par exemple, un fichier de service qui spécifie la source de l'assembly), l'assembly WCF est généré de manière dynamique, il reçoit un nom de fichier arbitraire et il est placé dans le dossier temporaire asp.net.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-105">When you are using IIS to host an embedded Windows Communication Foundation application (for example, a service file that specifies the assembly source), the WCF assembly will be dynamically generated, assigned an arbitrary file name, and placed in the asp.net temporary folder.</span></span> <span data-ttu-id="9c9d2-106">Le fichier de configuration de l'intercepteur exige les informations sur le manifeste : étant donné que les caractères génériques ou d'autres méthodes dynamiques permettant de spécifier le manifeste ne sont pas disponibles pour les fichiers de configuration de l'intercepteur, vous devez recompiler votre service, puis créer le fichier de configuration de l'intercepteur ou redéployer celui existant après avoir déployé toutes les pages Web asp.net contenant du code WCF incorporé.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-106">Since the interceptor configuration file requires manifest information and since wildcard characters or other dynamic methods for specifying the manifest are not available with interceptor configuration files, you must recompile your service and then build your interceptor configuration file or redeploy your interceptor configuration file after you have deployed all of the asp.net web pages containing embedded WCF code.</span></span>  
  
## <a name="use-of-the-bam-interceptor-for-windows-workflow-foundation-is-not-supported-in-office-and-sharepoint-server"></a><span data-ttu-id="9c9d2-107">L'utilisation de l'intercepteur BAM pour Windows Workflow Foundation n'est pas prise en charge dans Office ni Sharepoint Server</span><span class="sxs-lookup"><span data-stu-id="9c9d2-107">Use of the BAM interceptor for Windows Workflow Foundation is not supported in Office and Sharepoint Server</span></span>  
 <span data-ttu-id="9c9d2-108">Office et Windows Sharepoint Server ne lisent pas à partir du fichier de configuration de l'application lors de l'initialisation du composant d'exécution WF.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-108">Both office and Windows Sharepoint Server do not read from the application configuration file when initializing the WF runtime.</span></span> <span data-ttu-id="9c9d2-109">Par conséquent, l'intercepteur BAM pour WF peut être configuré pour une application, mais il ne sera pas chargé dans le composant d'exécution du workflow lorsqu'il est hébergé dans ces environnements.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-109">As a result, the BAM interceptor for WF may be configured for an application but it will not be loaded into the workflow runtime when hosted within these environments.</span></span>  
  
## <a name="client-service-locks-when-intiating-a-distributed-transaction"></a><span data-ttu-id="9c9d2-110">Le service client est verrouillé lors de l'initialisation d'une transaction distribuée</span><span class="sxs-lookup"><span data-stu-id="9c9d2-110">Client service locks when intiating a distributed transaction</span></span>  
 <span data-ttu-id="9c9d2-111">Si l'opération de service ne participe pas à la transaction initiée par le client et que ce dernier appelle le service d'après le contexte d'une étendue de transaction, un blocage peut survenir, notamment lorsque des données sont collectées au niveau du client avant la demande d'envoi et au niveau du service par la demande de réception pour la même activité.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-111">If the service operation will not be participating in the transaction initiated by the client and the client is invoking the service from the context of a transaction scope, a deadlock could result, especially if there is data being collected from the client before the send request and from the service by the receive request for the same activity.</span></span>  
  
 <span data-ttu-id="9c9d2-112">Pour éviter cette situation, vous devez indiquer que le client ne participe pas à la transaction en déclarant « Enlist = false » dans l'attribut `ConnectionString` du client pour l'extension de comportement BAM dans le fichier app.config du client, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-112">To avoid this situation, you should specify that the client does not participate in the transaction by declaring "Enlist = false" in the client `ConnectionString` attribute for the BAM behavior extension in the client's app.config file as demonstrated below.</span></span>  
  
```  
<behavior name="bamClientBehavior">  
  <bamClientBehaviorExtension ConnectionString="Integrated Security=SSPI;Initial Catalog=BAMPrimaryImport;Data Source=.;  Enlist=false"  PollingIntervalSec="1500" />  
</behavior>  
```  
  
## <a name="open-wcf-channel-before-sending-a-message-when-bam-interceptors-are-used"></a><span data-ttu-id="9c9d2-113">Ouverture du canal WCF avant l'envoi d'un message lors de l'utilisation des intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="9c9d2-113">Open WCF Channel Before Sending a Message when BAM Interceptors are used</span></span>  
 <span data-ttu-id="9c9d2-114">Lorsque l'intercepteur BAM est activé pour WCF avec une liaison BasicHttp, le proxy doit appeler proxy.Open() pour ouvrir de manière explicite le canal.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-114">When BAM interceptor is enabled for WCF with BasicHttp binding, proxy should call proxy.Open() to explicitly open the channel.</span></span> <span data-ttu-id="9c9d2-115">Si cette condition n'est pas remplie, l'interception BAM risque d'échouer en générant une exception.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-115">If the channel is not opened explicitly, BAM interception can fail with an exception.</span></span>