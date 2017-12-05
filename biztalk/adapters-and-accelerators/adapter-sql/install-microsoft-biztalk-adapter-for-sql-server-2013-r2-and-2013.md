---
title: "Installer l’adaptateur Microsoft BizTalk pour SQL Server - R2 de 2013 et 2013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c31d0d-783b-41ee-8265-56c9547e9dca
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af91ae787d5800738865980609bb86f96a73bfb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2013-r2-and-2013"></a><span data-ttu-id="63b07-102">Installer l’adaptateur Microsoft BizTalk pour SQL Server - R2 de 2013 et 2013</span><span class="sxs-lookup"><span data-stu-id="63b07-102">Install Microsoft BizTalk Adapter for SQL Server - 2013 R2 and 2013</span></span>
<span data-ttu-id="63b07-103">Installer le [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] inclus avec [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)], ou inclus avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 2013.</span><span class="sxs-lookup"><span data-stu-id="63b07-103">Install the [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] included with [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)], or included with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 2013.</span></span>

 <span data-ttu-id="63b07-104">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé avec :</span><span class="sxs-lookup"><span data-stu-id="63b07-104">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used with:</span></span>  
  
-   <span data-ttu-id="63b07-105">Une application .NET</span><span class="sxs-lookup"><span data-stu-id="63b07-105">A .NET application</span></span>  
  
-   <span data-ttu-id="63b07-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b07-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
 <span data-ttu-id="63b07-107">Selon la façon dont vous utilisez les adaptateurs, les logiciels requis varient.</span><span class="sxs-lookup"><span data-stu-id="63b07-107">Based on how you use the adapters, the required software varies.</span></span>  
 
<a name="BKMK_Prereqs_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a><span data-ttu-id="63b07-108">Configuration requise lors de l’utilisation de la carte avec une Application .NET</span><span class="sxs-lookup"><span data-stu-id="63b07-108">Prerequisites when using the adapter with a .NET Application</span></span>  
<span data-ttu-id="63b07-109">Installer les logiciels suivants sur l’ordinateur sur lequel vous écrivez des applications .NET qui consomment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-109">Install the following software on the computer where you are writing .NET applications that consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="63b07-110">Installez le logiciel dans l’ordre répertorié.</span><span class="sxs-lookup"><span data-stu-id="63b07-110">Install the software in the order as listed.</span></span>  

|<span data-ttu-id="63b07-111">2013 R2</span><span class="sxs-lookup"><span data-stu-id="63b07-111">2013 R2</span></span>|<span data-ttu-id="63b07-112">2013</span><span class="sxs-lookup"><span data-stu-id="63b07-112">2013</span></span>|  
|---|---|  
|[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]|<span data-ttu-id="63b07-113">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b07-113">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="63b07-114">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="63b07-114">Visual Studio 2013</span></span>|<span data-ttu-id="63b07-115">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="63b07-115">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|  
|<span data-ttu-id="63b07-116">Les bibliothèques clientes de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63b07-116">The SQL Server client libraries.</span></span> <span data-ttu-id="63b07-117">.</span><span class="sxs-lookup"><span data-stu-id="63b07-117">.</span></span>|<span data-ttu-id="63b07-118">Les bibliothèques clientes SQL Server...</span><span class="sxs-lookup"><span data-stu-id="63b07-118">The SQL Server client libraries..</span></span>|  

<a name="BKMK_Prereqs_BTS"></a>    
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a><span data-ttu-id="63b07-119">Configuration requise lors de l’utilisation de l’adaptateur avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="63b07-119">Prerequisites when using the adapter with BizTalk Server</span></span>  
<span data-ttu-id="63b07-120">Installer les logiciels suivants sur l’ordinateur où vous allez utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-120">Install the following software on the computer where you will be using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="63b07-121">Nous vous recommandons d’installer le logiciel dans le même ordre, comme indiqué ici.</span><span class="sxs-lookup"><span data-stu-id="63b07-121">We recommend installing the software in the same order as listed here.</span></span>  
 
 |<span data-ttu-id="63b07-122">2013 R2</span><span class="sxs-lookup"><span data-stu-id="63b07-122">2013 R2</span></span>|<span data-ttu-id="63b07-123">2013</span><span class="sxs-lookup"><span data-stu-id="63b07-123">2013</span></span>|  
|---|---|  
|[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]|<span data-ttu-id="63b07-124">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b07-124">Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]</span></span>|  
|<span data-ttu-id="63b07-125">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="63b07-125">Visual Studio 2013</span></span>|<span data-ttu-id="63b07-126">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="63b07-126">Visual Studio 2012</span></span>|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="63b07-127">Installer le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-127">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="63b07-128">Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-128">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="63b07-129">Installer le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-129">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="63b07-130">Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-130">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>|  
|<span data-ttu-id="63b07-131">BizTalk Server 2013 R2</span><span class="sxs-lookup"><span data-stu-id="63b07-131">BizTalk Server 2013 R2</span></span>|<span data-ttu-id="63b07-132">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="63b07-132">BizTalk Server 2013</span></span>|  
|<span data-ttu-id="63b07-133">Les bibliothèques clientes de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63b07-133">The SQL Server client libraries.</span></span> |<span data-ttu-id="63b07-134">Les bibliothèques clientes de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63b07-134">The SQL Server client libraries.</span></span> |  

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a><span data-ttu-id="63b07-135">Les versions de SQL Server prises en charge et des bibliothèques clientes</span><span class="sxs-lookup"><span data-stu-id="63b07-135">Supported SQL Server versions and client libraries</span></span>  
 <span data-ttu-id="63b07-136">La section suivante présente les versions prises en charge de SQL Server et le client, les bibliothèques requises par les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-136">The following section presents the supported SQL Server versions and the client libraries required by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="63b07-137">**Les versions de serveur prises en charge**: SQL Server 2005, SQL Server 2008 SP1, SQL Server 2008 R2, SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="63b07-137">**Supported server versions**: SQL Server 2005, SQL Server 2008 SP1, SQL Server 2008 R2, SQL Server 2012</span></span>  
  
-   <span data-ttu-id="63b07-138">**Prise en charge des versions de client**: Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] offres groupées de la DLL du client requises pour se connecter à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63b07-138">**Supported client versions**: Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] bundles the client DLLs required to connect to SQL Server.</span></span> <span data-ttu-id="63b07-139">Il est inutile d’installer explicitement n’importe quel client dll sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="63b07-139">You do not need to explicitly install any client DLLs on your computer.</span></span>  
  
-   <span data-ttu-id="63b07-140">**Pilotes requis**:</span><span class="sxs-lookup"><span data-stu-id="63b07-140">**Required drivers**:</span></span>  
  
    -   <span data-ttu-id="63b07-141">Si vous utilisez les UDT fournis avec les versions de SQL Server, par exemple, géographie, assurez-vous que les DLL suivantes sont présentes sur l’ordinateur où vous utilisez l’adaptateur pour effectuer des opérations sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63b07-141">If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server.</span></span> <span data-ttu-id="63b07-142">Par exemple, si vous créez des projets BizTalk pour effectuer des opérations sur SQL Server, ces DLL doit être présent sur l’ordinateur sur lequel BizTalk Server est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="63b07-142">For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.</span></span>  
  
        -   <span data-ttu-id="63b07-143">Assurez-vous que Microsoft.SqlServer.Types.dll est ajouté au GAC.</span><span class="sxs-lookup"><span data-stu-id="63b07-143">Make sure Microsoft.SqlServer.Types.dll is added to the GAC.</span></span>  
  
        -   <span data-ttu-id="63b07-144">Assurez-vous que SqlServerSpatial.dll est disponible dans le dossier System32.</span><span class="sxs-lookup"><span data-stu-id="63b07-144">Make sure SqlServerSpatial.dll is available in the System32 folder.</span></span>  
  
         <span data-ttu-id="63b07-145">Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="63b07-145">You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.</span></span>  
  
    -   <span data-ttu-id="63b07-146">Si vous utilisez l’adaptateur pour effectuer des opérations sur des colonnes de types de données FILESTREAM, assurez-vous que vous avez SQL Client Connectivity SDK est installé.</span><span class="sxs-lookup"><span data-stu-id="63b07-146">If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="63b07-147">Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="63b07-147">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="63b07-148">L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="63b07-148">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  
  
    -   <span data-ttu-id="63b07-149">Si vous créez votre propre UDT dans SQL Server, assurez-vous que les assemblys respectives pour les UDT sont ajoutés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="63b07-149">If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.</span></span>  
  
<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a><span data-ttu-id="63b07-150">prise en charge 64 bits</span><span class="sxs-lookup"><span data-stu-id="63b07-150">64-bit support</span></span> 

<span data-ttu-id="63b07-151">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut s’exécuter dans une instance d’hôte 32 bits ou 64 bits.</span><span class="sxs-lookup"><span data-stu-id="63b07-151">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can run in a 32-bit or 64-bit host instance.</span></span>

 <span data-ttu-id="63b07-152">Pour plus d’informations sur les scénarios d’installation pris en charge pour les 32 bits et 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)],.</span><span class="sxs-lookup"><span data-stu-id="63b07-152">For more information about the supported installation scenarios for the 32-bit and 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)],.</span></span> 
  
<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a><span data-ttu-id="63b07-153">Installer l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="63b07-153">Install the SQL Adapter</span></span>  
 <span data-ttu-id="63b07-154">Assurez-vous que vous avez les composants requis installés avant d’installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-154">Make sure you have the prerequisites installed before installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="63b07-155">Vous pouvez installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="63b07-155">You can install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="63b07-156">**En mode interactif** à l’aide de l’Assistant Installation</span><span class="sxs-lookup"><span data-stu-id="63b07-156">**In interactive mode** using the setup wizard</span></span>  
  
-   <span data-ttu-id="63b07-157">**En mode silencieux** dans la commande à l’aide de msiexec lin</span><span class="sxs-lookup"><span data-stu-id="63b07-157">**In silent mode** using msiexec in the command lin</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="63b07-158">Vous devez disposer des privilèges d’administrateur sur l’ordinateur où vous installerez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], indépendamment de si vous installez à l’aide de l’Assistant ou la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="63b07-158">You must have administrative privileges on the computer where you will install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], irrespective of whether you are installing by using the wizard or the command line.</span></span>  
  
<a name="BKMK_Install_Scenarios"></a>   
### <a name="32-bit-and-64-bit-install-scenarios"></a><span data-ttu-id="63b07-159">scénarios d’installation de 32 bits et 64 bits</span><span class="sxs-lookup"><span data-stu-id="63b07-159">32-bit and 64-bit install scenarios</span></span>
 <span data-ttu-id="63b07-160">Avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé pour :</span><span class="sxs-lookup"><span data-stu-id="63b07-160">With [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used for:</span></span>  
  
-   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="63b07-161">au moment du design (lors de la génération des métadonnées pour les opérations).</span><span class="sxs-lookup"><span data-stu-id="63b07-161"> design time (when generating metadata for operations).</span></span>  
  
-   <span data-ttu-id="63b07-162">Moment du design de console Administration de BizTalk Server (pour créer des ports physiques).</span><span class="sxs-lookup"><span data-stu-id="63b07-162">BizTalk Server Administration console design time (for creating physical ports).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b07-163">Console d’Administration de BizTalk Server s’exécute comme une application de la Console MMC (Microsoft Management Console) 32 bits.</span><span class="sxs-lookup"><span data-stu-id="63b07-163">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  
  
-   <span data-ttu-id="63b07-164">Durée d’exécution BizTalk (pendant l’envoi et réception de messages à partir d’applications métier).</span><span class="sxs-lookup"><span data-stu-id="63b07-164">BizTalk run time (when sending and receiving messages from LOB applications).</span></span>  
  
 <span data-ttu-id="63b07-165">Vous pouvez avoir une installation où vous effectuez toutes ces tâches sur le même ordinateur ou sur des ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="63b07-165">You can have an installation where you perform all these tasks on the same computer or different computers.</span></span> <span data-ttu-id="63b07-166">Étant donné que les deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et MMC de BizTalk sont des processus 32 bits, vous devez installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur l’ordinateur où vous souhaitez effectuer les tâches au moment du design.</span><span class="sxs-lookup"><span data-stu-id="63b07-166">Because both [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on the computer where you want to perform the design-time tasks.</span></span> <span data-ttu-id="63b07-167">Les scénarios suivants sont pris en charge pour l’installation de le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur les plateformes 32 bits et 64 bits.</span><span class="sxs-lookup"><span data-stu-id="63b07-167">The following scenarios are supported for installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on 32-bit and 64-bit platforms.</span></span>  
  
#### <a name="install-scenarios-on-a-32-bit-platform"></a><span data-ttu-id="63b07-168">Installer des scénarios sur une plateforme 32 bits</span><span class="sxs-lookup"><span data-stu-id="63b07-168">Install scenarios on a 32-bit platform</span></span>  
 <span data-ttu-id="63b07-169">Les scénarios suivants sont pris en charge lors de l’installation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur une plateforme 32 bits.</span><span class="sxs-lookup"><span data-stu-id="63b07-169">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 32-bit platform.</span></span>  
  
|<span data-ttu-id="63b07-170">Conception de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63b07-170">Visual Studio design time</span></span>|<span data-ttu-id="63b07-171">Moment du design MMC de BizTalk</span><span class="sxs-lookup"><span data-stu-id="63b07-171">BizTalk MMC design time</span></span>|<span data-ttu-id="63b07-172">Durée d’exécution de BizTalk</span><span class="sxs-lookup"><span data-stu-id="63b07-172">BizTalk run time</span></span>|<span data-ttu-id="63b07-173">Durée d’exécution Visual moment du design Studio et/ou de conception BizTalk MMC + BizTalk</span><span class="sxs-lookup"><span data-stu-id="63b07-173">Visual Studio design time and/or  BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="63b07-174">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-174">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-175">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-175">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-176">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-176">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="63b07-177">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-177">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-178">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-178">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-179">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-179">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="63b07-180">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-180">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-181">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-181">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-182">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-182">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="63b07-183">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-183">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-184">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-184">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-185">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-185">- Install 32-bit client and other required DLLs.</span></span>|  
  
#### <a name="install-scenarios-on-a-64-bit-platform"></a><span data-ttu-id="63b07-186">Installer des scénarios sur une plateforme 64 bits</span><span class="sxs-lookup"><span data-stu-id="63b07-186">Install scenarios on a 64-bit platform</span></span>  
 <span data-ttu-id="63b07-187">Les scénarios suivants sont pris en charge lors de l’installation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur une plateforme 64 bits.</span><span class="sxs-lookup"><span data-stu-id="63b07-187">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 64-bit platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63b07-188">Sur n’importe quel ordinateur où vous souhaitez effectuer des tâches au moment du design à l’aide [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou MMC de BizTalk, vous devez installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-188">On any computer where you want to perform design-time tasks using either [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
|<span data-ttu-id="63b07-189">Conception de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63b07-189">Visual Studio design time</span></span>|<span data-ttu-id="63b07-190">Moment du design MMC de BizTalk</span><span class="sxs-lookup"><span data-stu-id="63b07-190">BizTalk MMC design time</span></span>|<span data-ttu-id="63b07-191">Durée d’exécution de BizTalk</span><span class="sxs-lookup"><span data-stu-id="63b07-191">BizTalk run time</span></span>|<span data-ttu-id="63b07-192">Durée d’exécution Visual moment du design Studio et/ou de conception BizTalk MMC + BizTalk</span><span class="sxs-lookup"><span data-stu-id="63b07-192">Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="63b07-193">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-193">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-194">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-194">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-195">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-195">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="63b07-196">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-196">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-197">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-197">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-198">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-198">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="63b07-199">**Pour un processus de BizTalk 32 bits**:</span><span class="sxs-lookup"><span data-stu-id="63b07-199">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="63b07-200">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-200">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-201">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-201">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-202">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-202">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="63b07-203">**Pour un processus BizTalk de 64 bits**:</span><span class="sxs-lookup"><span data-stu-id="63b07-203">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="63b07-204">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-204">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-205">-Installer 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-205">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-206">-Installez des clients 64 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-206">- Install 64-bit client and other required DLLs.</span></span>|<span data-ttu-id="63b07-207">**Pour un processus de BizTalk 32 bits**:</span><span class="sxs-lookup"><span data-stu-id="63b07-207">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="63b07-208">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-208">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-209">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-209">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-210">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-210">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="63b07-211">**Pour un processus BizTalk de 64 bits**:</span><span class="sxs-lookup"><span data-stu-id="63b07-211">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="63b07-212">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-212">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-213">-Installer 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-213">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-214">-Installez des clients 64 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-214">- Install 64-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="63b07-215">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-215">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="63b07-216">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="63b07-216">- Install 32-bit client and other required DLLs.</span></span>|  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-sql-adapter-in-interactive-mode"></a><span data-ttu-id="63b07-217">Installer l’adaptateur SQL en mode interactif</span><span class="sxs-lookup"><span data-stu-id="63b07-217">Install the SQL Adapter in interactive mode</span></span>  
 
1.  <span data-ttu-id="63b07-218">Exécutez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-218">Run the installer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b07-219">Si vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur un ordinateur virtuel, l’Assistant installation ne peut pas continuer au-delà d’une boîte de dialogue informant que la vérification de l’espace disque disponible.</span><span class="sxs-lookup"><span data-stu-id="63b07-219">If you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space.</span></span> <span data-ttu-id="63b07-220">Dans ce cas, nous vous recommandons d’utiliser l’option d’installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="63b07-220">In such cases, we recommend that you use the silent installation option.</span></span>   
  
2.  <span data-ttu-id="63b07-221">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="63b07-221">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="63b07-222">Lisez et acceptez le contrat de licence utilisateur final (CLUF), puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="63b07-222">Read and accept the end-user license agreement (EULA), and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="63b07-223">Dans le **dossier de Destination** boîte de dialogue, spécifiez l’emplacement où vous souhaitez installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], cliquez sur **suivant**, puis cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="63b07-223">In the **Destination Folder** dialog box, specify the location where you want to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], click **Next**, and then click **Install**.</span></span>  
  
5.  <span data-ttu-id="63b07-224">Dans le **Customer Experience Improvement Program** boîte de dialogue, spécifiez si vous souhaitez inscrire pour le programme (amélioration).</span><span class="sxs-lookup"><span data-stu-id="63b07-224">In the **Customer Experience Improvement Program** dialog box, specify whether you would like to enroll for the Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="63b07-225">Dans le cadre de ce programme pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous allez partager les données suivantes avec Microsoft :</span><span class="sxs-lookup"><span data-stu-id="63b07-225">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="63b07-226">Les données relatives au matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-226">Data related to the computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    -   <span data-ttu-id="63b07-227">Les données relatives à des versions de SQL Server que vous utilisez pour vous connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-227">Data related to the SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="63b07-228">Spécifiez votre choix et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63b07-228">Specify your choice and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b07-229">Vous pouvez toujours modifier vos préférences concernant l’inscription pour CEIP en exécutant le programme d’installation en mode réparation à partir du panneau.</span><span class="sxs-lookup"><span data-stu-id="63b07-229">You can always change your preference regarding enrolling for CEIP by running the Setup in Repair mode from the Control Panel.</span></span>  
  
6.  <span data-ttu-id="63b07-230">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="63b07-230">Click **Finish**.</span></span>  
  
<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a><span data-ttu-id="63b07-231">Installer l’adaptateur SQL en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="63b07-231">Install the SQL adapter in Silent mode</span></span>  
 <span data-ttu-id="63b07-232">La procédure suivante montre comment effectuer une installation silencieuse de [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de la `msiexec` commande.</span><span class="sxs-lookup"><span data-stu-id="63b07-232">The following procedure demonstrates how to perform a silent installation of [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the `msiexec` command.</span></span>  
  
1.  <span data-ttu-id="63b07-233">Ouvrez une invite de commandes et accédez au dossier où vous avez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-233">Open a command prompt, and navigate to the folder where you have the installer.</span></span>  
  
2.  <span data-ttu-id="63b07-234">Exécutez la commande suivante pour installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="63b07-234">Run the following command to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b07-235">Pour effectuer une installation sans assistance sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi SqlAdapterSetup64.msi.</span><span class="sxs-lookup"><span data-stu-id="63b07-235">To perform silent installation on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn  
    ```  
  
     <span data-ttu-id="63b07-236">Vous pouvez également choisir d’inscrire pour CEIP dans le cadre de l’installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="63b07-236">You can also choose to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="63b07-237">Dans le cadre de ce programme pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous allez partager les données suivantes avec Microsoft :</span><span class="sxs-lookup"><span data-stu-id="63b07-237">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="63b07-238">Le matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-238">The computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    -   <span data-ttu-id="63b07-239">Les versions de SQL Server que vous utilisez pour vous connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-239">The SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="63b07-240">Pour vous inscrire pour CEIP, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="63b07-240">To enroll for CEIP, run the following command:</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
    ```  
  
     <span data-ttu-id="63b07-241">Par défaut, l’option a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="63b07-241">By default, the option is false.</span></span>  
  
     <span data-ttu-id="63b07-242">Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span><span class="sxs-lookup"><span data-stu-id="63b07-242">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a><span data-ttu-id="63b07-243">Tâches de post-installation</span><span class="sxs-lookup"><span data-stu-id="63b07-243">Post-installation tasks</span></span>  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a><span data-ttu-id="63b07-244">Inscrire les liaisons</span><span class="sxs-lookup"><span data-stu-id="63b07-244">Register the Bindings</span></span>  
<span data-ttu-id="63b07-245">Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="63b07-245">Complete these steps *only* if the setup wizard fails to register the adapter bindings in the machine.config file.</span></span>  
  
1.  <span data-ttu-id="63b07-246">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="63b07-246">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="63b07-247">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="63b07-247">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    -   <span data-ttu-id="63b07-248">Pour Microsoft .NET Framework 3.5 SP1, \< *version* \> est la version v2.0.50727 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63b07-248">For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="63b07-249">Pour Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \< *version* \> est la version v4.0.30319 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63b07-249">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="63b07-250">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="63b07-250">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="63b07-251">Pour enregistrer des liaisons de l’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="63b07-251">To register the adapter bindings:</span></span>  
  
    1.  <span data-ttu-id="63b07-252">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="63b07-252">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="63b07-253">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="63b07-253">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="63b07-254">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="63b07-254">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="63b07-255">Pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="63b07-255">For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="63b07-256">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="63b07-256">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="63b07-257">Ajoutez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="63b07-257">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="63b07-258">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="63b07-258">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
      
  
4.  <span data-ttu-id="63b07-259">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="63b07-259">Save and close the machine.config file.</span></span>  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a><span data-ttu-id="63b07-260">Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="63b07-260">Determining the Public Key and Version</span></span>  
<span data-ttu-id="63b07-261">Effectuez les étapes suivantes pour déterminer la clé publique et la version pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-261">Complete the following steps to determine the public key and version for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="63b07-262">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="63b07-262">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="63b07-263">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="63b07-263">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="63b07-264">Le tableau suivant répertorie le nom des DLL pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-264">The following table lists the name of the DLLs for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    |<span data-ttu-id="63b07-265">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="63b07-265">Adapter</span></span>|<span data-ttu-id="63b07-266">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="63b07-266">Name of the DLL</span></span>|  
    |---|---|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|<span data-ttu-id="63b07-267">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="63b07-267">Microsoft.Adapters.Sql.dll</span></span>|  
  
3.  <span data-ttu-id="63b07-268">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="63b07-268">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="63b07-269">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="63b07-269">Similarly, the value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="63b07-270">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="63b07-270">Copy the public key, and then click **Cancel**.</span></span>  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a><span data-ttu-id="63b07-271">Mettre à jour ou de modifier l’installation de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="63b07-271">Update or change the SQL adapter installation</span></span>  
 <span data-ttu-id="63b07-272">Procédez comme suit pour modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-272">Perform the following steps to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span> <span data-ttu-id="63b07-273">Assurez-vous que vous avez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installé avant d’exécuter l’Assistant Installation pour modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-273">Make sure you have the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span>  
  
 <span data-ttu-id="63b07-274">Vous pouvez modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="63b07-274">You can modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the following two ways:</span></span>  
  
-   <span data-ttu-id="63b07-275">**En mode interactif** en exécutant l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-275">**In interactive mode** by running the setup wizard.</span></span>  
  
-   <span data-ttu-id="63b07-276">**En mode silencieux** à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="63b07-276">**In silent mode** by using the command line.</span></span>  
  
#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a><span data-ttu-id="63b07-277">Mise à jour de l’installation de l’adaptateur SQL en mode interactif</span><span class="sxs-lookup"><span data-stu-id="63b07-277">Update the SQL Adapter installation in interactive mode</span></span>  
  
1.  <span data-ttu-id="63b07-278">Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="63b07-278">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="63b07-279">Dans le panneau de configuration, double-cliquez sur **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="63b07-279">In Control Panel, double-click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="63b07-280">Dans le **programmes et fonctionnalités** fenêtre, sélectionnez **l’adaptateur Microsoft BizTalk pour SQL Server**, puis cliquez sur **modification**.</span><span class="sxs-lookup"><span data-stu-id="63b07-280">In the **Programs and Features** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Change**.</span></span>  
  
4.  <span data-ttu-id="63b07-281">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="63b07-281">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="63b07-282">Dans le **modifier, réparer ou supprimer l’installation** boîte de dialogue, cliquez sur **réparer**.</span><span class="sxs-lookup"><span data-stu-id="63b07-282">In the **Change, repair, or remove installation** dialog box, click **Repair**.</span></span>  
  
6.  <span data-ttu-id="63b07-283">Dans le **prêt à réparer l’adaptateur Microsoft BizTalk pour SQL Server** boîte de dialogue, cliquez sur **réparer**.</span><span class="sxs-lookup"><span data-stu-id="63b07-283">In the **Ready to repair Microsoft BizTalk Adapter for SQL Server** dialog box, click **Repair**.</span></span>  
  
7.  <span data-ttu-id="63b07-284">Si nécessaire, modifiez vos préférences concernant le choix d’amélioration du produit, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63b07-284">If required, change your preferences regarding opting for CEIP, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="63b07-285">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="63b07-285">Click **Finish**.</span></span>  
  
#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a><span data-ttu-id="63b07-286">Mise à jour de l’installation de l’adaptateur SQL en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="63b07-286">Update the SQL Adapter installation in silent mode</span></span>  
  
1.  <span data-ttu-id="63b07-287">Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-287">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="63b07-288">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="63b07-288">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b07-289">Pour modifier la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi par SqlAdapterSetup64.msi.</span><span class="sxs-lookup"><span data-stu-id="63b07-289">To modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn /f  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="63b07-290">Lors de la modification du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation en mode silencieux, vous ne pouvez pas modifier vos préférences pour vous inscrire ou de refuser le CEIP.</span><span class="sxs-lookup"><span data-stu-id="63b07-290">While modifying the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="63b07-291">Les préférences reste le même que vous avez spécifié pendant l’installation, même si vous définissez explicitement la CEIP_OPTIN à true ou false.</span><span class="sxs-lookup"><span data-stu-id="63b07-291">The preferences will remain the same as you specified during the installation, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  
  
     <span data-ttu-id="63b07-292">Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span><span class="sxs-lookup"><span data-stu-id="63b07-292">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>   
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a><span data-ttu-id="63b07-293">Désinstaller ou supprimer l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="63b07-293">Uninstall or remove the SQL Adapter</span></span>  
 <span data-ttu-id="63b07-294">Procédez comme suit pour supprimer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à partir de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="63b07-294">Perform the following steps to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from your computer.</span></span> <span data-ttu-id="63b07-295">Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant Installation pour supprimer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-295">Make sure you have the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="63b07-296">Vous pouvez supprimer la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="63b07-296">You can remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="63b07-297">**En mode interactif** en exécutant l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-297">**In interactive mode** by running the setup wizard.</span></span>  
  
-   <span data-ttu-id="63b07-298">**En mode silencieux** à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="63b07-298">**In silent mode** by using the command line.</span></span>  
  
#### <a name="uninstall-in-interactive-mode"></a><span data-ttu-id="63b07-299">Désinstaller en mode interactif</span><span class="sxs-lookup"><span data-stu-id="63b07-299">Uninstall in interactive mode</span></span>  
  
1.  <span data-ttu-id="63b07-300">Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="63b07-300">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="63b07-301">Dans le panneau de configuration, double-cliquez sur **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="63b07-301">In Control Panel, double-click  **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="63b07-302">Dans le **Ajout / Suppression de programmes** fenêtre, sélectionnez **l’adaptateur Microsoft BizTalk pour SQL Server**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="63b07-302">In the **Add or Remove Programs** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Remove**.</span></span>  
  
4.  <span data-ttu-id="63b07-303">Dans la boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="63b07-303">In the dialog box, click **Yes**.</span></span>  
  
#### <a name="uninstall-in-silent-mode"></a><span data-ttu-id="63b07-304">Désinstaller en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="63b07-304">Uninstall in silent mode</span></span>  
  
1.  <span data-ttu-id="63b07-305">Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="63b07-305">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="63b07-306">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="63b07-306">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b07-307">Pour supprimer la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi par SqlAdapterSetup64.msi.</span><span class="sxs-lookup"><span data-stu-id="63b07-307">To remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /x SqlAdapterSetup.msi /qn  
    ```  
  
     <span data-ttu-id="63b07-308">Cette commande supprime le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à partir de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="63b07-308">This command removes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from the computer.</span></span>  
  
     <span data-ttu-id="63b07-309">Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span><span class="sxs-lookup"><span data-stu-id="63b07-309">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a><span data-ttu-id="63b07-310">Tâche post-désinstallation</span><span class="sxs-lookup"><span data-stu-id="63b07-310">Post-uninstall task</span></span>  
 <span data-ttu-id="63b07-311">Si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] le programme d’installation ne parvient pas à supprimer les liaisons de l’adaptateur lors de la suppression du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez les supprimer manuellement.</span><span class="sxs-lookup"><span data-stu-id="63b07-311">If the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] setup fails to remove the adapter bindings while removing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must remove them manually.</span></span> <span data-ttu-id="63b07-312">La section suivante décrit comment supprimer manuellement les liaisons pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b07-312">The following section describes how to manually remove the bindings for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
<a name="BKMK_Remove_Binding"></a>   
#### <a name="manually-remove-the-bindings"></a><span data-ttu-id="63b07-313">Supprimez manuellement les liaisons</span><span class="sxs-lookup"><span data-stu-id="63b07-313">Manually remove the bindings</span></span>  
 <span data-ttu-id="63b07-314">Effectuez ces opérations *uniquement* si l’Assistant installation ne parvient pas à supprimer les liaisons de l’adaptateur à partir du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="63b07-314">Perform these steps *only* if the setup wizard fails to remove the adapter bindings from the machine.config file.</span></span>  
  
1.  <span data-ttu-id="63b07-315">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="63b07-315">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="63b07-316">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="63b07-316">For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    -   <span data-ttu-id="63b07-317">Pour Microsoft .NET Framework 3.5 SP1, \< *version* \> est la version v2.0.50727 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63b07-317">For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="63b07-318">Pour Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \< *version* \> est la version v4.0.30319 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63b07-318">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="63b07-319">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="63b07-319">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="63b07-320">Pour supprimer l’inscription de la liaison de la carte :</span><span class="sxs-lookup"><span data-stu-id="63b07-320">To remove the adapter binding registration:</span></span>  
  
    1.  <span data-ttu-id="63b07-321">Recherchez l’élément « system.serviceModel » et supprimer les éléments suivants figurant dans l’élément :</span><span class="sxs-lookup"><span data-stu-id="63b07-321">Search for the element "system.serviceModel" and remove the following from under the element:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  <span data-ttu-id="63b07-322">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="63b07-322">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="63b07-323">Supprimez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="63b07-323">Remove the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="63b07-324">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="63b07-324">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="63b07-325">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="63b07-325">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="63b07-326">Supprimez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="63b07-326">Remove the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="63b07-327">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="63b07-327">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  <span data-ttu-id="63b07-328">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="63b07-328">Save and close the machine.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b07-329">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63b07-329">See also</span></span>
[<span data-ttu-id="63b07-330">Installer l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="63b07-330">Install the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[<span data-ttu-id="63b07-331">Présentation de l’adaptateur BizTalk pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="63b07-331">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)