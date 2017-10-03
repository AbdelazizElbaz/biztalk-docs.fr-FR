---
title: "Planification du développement, test, intermédiaire et les environnements de Production | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c83a42d-117f-4a24-a669-b3e4e1c9a056
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25eb6aadd41526adeecb9c5a249d38384fb532ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-the-development-testing-staging-and-production-environments"></a><span data-ttu-id="a5e73-102">Planification du développement, test, intermédiaire et les environnements de Production</span><span class="sxs-lookup"><span data-stu-id="a5e73-102">Planning the Development, Testing, Staging, and Production Environments</span></span>
<span data-ttu-id="a5e73-103">Cette rubrique décrit les environnements utilisées dans le processus de gestion de version d’une solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5e73-103">This topic discusses the environments used in the release management process for a BizTalk solution.</span></span> <span data-ttu-id="a5e73-104">Comme avec toute solution de logiciels d’entreprise, vous devez suivre les instructions de gestion de version logicielle établie lorsque vous développez et libérer une solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5e73-104">As with any enterprise software solution, you should follow established software release management guidelines when you develop and release a BizTalk solution.</span></span> <span data-ttu-id="a5e73-105">Ce processus doit inclure les étapes distinctes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a5e73-105">This process should include the following distinct stages:</span></span>  
  
-   <span data-ttu-id="a5e73-106">Développement</span><span class="sxs-lookup"><span data-stu-id="a5e73-106">Development</span></span>  
  
-   <span data-ttu-id="a5e73-107">Test</span><span class="sxs-lookup"><span data-stu-id="a5e73-107">Testing</span></span>  
  
-   <span data-ttu-id="a5e73-108">Mise en lots</span><span class="sxs-lookup"><span data-stu-id="a5e73-108">Staging</span></span>  
  
-   <span data-ttu-id="a5e73-109">Production</span><span class="sxs-lookup"><span data-stu-id="a5e73-109">Production</span></span>  
  
 <span data-ttu-id="a5e73-110">Dans l’idéal, vous devez effectuer chaque étape dans le processus de gestion de version dans un environnement discrète, distinct à partir d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="a5e73-110">Ideally, you should complete each stage in the release management process in a discrete environment, separate from the other environments.</span></span> <span data-ttu-id="a5e73-111">Dans la pratique, vous devrez combiner un ou plusieurs des environnements en raison de matériel ou d’autres contraintes de ressources.</span><span class="sxs-lookup"><span data-stu-id="a5e73-111">Realistically, you may have to combine one or more of the environments due to hardware, time, or other resource constraints.</span></span> <span data-ttu-id="a5e73-112">Au minimum, vous devez séparer l’environnement de production à partir d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="a5e73-112">At a bare minimum you should separate the production environment from the other environments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5e73-113">Les instructions d’installation et de mise à niveau plus récente pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sont disponibles en téléchargement séparé sur le [page de Documentation de BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkID=194815) (http://go.microsoft.com/fwlink/?LinkID=194815).</span><span class="sxs-lookup"><span data-stu-id="a5e73-113">The latest installation and upgrade instructions for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] are available as separate downloads on the [BizTalk Server 2010 Documentation page](http://go.microsoft.com/fwlink/?LinkID=194815) (http://go.microsoft.com/fwlink/?LinkID=194815).</span></span>  
  
##  <span data-ttu-id="a5e73-114"><a name="BKMK_VirtualServ"></a>À l’aide de Virtual Server pendant le processus de gestion de version</span><span class="sxs-lookup"><span data-stu-id="a5e73-114"><a name="BKMK_VirtualServ"></a> Using Virtual Server During the Release Management Process</span></span>  
 <span data-ttu-id="a5e73-115">Envisagez de développement, test unitaire et la mise en lots dans un environnement « virtuel ».</span><span class="sxs-lookup"><span data-stu-id="a5e73-115">Consider completing development, unit testing, and staging in a "virtual" environment.</span></span> <span data-ttu-id="a5e73-116">Microsoft propose une gamme de produits de virtualisation telles que Microsoft Virtual Server 2005 R2, Windows Server 2008 Hyper-V et Microsoft Hyper-V Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a5e73-116">Microsoft offers a range of virtualization products such as Microsoft Virtual Server 2005 R2, Windows Server 2008 Hyper-V, and Microsoft Hyper-V Server 2008.</span></span> <span data-ttu-id="a5e73-117">[Microsoft Virtual Server 2005 R2](http://go.microsoft.com/fwlink/?LinkId=71365) (http://go.microsoft.com/fwlink/?LinkId=71365) est disponible en téléchargement gratuit.</span><span class="sxs-lookup"><span data-stu-id="a5e73-117">[Microsoft Virtual Server 2005 R2](http://go.microsoft.com/fwlink/?LinkId=71365) (http://go.microsoft.com/fwlink/?LinkId=71365) is available as a free download.</span></span> <span data-ttu-id="a5e73-118">Effectue le travail de développement, test unitaire et mise en lots dans un environnement virtuel est très flexible et utilise beaucoup moins de ressources matérielles nécessaires dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="a5e73-118">Performing development work, unit testing, and staging in a virtual environment offers great flexibility and uses considerably fewer hardware resources than required otherwise.</span></span> <span data-ttu-id="a5e73-119">Si un environnement virtuel est utilisé, allouez au moins 512 Mo de mémoire pour chaque ordinateur virtuel qui s’exécute sur l’ordinateur hôte et 512 Mo de mémoire pour le système d’exploitation hôte supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="a5e73-119">If a virtual environment is used, allocate at least 512 MB of memory for each virtual machine that is running on the host computer and an additional 512 MB of memory for the host operating system.</span></span>  
  
 <span data-ttu-id="a5e73-120">Par exemple, pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement qui utilise cinq ordinateurs virtuels (deux ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], deux Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] nœuds de cluster et un contrôleur de domaine), vous devez prévoir 3 Go de mémoire installée sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="a5e73-120">For example, for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that uses five virtual machines (two computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], two Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster nodes, and one domain controller), you would plan to have 3 GB of memory installed on the host computer.</span></span> <span data-ttu-id="a5e73-121">Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement nécessite plus de 2 Go de mémoire, envisagez d’installer une version 64 bits de Windows sur l’ordinateur hôte pour vous assurer que la quantité maximale de la mémoire installée est accessible par le système d’exploitation hôte.</span><span class="sxs-lookup"><span data-stu-id="a5e73-121">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment requires more than 2 GB of memory, consider installing a 64-bit version of Windows on the host computer to ensure that the maximum amount of installed memory is accessible by the host operating system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5e73-122">Pour obtenir des recommandations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtuel, consultez [Guide BizTalk Server 2009 Hyper-V](http://go.microsoft.com/fwlink/?LinkId=151834) (http://go.microsoft.com/fwlink/?LinkId=151834).</span><span class="sxs-lookup"><span data-stu-id="a5e73-122">For recommendations on using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtual environment, see [BizTalk Server 2009 Hyper-V Guide](http://go.microsoft.com/fwlink/?LinkId=151834) (http://go.microsoft.com/fwlink/?LinkId=151834).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="a5e73-123">est entièrement pris en charge sur un système d’exploitation pris en charge qui s’exécute sur le logiciel de virtualisation répertoriées dans le 842301 de l’Article de Base de connaissances Microsoft [prise en charge de Microsoft BizTalk Server sur un ordinateur virtuel](http://go.microsoft.com/fwlink/?LinkId=158861) (http:// go.Microsoft.com/fwlink/ ? LinkId = 158861).</span><span class="sxs-lookup"><span data-stu-id="a5e73-123"> is fully supported on a supported operating system that is running on any of the virtualization software listed in the Microsoft Knowledge Base Article 842301 [Microsoft BizTalk Server supportability on a virtual machine](http://go.microsoft.com/fwlink/?LinkId=158861) (http://go.microsoft.com/fwlink/?LinkId=158861).</span></span> <span data-ttu-id="a5e73-124">Toutefois, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ne s’avèrent pas comme prévu si installé sur un système d’exploitation pris en charge qui s’exécute dans un logiciel de virtualisation différent de ceux mentionnés dans l’article.</span><span class="sxs-lookup"><span data-stu-id="a5e73-124">However, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] may not perform as expected if installed on a supported operating system that is running in a virtualization software other than the ones mentioned in the KB article.</span></span>  
  
## <a name="development-environment"></a><span data-ttu-id="a5e73-125">Environnement de développement</span><span class="sxs-lookup"><span data-stu-id="a5e73-125">Development Environment</span></span>  
 <span data-ttu-id="a5e73-126">Les projets BizTalk qui sont utilisées pour la solution BizTalk sont créés dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="a5e73-126">The BizTalk projects that are used for the BizTalk solution are created in the development environment.</span></span> <span data-ttu-id="a5e73-127">Vous devez installer les logiciels suivants sur les ordinateurs utilisés dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement de développement :</span><span class="sxs-lookup"><span data-stu-id="a5e73-127">You should install the following software on the computers used in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development environment:</span></span>  
  
-   <span data-ttu-id="a5e73-128">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="a5e73-128">Internet Information Services (IIS)</span></span>  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="a5e73-129">Outils clients [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e73-129">[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Client Tools</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a5e73-130">(y compris les composants suivants)</span><span class="sxs-lookup"><span data-stu-id="a5e73-130"> (including the following components)</span></span>  
  
    -   <span data-ttu-id="a5e73-131">Documentation</span><span class="sxs-lookup"><span data-stu-id="a5e73-131">Documentation</span></span>  
  
    -   <span data-ttu-id="a5e73-132">Outils d'administration</span><span class="sxs-lookup"><span data-stu-id="a5e73-132">Administrative tools</span></span>  
  
    -   <span data-ttu-id="a5e73-133">Outils de développement et Kit de développement logiciel</span><span class="sxs-lookup"><span data-stu-id="a5e73-133">Developer tools and SDK</span></span>  
  
    -   <span data-ttu-id="a5e73-134">Logiciels supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a5e73-134">Additional software</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="a5e73-135">, si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données doivent être hébergés localement au cours du développement.</span><span class="sxs-lookup"><span data-stu-id="a5e73-135">, if the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are to be hosted locally during development.</span></span>  
  
-   <span data-ttu-id="a5e73-136">En général, les développeurs doivent avoir leur propre ordinateur de développement (physique ou virtuel) avec les logiciels nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a5e73-136">Typically developers should have their own development computer (physical or virtual) with the necessary software installed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5e73-137">Nous recommandons que vous achetez et utilisez des licences d’abonnement MSDN pour les environnements hors production.</span><span class="sxs-lookup"><span data-stu-id="a5e73-137">We recommend that you purchase and use MSDN subscription licenses for non-production environments.</span></span> <span data-ttu-id="a5e73-138">Licences d’abonnement MSDN sont proposés à un prix réduit à partir du coût d’une licence de vente au détail pour le même logiciel.</span><span class="sxs-lookup"><span data-stu-id="a5e73-138">MSDN subscription licenses are offered at a significant discount from the cost of a retail license for the same software.</span></span> <span data-ttu-id="a5e73-139">Pour plus d’informations sur l’obtention d’un abonnement MSDN, consultez [abonnements MSDN](http://go.microsoft.com/fwlink/?LinkID=96006) (http://go.microsoft.com/fwlink/?LinkID=96006).</span><span class="sxs-lookup"><span data-stu-id="a5e73-139">For more information about obtaining an MSDN subscription see [MSDN Subscriptions](http://go.microsoft.com/fwlink/?LinkID=96006) (http://go.microsoft.com/fwlink/?LinkID=96006).</span></span>  
  
## <a name="testing-environment"></a><span data-ttu-id="a5e73-140">Environnement de test</span><span class="sxs-lookup"><span data-stu-id="a5e73-140">Testing Environment</span></span>  
 <span data-ttu-id="a5e73-141">Test unitaire peut être effectuée dans un environnement virtuel.</span><span class="sxs-lookup"><span data-stu-id="a5e73-141">Unit testing can be completed in a virtual environment.</span></span> <span data-ttu-id="a5e73-142">Vous devez, toutefois, effectuer des performances de votre test dans un environnement physique avec le matériel et logiciel qui est identique à l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="a5e73-142">You should, however, conduct your performance testing in a physical environment with hardware and software that is identical to the production environment.</span></span>  
  
 <span data-ttu-id="a5e73-143">L’environnement de test est utilisé pour mesurer les caractéristiques de performances telles que le débit maximal (MST) et le débit de suivi maximal acceptable de la solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5e73-143">The testing environment is used to measure performance characteristics such as maximum sustainable throughput (MST) and maximum sustainable tracking throughput of the BizTalk solution.</span></span> <span data-ttu-id="a5e73-144">Il doit par conséquent l’environnement de production physique aussi proche que possible.</span><span class="sxs-lookup"><span data-stu-id="a5e73-144">It should therefore match the physical production environment as closely as possible.</span></span> <span data-ttu-id="a5e73-145">Pour plus d’informations sur la mesure de performances Voir les caractéristiques d’une solution BizTalk [des caractéristiques de performances du moteur](http://go.microsoft.com/fwlink/?LinkId=155771) (http://go.Microsoft.com/fwlink/?) LinkId = 155771) ou le [Guide de l’optimisation des performances BizTalk Server 2009](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.Microsoft.com/fwlink/?) LinkID = 150492).</span><span class="sxs-lookup"><span data-stu-id="a5e73-145">For more information about measuring performance characteristics of a BizTalk solution see [Engine Performance Characteristics](http://go.microsoft.com/fwlink/?LinkId=155771) (http://go.microsoft.com/fwlink/?LinkId=155771) or the [BizTalk Server 2009 Performance Optimization Guide](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.microsoft.com/fwlink/?LinkID=150492).</span></span>  
  
## <a name="staging-environment"></a><span data-ttu-id="a5e73-146">Environnement intermédiaire</span><span class="sxs-lookup"><span data-stu-id="a5e73-146">Staging Environment</span></span>  
 <span data-ttu-id="a5e73-147">Vous utilisez généralement l’environnement intermédiaire à « test unitaire » le déploiement réel de la solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5e73-147">You typically use the staging environment to "unit test" the actual deployment of the BizTalk solution.</span></span> <span data-ttu-id="a5e73-148">Les logiciels installés dans l’environnement intermédiaire doivent correspondre étroitement aux logiciels installés dans l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="a5e73-148">The software installed in the staging environment should closely match the software installed in the production environment.</span></span> <span data-ttu-id="a5e73-149">Il peut, toutefois, être acceptable d’utiliser des ordinateurs virtuels dans l’environnement intermédiaire dans la mesure où cet environnement ne doit ne pas être utilisé pour mesurer les performances.</span><span class="sxs-lookup"><span data-stu-id="a5e73-149">It may, however, be acceptable to use virtual computers in the staging environment since this environment is not to be used for measuring performance.</span></span> <span data-ttu-id="a5e73-150">Pour plus d’informations sur le déploiement d’une application BizTalk dans un environnement intermédiaire, consultez [mise en lots de tâches pour le déploiement d’applications BizTalk](http://go.microsoft.com/fwlink/?LinkID=154686) (http://go.microsoft.com/fwlink/?LinkID=154686).</span><span class="sxs-lookup"><span data-stu-id="a5e73-150">For more information about deploying a BizTalk application to a staging environment see [Staging Tasks for BizTalk Application Deployment](http://go.microsoft.com/fwlink/?LinkID=154686) (http://go.microsoft.com/fwlink/?LinkID=154686).</span></span>  
  
## <a name="production-environment"></a><span data-ttu-id="a5e73-151">Environnement de production</span><span class="sxs-lookup"><span data-stu-id="a5e73-151">Production Environment</span></span>  
 <span data-ttu-id="a5e73-152">L’environnement de production est l’environnement « dynamique » qui hébergera la solution BizTalk en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a5e73-152">The production environment is the "live" environment that will host the running BizTalk solution.</span></span> <span data-ttu-id="a5e73-153">L’environnement de production est le point de terminaison final dans le processus de gestion de version et doit uniquement les applications de BizTalk hôte qui ont précédemment fait l’objet de développement, test unitaire, test de charge et la mise en lots dans les autres environnements.</span><span class="sxs-lookup"><span data-stu-id="a5e73-153">The production environment is the final endpoint in the release management process and should only host BizTalk applications that have previously undergone development, unit testing, load testing, and staging in the other environments.</span></span> <span data-ttu-id="a5e73-154">Unités minutieux test, de test de charge et de mise en avance va garantissent des performances maximales et les temps de fonctionnement de l’application BizTalk dans l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="a5e73-154">Thorough unit testing, load testing, and staging beforehand will help ensure maximum performance and uptime for the BizTalk application in the production environment.</span></span>  
  
## <a name="guidelines-for-allocating-servers"></a><span data-ttu-id="a5e73-155">Instructions pour allouer des serveurs</span><span class="sxs-lookup"><span data-stu-id="a5e73-155">Guidelines for Allocating Servers</span></span>  
 <span data-ttu-id="a5e73-156">Les instructions suivantes fournissent une règle empirique pour le nombre de serveurs BizTalk Server et SQL Server, vous devez allouer à chaque étape du processus de gestion de version donné d’un certain nombre d’ordinateurs physiques doit être utilisé en production : ils sont approximatives estimations sont susceptibles de changer en fonction de votre architecture.</span><span class="sxs-lookup"><span data-stu-id="a5e73-156">The following guidelines provide a rule of thumb for the number of BizTalk servers and SQL servers you should allocate to each stage in the release management process given a particular number of physical computers expected to be used in production: They are rough estimates which are subject to change depending on your architecture.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5e73-157">Serveurs virtuels peuvent être utilisées dans le développement et dans l’environnement intermédiaire et peuvent également être utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="a5e73-157">Virtual servers may be used in the development and in the staging environment and can also be used for unit testing.</span></span> <span data-ttu-id="a5e73-158">Tous les tests de performances doivent être effectuée sur du matériel physique qui correspond à du matériel physique dans l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="a5e73-158">All performance testing should be performed on physical hardware that matches the physical hardware in the production environment.</span></span>  
  
|<span data-ttu-id="a5e73-159">Ordinateurs qu'exécutant BizTalk Server utilisé en production (matériel recommandé)</span><span class="sxs-lookup"><span data-stu-id="a5e73-159">Computers running BizTalk Server used in production (physical hardware recommended)</span></span>|<span data-ttu-id="a5e73-160">Serveurs de développement (matériel virtuel ou physique)</span><span class="sxs-lookup"><span data-stu-id="a5e73-160">Development servers (virtual or physical hardware)</span></span>|<span data-ttu-id="a5e73-161">Serveurs de test (matériel recommandé)</span><span class="sxs-lookup"><span data-stu-id="a5e73-161">Testing servers (physical hardware recommended)</span></span>|<span data-ttu-id="a5e73-162">Serveurs de mise en lots (matériel virtuel ou physique)</span><span class="sxs-lookup"><span data-stu-id="a5e73-162">Staging servers (virtual or physical hardware)</span></span>|<span data-ttu-id="a5e73-163">Nb total.</span><span class="sxs-lookup"><span data-stu-id="a5e73-163">Total no.</span></span> <span data-ttu-id="a5e73-164">des ordinateurs exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a5e73-164">of computers running BizTalk Server</span></span>|  
|-------------------------------------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="a5e73-165">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-165">1</span></span>|<span data-ttu-id="a5e73-166">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-166">2</span></span>|<span data-ttu-id="a5e73-167">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-167">1</span></span>|<span data-ttu-id="a5e73-168">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-168">1</span></span>|<span data-ttu-id="a5e73-169">5</span><span class="sxs-lookup"><span data-stu-id="a5e73-169">5</span></span>|  
|<span data-ttu-id="a5e73-170">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-170">2</span></span>|<span data-ttu-id="a5e73-171">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-171">2</span></span>|<span data-ttu-id="a5e73-172">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-172">2</span></span>|<span data-ttu-id="a5e73-173">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-173">1</span></span>|<span data-ttu-id="a5e73-174">7</span><span class="sxs-lookup"><span data-stu-id="a5e73-174">7</span></span>|  
|<span data-ttu-id="a5e73-175">3</span><span class="sxs-lookup"><span data-stu-id="a5e73-175">3</span></span>|<span data-ttu-id="a5e73-176">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-176">2</span></span>|<span data-ttu-id="a5e73-177">3</span><span class="sxs-lookup"><span data-stu-id="a5e73-177">3</span></span>|<span data-ttu-id="a5e73-178">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-178">1</span></span>|<span data-ttu-id="a5e73-179">9</span><span class="sxs-lookup"><span data-stu-id="a5e73-179">9</span></span>|  
|<span data-ttu-id="a5e73-180">4</span><span class="sxs-lookup"><span data-stu-id="a5e73-180">4</span></span>|<span data-ttu-id="a5e73-181">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-181">2</span></span>|<span data-ttu-id="a5e73-182">4</span><span class="sxs-lookup"><span data-stu-id="a5e73-182">4</span></span>|<span data-ttu-id="a5e73-183">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-183">1</span></span>|<span data-ttu-id="a5e73-184">11</span><span class="sxs-lookup"><span data-stu-id="a5e73-184">11</span></span>|  
  
|<span data-ttu-id="a5e73-185">Aucune estimation.</span><span class="sxs-lookup"><span data-stu-id="a5e73-185">Estimated no.</span></span> <span data-ttu-id="a5e73-186">des ordinateurs exécutant SQL Server est utilisé en production (matériel recommandé)</span><span class="sxs-lookup"><span data-stu-id="a5e73-186">of computers running SQL Server used in production (physical hardware recommended)</span></span>|<span data-ttu-id="a5e73-187">Serveurs de développement (matériel virtuel ou physique)</span><span class="sxs-lookup"><span data-stu-id="a5e73-187">Development servers (virtual or physical hardware)</span></span>|<span data-ttu-id="a5e73-188">Serveurs de test (matériel recommandé)</span><span class="sxs-lookup"><span data-stu-id="a5e73-188">Testing servers (physical hardware recommended)</span></span>|<span data-ttu-id="a5e73-189">Serveurs de mise en lots (matériel virtuel ou physique)</span><span class="sxs-lookup"><span data-stu-id="a5e73-189">Staging servers (virtual or physical hardware)</span></span>|<span data-ttu-id="a5e73-190">Nb total.</span><span class="sxs-lookup"><span data-stu-id="a5e73-190">Total no.</span></span> <span data-ttu-id="a5e73-191">des ordinateurs qui exécutent SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5e73-191">of computers running SQL Server</span></span>|  
|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------|-----------------------------------------------|  
|<span data-ttu-id="a5e73-192">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-192">1</span></span>|<span data-ttu-id="a5e73-193">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-193">1</span></span>|<span data-ttu-id="a5e73-194">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-194">1</span></span>|<span data-ttu-id="a5e73-195">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-195">1</span></span>|<span data-ttu-id="a5e73-196">4</span><span class="sxs-lookup"><span data-stu-id="a5e73-196">4</span></span>|  
|<span data-ttu-id="a5e73-197">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-197">2</span></span>|<span data-ttu-id="a5e73-198">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-198">1</span></span>|<span data-ttu-id="a5e73-199">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-199">2</span></span>|<span data-ttu-id="a5e73-200">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-200">1</span></span>|<span data-ttu-id="a5e73-201">6</span><span class="sxs-lookup"><span data-stu-id="a5e73-201">6</span></span>|  
|<span data-ttu-id="a5e73-202">3</span><span class="sxs-lookup"><span data-stu-id="a5e73-202">3</span></span>|<span data-ttu-id="a5e73-203">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-203">2</span></span>|<span data-ttu-id="a5e73-204">3</span><span class="sxs-lookup"><span data-stu-id="a5e73-204">3</span></span>|<span data-ttu-id="a5e73-205">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-205">1</span></span>|<span data-ttu-id="a5e73-206">9</span><span class="sxs-lookup"><span data-stu-id="a5e73-206">9</span></span>|  
|<span data-ttu-id="a5e73-207">4</span><span class="sxs-lookup"><span data-stu-id="a5e73-207">4</span></span>|<span data-ttu-id="a5e73-208">2</span><span class="sxs-lookup"><span data-stu-id="a5e73-208">2</span></span>|<span data-ttu-id="a5e73-209">4</span><span class="sxs-lookup"><span data-stu-id="a5e73-209">4</span></span>|<span data-ttu-id="a5e73-210">1</span><span class="sxs-lookup"><span data-stu-id="a5e73-210">1</span></span>|<span data-ttu-id="a5e73-211">11</span><span class="sxs-lookup"><span data-stu-id="a5e73-211">11</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5e73-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5e73-212">See Also</span></span>  
 [<span data-ttu-id="a5e73-213">Planification de l’environnement pour BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a5e73-213">Planning the Environment for BizTalk Server</span></span>](../technical-guides/planning-the-environment-for-biztalk-server.md)