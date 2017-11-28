---
title: "Problèmes connus de l’Installation, la Configuration et déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1c08eb-d647-4a4a-b9a3-c4d84e8d4b82
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda1bd5c8167bbf9f6049b3620c0c949950b1e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-in-installation-configuration-and-deployment"></a><span data-ttu-id="19ceb-102">Problèmes connus rencontrés lors de l'installation, de la configuration et du déploiement</span><span class="sxs-lookup"><span data-stu-id="19ceb-102">Known Issues in Installation, Configuration, and Deployment</span></span>
## <a name="some-biztalk-edias2-artifacts-are-still-active-after-unconfiguring"></a><span data-ttu-id="19ceb-103">Certains artefacts d'EDI/AS2 BizTalk sont toujours actifs après annulation de la configuration</span><span class="sxs-lookup"><span data-stu-id="19ceb-103">Some BizTalk EDI/AS2 Artifacts Are Still Active After Unconfiguring</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="19ceb-104">Problem (Problème)</span><span class="sxs-lookup"><span data-stu-id="19ceb-104">Problem</span></span>  
 <span data-ttu-id="19ceb-105">Après que vous avez annulé la configuration de la fonction EDI/AS2 BizTalk de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], certains artefacts de BizTalk Server liés au traitement EDI et AS2 restent actifs dans le contexte de la configuration de groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="19ceb-105">After you unconfigure the BizTalk EDI/AS2 feature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some BizTalk Server artifacts related to EDI and AS2 processing will still be active in the context of the BizTalk group configuration.</span></span> <span data-ttu-id="19ceb-106">Ces derniers incluent des pipelines EDI et AS2 ainsi que l'orchestration du traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="19ceb-106">These artifacts will include EDI and AS2 pipelines and the batching orchestration.</span></span> <span data-ttu-id="19ceb-107">Vous pouvez donc continuer à effectuer un traitement EDI et AS2 de base, même après avoir annulé la configuration de la fonction EDI/AS2 BizTalk.</span><span class="sxs-lookup"><span data-stu-id="19ceb-107">As a result, you will still be able to perform basic EDI and AS2 processing even after unconfiguring the BizTalk EDI/AS2 feature.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="19ceb-108">Cause</span><span class="sxs-lookup"><span data-stu-id="19ceb-108">Cause</span></span>  
 <span data-ttu-id="19ceb-109">Il y a des ports actifs associés au traitement EDI et AS2.</span><span class="sxs-lookup"><span data-stu-id="19ceb-109">There are active ports associated with EDI and AS2 processing.</span></span> <span data-ttu-id="19ceb-110">Certains artefacts continuent de fonctionner tandis que ces ports restent actifs.</span><span class="sxs-lookup"><span data-stu-id="19ceb-110">Some artifacts will continue to function while these ports remain active.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="19ceb-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="19ceb-111">Resolution</span></span>  
 <span data-ttu-id="19ceb-112">Pour désactiver tous les artefacts EDI/AS2, vous devez désactiver, arrêter ou supprimer les ports associés au traitement EDI et AS2.</span><span class="sxs-lookup"><span data-stu-id="19ceb-112">To disable all EDI/AS2 artifacts, you should disable, stop, or delete the ports associated with EDI and AS2 processing.</span></span>  
  
## <a name="if-the-biztalk-server-computer-or-sql-server-computer-is-renamed-after-biztalk-server-configuration-the-configuration-wizard-will-fail"></a><span data-ttu-id="19ceb-113">Si l’ordinateur BizTalk Server ou l’ordinateur SQL Server est renommé après la configuration de BizTalk Server, l’Assistant Configuration échoue</span><span class="sxs-lookup"><span data-stu-id="19ceb-113">If the BizTalk Server Computer or SQL Server Computer Is Renamed After BizTalk Server Configuration, the Configuration Wizard Will Fail</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="19ceb-114">Problem (Problème)</span><span class="sxs-lookup"><span data-stu-id="19ceb-114">Problem</span></span>  
 <span data-ttu-id="19ceb-115">Ce problème peut se manifester de différentes manières :</span><span class="sxs-lookup"><span data-stu-id="19ceb-115">This problem may manifest itself in several ways:</span></span>  
  
-   <span data-ttu-id="19ceb-116">La configuration de BizTalk Server charge la page Vue d'ensemble correctement, mais lorsqu'il tente de configurer une fonctionnalité, les options associées ne s'affichent pas à l'écran.</span><span class="sxs-lookup"><span data-stu-id="19ceb-116">The BizTalk Server Configuration will load the Overview page correctly, but when attempting to configure a feature the feature options do not display on the screen.</span></span>  
  
-   <span data-ttu-id="19ceb-117">L'Assistant Configuration ne peut pas se connecter au serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19ceb-117">The configuration wizard cannot connect to the SQL Server.</span></span>  
  
-   <span data-ttu-id="19ceb-118">Les tentatives d'annulation de la configuration opèrent sur certaines fonctionnalités, mais pas sur toutes.</span><span class="sxs-lookup"><span data-stu-id="19ceb-118">Attempting to Unconfigure All unconfigures some features, but not all.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="19ceb-119">Cause</span><span class="sxs-lookup"><span data-stu-id="19ceb-119">Cause</span></span>  
 <span data-ttu-id="19ceb-120">La configuration de BizTalk Server stocke le nom de réseau de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="19ceb-120">The BizTalk Server configuration stores the computer network name.</span></span> <span data-ttu-id="19ceb-121">Lorsque l'ordinateur est renommé, la configuration de BizTalk Server et l'Assistant Configuration ne peuvent pas localiser le serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="19ceb-121">When the computer is renamed the BizTalk Server Configuration and configuration wizard cannot locate the BizTalk Server.</span></span> <span data-ttu-id="19ceb-122">Un problème semblable se produit si l'ordinateur SQL Server est renommé après la configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="19ceb-122">A similar problem will occur if the SQL Server computer is renamed after BizTalk Server is configured.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="19ceb-123">Résolution</span><span class="sxs-lookup"><span data-stu-id="19ceb-123">Resolution</span></span>  
 <span data-ttu-id="19ceb-124">Ne renommez pas l'ordinateur BizTalk Server ou l'ordinateur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19ceb-124">Do not rename the BizTalk Server computer or the SQL Server computer.</span></span> <span data-ttu-id="19ceb-125">Si un serveur doit être renommé, annulez la configuration des fonctionnalités de BizTalk avant de renommer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="19ceb-125">If a server must be renamed, unconfigure all BizTalk Features before renaming the computer.</span></span> <span data-ttu-id="19ceb-126">Une fois l'ordinateur renommé, reconfigurez les fonctionnalités de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="19ceb-126">After renaming the computer, reconfigure BizTalk Server features.</span></span>  
  
## <a name="the-biztalk-server-business-rules-configuration-wizard-fails"></a><span data-ttu-id="19ceb-127">Échec de l’Assistant Configuration des règles d’entreprises de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="19ceb-127">The BizTalk Server Business Rules Configuration Wizard Fails</span></span>  
  
### <a name="problem"></a><span data-ttu-id="19ceb-128">Problem (Problème)</span><span class="sxs-lookup"><span data-stu-id="19ceb-128">Problem</span></span>  
  
-   <span data-ttu-id="19ceb-129">L'Assistant Configuration des règles d'entreprise échoue avec l'erreur « La configuration a échoué pour certains composants et aucun paramètre n'a été appliqué pour ces composants ».</span><span class="sxs-lookup"><span data-stu-id="19ceb-129">The Business Rules Configuration Wizard fails with the error “Configuration failed for some components and no settings were applied for those components”.</span></span>  
  
-   <span data-ttu-id="19ceb-130">Sur les ordinateurs BizTalk Server pour lesquels le moteur de règles d'entreprise a déjà été configuré, le service de mise à jour du moteur de règles ne parvient pas à démarrer et ne peut pas être démarré manuellement.</span><span class="sxs-lookup"><span data-stu-id="19ceb-130">On BizTalk Server computers for which the Business Rules Engine has already been successfully configured, the Rules Engine Update service fails to start and cannot be started manually.</span></span>  
  
 <span data-ttu-id="19ceb-131">Lorsque ce problème se produit, une erreur similaire à ce qui suit peut être générée dans le journal de l'application de l'ordinateur BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="19ceb-131">When this problem occurs, an error similar to the following may be generated in the BizTalk Server computer Application log:</span></span>  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
### <a name="cause"></a><span data-ttu-id="19ceb-132">Cause</span><span class="sxs-lookup"><span data-stu-id="19ceb-132">Cause</span></span>  
 <span data-ttu-id="19ceb-133">Le Centre de protection Microsoft contre les programmes malveillants a publié un fichier de signature qui permet de se prémunir contre une menace possible de SettingsModifier:Win32/PossibleHostsFileHijack.</span><span class="sxs-lookup"><span data-stu-id="19ceb-133">The Microsoft Malware Protection Center released an updated signature file to address a possible threat from SettingsModifier:Win32/PossibleHostsFileHijack.</span></span> <span data-ttu-id="19ceb-134">Ce fichier de signature mis à jour peut entraîner la mise à jour du fichier HOSTS local par les logiciels Microsoft de détection des programmes malveillants tels que Windows Defender en vue d'atténuer la menace de SettingsModifier:Win32/PossibleHostsFileHijack.</span><span class="sxs-lookup"><span data-stu-id="19ceb-134">This updated signature file can cause Microsoft Malware Detection software such as Windows Defender to update the local HOSTS file to mitigate threats from SettingsModifier:Win32/PossibleHostsFileHijack.</span></span> <span data-ttu-id="19ceb-135">Ces modifications peuvent empêcher le démarrage du service de mise à jour du moteur de règles BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="19ceb-135">As a result of these changes, the BizTalk Server Rules Engine Update service may fail to start.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="19ceb-136">Résolution</span><span class="sxs-lookup"><span data-stu-id="19ceb-136">Resolution</span></span>  
 <span data-ttu-id="19ceb-137">Mettez à jour le fichier HOSTS local pour inclure la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="19ceb-137">Update the local HOSTS file to include the following line:</span></span>  
  
```  
127.0.0.1         localhost  
```  
  
 <span data-ttu-id="19ceb-138">Le fichier HOSTS se trouve dans le répertoire %systemroot%\drivers\etc\.</span><span class="sxs-lookup"><span data-stu-id="19ceb-138">The HOSTS file is located in the %systemroot%\drivers\etc\ directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19ceb-139">Pour plus d’informations sur la mise à jour des signatures du Centre de protection Microsoft contre les programmes malveillants en vue de se prémunir contre une menace possible de SettingsModifier:Win32/PossibleHostsFileHijack, consultez la page [http://go.microsoft.com/fwlink/?LinkId=146221](http://go.microsoft.com/fwlink/?LinkId=146221).</span><span class="sxs-lookup"><span data-stu-id="19ceb-139">For more information about the Microsoft Malware Protection Center signature update that addresses a possible threat from SettingsModifier:Win32/PossibleHostsFileHijack, go to [http://go.microsoft.com/fwlink/?LinkId=146221](http://go.microsoft.com/fwlink/?LinkId=146221).</span></span>  
  
## <a name="enlistment-of-an-orchestration-fails-if-referenced-assemblies-are-missing-from-the-gacmgmt-db"></a><span data-ttu-id="19ceb-140">L'inscription d'une orchestration échoue si les assemblys référencés sont absents de la base de données GAC/Mgmt</span><span class="sxs-lookup"><span data-stu-id="19ceb-140">Enlistment of an Orchestration Fails if Referenced Assemblies are Missing from the GAC/Mgmt DB</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="19ceb-141">Problem (Problème)</span><span class="sxs-lookup"><span data-stu-id="19ceb-141">Problem</span></span>  
 <span data-ttu-id="19ceb-142">L'inscription d'une orchestration échoue si les références (C# assemblys faisant référence aux orchestrations) sont absents de la base de données GAC/Mgmt.</span><span class="sxs-lookup"><span data-stu-id="19ceb-142">Enlistment of an orchestration fails if references (C# assemblies which are referenced to orchestrations) are missing from the GAC/Mgmt db.</span></span> <span data-ttu-id="19ceb-143">Durant le redéploiement, il peut être nécessaire d'inscrire l'orchestration en fonction de son état actuel.</span><span class="sxs-lookup"><span data-stu-id="19ceb-143">During re-deployment, there may be a need to enlist the orchestration based on its existing state.</span></span> <span data-ttu-id="19ceb-144">Si des références sont absentes, le déploiement échoue également.</span><span class="sxs-lookup"><span data-stu-id="19ceb-144">If references are missing then the deployment also fails.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="19ceb-145">Cause</span><span class="sxs-lookup"><span data-stu-id="19ceb-145">Cause</span></span>  
 <span data-ttu-id="19ceb-146">Les assemblys référencés sont absents de la base de données GAC/Mgmt.</span><span class="sxs-lookup"><span data-stu-id="19ceb-146">Referenced assemblies are missing from GAC/Mgmt db.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="19ceb-147">Résolution</span><span class="sxs-lookup"><span data-stu-id="19ceb-147">Resolution</span></span>  
 <span data-ttu-id="19ceb-148">Ajoutez les assemblys référencés à GAC ou ajoutez-les comme ressources, afin qu'ils soient stockés dans la base de données Mgmt et qu'ils soient accessibles lors de l'inscription de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="19ceb-148">Add the referenced assemblies in GAC or add them as resources, so that they are stored in Mgmt db and are accessible during enlistment of orchestration.</span></span>  

## <a name="community-blog-biztalk-2013-r2-bugs-issues--quirks"></a><span data-ttu-id="19ceb-149">Blog de la Communauté : Bogues, problèmes et quirks relatifs à BizTalk 2013 R2</span><span class="sxs-lookup"><span data-stu-id="19ceb-149">Community blog: BizTalk 2013 R2 bugs, issues & quirks</span></span>

[<span data-ttu-id="19ceb-150">BizTalk Server 2013 R2 – Bogues, problèmes et quirks connus</span><span class="sxs-lookup"><span data-stu-id="19ceb-150">BizTalk Server 2013 R2 known bugs, issues, quirks</span></span>](https://cdijkgraaf.wordpress.com/2016/08/12/biztalk-2013-r2-known-bugs-issues-quirks/)
  
## <a name="additional-configuration-topics"></a><span data-ttu-id="19ceb-151">Rubriques de configuration supplémentaires</span><span class="sxs-lookup"><span data-stu-id="19ceb-151">Additional Configuration Topics</span></span>  
  
 [<span data-ttu-id="19ceb-152">Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="19ceb-152">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)  
  
 [<span data-ttu-id="19ceb-153">Configuration de BizTalk Server sur une machine virtuelle Azure</span><span class="sxs-lookup"><span data-stu-id="19ceb-153">Configuring BizTalk Server on an Azure VM</span></span>](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
  [<span data-ttu-id="19ceb-154">Configuration de BizTalk Server dans un cluster</span><span class="sxs-lookup"><span data-stu-id="19ceb-154">Configure BizTalk Server in a Cluster</span></span>](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)
  
 [<span data-ttu-id="19ceb-155">Sécurisation d’un déploiement BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="19ceb-155">Securing Your BizTalk Server Deployment</span></span>](../install-and-config-guides/securing-your-biztalk-server-deployment.md)  
  