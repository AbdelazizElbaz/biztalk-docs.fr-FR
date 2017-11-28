---
title: "Résoudre les problèmes opérationnels avec l’adaptateur SAP dans BizTalk | Documents Microsoft"
description: "Erreurs courantes, des problèmes et résolutions avec mySAP adaptateur dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb0f005b-7548-478b-8243-69e07c29d02c
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5298782f23cb8c7c32a2bcbd512f3a1b78f8a69d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-sap-adapter"></a><span data-ttu-id="969cf-103">Résoudre les problèmes opérationnels avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-103">Troubleshoot Operational Issues with the SAP adapter</span></span>
<span data-ttu-id="969cf-104">Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-104">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
### <a name="enable-tracing"></a><span data-ttu-id="969cf-105">Activer le suivi</span><span class="sxs-lookup"><span data-stu-id="969cf-105">Enable tracing</span></span>  
 <span data-ttu-id="969cf-106">Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="969cf-106">For information about tracing support in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Diagnostic Tracing and Message Logging for the SAP adapter](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md).</span></span>  
  
##  <span data-ttu-id="969cf-107"><a name="client_dll"></a>Erreur lors du chargement de la liaison</span><span class="sxs-lookup"><span data-stu-id="969cf-107"><a name="client_dll"></a> Error loading the binding</span></span>  
 <span data-ttu-id="969cf-108">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-108">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-109">Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’interface graphique utilisateur attribue l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="969cf-109">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the GUI gives the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="969cf-110">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-110">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-111">Lorsque vous démarrez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] charge les liaisons de l’adaptateur pour tous les adaptateurs installés.</span><span class="sxs-lookup"><span data-stu-id="969cf-111">When you start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="969cf-112">À son tour, les liaisons de l’adaptateur sont dépendantes du logiciel client spécifique pour l’application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="969cf-112">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="969cf-113">Vous risquez de rencontrer ce problème pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="969cf-113">You might face this issue for one or both of the following reasons:</span></span>  
  
-   <span data-ttu-id="969cf-114">Le logiciel client LOB requis n’est pas installé sur l’ordinateur où vous avez installé l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="969cf-114">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
-   <span data-ttu-id="969cf-115">Vous avez effectué une installation standard ou complète de la carte, qui installe tous les adaptateurs contenus dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-115">You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="969cf-116">Toutefois, les bibliothèques clientes LOB peuvent être installés pour seulement une application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="969cf-116">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="969cf-117">Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="969cf-117">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="969cf-118">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-118">**Resolution**</span></span>  
  
-   <span data-ttu-id="969cf-119">Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="969cf-119">Make sure you do a Custom installation of the adapters to install only the adapter you need.</span></span>  
  
-   <span data-ttu-id="969cf-120">Assurez-vous que les versions de client LOB requises sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-120">Make sure the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="969cf-121">[Prise en charge des systèmes métier](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions prises en charge.</span><span class="sxs-lookup"><span data-stu-id="969cf-121">[Supported LOB systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported versions.</span></span> <span data-ttu-id="969cf-122">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] requiert également certaines DLL interagir avec le système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-122">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] also requires certain DLLs to interface with the SAP system.</span></span> <span data-ttu-id="969cf-123">Pour plus d’informations sur les DLL requises par l’adaptateur, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="969cf-123">For more information about the DLLs required by the adapter, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>
  
##  <span data-ttu-id="969cf-124"><a name="BKMK_SAPDisplay"></a>L’adaptateur SAP est manquant dans la console Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="969cf-124"><a name="BKMK_SAPDisplay"></a> The SAP adapter is missing in BizTalk Administration console</span></span>  
 <span data-ttu-id="969cf-125">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-125">**Problem**</span></span>  
  
<span data-ttu-id="969cf-126">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] inclus avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des adaptateurs dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="969cf-126">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] included with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="969cf-127">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-127">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-128">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée.</span><span class="sxs-lookup"><span data-stu-id="969cf-128">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="969cf-129">Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-129">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="969cf-130">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-130">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-131">Vous pouvez ajouter explicitement le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="969cf-131">You can explicitly add the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
##  <span data-ttu-id="969cf-132"><a name="BKMK_SAPConnOpen"></a>DLL sont manquantes erreur d’ouverture d’une connexion à SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-132"><a name="BKMK_SAPConnOpen"></a> DLLs are missing error opening a connection to SAP</span></span>  
 <span data-ttu-id="969cf-133">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-133">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-134">Lorsque vous essayez d’ouvrir une connexion au système SAP en utilisant le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], une boîte de dialogue s’affiche dans le système SAP, informant que certaines DLL est manquantes.</span><span class="sxs-lookup"><span data-stu-id="969cf-134">When you try to open a connection to the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], a dialog box appears in the SAP system, informing that some DLLs are missing.</span></span>  
  
 <span data-ttu-id="969cf-135">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-135">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-136">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise librfc32u.dll pour établir une connexion avec le système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-136">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses librfc32u.dll to establish a connection with the SAP system.</span></span> <span data-ttu-id="969cf-137">Le librfc32u.dll, exige à son tour, un ensemble de DLL pour fonctionner.</span><span class="sxs-lookup"><span data-stu-id="969cf-137">The librfc32u.dll, in turn, requires a set of DLLs to function.</span></span> <span data-ttu-id="969cf-138">Vous obtenez cette erreur si ces DLL de prise en charge ne sont pas ajoutés à la variable de chemin d’accès sur l’ordinateur où le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="969cf-138">You get this error if these supporting DLLs are not added to the PATH variable on the computer where the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is installed.</span></span>  
  
 <span data-ttu-id="969cf-139">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-139">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-140">Reportez-vous à la table spécifiée comme une solution à la [erreur lors du chargement des liaisons de l’adaptateur](#client_dll) problème.</span><span class="sxs-lookup"><span data-stu-id="969cf-140">Refer to the table provided as a resolution to the [Error in loading the adapter bindings](#client_dll) issue.</span></span> <span data-ttu-id="969cf-141">Le tableau répertorie les DLL de prise en charge nécessaires pour interagir avec le système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-141">The table lists the supporting DLLs required to interface with the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
##  <span data-ttu-id="969cf-142"><a name="BKMK_SAPXmlRetrieve"></a>Erreur durant la récupération de XML avec les nœuds de plus de 65 536</span><span class="sxs-lookup"><span data-stu-id="969cf-142"><a name="BKMK_SAPXmlRetrieve"></a> Error retrieving XML with more than 65,536 nodes</span></span>  
 <span data-ttu-id="969cf-143">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-143">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-144">L’adaptateur attribue l’erreur suivante lors de la récupération de sortie XML qui a plus de 65 536 nœuds.</span><span class="sxs-lookup"><span data-stu-id="969cf-144">The adapter gives the following error while retrieving XML output that has more than 65,536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="969cf-145">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-145">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-146">L’adaptateur ne peut pas sérialiser et désérialiser un objet avec des éléments de plus de 65 536.</span><span class="sxs-lookup"><span data-stu-id="969cf-146">The adapter cannot serialize and deserialize an object with more than 65,536 items.</span></span>  
  
 <span data-ttu-id="969cf-147">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-147">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-148">Vous pouvez résoudre ce problème en définissant le `maxItemsInObjectGraph` paramètre dans une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="969cf-148">You can fix this issue by setting the `maxItemsInObjectGraph` parameter in either of the following two ways:</span></span>  
  
-   <span data-ttu-id="969cf-149">Définissez ce paramètre en modifiant le `maxItemsInObjectGraph` paramètre dans le `ServiceBehavior` attribut sur votre classe de service.</span><span class="sxs-lookup"><span data-stu-id="969cf-149">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
-   <span data-ttu-id="969cf-150">Ajoutez le code suivant au fichier app.config de votre application.</span><span class="sxs-lookup"><span data-stu-id="969cf-150">Add the following to your application's app.config file.</span></span>  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 <span data-ttu-id="969cf-151">Un app.config exemple ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="969cf-151">A sample app.config will look like the following.</span></span>  
  
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
      <endpoint   behaviorConfiguration="NewBehavior" binding="sapBinding"  
       contract="IOutboundContract" name="sap_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
##  <span data-ttu-id="969cf-152"><a name="BKMK_SAPConnURI"></a>Erreur de saisie d’un URI de connexion pour un port personnalisé WCF dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="969cf-152"><a name="BKMK_SAPConnURI"></a> Error entering a connection URI for a WCF-Custom port in BizTalk Server</span></span>  
 <span data-ttu-id="969cf-153">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-153">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="969cf-154">attribue l’erreur suivante lorsque vous spécifiez un URI de connexion pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-154"> gives the following error when you specify a connection URI to connect to the SAP system.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="969cf-155">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-155">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-156">L’URI de connexion n’est pas conforme au format de codage standard.</span><span class="sxs-lookup"><span data-stu-id="969cf-156">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="969cf-157">Par exemple, la valeur d’un paramètre peut contenir un espace.</span><span class="sxs-lookup"><span data-stu-id="969cf-157">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="969cf-158">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-158">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-159">Vérifiez que la connexion URI que vous spécifiez respecte le format d’encodage standard.</span><span class="sxs-lookup"><span data-stu-id="969cf-159">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="969cf-160">Par exemple, un espace vide doit être remplacé par « %20 ».</span><span class="sxs-lookup"><span data-stu-id="969cf-160">For example, a blank space must be replaced by "%20".</span></span>  
  
##  <span data-ttu-id="969cf-161"><a name="BKMK_SAPOperate"></a>Erreur System.ArgumentNullException lors de l’exécution d’une opération sur SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-161"><a name="BKMK_SAPOperate"></a> System.ArgumentNullException error while completing an operation on SAP</span></span>  
 <span data-ttu-id="969cf-162">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-162">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-163">L’adaptateur renvoie l’erreur suivante lors de l’exécution de toute opération sur le système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-163">The adapter gives the following error when performing any operation on the SAP system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
```  
System.ArgumentNullException: Value cannot be null.  
```  
  
 <span data-ttu-id="969cf-164">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-164">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-165">L’action WCF pour le message n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="969cf-165">The WCF action for the message is not specified.</span></span> <span data-ttu-id="969cf-166">WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.</span><span class="sxs-lookup"><span data-stu-id="969cf-166">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="969cf-167">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-167">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-168">Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="969cf-168">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="969cf-169">Pour obtenir des instructions, consultez [configurer l’action SOAP pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="969cf-169">For instructions, see [Configure the SOAP action for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md).</span></span> <span data-ttu-id="969cf-170">Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) pour afficher la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="969cf-170">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) to see a list of actions for each operation.</span></span>  
  
##  <span data-ttu-id="969cf-171"><a name="BKMK_SAPXmlParsing"></a>XmlReaderParsingException en raison d’un fonctionnement incorrect dans l’action spécifiée</span><span class="sxs-lookup"><span data-stu-id="969cf-171"><a name="BKMK_SAPXmlParsing"></a> XmlReaderParsingException due to incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="969cf-172">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-172">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-173">La Console Administration de BizTalk Server attribue l’erreur suivante lors de l’envoi de messages à un système SAP :</span><span class="sxs-lookup"><span data-stu-id="969cf-173">The BizTalk Server Administration Console gives the following error when sending messages to an SAP system:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="969cf-174">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-174">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-175">Si vous configurez un port personnalisé WCF en important le fichier de liaison de port créé par le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’action dans le port est spécifiée dans le format suivant :</span><span class="sxs-lookup"><span data-stu-id="969cf-175">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="969cf-176">Dans le format ci-dessus, le nom de l’opération est régi par l’opération que vous avez choisi lors de la génération du schéma.</span><span class="sxs-lookup"><span data-stu-id="969cf-176">In the above format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="969cf-177">Par exemple, si vous avez généré le schéma pour RFC_CUSTOMER_GET, le nom de l’opération dans l’action sera « RFC_CUSTOMER_GET ».</span><span class="sxs-lookup"><span data-stu-id="969cf-177">For example, if you generated schema for RFC_CUSTOMER_GET, the operation name in the action will be "RFC_CUSTOMER_GET".</span></span> <span data-ttu-id="969cf-178">Toutefois, le nom de l’opération dans le port logique créé dans l’orchestration BizTalk de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] peut être différent.</span><span class="sxs-lookup"><span data-stu-id="969cf-178">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="969cf-179">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-179">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-180">Vérifiez que les noms des opérations dans les deux le port logique (dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) et le port physique (dans la Console Administration de BizTalk Server) sont les mêmes.</span><span class="sxs-lookup"><span data-stu-id="969cf-180">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration Console) are same.</span></span>  
  
##  <span data-ttu-id="969cf-181"><a name="BKMK_SAPHundredCons"></a>Erreur d’ouverture de plus de 100 connexions à SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-181"><a name="BKMK_SAPHundredCons"></a> Error opening more than 100 connections to SAP</span></span>  
 <span data-ttu-id="969cf-182">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-182">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-183">L’adaptateur lève l’exception suivante lors de l’ouverture de plus de 100 connexions au système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-183">The adapter throws the following exception when opening more than 100 connections to the SAP system.</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.ConnectionException: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  GWHOST=<gw_host>, GWSERV=<gw_serv>, SYSNR=<sys_number>  
LOCATION    CPIC (TCP/IP) on local host with Unicode  
ERROR       max no of 100 conversations exceeded  
```  
  
 <span data-ttu-id="969cf-184">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-184">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-185">Par défaut, SAP n’active pas plus de 100 connexions dans le système.</span><span class="sxs-lookup"><span data-stu-id="969cf-185">By default, SAP does not enable more than 100 connections into the system.</span></span>  
  
 <span data-ttu-id="969cf-186">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-186">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-187">Pour augmenter le nombre maximal de connexions, vous devez créer une variable d’environnement sur l’ordinateur qui a des bibliothèques clientes SAP installé et lui affecte une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="969cf-187">To increase the maximum number of connections, you must create an environment variable on the computer that has the SAP client libraries installed and set it to a numeric value.</span></span> <span data-ttu-id="969cf-188">La valeur que vous spécifiez pour cette variable d’environnement est le nombre maximal de connexions qui peuvent être effectuées dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-188">The value you specify for this environment variable is the maximum number of connections that can be made into the SAP system.</span></span> <span data-ttu-id="969cf-189">Créer la variable d’environnement avec les détails suivants :</span><span class="sxs-lookup"><span data-stu-id="969cf-189">Create the environment variable with the following details:</span></span>  
  
-   <span data-ttu-id="969cf-190">**Nom de la variable**: CPIC_MAX_CONV</span><span class="sxs-lookup"><span data-stu-id="969cf-190">**Variable name**: CPIC_MAX_CONV</span></span>  
  
-   <span data-ttu-id="969cf-191">**Valeur de la variable**: une valeur numérique positive.</span><span class="sxs-lookup"><span data-stu-id="969cf-191">**Variable value**: any positive numeric value.</span></span> <span data-ttu-id="969cf-192">Par exemple, pour activer les 200 connexions dans le système SAP, spécifiez la valeur 200.</span><span class="sxs-lookup"><span data-stu-id="969cf-192">For example, to enable 200 connections into the SAP system, specify the value as 200.</span></span>  
  
 <span data-ttu-id="969cf-193">Pour obtenir des instructions sur la création d’une variable d’environnement, consultez « Comment faire pour créer les Variables système dans Windows 2000 » à [http://go.microsoft.com/fwlink/?LinkId=95020](http://go.microsoft.com/fwlink/?LinkId=95020).</span><span class="sxs-lookup"><span data-stu-id="969cf-193">For instructions on creating an environment variable, see "How To Create System Variables in Windows 2000" at [http://go.microsoft.com/fwlink/?LinkId=95020](http://go.microsoft.com/fwlink/?LinkId=95020).</span></span>  
  
##  <span data-ttu-id="969cf-194"><a name="BKMK_SAPIDOCMetadata"></a>Erreur de la génération ou de la récupération des métadonnées des IDOC</span><span class="sxs-lookup"><span data-stu-id="969cf-194"><a name="BKMK_SAPIDOCMetadata"></a> Error generating or retrieving metadata for IDOCs</span></span>  
 <span data-ttu-id="969cf-195">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-195">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-196">Lors de la génération de métadonnées pour le **réception** opération pour un IDOC dans un système SAP, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] attribue l’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="969cf-196">While generating metadata for the **Receive** operation for an IDOC in an SAP system, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives the following error.</span></span>  
  
```  
Error while retrieving or generating the WSDL.  
Adapter message: Details: ErrorCode=RFC_EXCEPTION.  
ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage= OBJECT_UNKNOWN.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: IDOCTYPE_READ_COMPLETE.  
```  
  
 <span data-ttu-id="969cf-197">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-197">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-198">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise la RFC IDOCTYPE_READ_COMPLETE pour récupérer les métadonnées pour le **réception** opération pour un IDOC.</span><span class="sxs-lookup"><span data-stu-id="969cf-198">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the IDOCTYPE_READ_COMPLETE RFC to retrieve the metadata for the **Receive** operation for an IDOC.</span></span> <span data-ttu-id="969cf-199">Appel de ce document RFC requiert des autorisations d’utilisateur spécifique dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-199">Invoking this RFC requires specific user permissions in the SAP system.</span></span> <span data-ttu-id="969cf-200">Pour générer des métadonnées, si vous êtes connecté au système SAP à l’aide des informations d’identification qui ne sont pas autorisé à appeler la RFC IDOCTYPE_READ_COMPLETE, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="969cf-200">To generate metadata, if you have connected to the SAP system using a credential that does not have permission to invoke the IDOCTYPE_READ_COMPLETE RFC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an error.</span></span>  
  
 <span data-ttu-id="969cf-201">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-201">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-202">Connectez-vous à l’interface utilisateur graphique SAP à l’aide de ces mêmes informations que vous aviez utilisé pour la carte.</span><span class="sxs-lookup"><span data-stu-id="969cf-202">Log in to the SAP GUI using the same credentials you had used for the adapter.</span></span> <span data-ttu-id="969cf-203">Accédez à la transaction SE37 et entrez le nom de la RFC à exécuter en tant que IDOCTYPE_READ_COMPLETE.</span><span class="sxs-lookup"><span data-stu-id="969cf-203">Navigate to transaction SE37, and enter the name of the RFC to execute as IDOCTYPE_READ_COMPLETE.</span></span>  
  
 <span data-ttu-id="969cf-204">Pour les paramètres d’entrée PI_IDOCTYP et PI_CIMTYP, entrez les valeurs correspondant à l’IDoc personnalisé.</span><span class="sxs-lookup"><span data-stu-id="969cf-204">For the input parameters PI_IDOCTYP and PI_CIMTYP, enter the values corresponding to the custom IDoc.</span></span> <span data-ttu-id="969cf-205">Pour les paramètres PI_VERSION et PI_RELEASE, entrez les mêmes valeurs comme étant choisi dans l’interface de métadonnées d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="969cf-205">For the parameters PI_VERSION and PI_RELEASE, enter the same values as being chosen in the Adapter Metadata UI.</span></span> <span data-ttu-id="969cf-206">Puis, appuyez sur F8 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="969cf-206">And, press F8 to execute.</span></span>  
  
 <span data-ttu-id="969cf-207">Vous devez obtenir la même exception que ce que l’adaptateur reçoit, avec plus d’informations sur le problème.</span><span class="sxs-lookup"><span data-stu-id="969cf-207">You should get the same exception as what the adapter receives, with more information about the issue.</span></span>  
  
 <span data-ttu-id="969cf-208">Si vous êtes toujours pas en mesure de résoudre le problème, générer un schéma pour le **ReceiveIdoc** opération au lieu du **réception** opération.</span><span class="sxs-lookup"><span data-stu-id="969cf-208">If you are still not able to resolve the issue, generate a schema for the **ReceiveIdoc** operation instead of the **Receive** operation.</span></span> <span data-ttu-id="969cf-209">Dans ce cas, l’adaptateur SAP n’utilise pas IDOCTYPE_READ_COMPLETE et ne lève pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="969cf-209">In this case, the SAP adapter does not use IDOCTYPE_READ_COMPLETE, and does not throw any error.</span></span>  
  
##  <span data-ttu-id="969cf-210"><a name="BKMK_SAPIDOCReceive"></a>Erreur envoyer ou recevoir des IDOC qui ont non commerciales des segments</span><span class="sxs-lookup"><span data-stu-id="969cf-210"><a name="BKMK_SAPIDOCReceive"></a> Error sending or receiving IDOCs that have unreleased segments</span></span>  
 <span data-ttu-id="969cf-211">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-211">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-212">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] donne une XmlReaderParsingException lors de l’envoi des IDOC (à l’aide de **envoyer** opération) ou de recevoir des IDOC (à l’aide de **réception** opération) qui ont non commerciales des segments.</span><span class="sxs-lookup"><span data-stu-id="969cf-212">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an XmlReaderParsingException while sending IDOCs (using **Send** operation) or receiving IDOCs (using **Receive** operation) that have unreleased segments.</span></span>  
  
 <span data-ttu-id="969cf-213">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-213">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-214">IDOC sont constitués de segments.</span><span class="sxs-lookup"><span data-stu-id="969cf-214">IDOCs are constituted of segments.</span></span> <span data-ttu-id="969cf-215">Lors de la génération de métadonnées, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère tous les segments publiées qui sont présents dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-215">While generating metadata, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves all the released segments that are present in the SAP system.</span></span> <span data-ttu-id="969cf-216">Toutefois, lorsque l’adaptateur utilise les métadonnées pour effectuer une opération telle que la réception d’un IDOC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] donne une XmlReaderParsingException.</span><span class="sxs-lookup"><span data-stu-id="969cf-216">However, when the adapter client uses the metadata to perform an operation such as receiving an IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an XmlReaderParsingException.</span></span> <span data-ttu-id="969cf-217">Cela se produit, car lorsque l’IDOC est reçu, le système SAP peut envoyé certains segments non commercialisés, les métadonnées pour ce qui n’a pas été générée par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="969cf-217">This occurs because when the IDOC is received, the SAP system might have sent some unreleased segments as well, the metadata for which was not generated by the adapter.</span></span>  
  
 <span data-ttu-id="969cf-218">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-218">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-219">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="969cf-219">Do any of the following:</span></span>  
  
-   <span data-ttu-id="969cf-220">Mettre à niveau votre système SAP en appliquant les correctifs appropriés pour les segments non commercialisés.</span><span class="sxs-lookup"><span data-stu-id="969cf-220">Upgrade your SAP system by applying appropriate patches for the unreleased segments.</span></span>  
  
-   <span data-ttu-id="969cf-221">Utilisez **SendIdoc** ou **ReceiveIdoc** operations pour envoyer et recevoir des IDOC respectivement.</span><span class="sxs-lookup"><span data-stu-id="969cf-221">Use **SendIdoc** or **ReceiveIdoc** operations to send and receive IDOCs respectively.</span></span> <span data-ttu-id="969cf-222">Pour plus d’informations sur ces opérations, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="969cf-222">For more information about these operations, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span></span>  
  
##  <span data-ttu-id="969cf-223"><a name="BKMK_SAPIDOCSend"></a>Erreur d’envoi de fichier plat IDOC à SAP qui ont été reçus à l’aide de la FilePort SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-223"><a name="BKMK_SAPIDOCSend"></a> Error sending flat-file IDOCs to SAP that were received using the SAP FilePort</span></span>  
 <span data-ttu-id="969cf-224">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-224">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-225">Si vous essayez d’envoyer (à l’aide de **envoyer** opération) un IDOC de fichier plat à un système SAP qui a été généré à l’aide d’un FilePort SAP, l’Analyseur de fichier plat dans l’orchestration BizTalk ne peut pas convertir le fichier flatf dans un format XML, ce qui échouent le IDOD **envoyer** opération.</span><span class="sxs-lookup"><span data-stu-id="969cf-225">If you try to send (using **Send** operation) a flat-file IDOC to an SAP system that was generated using an SAP FilePort, the flat-file parser in the BizTalk orchestration fails to convert the flatf-file to an XML format, thereby failing the IDOD **Send** operation.</span></span>  
  
 <span data-ttu-id="969cf-226">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-226">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-227">Lorsque le système SAP génère un IDOC à l’aide d’un FilePort, il supprime les désactiver tous les espaces à la fin d’un segment vides.</span><span class="sxs-lookup"><span data-stu-id="969cf-227">When the SAP system generates an IDOC using a FilePort, it trims off all the empty spaces at the end of a segment.</span></span> <span data-ttu-id="969cf-228">Toutefois, l’Analyseur de fichier plat attend que les données du dernier champ du segment doivent être présents pour convertir le format de fichier plat au format XML.</span><span class="sxs-lookup"><span data-stu-id="969cf-228">However, the flat-file parser expects the data of the last field in the segment to be present to successfully convert the flat-file to XML.</span></span> <span data-ttu-id="969cf-229">Étant donné que les espaces vides ne sont pas présents dans le segment, l’Analyseur de fichier plat ne parvient pas à analyser le fichier plat au format XML.</span><span class="sxs-lookup"><span data-stu-id="969cf-229">Because the empty spaces are not present in the segment, the flat-file parser fails to parse the flat-file to XML.</span></span>  
  
 <span data-ttu-id="969cf-230">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-230">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-231">Pour ce type IDOC de fichier plat générés à l’aide de le FilePort de SAP, utilisez le **SendIdoc** opération à la place.</span><span class="sxs-lookup"><span data-stu-id="969cf-231">For such flat-file IDOCs generated using the SAP FilePort, use the **SendIdoc** operation instead.</span></span> <span data-ttu-id="969cf-232">Pour plus d’informations sur cette opération, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="969cf-232">For more information about this operation, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span></span>  
  
##  <span data-ttu-id="969cf-233"><a name="BKMK_SAPRecIDOCCompat"></a>Erreur de réception IDOC de SAP si EnableBizTalkCompatibilityMode est définie sur true</span><span class="sxs-lookup"><span data-stu-id="969cf-233"><a name="BKMK_SAPRecIDOCCompat"></a> Error receiving IDOCs from SAP if EnableBizTalkCompatibilityMode property is set to true</span></span>  
 <span data-ttu-id="969cf-234">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-234">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-235">L’exception suivante est rencontrée lors de la réception d’un IDOC avec la **EnableBizTalkCompatibilityMode** jeu de propriétés de liaison à la valeur true :</span><span class="sxs-lookup"><span data-stu-id="969cf-235">The following exception is encountered while receiving an IDOC with the **EnableBizTalkCompatibilityMode** binding property set to true:</span></span>  
  
```  
System.Exception: Loading property information list by namespace failed or property not found in the list. Verify that the schema is deployed properly.  
```  
  
 <span data-ttu-id="969cf-236">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-236">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-237">Si la propriété de liaison **EnableBizTalkCompatibilityMode** a la valeur **true**, vous devez ajouter le fichier DLL du schéma de propriété BizTalk pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en tant que ressource dans votre application BizTalk, autrement dit, le application dans laquelle votre projet est déployé.</span><span class="sxs-lookup"><span data-stu-id="969cf-237">If the binding property **EnableBizTalkCompatibilityMode** is set to **true**, you must add the BizTalk property schema DLL for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a resource in your BizTalk application, that is, the application in which your project is deployed.</span></span>  
  
 <span data-ttu-id="969cf-238">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-238">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-239">Le nom du schéma de propriété BizTalk pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*.</span><span class="sxs-lookup"><span data-stu-id="969cf-239">The name for the BizTalk property schema for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*.</span></span> <span data-ttu-id="969cf-240">Il est installé par le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation sous \<lecteur d’installation > : \ Programme Files\Microsoft BizTalk adaptateur Pack\bin.</span><span class="sxs-lookup"><span data-stu-id="969cf-240">This is installed by the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup under \<installation drive>:\ Program Files\Microsoft BizTalk Adapter Pack\bin.</span></span> <span data-ttu-id="969cf-241">Procédez comme suit pour ajouter cet assembly en tant que ressource dans votre application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="969cf-241">Perform the following tasks to add this assembly as a resource in your BizTalk application.</span></span>  
  
#### <a name="add-an-assembly-as-a-resource-in-biztalk-application"></a><span data-ttu-id="969cf-242">Ajouter un assembly en tant que ressource dans l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="969cf-242">Add an assembly as a resource in BizTalk application</span></span>  
  
1.  <span data-ttu-id="969cf-243">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="969cf-243">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="969cf-244">Dans l’arborescence de la console, développez **groupe BizTalk**, développez **Applications**et puis l’application à laquelle vous souhaitez ajouter un assembly BizTalk.</span><span class="sxs-lookup"><span data-stu-id="969cf-244">In the console tree, expand **BizTalk Group**, expand **Applications**, and then the application to which you want to add a BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="969cf-245">Développez **Applications** et l’application à laquelle vous souhaitez ajouter un assembly BizTalk.</span><span class="sxs-lookup"><span data-stu-id="969cf-245">Expand **Applications** and the application to which you want to add a BizTalk assembly.</span></span>  
  
4.  <span data-ttu-id="969cf-246">Avec le bouton droit **ressources**, pointez sur **ajouter**, puis cliquez sur **assemblys BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="969cf-246">Right-click **Resources**, point to **Add**, and then click **BizTalk Assemblies**.</span></span>  
  
5.  <span data-ttu-id="969cf-247">Cliquez sur **ajouter**, accédez au dossier contenant le fichier d’assembly BizTalk, sélectionnez le fichier d’assembly BizTalk, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="969cf-247">Click **Add**, navigate to the folder containing the BizTalk assembly file, select the BizTalk assembly file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="969cf-248">Dans **Options**, spécifiez les options d’installation de l’assembly BizTalk dans le GAC, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="969cf-248">In **Options**, specify the options for installing the BizTalk assembly to the GAC, and then click **OK**.</span></span>  
  
##  <span data-ttu-id="969cf-249"><a name="BKMK_SAPIDOCValidate"></a>Erreur de validation lors de la réception des IDOC à partir d’un système SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-249"><a name="BKMK_SAPIDOCValidate"></a> Error in validation while receiving IDOCs from an SAP system</span></span>  
 <span data-ttu-id="969cf-250">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-250">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-251">Un IDOC reçu à partir d’un système SAP échoue à la validation avec une erreur semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="969cf-251">An IDOC received from an SAP system fails validation with an error similar to the following:</span></span>  
  
```  
There was a failure executing the receive pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=<token>"  
Source: "Pipeline " Receive Port: "ReceiveIdoc" URI: "<connection uri>"  
Reason: The document failed to validate because of the following error:  
"The 'http://Microsoft.LobServices.Sap/2007/03/Types/Idoc/3/CREMAS03//620:TAXBS' element has an invalid value according to its data type."  
```  
  
 <span data-ttu-id="969cf-252">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-252">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-253">Les métadonnées générées pour la réception d’un IDOC contient les valeurs possibles qui peuvent être reçus d’une colonne particulière dans le cadre de l’opération de réception.</span><span class="sxs-lookup"><span data-stu-id="969cf-253">The metadata generated for receiving an IDOC contains the permissible values that can be received for a particular column as part of the receive operation.</span></span> <span data-ttu-id="969cf-254">Ces valeurs sont exposées en tant qu’énumération dans les métadonnées générées.</span><span class="sxs-lookup"><span data-stu-id="969cf-254">These values are exposed as enumeration in the generated metadata.</span></span> <span data-ttu-id="969cf-255">Toutefois, lorsque l’IDOC est reçu, la valeur reçue peut être différente de valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="969cf-255">However, when the IDOC is actually received, the value received could be different from the enumerated values.</span></span> <span data-ttu-id="969cf-256">Par conséquent, l’opération de réception échoue lors de la validation des valeurs.</span><span class="sxs-lookup"><span data-stu-id="969cf-256">Hence the receive operation fails while validating the values.</span></span> <span data-ttu-id="969cf-257">Par exemple, l’erreur ci-dessus, validation de message échoue pour la colonne TAXBS.</span><span class="sxs-lookup"><span data-stu-id="969cf-257">For example, in the above error message validation fails for the TAXBS column.</span></span>  
  
 <span data-ttu-id="969cf-258">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-258">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-259">Vous devez modifier manuellement l’énumération dans le schéma (pour les projets BizTalk) ou le proxy client (pour les projets .NET à l’aide de WCF de modèle de service) pour inclure la valeur reçue à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-259">You must manually edit the enumeration in schema (for BizTalk projects) or the client proxy (for .NET projects using WCF service model) to include the value received from the SAP system.</span></span>  
  
##  <span data-ttu-id="969cf-260"><a name="BKMK_SAPFFIDOC"></a>Format de fichier plat IDOC, avant et après la conversion en XML, ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="969cf-260"><a name="BKMK_SAPFFIDOC"></a> Flat-file IDOCs, before and after converting to XML, are not identical</span></span>  
 <span data-ttu-id="969cf-261">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-261">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-262">Si vous utilisez un analyseur de fichier plat pour convertir un IDOC de fichier plat en utilisant le schéma XML, puis convertir le code XML vers un fichier plat IDOC via un pipeline à l’aide du schéma, les deux IDOC de fichier plat ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="969cf-262">If you use a flat file parser to convert a flat-file IDOC to an XML using the schema, and then convert the XML back to a flat-file IDOC through a pipeline using the schema, the two flat-file IDOCs are not identical.</span></span>  
  
 <span data-ttu-id="969cf-263">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-263">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-264">Lorsque vous générez le code XML à partir d’un fichier plat IDOC, l’Analyseur de fichier plat ne génère pas les nœuds XML avec des valeurs vides.</span><span class="sxs-lookup"><span data-stu-id="969cf-264">When generating the XML from a flat-file IDOC, the flat file parser does not generate the XML nodes with blank values.</span></span> <span data-ttu-id="969cf-265">Lorsque ce code XML est converti en un format de fichier plat, les nœuds manquants à partir du XML ne sont pas répercutées dans le format de fichier plat IDOC.</span><span class="sxs-lookup"><span data-stu-id="969cf-265">When this XML is converted back to a flat-file, the nodes missing from the XML are not reflected in the flat-file IDOC.</span></span> <span data-ttu-id="969cf-266">Par conséquent, les format de fichier plat IDOC ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="969cf-266">Hence the flat-file IDOCs are not identical.</span></span>  
  
 <span data-ttu-id="969cf-267">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-267">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-268">Dans le schéma utilisé pour convertir le format de fichier plat en XML et vice versa, dans la définition du nœud « Envoi » ou « Réception », procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="969cf-268">In the schema used to convert the flat-file to XML and vice-versa, within the "Send" or "Receive" node definition, do the following:</span></span>  
  
1.  <span data-ttu-id="969cf-269">Définir le **suppress_empty_nodes** propriété **false** et définir le **generate_empty_nodes** propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="969cf-269">Set the **suppress_empty_nodes** property to **false** and set the **generate_empty_nodes** property to **true**.</span></span> <span data-ttu-id="969cf-270">Par défaut, le **suppress_empty_nodes** est définie sur **true** et **generate_empty_nodes** est définie sur **false**, et Par conséquent, tous les nœuds vides ne sont pas répercutées dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="969cf-270">By default, the **suppress_empty_nodes** property is set to **true** and the **generate_empty_nodes** property is set to **false**, and hence all empty nodes are not reflected in the XML.</span></span>  
  
2.  <span data-ttu-id="969cf-271">Le format de fichier plat peut contenir un retour chariot supplémentaire à la fin.</span><span class="sxs-lookup"><span data-stu-id="969cf-271">The flat-file may contain an extra carriage return at the end.</span></span> <span data-ttu-id="969cf-272">Vous pouvez définir le **suppress_trailing_delimiters** propriété **Oui** afin d’éviter ce retour de chariot supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="969cf-272">You can set the **suppress_trailing_delimiters** property to **Yes** to avoid this extra carriage return.</span></span> <span data-ttu-id="969cf-273">Cette propriété est également exposée en tant que le **supprimer les délimiteurs** si vous ouvrez le schéma de propriété [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-273">This property is also exposed as the **Suppress Trailing Delimiters** property if you open the schema in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
##  <span data-ttu-id="969cf-274"><a name="BKMK_SAPAction"></a>Erreur d’Action incorrecte à l’aide d’un port physique création d’un fichier de liaison</span><span class="sxs-lookup"><span data-stu-id="969cf-274"><a name="BKMK_SAPAction"></a> Incorrect Action error using a physical port creating with a binding file</span></span>  
 <span data-ttu-id="969cf-275">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-275">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-276">Après avoir utilisé le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour une opération spécifique sur le système SAP, le complément crée également un fichier de liaison de port.</span><span class="sxs-lookup"><span data-stu-id="969cf-276">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the SAP system, the add-in also creates a port binding file.</span></span> <span data-ttu-id="969cf-277">Vous pouvez importer ce fichier à l’aide de la liaison la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports physiques dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="969cf-277">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="969cf-278">Toutefois, lorsque vous envoyez des messages au système SAP à l’aide de ces ports, l’adaptateur ne parvient pas à comprendre l’action spécifiée sur le port et génère une erreur semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="969cf-278">However, when you send messages to the SAP system using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="969cf-279">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-279">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-280">Lorsque vous créez des ports logiques dans une orchestration BizTalk, vous spécifiez certains noms pour les opérations sur ces ports ou vous utilisez simplement les noms par défaut comme Operation_1, Operation_2, etc.. Toutefois, dans le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le nom de l’opération est identique au nom de l’opération pour laquelle générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="969cf-280">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the operation for which you generate metadata.</span></span> <span data-ttu-id="969cf-281">Par exemple, si vous générez des métadonnées pour RFC_CUSTOMER_GET, l’action est fixée à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="969cf-281">For example, if you generate metadata for RFC_CUSTOMER_GET, the action will be set to the following:</span></span>  
  
```  
<Operation Name="RFC_CUSTOMER_GET" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
```  
  
 <span data-ttu-id="969cf-282">Lorsque vous importez le fichier de liaison, la même action est définie sur le port physique.</span><span class="sxs-lookup"><span data-stu-id="969cf-282">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="969cf-283">Par conséquent, les noms de l’opération sur le port logique (Operation_1, Operation_2, etc.) ne correspondent pas les noms de l’opération spécifiées dans l’action sur le port physique, ce qui entraîne une erreur.</span><span class="sxs-lookup"><span data-stu-id="969cf-283">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="969cf-284">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-284">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-285">Assurez-vous que le nom de l’opération dans le port logique est la même que le nom d’opération spécifié dans le cadre de l’action dans le port physique.</span><span class="sxs-lookup"><span data-stu-id="969cf-285">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="969cf-286">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="969cf-286">Do one of the following:</span></span>  
  
-   <span data-ttu-id="969cf-287">Modifier le nom de l’opération dans le port logique dans le Concepteur d’orchestration BizTalk à partir de Operation_1, etc. à l’opération pour laquelle générer des métadonnées, par exemple RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="969cf-287">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example RFC_CUSTOMER_GET.</span></span>  
  
-   <span data-ttu-id="969cf-288">Modifier le nom de l’opération dans l’action sur le port physique pour le nom de l’opération dans le port logique.</span><span class="sxs-lookup"><span data-stu-id="969cf-288">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="969cf-289">Par exemple, vous pouvez modifier l’action dans le port physique pour ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="969cf-289">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
    ```  
  
##  <span data-ttu-id="969cf-290"><a name="BKMK_SAPTableParams"></a>Le message de réponse pour une opération s’exécutait sur SAP ne contient pas tous les paramètres table</span><span class="sxs-lookup"><span data-stu-id="969cf-290"><a name="BKMK_SAPTableParams"></a> The response message for an operation ran on SAP does not contain any table parameters</span></span>  
 <span data-ttu-id="969cf-291">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-291">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-292">Si vous utilisez le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour exécuter une opération sur le système SAP, qui retourne un grand nombre de tables, et chaque table possède un grand nombre d’enregistrements, qui s’élève à un dataset volumineux en tant que partie du message de réponse retourné à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-292">If you use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to execute an operation on the SAP system that returns a large number of tables, and each table has a large number of records, that will amount to a large dataset being returned as part of the response message from the SAP system.</span></span> <span data-ttu-id="969cf-293">C’est le cas, par défaut, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne retourne pas les paramètres de la table en tant que partie du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="969cf-293">So, by default, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not return any table parameters as part of the response message.</span></span>  
  
 <span data-ttu-id="969cf-294">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-294">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-295">Vous pouvez demander les tables que vous souhaitez [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à retourner dans le cadre de la réponse.</span><span class="sxs-lookup"><span data-stu-id="969cf-295">You can request the tables that you want [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to return as part of the response.</span></span> <span data-ttu-id="969cf-296">Vous pouvez le faire en fournissant un paramètre table vide en tant que partie du message de demande que vous envoyez au système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-296">You can do so by providing an empty table parameter as part of the request message that you send to the SAP system.</span></span> <span data-ttu-id="969cf-297">Par exemple, `<table_parameter_name />`.</span><span class="sxs-lookup"><span data-stu-id="969cf-297">For example, `<table_parameter_name />`.</span></span>  
  
##  <span data-ttu-id="969cf-298"><a name="BKMK_SAPIncorrectCreds"></a>Les Clients de l’adaptateur ne reçoivent pas de la réponse à partir de SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-298"><a name="BKMK_SAPIncorrectCreds"></a> Adapter Clients do not receive the response from SAP</span></span>
 <span data-ttu-id="969cf-299">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-299">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-300">Lorsque vous utilisez les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], si les informations d’identification sur WCF-custom envoie de port sont incorrectes, les messages de demande ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="969cf-300">When using the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], if the credentials on the WCF-custom send port are incorrect, the request messages are not processed.</span></span> <span data-ttu-id="969cf-301">Après avoir spécifié les informations d’identification correctes, le message est envoyé au système SAP et une réponse est reçue.</span><span class="sxs-lookup"><span data-stu-id="969cf-301">After you specify the correct credentials, the message is sent to the SAP system and a response is received.</span></span> <span data-ttu-id="969cf-302">Toutefois, le message de réponse n’est pas disponible pour le port de sortie.</span><span class="sxs-lookup"><span data-stu-id="969cf-302">However, the response message is not available to the out port.</span></span>  
  
 <span data-ttu-id="969cf-303">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-303">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-304">Redémarrez l’instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="969cf-304">Restart the BizTalk host instance.</span></span>  
  
##  <span data-ttu-id="969cf-305"><a name="BKMK_SAPInboundConn"></a>Problèmes de connectivité de la réception d’un message entrant à partir du serveur SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-305"><a name="BKMK_SAPInboundConn"></a> Connectivity issues receiving an inbound message from the SAP server</span></span>  
 <span data-ttu-id="969cf-306">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-306">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-307">Vous obtenez l’erreur suivante uniquement lors de la réception d’un message entrant à partir du serveur SAP à l’aide de WCF-Custom port de réception pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-307">You get the following error only while receiving an inbound message from the SAP server using a WCF-Custom receive port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
```  
The Messaging Engine failed to add a receive location "<location_name>" with URL "<connection URI>" to the adapter "WCF-Custom".  
Reason: "Microsoft.Adapters.SAP.RFCException: Details: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  TPNAME=<name>, GWHOST=<host>, GWSERV=<server>  
```  
  
 <span data-ttu-id="969cf-308">Toutefois, vous êtes correctement capable d’envoyer des messages au système SAP à l’aide de WCF-Custom port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="969cf-308">However, you are successfully able to send messages to the SAP system using a WCF-Custom send port.</span></span>  
  
 <span data-ttu-id="969cf-309">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-309">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-310">Installez l’interface utilisateur graphique SAP sur le même ordinateur où vous exécutez le client de carte et essayez de recevoir le message entrant à nouveau.</span><span class="sxs-lookup"><span data-stu-id="969cf-310">Install the SAP GUI on the same computer where you are running the adapter client and try receiving the inbound message again.</span></span> <span data-ttu-id="969cf-311">Pour plus d’informations sur l’installation de l’interface GUI SAP, reportez-vous à la documentation de SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-311">For more information about how to install the SAP GUI, refer to SAP documentation.</span></span>  
  
##  <span data-ttu-id="969cf-312"><a name="BKMK_SAPRootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="969cf-312"><a name="BKMK_SAPRootNode"></a> Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="969cf-313">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-313">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-314">Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :</span><span class="sxs-lookup"><span data-stu-id="969cf-314">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="969cf-315">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-315">**Resolution**</span></span>  
  
1.  <span data-ttu-id="969cf-316">Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="969cf-316">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="969cf-317">Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).</span><span class="sxs-lookup"><span data-stu-id="969cf-317">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
##  <span data-ttu-id="969cf-318"><a name="BKMK_SAPVS2008"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="969cf-318"><a name="BKMK_SAPVS2008"></a> Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="969cf-319">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-319">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-320">Lorsque vous utilisez l’adaptateur pour créer une application dans Visual Studio et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="969cf-320">When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'sapBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="969cf-321">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-321">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-322">Cet avertissement s’affiche, car le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] de liaison, `sapBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969cf-322">This warning appears because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding, `sapBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="969cf-323">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-323">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-324">Vous pouvez ignorer cet avertissement sans problème.</span><span class="sxs-lookup"><span data-stu-id="969cf-324">You can safely ignore this warning.</span></span>  
  
##  <span data-ttu-id="969cf-325"><a name="BKMK_SAPSimilarSchema"></a>Exception XLANG dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="969cf-325"><a name="BKMK_SAPSimilarSchema"></a> XLANG exception in BizTalk Server</span></span>
 <span data-ttu-id="969cf-326">**Problème**</span><span class="sxs-lookup"><span data-stu-id="969cf-326">**Problem**</span></span>  
  
 <span data-ttu-id="969cf-327">BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.</span><span class="sxs-lookup"><span data-stu-id="969cf-327">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="969cf-328">**Cause**</span><span class="sxs-lookup"><span data-stu-id="969cf-328">**Cause**</span></span>  
  
 <span data-ttu-id="969cf-329">Cela se produit en raison de le des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="969cf-329">This happens because of either of the following:</span></span>  
  
-   <span data-ttu-id="969cf-330">Vous avez généré plus d’un schéma d’une opération générique (par exemple, SendIdoc et ReceiveIdoc) dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour effectuer des opérations respectives sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-330">You have generated more than one schema of a generic operation (such as SendIdoc and ReceiveIdoc) in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to perform respective operations on an SAP system.</span></span> <span data-ttu-id="969cf-331">Étant donné que les schémas sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="969cf-331">Because the schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
-   <span data-ttu-id="969cf-332">En cas de plusieurs projets, vous avez généré un schéma générique opération pour chacun des projets BizTalk Server, déployé chaque projet séparément de l’application BizTalk Server sur le même hôte et puis exécuté une application ou applications d’exécuter respectifs opérations sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="969cf-332">In case of multiple projects, you have generated a generic operation schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to perform respective operations on an SAP system.</span></span> <span data-ttu-id="969cf-333">Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="969cf-333">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
 <span data-ttu-id="969cf-334">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="969cf-334">**Resolution**</span></span>  
  
 <span data-ttu-id="969cf-335">Utiliser un fichier de schéma d’opération générique unique pour une application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="969cf-335">Use a single generic operation schema file for a BizTalk Server application.</span></span> <span data-ttu-id="969cf-336">Si vous avez besoin d’utiliser un schéma d’opération générique dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un schéma de la seule opération générique et ensuite utiliser le schéma d’opération générique à partir de toutes les autres applications dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="969cf-336">If you need to use a generic operation schema in multiple BizTalk Server applications on the same host, create an application containing a single generic operation schema, and then use the generic operation schema from all other applications in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969cf-337">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="969cf-337">See Also</span></span>  
[<span data-ttu-id="969cf-338">Résoudre les problèmes de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="969cf-338">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)