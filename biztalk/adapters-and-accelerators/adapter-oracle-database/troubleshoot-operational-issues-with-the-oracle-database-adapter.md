---
title: "Résoudre les problèmes opérationnels avec l’adaptateur de base de données Oracle | Documents Microsoft"
description: "Problèmes courants et des résolutions de carte de base de données Oracle dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fb83245-2b6a-48cc-8601-b923bb009a58
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ac926a378224e09dce36a52b52c171fb27911b0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshoot-operational-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="51989-103">Résoudre les problèmes opérationnels avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="51989-103">Troubleshoot operational issues with the Oracle Database adapter</span></span>
<span data-ttu-id="51989-104">Résolution des problèmes techniques pour résoudre les erreurs opérationnels que vous pouvez rencontrer à l’aide de [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-104">Troubleshooting techniques to resolve operational errors that you may experience using [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="enable-tracing"></a><span data-ttu-id="51989-105">Activer le suivi</span><span class="sxs-lookup"><span data-stu-id="51989-105">Enable tracing</span></span>  
 <span data-ttu-id="51989-106">Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="51989-106">For information about tracing support in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Diagnostic tracing and message logging for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="51989-107">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="51989-107">Known Issues</span></span>  
 <span data-ttu-id="51989-108">Voici les erreurs les plus courantes que vous pouvez rencontrer en utilisant le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ainsi que leur cause probable et de la résolution.</span><span class="sxs-lookup"><span data-stu-id="51989-108">The following are the most common errors you might encounter when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], along with their probable cause and resolution.</span></span>   
  
### <a name="BKMK_OraDBLoading"></a><span data-ttu-id="51989-109">Erreur lors du chargement des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="51989-109">Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="51989-110">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-110">**Problem**</span></span>  
  
 <span data-ttu-id="51989-111">Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="51989-111">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="51989-112">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-112">**Cause**</span></span>  
  
 <span data-ttu-id="51989-113">Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF charge les liaisons de l’adaptateur pour tous les adaptateurs installés.</span><span class="sxs-lookup"><span data-stu-id="51989-113">When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="51989-114">À son tour, les liaisons de l’adaptateur sont dépendantes du logiciel client spécifique pour l’application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="51989-114">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="51989-115">Vous risquez de rencontrer ce problème pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="51989-115">You might face this issue for one or both of the following reasons:</span></span>  
  
-   <span data-ttu-id="51989-116">Le logiciel client LOB requis n’est pas installé sur l’ordinateur où vous avez installé l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="51989-116">The required LOB client software is not installed on the computer where you installed the adapter.</span></span>  
  
-   <span data-ttu-id="51989-117">Vous avez effectué une installation standard ou complète de la carte, qui installe tous les adaptateurs contenus dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-117">You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="51989-118">Toutefois, les bibliothèques clientes LOB peuvent être installés pour seulement une application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="51989-118">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="51989-119">Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="51989-119">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="51989-120">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-120">**Resolution**</span></span>  
  
-   <span data-ttu-id="51989-121">Assurez-vous que les versions de client LOB requis sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-121">Make sure that the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="51989-122">[Prise en charge des systèmes d’entreprise et de métier (LOB)](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions de client pris en charge.</span><span class="sxs-lookup"><span data-stu-id="51989-122">[Supported Line-of-Business (LOB) and Enterprise systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported client versions.</span></span>  
  
-   <span data-ttu-id="51989-123">Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="51989-123">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51989-124">Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="51989-124">To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC.</span></span> <span data-ttu-id="51989-125">Pour plus d’informations, consultez [le fournisseur de données Oracle pour .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) sur le site Web d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="51989-125">For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.</span></span>  
  
###  <a name="BKMK_OraDBAdapDisplay"></a><span data-ttu-id="51989-126">L’adaptateur de base de données Oracle n’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="51989-126">The Oracle database adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="51989-127">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-127">**Problem**</span></span>  
  
<span data-ttu-id="51989-128">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] inclus avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] ne figure pas dans la liste des adaptateurs dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51989-128">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] inlcuded with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is not listed in the list of adapters in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="51989-129">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-129">**Cause**</span></span>  
  
 <span data-ttu-id="51989-130">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée.</span><span class="sxs-lookup"><span data-stu-id="51989-130">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="51989-131">Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-131">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
 <span data-ttu-id="51989-132">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-132">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-133">Vous pouvez ajouter explicitement le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="51989-133">You can explicitly add the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <a name="BKMK_OraDBXMLRetrieve"></a><span data-ttu-id="51989-134">Erreur lors de la récupération de sortie XML avec les nœuds de plus de 65 536</span><span class="sxs-lookup"><span data-stu-id="51989-134">Error while retrieving XML output with more than 65,536 nodes</span></span>  
 <span data-ttu-id="51989-135">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-135">**Problem**</span></span>  
  
 <span data-ttu-id="51989-136">L’adaptateur renvoie l’erreur suivante lors de la récupération du XML de sortie qui a plus de 65 536 nœuds.</span><span class="sxs-lookup"><span data-stu-id="51989-136">The adapter gives the following error when retrieving XML output that has more than 65,536 nodes.</span></span>  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 <span data-ttu-id="51989-137">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-137">**Cause**</span></span>  
  
 <span data-ttu-id="51989-138">L’adaptateur ne peut pas sérialiser et désérialiser un objet avec des éléments de plus de 65 536.</span><span class="sxs-lookup"><span data-stu-id="51989-138">The adapter cannot serialize and deserialize an object with more than 65,536 items.</span></span>  
  
 <span data-ttu-id="51989-139">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-139">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-140">Vous pouvez résoudre ce problème en définissant le `maxItemsInObjectGraph` paramètre.</span><span class="sxs-lookup"><span data-stu-id="51989-140">You can fix this issue by setting the `maxItemsInObjectGraph` parameter.</span></span> <span data-ttu-id="51989-141">Vous pouvez le définir dans une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="51989-141">You can set this in either of the following two ways:</span></span>  
  
-   <span data-ttu-id="51989-142">Définissez ce paramètre en modifiant le `maxItemsInObjectGraph` paramètre dans le `ServiceBehavior` attribut sur votre classe de service.</span><span class="sxs-lookup"><span data-stu-id="51989-142">Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.</span></span>  
  
-   <span data-ttu-id="51989-143">Ajoutez le code suivant au fichier app.config de votre application.</span><span class="sxs-lookup"><span data-stu-id="51989-143">Add the following to your application's app.config file.</span></span>  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 <span data-ttu-id="51989-144">Un fichier app.config exemple ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="51989-144">A sample app.config looks like this.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="oracleDBBinding"  
       contract="IOutboundContract" name="oracle_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_OraDBPerfOps"></a><span data-ttu-id="51989-145">Erreur lors de l’exécution d’opérations sur la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="51989-145">Error while performing operations on the Oracle database</span></span>  
 <span data-ttu-id="51989-146">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-146">**Problem**</span></span>  
  
 <span data-ttu-id="51989-147">L’adaptateur renvoie l’erreur suivante lors de l’exécution de toute opération sur la base de données Oracle à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-147">The adapter gives the following error when performing any operation on the Oracle database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="51989-148">**Pour BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="51989-148">**For BizTalk Server**</span></span>  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 <span data-ttu-id="51989-149">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-149">**Cause**</span></span>  
  
 <span data-ttu-id="51989-150">L’action WCF pour le message n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51989-150">The WCF action for the message is not specified.</span></span> <span data-ttu-id="51989-151">WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.</span><span class="sxs-lookup"><span data-stu-id="51989-151">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="51989-152">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-152">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-153">Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="51989-153">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="51989-154">Pour obtenir des instructions, consultez [configurer l’action SOAP pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="51989-154">For instructions, see [Configure the SOAP action for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md).</span></span> <span data-ttu-id="51989-155">Consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) pour afficher la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="51989-155">See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) to see a list of actions for each operation.</span></span>  
  
###  <a name="BKMK_OraDBXmlParsing"></a><span data-ttu-id="51989-156">XmlReaderParsingException en raison d’un nom d’opération incorrecte dans l’action spécifiée</span><span class="sxs-lookup"><span data-stu-id="51989-156">XmlReaderParsingException due to an incorrect operation name in the specified action</span></span>  
 <span data-ttu-id="51989-157">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-157">**Problem**</span></span>  
  
 <span data-ttu-id="51989-158">La Console Administration de BizTalk Server attribue l’erreur suivante lors de l’envoi de messages à une base de données Oracle :</span><span class="sxs-lookup"><span data-stu-id="51989-158">The BizTalk Server Administration Console gives the following error when sending messages to an Oracle database:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="51989-159">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-159">**Cause**</span></span>  
  
 <span data-ttu-id="51989-160">Si vous configurez un port personnalisé WCF en important le fichier de liaison de port créé par le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’action dans le port est spécifiée dans le format suivant :</span><span class="sxs-lookup"><span data-stu-id="51989-160">If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:</span></span>  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="51989-161">Dans le format ci-dessus, le nom de l’opération est régi par l’opération que vous avez choisi lors de la génération du schéma.</span><span class="sxs-lookup"><span data-stu-id="51989-161">In the above format, the operation name is governed by the operation you chose while generating the schema.</span></span> <span data-ttu-id="51989-162">Par exemple, si vous avez généré le schéma pour l’opération d’insertion sur une table, le nom de l’opération dans l’action sera « Insert ».</span><span class="sxs-lookup"><span data-stu-id="51989-162">For example, if you generated schema for the Insert operation on a table, the operation name in the action will be "Insert".</span></span> <span data-ttu-id="51989-163">Toutefois, le nom de l’opération dans le port logique créé dans l’orchestration BizTalk de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] peut être différent.</span><span class="sxs-lookup"><span data-stu-id="51989-163">However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.</span></span>  
  
 <span data-ttu-id="51989-164">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-164">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-165">Vérifiez que les noms des opérations dans les deux le port logique (dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) et le port physique (dans la Console Administration de BizTalk Server) sont les mêmes.</span><span class="sxs-lookup"><span data-stu-id="51989-165">Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration Console) are same.</span></span>  
  
###  <a name="BKMK_OraDBConnURI"></a><span data-ttu-id="51989-166">Erreur lors de la spécification d’un URI de connexion pour un port personnalisé WCF dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="51989-166">Error while specifying a connection URI for a WCF-Custom port in BizTalk</span></span>  
 <span data-ttu-id="51989-167">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-167">**Problem**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="51989-168">attribue l’erreur suivante lorsque vous spécifiez un URI de connexion pour se connecter à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="51989-168"> gives the following error when you specify a connection URI to connect to the Oracle database.</span></span>  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 <span data-ttu-id="51989-169">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-169">**Cause**</span></span>  
  
 <span data-ttu-id="51989-170">L’URI de connexion n’est pas conforme au format de codage standard.</span><span class="sxs-lookup"><span data-stu-id="51989-170">The connection URI does not adhere to the standard encoding format.</span></span> <span data-ttu-id="51989-171">Par exemple, la valeur d’un paramètre peut contenir un espace.</span><span class="sxs-lookup"><span data-stu-id="51989-171">For example, the value for a parameter might contain a space.</span></span>  
  
 <span data-ttu-id="51989-172">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-172">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-173">Vérifiez que la connexion URI que vous spécifiez respecte le format d’encodage standard.</span><span class="sxs-lookup"><span data-stu-id="51989-173">Make sure the connection URI you specify adheres to the standard encoding format.</span></span> <span data-ttu-id="51989-174">Par exemple, un espace vide doit être remplacé par « %20 ».</span><span class="sxs-lookup"><span data-stu-id="51989-174">For example, a blank space must be replaced by "%20".</span></span>  
  
###  <a name="BKMK_OraDBInvalCursor"></a><span data-ttu-id="51989-175">Exception de curseur non valide lors de l’appel de procédures stockées qui acceptent des paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="51989-175">Invalid cursor exception while invoking stored procedures that take REF CURSOR parameters</span></span>  
 <span data-ttu-id="51989-176">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-176">**Problem**</span></span>  
  
 <span data-ttu-id="51989-177">Lorsque vous appelez les procédures dans la base de données Oracle qui acceptent des entrées de REF CURSOR, vous pouvez obtenir l’exception suivante :</span><span class="sxs-lookup"><span data-stu-id="51989-177">When you invoke procedures in the Oracle database that take REF CURSOR inputs, you might get the following exception:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.TargetSystemException: ORA-01001: invalid cursor ---> Oracle.DataAccess.Client.OracleException  
```  
  
 <span data-ttu-id="51989-178">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-178">**Cause**</span></span>  
  
 <span data-ttu-id="51989-179">Le bloc de PL/SQL pour la procédure que vous appelez pourrait être transférant les REF CURSOR, autrement dit, le IN REF CURSOR peut être mise en route attribué à des REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="51989-179">The PL/SQL block for the procedure that you are invoking could be piping the REF CURSORs, that is, the IN REF CURSOR could be getting assigned to the OUT REF CURSOR.</span></span>  
  
 <span data-ttu-id="51989-180">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-180">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-181">Le bloc de PL/SQL doit diriger pas IN à la sortie REF CURSOR sans traitement approprié.</span><span class="sxs-lookup"><span data-stu-id="51989-181">The PL/SQL block must not pipe the IN to the OUT REF CURSORs without proper processing.</span></span>  
  
###  <a name="BKMK_OraDBValidateResp"></a><span data-ttu-id="51989-182">Erreur lors de la validation de la réponse pour l’opération ReadLOB à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="51989-182">Error while validating the response for the ReadLOB operation using BizTalk Server</span></span>  
 <span data-ttu-id="51989-183">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-183">**Problem**</span></span>  
  
 <span data-ttu-id="51989-184">Lors de l’exécution d’une opération de ReadLOB à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], la réponse à partir de la base de données Oracle échoue à la validation par rapport à la Description langage WSDL (Web Services).</span><span class="sxs-lookup"><span data-stu-id="51989-184">While performing a ReadLOB operation using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the response from the Oracle database fails validation against the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="51989-185">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-185">**Cause**</span></span>  
  
 <span data-ttu-id="51989-186">Le fichier WSDL contient un nom de nœud StreamBody qui est défini pour l’exécution de demandes basées sur le service, mais n’est pas nécessaire pour les scénarios de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="51989-186">The WSDL contains a StreamBody node name that is defined for execution of service-based requests, but is not needed for BizTalk scenarios.</span></span> <span data-ttu-id="51989-187">Par conséquent, lorsque le fichier de sortie XML, qui ne contient pas le nœud StreamBody, est comparée avec le WSDL, la validation échoue.</span><span class="sxs-lookup"><span data-stu-id="51989-187">Therefore, when the output XML, which does not contain the StreamBody node, is compared with the WSDL, validation fails.</span></span>  
  
 <span data-ttu-id="51989-188">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-188">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-189">Supprimez le nœud StreamBody à partir de WSDL lors de la validation par rapport à la sortie qui a été générée à l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51989-189">Remove the StreamBody node from the WSDL when validating against the output that was generated using BizTalk Server.</span></span> <span data-ttu-id="51989-190">Effectuez les étapes suivantes pour ce faire :</span><span class="sxs-lookup"><span data-stu-id="51989-190">Perform the following steps to do so:</span></span>  
  
1.  <span data-ttu-id="51989-191">Le fichier WSDL qui contient le nœud StreamBody ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="51989-191">The WSDL containing the StreamBody node looks like this.</span></span>  
  
    ```  
    <xs:element name="ReadLOBResponse">  
        <xs:annotation>  
          <xs:documentation>  
            <doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>  
          </xs:documentation>  
        </xs:annotation>  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" nillable="true" type="ns3:StreamBody" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    ```  
  
     <span data-ttu-id="51989-192">Remplacez l’exemple précédent avec les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="51989-192">Replace the preceding with the following.</span></span>  
  
    ```  
    <xs:element name="ReadLOBResponse">  
     <xs:annotation>  
     <xs:documentation>  
      <doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>   
      </xs:documentation>  
      </xs:annotation>  
     <xs:complexType>  
     <xs:sequence>  
      <xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" type="xs:base64Binary" />   
      </xs:sequence>  
      </xs:complexType>  
      </xs:element>  
    ```  
  
     <span data-ttu-id="51989-193">Dans cette étape, vous avez supprimé la référence au type = « ns3:StreamBody » dans le schéma XSD d’origine et l’a remplacé avec type = « xs : base64Binary ».</span><span class="sxs-lookup"><span data-stu-id="51989-193">In this step, you removed the reference to type="ns3:StreamBody" in the original XSD and replaced it with type="xs:base64Binary".</span></span> <span data-ttu-id="51989-194">En outre, vous avez supprimé la valeur « true » = « nillable » à partir du XSD d’origine.</span><span class="sxs-lookup"><span data-stu-id="51989-194">Also, you removed the nillable="true" value from the original XSD.</span></span>  
  
2.  <span data-ttu-id="51989-195">Supprimer les éléments suivants à partir de WSDL.</span><span class="sxs-lookup"><span data-stu-id="51989-195">Remove the following from the WSDL.</span></span>  
  
    ```  
    <xs:complexType name="StreamBody">  
        <xs:sequence>  
          <xs:element minOccurs="1" maxOccurs="1" name="Stream">  
            <xs:simpleType>  
              <xs:restriction base="xs:base64Binary">  
                <xs:minLength value="0" />  
              </xs:restriction>  
            </xs:simpleType>  
          </xs:element>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:element name="StreamBody" nillable="true" type="ns3:StreamBody" />  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="51989-196">Opération de ReadLOB n’est pas pris en charge avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-196">ReadLOB operation is not supported with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="51989-197">Vous devez utiliser une opération de sélection de table pour lire des données LOB à partir d’un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="51989-197">You should use a table Select operation to read LOB data from a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
###  <a name="BKMK_OraDBSchemaValidateFail"></a><span data-ttu-id="51989-198">Validation de schéma risque d’échouer dans les scénarios d’interrogation</span><span class="sxs-lookup"><span data-stu-id="51989-198">Schema validation may fail in polling scenarios</span></span>  
 <span data-ttu-id="51989-199">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-199">**Problem**</span></span>  
  
 <span data-ttu-id="51989-200">Échec de la validation de schéma dans les scénarios où le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interroge les tables qui contiennent des champs de type ROWID ou UNROWID de base de données.</span><span class="sxs-lookup"><span data-stu-id="51989-200">Schema validation fails in scenarios where the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] polls database tables that contain fields of type ROWID or UNROWID.</span></span>  
  
 <span data-ttu-id="51989-201">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-201">**Cause**</span></span>  
  
 <span data-ttu-id="51989-202">Au moment du design, lorsque l’adaptateur génère des métadonnées pour la table contenant les champs de type ROWID ou UNROWID, le schéma inclut « nillable = false », ce qui signifie que les champs de type ROWID ou UNROWID ne peut pas être null.</span><span class="sxs-lookup"><span data-stu-id="51989-202">At design-time, when the adapter generates metadata for the table containing fields of type ROWID or UNROWID, the schema includes “nillable=false”, which means that fields of type ROWID or UNROWID cannot be null.</span></span> <span data-ttu-id="51989-203">Toutefois, au moment de l’exécution lorsque l’adaptateur récupère les métadonnées, les champs de type ROWID ou UNROWID contiennent des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="51989-203">However, at run-time when the adapter retrieves the metadata, the fields of type ROWID or UNROWID contain null values.</span></span> <span data-ttu-id="51989-204">Par conséquent, la validation de schéma échoue.</span><span class="sxs-lookup"><span data-stu-id="51989-204">Hence the schema validation fails.</span></span>  
  
 <span data-ttu-id="51989-205">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-205">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-206">Si vous utilisez la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez choisir de désactiver la validation de schéma.</span><span class="sxs-lookup"><span data-stu-id="51989-206">If you are using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you may choose to disable schema validation.</span></span> <span data-ttu-id="51989-207">Ou bien, vous pouvez modifier manuellement le schéma pour modifier « nillbale = true » pour les types de données ROWID et UNROWID.</span><span class="sxs-lookup"><span data-stu-id="51989-207">Alternatively, you may manually edit the schema to change “nillbale=true” for ROWID and UNROWID data types.</span></span>  
  
###  <a name="BKMK_OraDBUnreasonConv"></a><span data-ttu-id="51989-208">Erreur 'Conversion déraisonnable demandée' lors de l’exécution de procédures stockées avec des Types d’enregistrements en tant que paramètres</span><span class="sxs-lookup"><span data-stu-id="51989-208">'Unreasonable conversion requested' error when executing stored procedures with Record Types as parameters</span></span>  
 <span data-ttu-id="51989-209">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-209">**Cause**</span></span>  
  
 <span data-ttu-id="51989-210">Envisagez un scénario où Oracle stockées procédure prend un Type d’enregistrement en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="51989-210">Consider a scenario where an Oracle stored procedure takes a Record Type as a parameter.</span></span> <span data-ttu-id="51989-211">Supposons que le Type d’enregistrement est déclaré comme \<nom de la table\>% ROWTYPE, où la table contient une colonne de type de données de type LONG.</span><span class="sxs-lookup"><span data-stu-id="51989-211">Assume that the Record Type is declared as \<table name\>%ROWTYPE, where the table has a column of LONG data type.</span></span> <span data-ttu-id="51989-212">Lorsque le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] rencontre le LONG type de données, il définit la taille du type de données égal à la valeur spécifiée pour le **LongDatatypeColumnSize** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="51989-212">When the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] encounters the LONG data type, it sets the size of the data type equal to the value specified for the **LongDatatypeColumnSize** binding property.</span></span> <span data-ttu-id="51989-213">Toutefois, la base de données Oracle ne définit pas une taille pour le type de données de type LONG.</span><span class="sxs-lookup"><span data-stu-id="51989-213">However, the Oracle database does not define a size for the LONG data type.</span></span> <span data-ttu-id="51989-214">Par conséquent, lorsque l’adaptateur appelle la procédure stockée, il génère une erreur « Conversion déraisonnable demandée ».</span><span class="sxs-lookup"><span data-stu-id="51989-214">So, when the adapter invokes the stored procedure, it results in an ‘Unreasonable conversion requested’ error.</span></span>  
  
 <span data-ttu-id="51989-215">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-215">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-216">Si un Type d’enregistrement a un type de données de type LONG, vous devez le définir explicitement en tant que partie d’un package.</span><span class="sxs-lookup"><span data-stu-id="51989-216">If a Record Type has a LONG data type, you must explicitly define it as part of a package.</span></span>  
  
###  <a name="BKMK_OraDBAdapRecognize"></a><span data-ttu-id="51989-217">L’adaptateur ne reconnaît pas l’action sur le port physique, même si le fichier de liaison généré par le complément Consume Adapter Service vous permet de créer les ports</span><span class="sxs-lookup"><span data-stu-id="51989-217">The adapter does not recognize the action on the physical port even though you use the binding file generated by the Consume Adapter Service add-in to create the ports</span></span>  
 <span data-ttu-id="51989-218">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-218">**Problem**</span></span>  
  
 <span data-ttu-id="51989-219">Après avoir utilisé le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour une opération spécifique sur la base de données Oracle, le complément crée également un fichier de liaison de port.</span><span class="sxs-lookup"><span data-stu-id="51989-219">After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the Oracle database, the add-in also creates a port binding file.</span></span> <span data-ttu-id="51989-220">Vous pouvez importer ce fichier à l’aide de la liaison la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports physiques dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51989-220">You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server.</span></span> <span data-ttu-id="51989-221">Toutefois, lorsque vous envoyez des messages à la base de données Oracle à l’aide de ces ports, l’adaptateur ne parvient pas à comprendre l’action spécifiée sur le port et génère une erreur semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="51989-221">However, when you send messages to the Oracle database using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 <span data-ttu-id="51989-222">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-222">**Cause**</span></span>  
  
 <span data-ttu-id="51989-223">Lorsque vous créez des ports logiques dans une orchestration BizTalk, vous spécifiez certains noms pour les opérations sur ces ports ou vous utilisez simplement les noms par défaut comme Operation_1, Operation_2, etc. Toutefois, dans le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le nom de l’opération est identique au nom de l’opération de base de données Oracle pour lequel générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="51989-223">When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the Oracle database operation for which you generate metadata.</span></span> <span data-ttu-id="51989-224">Par exemple, si vous générez des métadonnées pour une opération Select sur la table ACCOUNTACTIVITY dans la base de données Oracle, l’action est fixée à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="51989-224">For example, if you generate metadata for Select operation on ACCOUNTACTIVITY table in the Oracle database, the action will be set to the following:</span></span>  
  
```  
<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
```  
  
 <span data-ttu-id="51989-225">Lorsque vous importez le fichier de liaison, la même action est définie sur le port physique.</span><span class="sxs-lookup"><span data-stu-id="51989-225">When you import the binding file, the same action is set on physical port.</span></span> <span data-ttu-id="51989-226">Par conséquent, les noms de l’opération sur le port logique (Operation_1, Operation_2, etc.) ne correspondent pas les noms de l’opération spécifiées dans l’action sur le port physique, ce qui entraîne une erreur.</span><span class="sxs-lookup"><span data-stu-id="51989-226">So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.</span></span>  
  
 <span data-ttu-id="51989-227">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-227">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-228">Assurez-vous que le nom de l’opération dans le port logique est la même que le nom d’opération spécifié dans le cadre de l’action dans le port physique.</span><span class="sxs-lookup"><span data-stu-id="51989-228">Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port.</span></span> <span data-ttu-id="51989-229">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="51989-229">Do one of the following:</span></span>  
  
-   <span data-ttu-id="51989-230">Modifier le nom de l’opération dans le port logique dans le Concepteur d’orchestration BizTalk à partir de Operation_1, etc. à l’opération pour laquelle générer des métadonnées, par exemple Select.</span><span class="sxs-lookup"><span data-stu-id="51989-230">Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example Select.</span></span>  
  
-   <span data-ttu-id="51989-231">Modifier le nom de l’opération dans l’action sur le port physique pour le nom de l’opération dans le port logique.</span><span class="sxs-lookup"><span data-stu-id="51989-231">Change the operation name in the action on the physical port to the operation name in the logical port.</span></span> <span data-ttu-id="51989-232">Par exemple, vous pouvez modifier l’action dans le port physique pour ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="51989-232">For example, you could change the action in the physical port to resemble the following:</span></span>  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
    ```  
  
###  <a name="BKMK_OraDBOverflowExcep"></a><span data-ttu-id="51989-233">Adaptateur lève une exception de dépassement de capacité (« System.OverflowException ») sur l’exécution d’une opération</span><span class="sxs-lookup"><span data-stu-id="51989-233">Adapter throws an overflow exception (“System.OverflowException”) on executing an operation</span></span>  
 <span data-ttu-id="51989-234">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-234">**Problem**</span></span>  
  
 <span data-ttu-id="51989-235">À l’aide de la carte, si vous essayez d’effectuer une opération qui contiennent des types de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR, l’adaptateur peut lever une exception de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="51989-235">Using the adapter, if you try to perform an operation containing Oracle numeric data types inside DataSets or weakly-typed REF CURSORS, the adapter might throw an overflow exception.</span></span>  
  
 <span data-ttu-id="51989-236">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-236">**Cause**</span></span>  
  
 <span data-ttu-id="51989-237">Cela se produit si vous fournissez une valeur élevée pour le type de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR qui ne tiennent pas dans le type .NET respectif.</span><span class="sxs-lookup"><span data-stu-id="51989-237">This happens if you supply a large value for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS that cannot fit into the respective .NET type.</span></span>  
  
 <span data-ttu-id="51989-238">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-238">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-239">Si vous souhaitez passer des valeurs élevées pour le type de données numériques à l’intérieur des jeux de données ou faiblement typée REF CURSOR Oracle, vous devez activer la saisie sécurisée en définissant la valeur de la **EnableSafeTyping** liaison de propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="51989-239">If you want to pass large values for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS, you must enable safe typing by setting the value of the **EnableSafeTyping** binding property to **true**.</span></span> <span data-ttu-id="51989-240">L’activation de la saisie sécurisée expose les type de données numériques à l’intérieur des jeux de données ou faiblement typée REF CURSOR Oracle en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="51989-240">Enabling safe typing exposes the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS as strings.</span></span>  
  
###  <a name="BKMK_OraDBRootNode"></a><span data-ttu-id="51989-241">Erreur avec RootNode TypeName dans les projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="51989-241">Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="51989-242">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-242">**Problem**</span></span>  
  
 <span data-ttu-id="51989-243">Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :</span><span class="sxs-lookup"><span data-stu-id="51989-243">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="51989-244">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-244">**Resolution**</span></span>  
  
1.  <span data-ttu-id="51989-245">Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="51989-245">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="51989-246">Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).</span><span class="sxs-lookup"><span data-stu-id="51989-246">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <a name="BKMK_OraDBInvalBinding"></a><span data-ttu-id="51989-247">Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51989-247">Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="51989-248">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-248">**Problem**</span></span>  
  
 <span data-ttu-id="51989-249">Lorsque vous utilisez l’adaptateur pour créer une application dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="51989-249">When you use the adapter to create an application in [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'oracleDBBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="51989-250">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-250">**Cause**</span></span>  
  
 <span data-ttu-id="51989-251">Cet avertissement s’affiche, car le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] de liaison, `oracleDBBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51989-251">This warning appears because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding, `oracleDBBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="51989-252">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-252">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-253">Vous pouvez ignorer cet avertissement sans problème.</span><span class="sxs-lookup"><span data-stu-id="51989-253">You can safely ignore this warning.</span></span>  
  
###  <a name="BKMK_OraDBNotification"></a><span data-ttu-id="51989-254">BizTalk Server lève une exception si vous utilisez plusieurs schémas de Notification dans la même application ou le schéma de Notification entre plusieurs applications sur le même hôte</span><span class="sxs-lookup"><span data-stu-id="51989-254">BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host</span></span>  
 <span data-ttu-id="51989-255">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-255">**Problem**</span></span>  
  
 <span data-ttu-id="51989-256">BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.</span><span class="sxs-lookup"><span data-stu-id="51989-256">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="51989-257">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-257">**Cause**</span></span>  
  
 <span data-ttu-id="51989-258">Cela se produit en raison de le des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="51989-258">This happens because of either of the following:</span></span>  
  
-   <span data-ttu-id="51989-259">Vous avez généré plus d’un schéma de Notification dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour recevoir des notifications à partir de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="51989-259">You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the Oracle database.</span></span> <span data-ttu-id="51989-260">Étant donné que les schémas de Notification sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51989-260">Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
-   <span data-ttu-id="51989-261">En cas de plusieurs projets, vous avez généré un schéma de Notification pour chacun des projets, déployés dans chaque projet à une application BizTalk Server distincte sur le même hôte BizTalk Server, puis exécutez une application ou les applications de recevoir des notifications à partir de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="51989-261">In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the Oracle database.</span></span> <span data-ttu-id="51989-262">Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="51989-262">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
 <span data-ttu-id="51989-263">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-263">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-264">Utiliser un seul fichier de schéma de Notification pour une application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51989-264">Use a single Notification schema file for a BizTalk Server application.</span></span> <span data-ttu-id="51989-265">Si vous avez besoin d’utiliser le schéma de Notification dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un seul schéma de Notification, puis utiliser le schéma de notification à partir de toutes les autres applications dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51989-265">If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.</span></span>  
  
###  <a name="BKMK_MemUsage"></a><span data-ttu-id="51989-266">Utilisation de la mémoire et de thread nombre augmente lors de l’utilisation de la carte dans une opération entrante</span><span class="sxs-lookup"><span data-stu-id="51989-266">Memory usage and thread count increases when using the adapter in a transacted inbound operation</span></span>  
 <span data-ttu-id="51989-267">**Problème**</span><span class="sxs-lookup"><span data-stu-id="51989-267">**Problem**</span></span>  
  
 <span data-ttu-id="51989-268">Dans une opération entrante, telles que l’interrogation, **si aucune donnée n’est disponible dans la table interrogée** et l’adaptateur continue à interroger, sur une période de temps, vous rencontrez une augmentation de l’utilisation de la mémoire et le nombre de threads.</span><span class="sxs-lookup"><span data-stu-id="51989-268">In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.</span></span>  
  
 <span data-ttu-id="51989-269">**Cause**</span><span class="sxs-lookup"><span data-stu-id="51989-269">**Cause**</span></span>  
  
 <span data-ttu-id="51989-270">**Si aucune donnée n’est disponible dans la table interrogée**, après chaque cycle de délai d’attente de réception [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] génère un nouveau thread pour poursuivre l’opération d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="51989-270">**If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation.</span></span> <span data-ttu-id="51989-271">Par conséquent, l’utilisation de count et de la mémoire du thread augmente sur une période de temps.</span><span class="sxs-lookup"><span data-stu-id="51989-271">Hence, the thread count and memory usage increases over a period of time.</span></span> <span data-ttu-id="51989-272">Toutefois, si la table interrogée possède des données, le même thread continue à effectuer toutes les interrogations suivantes.</span><span class="sxs-lookup"><span data-stu-id="51989-272">However, if the table being polled has some data, the same thread continues to perform all subsequent polls.</span></span>  
  
 <span data-ttu-id="51989-273">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="51989-273">**Resolution**</span></span>  
  
 <span data-ttu-id="51989-274">Nous vous recommandons d’affecter le **ReceiveTimeout** à la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours) afin qu’un nouveau thread est généré uniquement 24 jours.</span><span class="sxs-lookup"><span data-stu-id="51989-274">We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days.</span></span> <span data-ttu-id="51989-275">Cela garantit que le nombre de threads et de l’utilisation de mémoire n’augmente pas trop trop tôt.</span><span class="sxs-lookup"><span data-stu-id="51989-275">This will ensure that the memory usage and thread count does not grow too much too soon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51989-276">Si SqlAdapterInboundTransactionBehavior a été défini, assurez-vous que le TransactionTimeout est également configuré pour la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours).</span><span class="sxs-lookup"><span data-stu-id="51989-276">If SqlAdapterInboundTransactionBehavior has been set, make sure the TransactionTimeout is also configured to maximum possible value, which is 24.20:31:23.6470000 (24 days).</span></span> <span data-ttu-id="51989-277">Lorsque vous utilisez cette solution de contournement, nous pouvons ajouter la SqlAdapterInboundTransactionBehavior uniquement si le niveau d’isolation de transaction doit être configurée.</span><span class="sxs-lookup"><span data-stu-id="51989-277">When using this workaround, we can add the SqlAdapterInboundTransactionBehavior only if the transaction isolation level has to be configured.</span></span> <span data-ttu-id="51989-278">Sinon, il est recommandé de supprimer ce comportement.</span><span class="sxs-lookup"><span data-stu-id="51989-278">Else, it is a best practice to remove that behavior.</span></span>  
  
 <span data-ttu-id="51989-279">Pour plus d’informations sur la **ReceiveTimeout** liaison de propriété, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="51989-279">For more information about the **ReceiveTimeout** binding property, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="51989-280">Pour obtenir des instructions sur la spécification des propriétés de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="51989-280">For instructions on specifying binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51989-281">Lors de l’utilisation de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], définir le délai d’attente pour une valeur élevée n’affecte pas les fonctionnalités de la carte.</span><span class="sxs-lookup"><span data-stu-id="51989-281">When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51989-282">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51989-282">See Also</span></span>  
[<span data-ttu-id="51989-283">Dépanner l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="51989-283">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[<span data-ttu-id="51989-284">Résoudre les problèmes d’installation de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="51989-284">Troubleshoot installation issues with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)