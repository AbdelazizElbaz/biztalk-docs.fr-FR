---
title: "Résoudre les problèmes opérationnels avec l’adaptateur Siebel dans BizTalk | Documents Microsoft"
description: "Problèmes courants et des solutions pour l’adaptateur Siebel dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d152d9-9893-4f93-894a-350bae8be7bd
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62d1ffae1318f4d04f7bd61ef27dd24fd1d5a2b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-siebel-adapter"></a><span data-ttu-id="ed1c8-103">Résoudre les problèmes opérationnels avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="ed1c8-103">Troubleshoot Operational Issues with the Siebel adapter</span></span>
<span data-ttu-id="ed1c8-104">Cette section fournit un emplacement centralisé pour plus d’informations sur les problèmes opérationnels, vous pouvez rencontrer en utilisant le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-104">This section provides a centralized location for information about operational issues you might encounter when using the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="ed1c8-105">L’activation du traçage</span><span class="sxs-lookup"><span data-stu-id="ed1c8-105">Enabling Tracing</span></span>  
 <span data-ttu-id="ed1c8-106">Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ed1c8-106">For information about tracing support in the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Diagnostic Tracing and Message Logging for the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="ed1c8-107">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="ed1c8-107">Known Issues</span></span>  
 <span data-ttu-id="ed1c8-108">Voici certains problèmes et les solutions recommandées que vous pouvez rencontrer lors de l’utilisation du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-108">The following are some issues and recommended solutions that you might encounter while using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
  
###  <span data-ttu-id="ed1c8-109"><a name="BKMK_SiebelBindingError"></a>Erreur lors du chargement des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="ed1c8-109"><a name="BKMK_SiebelBindingError"></a> Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="ed1c8-110">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-110">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-111">Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’interface graphique utilisateur attribue l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-111">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the GUI gives the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="ed1c8-112">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-112">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-113">Lorsque vous démarrez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF charge les liaisons de l’adaptateur pour tous les adaptateurs installés.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-113">When you start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="ed1c8-114">À son tour, les liaisons de l’adaptateur sont dépendants sur le logiciel client d’application spécifiques de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-114">In turn, the adapter bindings are dependent on the specific enterprise application client software.</span></span> <span data-ttu-id="ed1c8-115">Par conséquent, vous pourriez être confronté ce problème pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-115">So, you could face this issue for one or both of the following reasons:</span></span>  
  
-   <span data-ttu-id="ed1c8-116">Le logiciel client LOB requis n’est pas installé sur l’ordinateur où vous avez installé l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-116">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
-   <span data-ttu-id="ed1c8-117">Vous avez effectué une installation « Standard » ou « Terminé » de l’adaptateur, qui installe tous les adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-117">You did a "Typical" or "Complete" installation of the adapter, which installs all the adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="ed1c8-118">Toutefois, les bibliothèques clientes peuvent être installés pour seulement une application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-118">However, the client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="ed1c8-119">Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-119">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="ed1c8-120">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-120">**Resolution**</span></span>  
  
-   <span data-ttu-id="ed1c8-121">Assurez-vous que les versions de client requises sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-121">Make sure the required client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ed1c8-122">Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-122">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
###  <span data-ttu-id="ed1c8-123"><a name="BKMK_SiebelDispAdap"></a>L’adaptateur Siebel n’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ed1c8-123"><a name="BKMK_SiebelDispAdap"></a> The Siebel adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="ed1c8-124">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-124">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-125">Contrairement à la version antérieure des adaptateurs livrés avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournie avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des adaptateurs dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-125">Unlike the earlier version of the adapters that shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] that shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="ed1c8-126">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-126">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-127">La dernière version [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est une liaison WCF personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-127">The latest [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="ed1c8-128">Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-128">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
 <span data-ttu-id="ed1c8-129">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-129">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-130">Vous pouvez ajouter explicitement le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="ed1c8-130">You can explicitly add the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <span data-ttu-id="ed1c8-131"><a name="BKMK_SiebelConnecting"></a>Erreur lors de la connexion au système Siebel</span><span class="sxs-lookup"><span data-stu-id="ed1c8-131"><a name="BKMK_SiebelConnecting"></a> Error while connecting to the Siebel system</span></span>  
 <span data-ttu-id="ed1c8-132">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-132">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-133">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] attribue l’erreur suivante lorsque vous essayez de vous connecter au système Siebel :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-133">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] gives the following error when you try to connect to the Siebel system:</span></span>  
  
```  
Connecting to the system LOB has failed. Retrieving the COM class factory for component with CLSID {ID} failed due to the following error: 80040154  
```  
  
 <span data-ttu-id="ed1c8-134">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-134">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-135">Le client Siebel Web ne peut pas être installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-135">The Siebel Web client might not be installed on the computer.</span></span>  
  
 <span data-ttu-id="ed1c8-136">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-136">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-137">Assurez-vous que la version prise en charge du client Siebel Web est installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-137">Make sure the supported version of the Siebel Web client is installed on the computer.</span></span> <span data-ttu-id="ed1c8-138">Consultez le guide d’installation de clients pris en charge et les versions de serveur pour Siebel.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-138">Refer to the installation guide for supported client and server versions for Siebel.</span></span> <span data-ttu-id="ed1c8-139">Le guide d’installation est disponible à l’adresse \<lecteur système > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-139">The installation guide is available at \<system drive>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
  
###  <span data-ttu-id="ed1c8-140"><a name="BKMK_SiebelXMLRetrieve"></a>Erreur lors de la récupération XMLs avec plus de 65 536 nœuds</span><span class="sxs-lookup"><span data-stu-id="ed1c8-140"><a name="BKMK_SiebelXMLRetrieve"></a> Error while retrieving XMLs with more than 65536 nodes</span></span>  
 <span data-ttu-id="ed1c8-141">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-141">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-142">L’adaptateur attribue l’erreur suivante lors de la récupération de sortie XML qui a plus de 65 536 nœuds.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-142">The adapter gives the following error while retrieving XML output that has more than 65536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="ed1c8-143">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-143">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-144">L’adaptateur ne peut pas sérialiser et désérialiser un objet avec des éléments de plus de 65 536.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-144">The adapter cannot serialize and deserialize an object with more than 65536 items.</span></span>  
  
 <span data-ttu-id="ed1c8-145">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-145">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-146">Vous pouvez résoudre ce problème en définissant le `maxItemsInObjectGraph` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-146">You can fix this issue by setting the `maxItemsInObjectGraph` parameter.</span></span> <span data-ttu-id="ed1c8-147">Vous pouvez le définir dans un des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-147">You can set this in any of the following two ways:</span></span>  
  
-   <span data-ttu-id="ed1c8-148">Définissez ce paramètre en modifiant le `maxItemsInObjectGraph` paramètre dans le `ServiceBehavior` attribut sur votre classe de service.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-148">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
-   <span data-ttu-id="ed1c8-149">Ajoutez le code suivant au fichier app.config de votre application.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-149">Add the following to your application's app.config file.</span></span>  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 <span data-ttu-id="ed1c8-150">Un exemple app.config doit ressembler à :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-150">A sample app.config will look like:</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  \<system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="siebelBinding"  
       contract="IOutboundContract" name="siebel_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
###  <span data-ttu-id="ed1c8-151"><a name="BKMK_SiebelConnURI"></a>Erreur lors de la spécification d’un URI de connexion pour un port personnalisé WCF dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ed1c8-151"><a name="BKMK_SiebelConnURI"></a> Error while specifying a connection URI for a WCF-Custom port in BizTalk</span></span>  
 <span data-ttu-id="ed1c8-152">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-152">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ed1c8-153">attribue l’erreur suivante lorsque vous spécifiez un URI de connexion pour se connecter au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-153"> gives the following error when you specify a connection URI to connect to the Siebel system.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="ed1c8-154">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-154">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-155">L’URI de connexion n’est pas conforme au format de codage standard.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-155">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="ed1c8-156">Par exemple, la valeur d’un paramètre peut contenir un espace.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-156">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="ed1c8-157">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-157">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-158">Vérifiez que la connexion URI que vous spécifiez respecte le format d’encodage standard.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-158">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="ed1c8-159">Par exemple, un espace vide doit être remplacé par « %20 ».</span><span class="sxs-lookup"><span data-stu-id="ed1c8-159">For example, a blank space must be replaced by "%20".</span></span>  
  
###  <span data-ttu-id="ed1c8-160"><a name="BKMK_SiebelPerfOps"></a>Erreur lors de l’opération sur le système Siebel</span><span class="sxs-lookup"><span data-stu-id="ed1c8-160"><a name="BKMK_SiebelPerfOps"></a> Error while performing operation on the Siebel system</span></span>  
 <span data-ttu-id="ed1c8-161">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-161">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-162">L’adaptateur attribue l’erreur suivante lors de l’exécution de toute opération sur le système Siebel en utilisant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-162">The adapter gives the following error when performing any operation on the Siebel system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ed1c8-163">**Pour[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-163">**For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**</span></span>  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 <span data-ttu-id="ed1c8-164">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-164">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-165">L’action WCF pour le message n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-165">The WCF action for the message is not specified.</span></span> <span data-ttu-id="ed1c8-166">WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-166">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="ed1c8-167">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-167">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-168">Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-168">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="ed1c8-169">Pour obtenir des instructions, consultez [configurer l’action SOAP pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="ed1c8-169">For instructions, see [Configure the SOAP action for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md).</span></span> <span data-ttu-id="ed1c8-170">Consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) pour obtenir la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-170">See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation.</span></span>  
  
###  <span data-ttu-id="ed1c8-171"><a name="BKMK_SiebelXmlParsing"></a>XmlReaderParsingException en raison d’un nom d’opération incorrecte dans l’action spécifiée</span><span class="sxs-lookup"><span data-stu-id="ed1c8-171"><a name="BKMK_SiebelXmlParsing"></a> XmlReaderParsingException due to an incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="ed1c8-172">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-172">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-173">La console Administration de BizTalk Server attribue l’erreur suivante lors de l’envoi de messages à un système Siebel :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-173">The BizTalk Server Administration console gives the following error when sending messages to a Siebel system:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="ed1c8-174">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-174">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-175">Si vous configurez un port personnalisé WCF en important le fichier de liaison de port créé par le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’action dans le port est spécifiée dans le format suivant :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-175">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="ed1c8-176">Dans le format précédent, le nom de l’opération est régi par l’opération que vous avez choisi lors de la génération du schéma.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-176">In the preceding format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="ed1c8-177">Par exemple, si vous avez généré le schéma pour une opération de requête sur un composant d’entreprise Siebel, le nom de l’opération dans l’action sera « Requête ».</span><span class="sxs-lookup"><span data-stu-id="ed1c8-177">For example, if you generated schema for a Query operation on a Siebel business component, the operation name in the action will be "Query".</span></span> <span data-ttu-id="ed1c8-178">Toutefois, le nom de l’opération dans le port logique créé dans l’orchestration BizTalk de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] peut être différent.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-178">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="ed1c8-179">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-179">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-180">Vérifiez que les noms des opérations dans les deux le port logique (dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) et le port physique (dans la console Administration de BizTalk Server) sont les mêmes.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-180">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration console) are the same.</span></span>  
  
###  <span data-ttu-id="ed1c8-181"><a name="BKMK_SiebelTerminate"></a>Application à l’aide de l’adaptateur Siebel n’arrête pas</span><span class="sxs-lookup"><span data-stu-id="ed1c8-181"><a name="BKMK_SiebelTerminate"></a> Application using the Siebel adapter does not terminate</span></span>  
 <span data-ttu-id="ed1c8-182">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-182">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-183">Une application qui utilise le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Siebel 7.5 version du client n’arrête pas.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-183">An application that uses the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Siebel client version 7.5 does not terminate.</span></span>  
  
 <span data-ttu-id="ed1c8-184">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-184">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-185">Cela est dû à un problème de client Siebel où le processus ne se termine pas lorsque la déconnexion d’un serveur Siebel.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-185">This is because of a Siebel client issue where the process does not terminate when logging off from a Siebel server.</span></span>  
  
 <span data-ttu-id="ed1c8-186">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-186">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-187">Assurez-vous que vous disposez du correctif 7.5.3.17 installé pour le serveur Siebel, ainsi que la correction rapide QF0H05.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-187">Make sure you have the patch 7.5.3.17 installed for the Siebel server, along with the quick fix QF0H05.</span></span>  
  
###  <span data-ttu-id="ed1c8-188"><a name="BKMK_SiebelHang"></a>L’adaptateur Siebel peut se bloquer si le redémarrage du serveur Siebel</span><span class="sxs-lookup"><span data-stu-id="ed1c8-188"><a name="BKMK_SiebelHang"></a> Siebel adapter may hang if the Siebel server is restarted</span></span>  
 <span data-ttu-id="ed1c8-189">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-189">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-190">Si le serveur Siebel est redémarré pendant la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] envoie un message à l’utilisation de serveur Siebel, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut se bloquer.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-190">If the Siebel server is restarted while the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is sending a message to the Siebel server using, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] may hang.</span></span>  
  
 <span data-ttu-id="ed1c8-191">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-191">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-192">Redémarrez l’instance d’hôte BizTalk application.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-192">Restart the BizTalk application host instance.</span></span> <span data-ttu-id="ed1c8-193">Pour le faire à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, dans l’arborescence de la console, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-193">To do so from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, in the console tree expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="ed1c8-194">Dans le volet droit, cliquez sur le nom d’hôte, puis sélectionnez **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-194">From the right pane, right-click the host name, and then select **Restart**.</span></span>  
  
###  <span data-ttu-id="ed1c8-195"><a name="BKMK_SiebelAction"></a>L’adaptateur ne reconnaît pas l’action sur le port physique, même si le fichier de liaison généré par le complément Consume Adapter Service vous permet de créer les ports</span><span class="sxs-lookup"><span data-stu-id="ed1c8-195"><a name="BKMK_SiebelAction"></a> The adapter does not recognize the action on the physical port even though you use the binding file generated by the Consume Adapter Service add-in to create the ports</span></span>  
 <span data-ttu-id="ed1c8-196">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-196">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-197">Après avoir utilisé le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour une opération spécifique sur le système Siebel, le complément crée également un fichier de liaison de port.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-197">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the Siebel system, the add-in also creates a port binding file.</span></span> <span data-ttu-id="ed1c8-198">Vous pouvez importer ce fichier à l’aide de la liaison la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports physiques dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-198">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="ed1c8-199">Toutefois, lorsque vous envoyez des messages au système Siebel à l’aide de ces ports, l’adaptateur ne parvient pas à comprendre l’action spécifiée sur le port et génère une erreur semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-199">However, when you send messages to the Siebel system using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="ed1c8-200">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-200">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-201">Lorsque vous créez des ports logiques dans une orchestration BizTalk, vous spécifiez certains noms pour les opérations sur ces ports ou vous utilisez simplement les noms par défaut comme Operation_1, Operation_2, etc.. Toutefois, dans le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le nom de l’opération est identique au nom de l’opération pour laquelle générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-201">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the operation for which you generate metadata.</span></span> <span data-ttu-id="ed1c8-202">Par exemple, si vous générez des métadonnées pour l’opération d’insertion sur le composant de gestion de compte, l’action est fixée à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-202">For example, if you generate metadata for Insert operation on the Account business component, the action will be set to the following:</span></span>  
  
```  
<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
```  
  
 <span data-ttu-id="ed1c8-203">Lorsque vous importez le fichier de liaison, la même action est définie sur le port physique.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-203">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="ed1c8-204">Par conséquent, les noms de l’opération sur le port logique (Operation_1, Operation_2, etc.) ne correspondent pas les noms de l’opération spécifiées dans l’action sur le port physique, ce qui entraîne une erreur.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-204">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="ed1c8-205">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-205">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-206">Assurez-vous que le nom de l’opération dans le port logique est la même que le nom d’opération spécifié dans le cadre de l’action dans le port physique.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-206">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="ed1c8-207">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-207">Do one of the following:</span></span>  
  
-   <span data-ttu-id="ed1c8-208">Modifier le nom de l’opération dans le port logique dans le Concepteur d’orchestration BizTalk à partir de Operation_1, etc. à l’opération pour laquelle générer des métadonnées, par exemple, Insert.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-208">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example Insert.</span></span>  
  
-   <span data-ttu-id="ed1c8-209">Modifier le nom de l’opération dans l’action sur le port physique pour le nom de l’opération dans le port logique.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-209">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="ed1c8-210">Par exemple, vous pouvez modifier l’action dans le port physique pour ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-210">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
    ```  
  
###  <span data-ttu-id="ed1c8-211"><a name="BKMK_SiebelXMLEncode"></a>L’adaptateur Siebel ne gère pas les objets Siebel avec des chaînes XML encodé dans le nom</span><span class="sxs-lookup"><span data-stu-id="ed1c8-211"><a name="BKMK_SiebelXMLEncode"></a> Siebel adapter does not handle Siebel objects with XML encoded strings in the name</span></span>  
 <span data-ttu-id="ed1c8-212">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-212">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-213">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne peut pas effectuer des opérations impliquant des objets Siebel (des objets métier, des composants d’entreprise, services d’entreprise, liste de choix, méthodes, champs, arguments, etc.) qui ont des chaînes XML encodé dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-213">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] cannot perform operations involving Siebel objects (business objects, business components, business services, picklist, methods, fields, arguments, etc) that have XML encoded strings in their name.</span></span> <span data-ttu-id="ed1c8-214">Par exemple, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne sera pas en mesure d’appeler une méthode de service d’entreprise avec le nom Time_x0020_Stamp.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-214">For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will not be able to invoke a business service method with the name Time_x0020_Stamp.</span></span>  
  
 <span data-ttu-id="ed1c8-215">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-215">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-216">Assurez-vous que les objets Siebel ne contiennent pas de chaînes XML encodé dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-216">Make sure the Siebel objects do not contain XML encoded strings in their name.</span></span>  
  
###  <span data-ttu-id="ed1c8-217"><a name="BKMK_SiebelRootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="ed1c8-217"><a name="BKMK_SiebelRootNode"></a> Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="ed1c8-218">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-218">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-219">Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-219">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="ed1c8-220">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-220">**Resolution**</span></span>  
  
1.  <span data-ttu-id="ed1c8-221">Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-221">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ed1c8-222">Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).</span><span class="sxs-lookup"><span data-stu-id="ed1c8-222">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <span data-ttu-id="ed1c8-223"><a name="BKMK_SiebelVS2008"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed1c8-223"><a name="BKMK_SiebelVS2008"></a> Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="ed1c8-224">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-224">**Problem**</span></span>  
  
 <span data-ttu-id="ed1c8-225">Lorsque vous utilisez l’adaptateur pour créer une application dans [!INCLUDE[vs2010](../../includes/vs2010-md.md)] et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="ed1c8-225">When you use the adapter to create an application in [!INCLUDE[vs2010](../../includes/vs2010-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'siebelBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="ed1c8-226">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-226">**Cause**</span></span>  
  
 <span data-ttu-id="ed1c8-227">Cet avertissement s’affiche, car le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] de liaison, `siebelBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed1c8-227">This warning appears because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding, `siebelBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="ed1c8-228">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed1c8-228">**Resolution**</span></span>  
  
 <span data-ttu-id="ed1c8-229">Vous pouvez ignorer cet avertissement sans problème.</span><span class="sxs-lookup"><span data-stu-id="ed1c8-229">You can safely ignore this warning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1c8-230">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed1c8-230">See Also</span></span>  
[<span data-ttu-id="ed1c8-231">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="ed1c8-231">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)