---
title: "Installez l’adaptateur Microsoft BizTalk pour SQL Server - 2016 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc6b94e-1cac-4b90-8567-05b33caa9bf3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d4df12cfc9e37ed5deff59051cb483dd092facb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-microsoft-biztalk-adapter-for-sql-server---2016"></a><span data-ttu-id="12559-102">Installez l’adaptateur Microsoft BizTalk pour SQL Server - 2016</span><span class="sxs-lookup"><span data-stu-id="12559-102">Install Microsoft BizTalk Adapter for SQL Server - 2016</span></span>
<span data-ttu-id="12559-103">Installer le [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] inclus avec [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-103">Install the [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] included with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span>

 <span data-ttu-id="12559-104">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé avec :</span><span class="sxs-lookup"><span data-stu-id="12559-104">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used with:</span></span>  
  
-   <span data-ttu-id="12559-105">Une application .NET</span><span class="sxs-lookup"><span data-stu-id="12559-105">A .NET application</span></span>  
  
-   <span data-ttu-id="12559-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12559-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
 <span data-ttu-id="12559-107">Selon la façon dont vous utilisez les adaptateurs, les logiciels requis varient.</span><span class="sxs-lookup"><span data-stu-id="12559-107">Based on how you use the adapters, the required software varies.</span></span>  
 
  
<a name="BKMK_prereq_NET"></a>   
## <a name="prerequisites-when-using-the-adapter-with-a-net-application"></a><span data-ttu-id="12559-108">Configuration requise lors de l’utilisation de la carte avec une Application .NET</span><span class="sxs-lookup"><span data-stu-id="12559-108">Prerequisites when using the adapter with a .NET Application</span></span>  
<span data-ttu-id="12559-109">Installer les logiciels suivants sur l’ordinateur sur lequel vous écrivez des applications .NET qui consomment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-109">Install the following software on the computer where you are writing .NET applications that consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="12559-110">Installez le logiciel dans l’ordre répertorié.</span><span class="sxs-lookup"><span data-stu-id="12559-110">Install the software in the order as listed.</span></span>  

||
|---|
|<span data-ttu-id="12559-111">-Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="12559-111">- Windows Server 2016</span></span> <br /><span data-ttu-id="12559-112">-Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="12559-112">- Windows Server 2012 R2</span></span> <br /><span data-ttu-id="12559-113">-Windows 10</span><span class="sxs-lookup"><span data-stu-id="12559-113">- Windows 10</span></span> <br /><span data-ttu-id="12559-114">-Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="12559-114">- Windows 8.1</span></span>    |
|<span data-ttu-id="12559-115">.NET Framework 4.6.*x*</span><span class="sxs-lookup"><span data-stu-id="12559-115">.NET Framework 4.6.*x*</span></span>|
|<span data-ttu-id="12559-116">Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="12559-116">Visual Studio 2015</span></span>|
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]|
|<span data-ttu-id="12559-117">Bibliothèques de client de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="12559-117">SQL Server client libraries.</span></span> <span data-ttu-id="12559-118">Consultez le [versions prises en charge](#BKMK_SuppLOB) (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="12559-118">See the [supported versions](#BKMK_SuppLOB) (in this topic).</span></span>|

<a name="BKMK_prereq_BTS"></a>     
## <a name="prerequisites-when-using-the-adapter-with-biztalk-server"></a><span data-ttu-id="12559-119">Configuration requise lors de l’utilisation de l’adaptateur avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="12559-119">Prerequisites when using the adapter with BizTalk Server</span></span>  
<span data-ttu-id="12559-120">Installer les logiciels suivants sur l’ordinateur où vous utilisez la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-120">Install the following software on the computer where you are using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="12559-121">Installer le logiciel dans l’ordre indiqué.</span><span class="sxs-lookup"><span data-stu-id="12559-121">Install the software in the order listed.</span></span>  

||
|---|
|<span data-ttu-id="12559-122">-Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="12559-122">- Windows Server 2016</span></span> <br /><span data-ttu-id="12559-123">-Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="12559-123">- Windows Server 2012 R2</span></span> <br /><span data-ttu-id="12559-124">-Windows 10</span><span class="sxs-lookup"><span data-stu-id="12559-124">- Windows 10</span></span> <br /><span data-ttu-id="12559-125">-Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="12559-125">- Windows 8.1</span></span>    |
|<span data-ttu-id="12559-126">.NET Framework 4.6.*x*</span><span class="sxs-lookup"><span data-stu-id="12559-126">.NET Framework 4.6.*x*</span></span>|
|<span data-ttu-id="12559-127">Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="12559-127">Visual Studio 2015</span></span>|
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> <span data-ttu-id="12559-128">Installer le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] inclus avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-128">Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="12559-129">Pour installer, procédez comme un **personnalisé** (sélectionnez **du complément de BizTalk Server**) ou **Complete** installation de le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-129">To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>|
|[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|
|<span data-ttu-id="12559-130">Bibliothèques de client de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="12559-130">SQL Server client libraries.</span></span> <span data-ttu-id="12559-131">Consultez le [versions prises en charge](#BKMK_SuppLOB) (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="12559-131">See the [supported versions](#BKMK_SuppLOB) (in this topic).</span></span>|

<a name="BKMK_SuppLOB"></a>   
## <a name="supported-sql-server-versions-and-client-libraries"></a><span data-ttu-id="12559-132">Les versions de SQL Server prises en charge et des bibliothèques clientes</span><span class="sxs-lookup"><span data-stu-id="12559-132">Supported SQL Server versions and client libraries</span></span>  
 <span data-ttu-id="12559-133">La section suivante présente les versions prises en charge de SQL Server et le client, les bibliothèques requises par les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-133">The following section presents the supported SQL Server versions and the client libraries required by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="12559-134">**Les versions de serveur prises en charge**: SQL Server 2016, SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="12559-134">**Supported server versions**: SQL Server 2016, SQL Server 2014</span></span>
  
-   <span data-ttu-id="12559-135">**Prise en charge des versions de client**: Microsoft [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)] offres groupées de la DLL du client requises pour se connecter à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="12559-135">**Supported client versions**: Microsoft [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)] bundles the client DLLs required to connect to SQL Server.</span></span> <span data-ttu-id="12559-136">Il est inutile d’installer explicitement n’importe quel client dll sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12559-136">You do not need to explicitly install any client DLLs on your computer.</span></span>  
  
-   <span data-ttu-id="12559-137">**Pilotes requis**:</span><span class="sxs-lookup"><span data-stu-id="12559-137">**Required drivers**:</span></span>  
  
    -   <span data-ttu-id="12559-138">Si vous utilisez les UDT fournis avec les versions de SQL Server, par exemple, géographie, assurez-vous que les DLL suivantes sont présentes sur l’ordinateur où vous utilisez l’adaptateur pour effectuer des opérations sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="12559-138">If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server.</span></span> <span data-ttu-id="12559-139">Par exemple, si vous créez des projets BizTalk pour effectuer des opérations sur SQL Server, ces DLL doit être présent sur l’ordinateur sur lequel BizTalk Server est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="12559-139">For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.</span></span>  
  
        -   <span data-ttu-id="12559-140">Assurez-vous que Microsoft.SqlServer.Types.dll est ajouté au GAC.</span><span class="sxs-lookup"><span data-stu-id="12559-140">Make sure Microsoft.SqlServer.Types.dll is added to the GAC.</span></span>  
  
        -   <span data-ttu-id="12559-141">Assurez-vous que SqlServerSpatial.dll est disponible dans le dossier System32.</span><span class="sxs-lookup"><span data-stu-id="12559-141">Make sure SqlServerSpatial.dll is available in the System32 folder.</span></span>  
  
         <span data-ttu-id="12559-142">Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="12559-142">You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.</span></span>  
  
    -   <span data-ttu-id="12559-143">Si vous utilisez l’adaptateur pour effectuer des opérations sur des colonnes de types de données FILESTREAM, assurez-vous que vous avez SQL Client Connectivity SDK est installé.</span><span class="sxs-lookup"><span data-stu-id="12559-143">If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="12559-144">Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="12559-144">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="12559-145">L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="12559-145">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  
  
    -   <span data-ttu-id="12559-146">Si vous créez votre propre UDT dans SQL Server, assurez-vous que les assemblys respectives pour les UDT sont ajoutés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="12559-146">If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.</span></span>  
  
<a name="BKMK_Compat"></a>   
## <a name="64-bit-support"></a><span data-ttu-id="12559-147">prise en charge 64 bits</span><span class="sxs-lookup"><span data-stu-id="12559-147">64-bit support</span></span> 

<span data-ttu-id="12559-148">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut s’exécuter dans une instance d’hôte 32 bits ou 64 bits.</span><span class="sxs-lookup"><span data-stu-id="12559-148">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can run in a 32-bit or 64-bit host instance.</span></span>

 <span data-ttu-id="12559-149">Pour plus d’informations sur les scénarios d’installation pris en charge pour les 32 bits et 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [32 bits et 64 bits de scénarios installent](#BKMK_Install_Scenarios) (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="12559-149">For information about the supported installation scenarios for the 32-bit and 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see  [32-bit and 64-bit install scenarios](#BKMK_Install_Scenarios) (in this topic).</span></span>
  
<a name="BKMK_Install_Adap"></a>   
## <a name="install-the-sql-adapter"></a><span data-ttu-id="12559-150">Installer l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="12559-150">Install the SQL adapter</span></span>  
 <span data-ttu-id="12559-151">Assurez-vous que vous avez les composants requis installés avant d’installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-151">Make sure you have the prerequisites installed before installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="12559-152">Consultez [.NET prerequisites](#BKMK_prereq_NET) (dans cette rubrique), ou [conditions préalables de BizTalk Server](#BKMK_prereq_BTS) (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="12559-152">See [.NET prerequisites](#BKMK_prereq_NET) (in this topic), or [BizTalk Server prerequisites](#BKMK_prereq_BTS) (in this topic).</span></span>
  
 <span data-ttu-id="12559-153">Vous pouvez installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="12559-153">You can install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="12559-154">**En mode interactif** à l’aide de l’Assistant Installation</span><span class="sxs-lookup"><span data-stu-id="12559-154">**In interactive mode** using the setup wizard</span></span>
  
-   <span data-ttu-id="12559-155">**En mode silencieux** à l’aide de msiexec dans la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="12559-155">**In silent mode** using msiexec in the command line</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="12559-156">Vous devez disposer des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], indépendamment de si vous installez à l’aide de l’Assistant ou la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="12559-156">You must have administrative privileges on the computer where you install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], irrespective of whether you are installing by using the wizard or the command line.</span></span>    

### <span data-ttu-id="12559-157"><a name="BKMK_Install_Scenarios"></a>scénarios d’installation de 32 bits et 64 bits</span><span class="sxs-lookup"><span data-stu-id="12559-157"><a name="BKMK_Install_Scenarios"></a> 32-bit and 64-bit install scenarios</span></span>
 <span data-ttu-id="12559-158">Avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé pour :</span><span class="sxs-lookup"><span data-stu-id="12559-158">With [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used for:</span></span>  
  
-   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="12559-159">au moment du design (lors de la génération des métadonnées pour les opérations).</span><span class="sxs-lookup"><span data-stu-id="12559-159"> design time (when generating metadata for operations).</span></span>  
  
-   <span data-ttu-id="12559-160">Moment du design de console Administration de BizTalk Server (pour créer des ports physiques).</span><span class="sxs-lookup"><span data-stu-id="12559-160">BizTalk Server Administration console design time (for creating physical ports).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-161">Console d’Administration de BizTalk Server s’exécute comme une application de la Console MMC (Microsoft Management Console) 32 bits.</span><span class="sxs-lookup"><span data-stu-id="12559-161">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  
  
-   <span data-ttu-id="12559-162">Durée d’exécution BizTalk (pendant l’envoi et réception de messages à partir d’applications métier).</span><span class="sxs-lookup"><span data-stu-id="12559-162">BizTalk run time (when sending and receiving messages from LOB applications).</span></span>  
  
 <span data-ttu-id="12559-163">Vous pouvez avoir une installation où vous effectuez toutes ces tâches sur le même ordinateur ou sur des ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="12559-163">You can have an installation where you perform all these tasks on the same computer or different computers.</span></span> <span data-ttu-id="12559-164">Étant donné que les deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et MMC de BizTalk sont des processus 32 bits, vous devez installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur l’ordinateur où vous souhaitez effectuer les tâches au moment du design.</span><span class="sxs-lookup"><span data-stu-id="12559-164">Because both [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on the computer where you want to perform the design-time tasks.</span></span> <span data-ttu-id="12559-165">Les scénarios suivants sont pris en charge pour l’installation de le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur les plateformes 32 bits et 64 bits.</span><span class="sxs-lookup"><span data-stu-id="12559-165">The following scenarios are supported for installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on 32-bit and 64-bit platforms.</span></span>  
  
#### <a name="32-bit-install-scenarios"></a><span data-ttu-id="12559-166">scénarios d’installation 32 bits</span><span class="sxs-lookup"><span data-stu-id="12559-166">32-bit install scenarios</span></span>  
 <span data-ttu-id="12559-167">Les scénarios suivants sont pris en charge lors de l’installation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur une plateforme 32 bits.</span><span class="sxs-lookup"><span data-stu-id="12559-167">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 32-bit platform.</span></span>  
  
|<span data-ttu-id="12559-168">Conception de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="12559-168">Visual Studio design time</span></span>|<span data-ttu-id="12559-169">Moment du design MMC de BizTalk</span><span class="sxs-lookup"><span data-stu-id="12559-169">BizTalk MMC design time</span></span>|<span data-ttu-id="12559-170">Durée d’exécution de BizTalk</span><span class="sxs-lookup"><span data-stu-id="12559-170">BizTalk run time</span></span>|<span data-ttu-id="12559-171">Durée d’exécution Visual moment du design Studio et/ou de conception BizTalk MMC + BizTalk</span><span class="sxs-lookup"><span data-stu-id="12559-171">Visual Studio design time and/or  BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="12559-172">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-172">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-173">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-173">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-174">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-174">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="12559-175">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-175">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-176">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-176">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-177">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-177">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="12559-178">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-178">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-179">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-179">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-180">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-180">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="12559-181">-Installer 32 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-181">- Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-182">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-182">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-183">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-183">- Install 32-bit client and other required DLLs.</span></span>|  
  
#### <a name="64-bit-install-scenarios"></a><span data-ttu-id="12559-184">scénarios d’installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="12559-184">64-bit install scenarios</span></span>  
 <span data-ttu-id="12559-185">Les scénarios suivants sont pris en charge lors de l’installation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur une plateforme 64 bits.</span><span class="sxs-lookup"><span data-stu-id="12559-185">The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 64-bit platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12559-186">Sur n’importe quel ordinateur où vous souhaitez effectuer des tâches au moment du design à l’aide [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou MMC de BizTalk, vous devez installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-186">On any computer where you want to perform design-time tasks using either [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
|<span data-ttu-id="12559-187">Conception de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="12559-187">Visual Studio design time</span></span>|<span data-ttu-id="12559-188">Moment du design MMC de BizTalk</span><span class="sxs-lookup"><span data-stu-id="12559-188">BizTalk MMC design time</span></span>|<span data-ttu-id="12559-189">Durée d’exécution de BizTalk</span><span class="sxs-lookup"><span data-stu-id="12559-189">BizTalk run time</span></span>|<span data-ttu-id="12559-190">Durée d’exécution Visual moment du design Studio et/ou de conception BizTalk MMC + BizTalk</span><span class="sxs-lookup"><span data-stu-id="12559-190">Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="12559-191">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-191">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-192">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-192">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-193">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-193">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="12559-194">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-194">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-195">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-195">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-196">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-196">- Install 32-bit client and other required DLLs.</span></span>|<span data-ttu-id="12559-197">**Pour un processus de BizTalk 32 bits**:</span><span class="sxs-lookup"><span data-stu-id="12559-197">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="12559-198">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-198">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-199">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-199">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-200">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-200">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="12559-201">**Pour un processus BizTalk de 64 bits**:</span><span class="sxs-lookup"><span data-stu-id="12559-201">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="12559-202">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-202">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-203">-Installer 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-203">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-204">-Installez des clients 64 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-204">- Install 64-bit client and other required DLLs.</span></span>|<span data-ttu-id="12559-205">**Pour un processus de BizTalk 32 bits**:</span><span class="sxs-lookup"><span data-stu-id="12559-205">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="12559-206">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-206">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-207">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-207">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-208">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-208">- Install 32-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="12559-209">**Pour un processus BizTalk de 64 bits**:</span><span class="sxs-lookup"><span data-stu-id="12559-209">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="12559-210">-Installer 64 bits [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-210">- Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-211">-Installer 64 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-211">- Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-212">-Installez des clients 64 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-212">- Install 64-bit client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="12559-213">-Installer 32 bits [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-213">- Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span><br /><br /> <span data-ttu-id="12559-214">-Installer les clients 32 bits et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="12559-214">- Install 32-bit client and other required DLLs.</span></span>|  
  
<a name="BKMK_Install_wizard"></a>   
### <a name="install-the-adapter-in-interactive-mode"></a><span data-ttu-id="12559-215">Installer l’adaptateur en mode interactif</span><span class="sxs-lookup"><span data-stu-id="12559-215">Install the adapter in interactive mode</span></span>  
<span data-ttu-id="12559-216">Effectuez les étapes suivantes pour installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="12559-216">Complete the following steps to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the setup wizard.</span></span>  
  
1.  <span data-ttu-id="12559-217">Exécutez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="12559-217">Run the installer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-218">Si vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur un ordinateur virtuel, l’Assistant installation ne peut pas continuer au-delà d’une boîte de dialogue informant que la vérification de l’espace disque disponible.</span><span class="sxs-lookup"><span data-stu-id="12559-218">If you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space.</span></span> <span data-ttu-id="12559-219">Dans ce cas, nous vous recommandons d’utiliser l’option d’installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="12559-219">In such cases, we recommend that you use the silent installation option.</span></span> <span data-ttu-id="12559-220">Pour plus d’informations, consultez [installer l’adaptateur SQL en mode silencieux](#BKMK_SilentInst) (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="12559-220">For more information, see [Install the SQL adapter in silent mode](#BKMK_SilentInst) (in this topic).</span></span>
  
2.  <span data-ttu-id="12559-221">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="12559-221">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="12559-222">Lisez et acceptez le contrat de licence utilisateur final (CLUF), puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="12559-222">Read and accept the end-user license agreement (EULA), and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="12559-223">Dans le **dossier de Destination** boîte de dialogue, spécifiez l’emplacement où vous souhaitez installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], cliquez sur **suivant**, puis cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="12559-223">In the **Destination Folder** dialog box, specify the location where you want to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], click **Next**, and then click **Install**.</span></span>  
  
5.  <span data-ttu-id="12559-224">Dans le **Customer Experience Improvement Program** boîte de dialogue, spécifiez si vous souhaitez inscrire pour le programme (amélioration).</span><span class="sxs-lookup"><span data-stu-id="12559-224">In the **Customer Experience Improvement Program** dialog box, specify whether you would like to enroll for the Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="12559-225">Dans le cadre de ce programme pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous allez partager les données suivantes avec Microsoft :</span><span class="sxs-lookup"><span data-stu-id="12559-225">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="12559-226">Les données relatives au matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-226">Data related to the computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    -   <span data-ttu-id="12559-227">Les données relatives à des versions de SQL Server que vous utilisez pour vous connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-227">Data related to the SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="12559-228">Spécifiez votre choix et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="12559-228">Specify your choice and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-229">Vous pouvez toujours modifier vos préférences concernant l’inscription pour CEIP en exécutant le programme d’installation en mode réparation à partir du panneau.</span><span class="sxs-lookup"><span data-stu-id="12559-229">You can always change your preference regarding enrolling for CEIP by running the Setup in Repair mode from the Control Panel.</span></span>  
  
6.  <span data-ttu-id="12559-230">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="12559-230">Click **Finish**.</span></span>  
  
<a name="BKMK_SilentInst"></a>   
### <a name="install-the-sql-adapter-in-silent-mode"></a><span data-ttu-id="12559-231">Installer l’adaptateur SQL en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="12559-231">Install the SQL adapter in silent mode</span></span> 
<span data-ttu-id="12559-232">Effectuez les étapes suivantes pour effectuer une installation sans assistance de [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de la `msiexec` commande.</span><span class="sxs-lookup"><span data-stu-id="12559-232">Complete the following steps to do a silent installation of [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the `msiexec` command.</span></span>  
  
1.  <span data-ttu-id="12559-233">Ouvrez une invite de commandes et accédez au dossier où vous avez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="12559-233">Open a command prompt, and navigate to the folder where you have the installer.</span></span>  
  
2.  <span data-ttu-id="12559-234">Exécutez la commande suivante pour installer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="12559-234">Run the following command to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-235">Pour effectuer une installation sans assistance sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi SqlAdapterSetup64.msi.</span><span class="sxs-lookup"><span data-stu-id="12559-235">To perform silent installation on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn  
    ```  
  
     <span data-ttu-id="12559-236">Vous pouvez également choisir d’inscrire pour CEIP dans le cadre de l’installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="12559-236">You can also choose to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="12559-237">Dans le cadre de ce programme pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous allez partager les données suivantes avec Microsoft :</span><span class="sxs-lookup"><span data-stu-id="12559-237">As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="12559-238">Le matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-238">The computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    -   <span data-ttu-id="12559-239">Les versions de SQL Server que vous utilisez pour vous connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-239">The SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="12559-240">Pour vous inscrire pour CEIP, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="12559-240">To enroll for CEIP, run the following command:</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
    ```  
  
     <span data-ttu-id="12559-241">Par défaut, l’option a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="12559-241">By default, the option is false.</span></span>  
  
     <span data-ttu-id="12559-242">Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span><span class="sxs-lookup"><span data-stu-id="12559-242">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_PostInst"></a>   
## <a name="post-installation-tasks"></a><span data-ttu-id="12559-243">Tâches de post-installation</span><span class="sxs-lookup"><span data-stu-id="12559-243">Post-installation tasks</span></span>  
  
<a name="BKMK_Register_Bindings"></a>   
#### <a name="register-the-bindings"></a><span data-ttu-id="12559-244">Inscrire les liaisons</span><span class="sxs-lookup"><span data-stu-id="12559-244">Register the bindings</span></span>  
<span data-ttu-id="12559-245">Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à inscrire des liaisons de l’adaptateur dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="12559-245">Complete these steps *only* if the setup wizard fails to register the adapter bindings in the machine.config file.</span></span>  
  
1.  <span data-ttu-id="12559-246">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12559-246">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="12559-247">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="12559-247">For example, on a 32-bit platform, the machine.config is available under \<system drive>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
2.  <span data-ttu-id="12559-248">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="12559-248">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="12559-249">Pour enregistrer des liaisons de l’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="12559-249">To register the adapter bindings:</span></span>  
  
    1.  <span data-ttu-id="12559-250">Recherchez l’élément « system.serviceModel » et ajoutez le code suivant dans cette section :</span><span class="sxs-lookup"><span data-stu-id="12559-250">Search for the element "system.serviceModel" and add the following under it:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
        ```  
  
    2.  <span data-ttu-id="12559-251">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="12559-251">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="12559-252">Ajoutez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="12559-252">Add the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="12559-253">Pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="12559-253">For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="12559-254">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="12559-254">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="12559-255">Ajoutez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="12559-255">Add the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="12559-256">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ajoutez :</span><span class="sxs-lookup"><span data-stu-id="12559-256">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-257">Pour plus d’informations sur la façon de déterminer la clé publique, consultez [détermination de la clé publique et la Version](#BKMK_PubKey).</span><span class="sxs-lookup"><span data-stu-id="12559-257">For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).</span></span>  
  
4.  <span data-ttu-id="12559-258">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="12559-258">Save and close the machine.config file.</span></span>  
  
<a name="BKMK_PubKey"></a>   
#### <a name="determining-the-public-key-and-version"></a><span data-ttu-id="12559-259">Détermination de la clé publique et la Version</span><span class="sxs-lookup"><span data-stu-id="12559-259">Determining the Public Key and Version</span></span>  
<span data-ttu-id="12559-260">Effectuez les étapes suivantes pour déterminer la clé publique et la version pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-260">Complete the following steps to determine the public key and version for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="12559-261">Accédez au répertoire Windows, généralement C:\WINDOWS\assembly.</span><span class="sxs-lookup"><span data-stu-id="12559-261">Navigate to the Windows directory, typically C:\WINDOWS\assembly.</span></span>  
  
2.  <span data-ttu-id="12559-262">Avec le bouton droit de la DLL pour laquelle vous souhaitez que la clé publique, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="12559-262">Right-click the DLL for which you want the public key, and then select **Properties**.</span></span> <span data-ttu-id="12559-263">Le tableau suivant répertorie le nom des DLL pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-263">The following table lists the name of the DLLs for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
    |<span data-ttu-id="12559-264">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="12559-264">Adapter</span></span>|<span data-ttu-id="12559-265">Nom de la DLL</span><span class="sxs-lookup"><span data-stu-id="12559-265">Name of the DLL</span></span>|  
    |---|---|  
    |[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]|<span data-ttu-id="12559-266">Microsoft.Adapters.Sql.dll</span><span class="sxs-lookup"><span data-stu-id="12559-266">Microsoft.Adapters.Sql.dll</span></span>|  
  
3.  <span data-ttu-id="12559-267">Sur le **général** onglet, la valeur par rapport à la **jeton de clé publique** étiquette spécifie la clé publique pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="12559-267">On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL.</span></span> <span data-ttu-id="12559-268">De même, la valeur par rapport à la **Version** étiquette Spécifie le numéro de version de la DLL.</span><span class="sxs-lookup"><span data-stu-id="12559-268">Similarly, the value against the **Version** label specifies the version number for the DLL.</span></span>  
  
4.  <span data-ttu-id="12559-269">Copiez la clé publique, puis cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="12559-269">Copy the public key, and then click **Cancel**.</span></span>  
  
<a name="BKMK_Modify_Adap"></a>   
## <a name="update-or-change-the-sql-adapter-installation"></a><span data-ttu-id="12559-270">Mettre à jour ou de modifier l’installation de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="12559-270">Update or change the SQL adapter installation</span></span>  
 <span data-ttu-id="12559-271">Procédez comme suit pour modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="12559-271">Perform the following steps to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span> <span data-ttu-id="12559-272">Assurez-vous que vous avez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installé avant d’exécuter l’Assistant Installation pour modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="12559-272">Make sure you have the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.</span></span>  
  
 <span data-ttu-id="12559-273">Vous pouvez modifier le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="12559-273">You can modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the following two ways:</span></span>  
  
-   <span data-ttu-id="12559-274">**En mode interactif** en exécutant l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="12559-274">**In interactive mode** by running the setup wizard.</span></span>  
  
-   <span data-ttu-id="12559-275">**En mode silencieux** à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="12559-275">**In silent mode** by using the command line.</span></span>  
  
#### <a name="update-the-sql-adapter-installation-in-interactive-mode"></a><span data-ttu-id="12559-276">Mise à jour de l’installation de l’adaptateur SQL en mode interactif</span><span class="sxs-lookup"><span data-stu-id="12559-276">Update the SQL Adapter installation in interactive mode</span></span>  
  
1.  <span data-ttu-id="12559-277">Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="12559-277">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="12559-278">Dans le panneau de configuration, double-cliquez sur **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="12559-278">In Control Panel, double-click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="12559-279">Dans le **programmes et fonctionnalités** fenêtre, sélectionnez **l’adaptateur Microsoft BizTalk pour SQL Server**, puis cliquez sur **modification**.</span><span class="sxs-lookup"><span data-stu-id="12559-279">In the **Programs and Features** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Change**.</span></span>  
  
4.  <span data-ttu-id="12559-280">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="12559-280">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="12559-281">Dans le **modifier, réparer ou supprimer l’installation** boîte de dialogue, cliquez sur **réparer**.</span><span class="sxs-lookup"><span data-stu-id="12559-281">In the **Change, repair, or remove installation** dialog box, click **Repair**.</span></span>  
  
6.  <span data-ttu-id="12559-282">Dans le **prêt à réparer l’adaptateur Microsoft BizTalk pour SQL Server** boîte de dialogue, cliquez sur **réparer**.</span><span class="sxs-lookup"><span data-stu-id="12559-282">In the **Ready to repair Microsoft BizTalk Adapter for SQL Server** dialog box, click **Repair**.</span></span>  
  
7.  <span data-ttu-id="12559-283">Si nécessaire, modifiez vos préférences concernant le choix d’amélioration du produit, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="12559-283">If required, change your preferences regarding opting for CEIP, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="12559-284">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="12559-284">Click **Finish**.</span></span>  
  
#### <a name="update-the-sql-adapter-installation-in-silent-mode"></a><span data-ttu-id="12559-285">Mise à jour de l’installation de l’adaptateur SQL en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="12559-285">Update the SQL Adapter installation in silent mode</span></span>  
  
1.  <span data-ttu-id="12559-286">Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="12559-286">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="12559-287">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="12559-287">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-288">Pour modifier la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi par SqlAdapterSetup64.msi.</span><span class="sxs-lookup"><span data-stu-id="12559-288">To modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /i SqlAdapterSetup.msi /qn /f  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="12559-289">Lors de la modification du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation en mode silencieux, vous ne pouvez pas modifier vos préférences pour vous inscrire ou de refuser le CEIP.</span><span class="sxs-lookup"><span data-stu-id="12559-289">While modifying the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="12559-290">Les préférences reste le même que vous avez spécifié pendant l’installation, même si vous définissez explicitement la CEIP_OPTIN à true ou false.</span><span class="sxs-lookup"><span data-stu-id="12559-290">The preferences will remain the same as you specified during the installation, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  
  
     <span data-ttu-id="12559-291">Pour plus d’informations sur la `msiexec` type de commande `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span><span class="sxs-lookup"><span data-stu-id="12559-291">For more information about the `msiexec` command type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_Remove_Adap"></a>   
## <a name="uninstall-or-remove-the-sql-adapter"></a><span data-ttu-id="12559-292">Désinstaller ou supprimer l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="12559-292">Uninstall or remove the SQL Adapter</span></span>  
 <span data-ttu-id="12559-293">Procédez comme suit pour supprimer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à partir de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12559-293">Perform the following steps to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from your computer.</span></span> <span data-ttu-id="12559-294">Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant Installation pour supprimer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-294">Make sure you have the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="12559-295">Vous pouvez supprimer la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="12559-295">You can remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="12559-296">**En mode interactif** en exécutant l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="12559-296">**In interactive mode** by running the setup wizard.</span></span>  
  
-   <span data-ttu-id="12559-297">**En mode silencieux** à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="12559-297">**In silent mode** by using the command line.</span></span>  
  
#### <a name="uninstall-the-sql-adapter-in-interactive-mode"></a><span data-ttu-id="12559-298">Désinstaller l’adaptateur SQL en mode interactif</span><span class="sxs-lookup"><span data-stu-id="12559-298">Uninstall the SQL Adapter in interactive mode</span></span>  
  
1.  <span data-ttu-id="12559-299">Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="12559-299">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="12559-300">Dans le panneau de configuration, double-cliquez sur **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="12559-300">In Control Panel, double-click  **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="12559-301">Dans le **Ajout / Suppression de programmes** fenêtre, sélectionnez **l’adaptateur Microsoft BizTalk pour SQL Server**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="12559-301">In the **Add or Remove Programs** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Remove**.</span></span>  
  
4.  <span data-ttu-id="12559-302">Dans la boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="12559-302">In the dialog box, click **Yes**.</span></span>  
  
#### <a name="uninstall-the-sql-adapter-in-silent-mode"></a><span data-ttu-id="12559-303">Désinstaller l’adaptateur SQL en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="12559-303">Uninstall the SQL Adapter in silent mode</span></span>  
  
1.  <span data-ttu-id="12559-304">Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="12559-304">Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="12559-305">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="12559-305">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12559-306">Pour supprimer la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez SqlAdapterSetup.msi par SqlAdapterSetup64.msi.</span><span class="sxs-lookup"><span data-stu-id="12559-306">To remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.</span></span>  
  
    ```  
    msiexec /x SqlAdapterSetup.msi /qn  
    ```  
  
     <span data-ttu-id="12559-307">Cette commande supprime le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à partir de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12559-307">This command removes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from the computer.</span></span>  
  
     <span data-ttu-id="12559-308">Pour plus d’informations sur la `msiexec` de commandes, tapez `msiexec` sur la ligne de commande et appuyez sur `ENTER`, ou consultez [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span><span class="sxs-lookup"><span data-stu-id="12559-308">For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).</span></span>  
  
<a name="BKMK_PostRemove"></a>   
### <a name="post-uninstall-task"></a><span data-ttu-id="12559-309">Tâche post-désinstallation</span><span class="sxs-lookup"><span data-stu-id="12559-309">Post-uninstall task</span></span>  
 <span data-ttu-id="12559-310">Si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] le programme d’installation ne parvient pas à supprimer les liaisons de l’adaptateur lors de la suppression du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez les supprimer manuellement.</span><span class="sxs-lookup"><span data-stu-id="12559-310">If the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] setup fails to remove the adapter bindings while removing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must remove them manually.</span></span> <span data-ttu-id="12559-311">La section suivante décrit comment supprimer manuellement les liaisons pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12559-311">The following section describes how to manually remove the bindings for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
<span data-ttu-id="12559-312">Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à supprimer les liaisons de l’adaptateur à partir du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="12559-312">Complete these steps *only* if the setup wizard fails to remove the adapter bindings from the machine.config file.</span></span>  
  
1.  <span data-ttu-id="12559-313">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12559-313">Navigate to the machine.config file on the computer.</span></span> <span data-ttu-id="12559-314">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="12559-314">For example, on a 32-bit platform, the machine.config is available under \<system drive>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    -   <span data-ttu-id="12559-315">Pour Microsoft .NET Framework 3.5 SP1, \< *version*> est le v2.0.50727 version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12559-315">For Microsoft .NET Framework 3.5 SP1, \<*version*> is the version v2.0.50727 of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="12559-316">Pour Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \< *version*> est le v4.0.30319 de version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12559-316">For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*> is the version v4.0.30319 of the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="12559-317">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="12559-317">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="12559-318">Pour supprimer l’inscription de la liaison de la carte :</span><span class="sxs-lookup"><span data-stu-id="12559-318">To remove the adapter binding registration:</span></span>  
  
    1.  <span data-ttu-id="12559-319">Recherchez l’élément « system.serviceModel » et supprimer les éléments suivants figurant dans l’élément :</span><span class="sxs-lookup"><span data-stu-id="12559-319">Search for the element "system.serviceModel" and remove the following from under the element:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  <span data-ttu-id="12559-320">Recherchez l’élément « bindingElementExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="12559-320">Search for the element "bindingElementExtensions" under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="12559-321">Supprimez la section suivante sous le nœud « bindingElementExtensions ».</span><span class="sxs-lookup"><span data-stu-id="12559-321">Remove the following section under the "bindingElementExtensions" node.</span></span>  
  
         <span data-ttu-id="12559-322">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="12559-322">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="12559-323">Recherchez l’élément « bindingExtensions » sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="12559-323">Search for the element "bindingExtensions" under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="12559-324">Supprimez la section suivante sous le nœud « bindingExtensions ».</span><span class="sxs-lookup"><span data-stu-id="12559-324">Remove the following section under the "bindingExtensions" node.</span></span>  
  
         <span data-ttu-id="12559-325">Pour [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="12559-325">For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  <span data-ttu-id="12559-326">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="12559-326">Save and close the machine.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12559-327">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12559-327">See also</span></span>
[<span data-ttu-id="12559-328">Installer l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="12559-328">Install the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[<span data-ttu-id="12559-329">Comprendre l’adaptateur BizTalk pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="12559-329">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)