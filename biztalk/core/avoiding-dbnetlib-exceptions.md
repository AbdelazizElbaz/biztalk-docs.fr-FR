---
title: Des exceptions DBNETLIB | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fbee0cf-d249-4d98-8d16-168ded32f9f1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decd258c5f4c965c79d9821c82671c6997ac9e3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="avoiding-dbnetlib-exceptions"></a><span data-ttu-id="b1a20-102">Contournement des exceptions DBNETLIB</span><span class="sxs-lookup"><span data-stu-id="b1a20-102">Avoiding DBNETLIB Exceptions</span></span>
<span data-ttu-id="b1a20-103">Des erreurs DBNetLib (Database Network Library) se produisent lorsque le composant d'exécution de BizTalk Server ne peut pas communiquer avec la base de données MessageBox ou celle de gestion.</span><span class="sxs-lookup"><span data-stu-id="b1a20-103">DBNetLib (Database Network Library) errors occur when the BizTalk Server runtime is unable to communicate with either the MessageBox or Management databases.</span></span> <span data-ttu-id="b1a20-104">Lorsque cela se produit, l'instance d'exécution BizTalk Server qui intercepte l'exception s'arrête et effectue une interrogation toutes les minutes pour voir si la base de données est disponible.</span><span class="sxs-lookup"><span data-stu-id="b1a20-104">When this occurs, the BizTalk Server runtime instance that catches the exception shuts down and then cycles every minute to check to see if the database is available.</span></span>  
  
 <span data-ttu-id="b1a20-105">La cause la plus fréquente d'une erreur DBNetLib est lorsque l'un des serveurs de base de données MessageBox devient occupé. Toute tentative ultérieure de communiquer avec lui se solde alors par un délai d'expiration, causant une exception DBNetLib.</span><span class="sxs-lookup"><span data-stu-id="b1a20-105">The most common cause of a DBNetLib error is when one of the (possibly many) MessageBox database servers becomes extremely busy and further attempts to communicate with it result in a timeout, which causes a DBNetLib exception.</span></span>  
  
 <span data-ttu-id="b1a20-106">Outre ce cas de figure, l'erreur DBNetLib peut se produire dans un environnement de production lorsque les serveurs de base de données BizTalk hébergeant une ou plusieurs bases de données MessageBox  deviennent liés aux E/S (Entrées/Sorties).</span><span class="sxs-lookup"><span data-stu-id="b1a20-106">In addition to the case where the MessageBox database is simply very busy, the DBNetLib error can occur in a production environment when BizTalk database servers hosting one of more MessageBox databases become I/O (Input/Output) bound.</span></span>  
  
 <span data-ttu-id="b1a20-107">Cette rubrique décrit les conditions pouvant conduire à des erreurs DBNetLib et les recommandations permettant de les éviter.</span><span class="sxs-lookup"><span data-stu-id="b1a20-107">This topic describes conditions that can lead to DBNetLib errors and recommendations for avoiding these errors.</span></span>  
  
## <a name="cause-and-resolution-for-the-dbnetlib-error"></a><span data-ttu-id="b1a20-108">Cause et résolution de l'erreur DBNetLib</span><span class="sxs-lookup"><span data-stu-id="b1a20-108">Cause and Resolution for the DBNetLib error</span></span>  
  
### <a name="symptoms-of-a-dbnetlib-error"></a><span data-ttu-id="b1a20-109">Symptômes d'une erreur DBNetLib</span><span class="sxs-lookup"><span data-stu-id="b1a20-109">Symptoms of a DBNetLib error</span></span>  
 <span data-ttu-id="b1a20-110">Une instance d'hôte Microsoft BizTalk Server prend fin, puis redémarre d'elle-même, et des erreurs semblables à celles qui suivent sont consignées dans le journal de l'application de BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="b1a20-110">A Microsoft BizTalk Server host instance terminates and then restarts itself, and errors that are similar to the following are written to the BizTalk Server Application log:</span></span>  
  
```  
Event Type:Warning  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:5410  
Computer:BIZTALKSERVER  
Description:  
An error occurred that requires the BizTalk service to terminate. The most common causes are the following:  
 1) An unexpected out of memory error.  
 OR  
 2) An inability to connect or a loss of connectivity to one of the BizTalk databases.   
 The service will shutdown and auto-restart in 1 minute. If the problematic database remains unavailable, this cycle will repeat.  
  
 Error message: [DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation.  
 Error source:    
  
 BizTalk host name: BizTalkHost  
 Windows service name: BTSSvc$BizTalkHost   
  
---------------------------------------------------------  
Event Type:Error  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:6913  
Computer:BIZTALKSERVER  
Description:  
An attempt to connect to "BizTalkMsgBoxDb" SQL Server database on server "SQLSERVER " failed.  
 Error: "[DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation."  
```  
  
### <a name="biztalk-database-servers-hosting-messagebox-databases-becoming-io-bound"></a><span data-ttu-id="b1a20-111">Serveurs BizTalk hébergeant les bases de données MessageBox devenant liés aux E/S</span><span class="sxs-lookup"><span data-stu-id="b1a20-111">BizTalk database servers hosting MessageBox databases becoming I/O bound</span></span>  
 <span data-ttu-id="b1a20-112">Les serveurs BizTalk communiquent et agissent directement avec les serveurs hébergeant les bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="b1a20-112">BizTalk servers communicate and act directly with the database servers hosting the MessageBox databases.</span></span> <span data-ttu-id="b1a20-113">Si l'un des serveurs hébergeant les bases de données MessageBox vient à être trop sollicité et à se trouver lié aux E/S, il risque de ne plus répondre.</span><span class="sxs-lookup"><span data-stu-id="b1a20-113">If any of the database servers hosting the MessageBox databases get too consumed and gets into an I/O (Input/Output) bound situation, then it might become unresponsive.</span></span> <span data-ttu-id="b1a20-114">Un des serveurs BizTalk peut alors perdre à son tour la connectivité avec l'un de ces serveurs, produisant une erreur DBNetLib.</span><span class="sxs-lookup"><span data-stu-id="b1a20-114">One of the BizTalk servers might in turn lose connectivity with one of those database servers, and a DBNetLib error will occur.</span></span>  
  
 <span data-ttu-id="b1a20-115">Nos tests montrent qu'un serveur de base de données hautement utilisé devient lié aux E/S quand la durée d'inactivité (« %Idle time ») de son disque physique diminue jusqu'à atteindre une valeur inférieure à 10 %.</span><span class="sxs-lookup"><span data-stu-id="b1a20-115">Our tests show that a highly consumed database server becomes I/O bound when its physical disk’s "%Idle time" continues to drop and reaches below 10%.</span></span> <span data-ttu-id="b1a20-116">Si la durée d'inactivité tombe en dessous de ce niveau, cela signifie que votre serveur de base de données a de grandes chances de ne plus répondre.</span><span class="sxs-lookup"><span data-stu-id="b1a20-116">If the “%Idle time” continues to drop below that level, then this is an indication that your database server is likely to become unresponsive.</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="b1a20-117">Cause</span><span class="sxs-lookup"><span data-stu-id="b1a20-117">Cause</span></span>  
 <span data-ttu-id="b1a20-118">Plusieurs situations peuvent faire que les serveurs hébergeant les bases de données MessageBox deviennent liés aux E/S, notamment :</span><span class="sxs-lookup"><span data-stu-id="b1a20-118">There are several reasons that can cause the database servers hosting the MessageBox databases to become I/O bound, some of these are the following:</span></span>  
  
-   <span data-ttu-id="b1a20-119">Lorsque l'ordinateur hébergeant la base de données MessageBox est limité par des spécifications matérielles faibles telles que : mémoire insuffisante, processeurs insuffisants et pas assez rapides, etc.</span><span class="sxs-lookup"><span data-stu-id="b1a20-119">If the database machine hosting the MessageBox database is bound by low hardware specifications such as: low memory, number and speed of processors etc.</span></span>  
  
-   <span data-ttu-id="b1a20-120">Lorsque le disque physique de l'ordinateur hébergeant une base de données MessageBox est également employé par d'autres bases de données fortement utilisées.</span><span class="sxs-lookup"><span data-stu-id="b1a20-120">If the physical disk on the database machine hosting a MessageBox database is being shared by other highly consumed databases.</span></span> <span data-ttu-id="b1a20-121">Si plusieurs bases de données (dont la MessageBox) sont fortement utilisées en même temps, le disque physique peut se retrouver tributaire des E/S.</span><span class="sxs-lookup"><span data-stu-id="b1a20-121">In cases when several databases (including the MessageBox) are being highly consumed at the same time, the physical disk can get into an I/O bound situation.</span></span>  
  
     <span data-ttu-id="b1a20-122">Voici un exemple d’une telle situation :</span><span class="sxs-lookup"><span data-stu-id="b1a20-122">An example of such a situation is the following:</span></span>  
  
     <span data-ttu-id="b1a20-123">Nos tests montrent que le serveur hébergeant les bases de données BizTalkDTADb et/ou BAM utilise parfois d'importantes ressources lors de la lecture et de l'écriture sur le disque physique.</span><span class="sxs-lookup"><span data-stu-id="b1a20-123">Our tests show that the database server hosting the BizTalkDTADb and/or BAM databases sometimes consume high percentages of a physical disk’s %Disk Read and Write Times.</span></span> <span data-ttu-id="b1a20-124">Lorsque le disque du serveur sur lequel réside la base de données MessageBox est également utilisé par une telle base de données, et que vous avez recours aux deux bases en même temps, le disque peut se retrouver tributaire des E/S et ne plus être en mesure de répondre.</span><span class="sxs-lookup"><span data-stu-id="b1a20-124">When the database server disk that hosts a MessageBox database is being shared by another highly consumed database such as BizTalkDTADb or BAM, and if both databases are highly consumed simultaneously, they might cause the database server physical disk to become I/O bound and then unresponsive.</span></span>  
  
-   <span data-ttu-id="b1a20-125">Lorsque la base de données BizTalkDTADb et une ou plusieurs bases de données MessageBox partagent le même disque physique et que la fréquence d'exécution des archivages et des purges n'est pas suffisante, le disque devient lié aux E/S.</span><span class="sxs-lookup"><span data-stu-id="b1a20-125">If BizTalkDTADb and one or more of the MessageBox databases are sharing the same physical disk on the database server, if archiving and purging is not being run frequently, the disk might become I/O bound.</span></span>  
  
#### <a name="resolution"></a><span data-ttu-id="b1a20-126">Résolution</span><span class="sxs-lookup"><span data-stu-id="b1a20-126">Resolution</span></span>  
 <span data-ttu-id="b1a20-127">Assurez-vous que les serveurs hébergeant les bases de données MessageBox de BizTalk ne soient pas trop sollicités, ce qui aurait pour conséquence de les rendre inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="b1a20-127">Ensure the database server(s) hosting the BizTalk MessageBox(s) do not get into a situation where they become highly consumed and possibly unresponsive.</span></span>  
  
 <span data-ttu-id="b1a20-128">La section suivante indique certaines des principales situations pouvant entraîner une forte sollicitation du disque du serveur et présente quelques conseils permettant de résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="b1a20-128">Some of the primary causes of a server disk becoming highly consumed are listed below along with recommendations on how to mitigate this problem.</span></span>  
  
##### <a name="low-hardware-specs"></a><span data-ttu-id="b1a20-129">Spécifications matérielles faibles</span><span class="sxs-lookup"><span data-stu-id="b1a20-129">Low Hardware Specs</span></span>  
 <span data-ttu-id="b1a20-130">Nos tests montrent que la sollicitation du serveur devient trop importante lorsque ses spécifications matérielles ne peuvent suivre la charge de travail qu'il tente de traiter.</span><span class="sxs-lookup"><span data-stu-id="b1a20-130">Our tests show that the server starts getting more consumed when its hardware specifications cannot keep up with the amount of load it’s trying to process.</span></span> <span data-ttu-id="b1a20-131">Un système aux spécifications matérielles trop faibles se retrouve vite submergé par la quantité d'activités se produisant sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="b1a20-131">With lower hardware specs, the system gets overwhelmed quickly by the amount of activities happening on the databases.</span></span> <span data-ttu-id="b1a20-132">Les temps de lecture et d'écriture augmentent alors sans cesse, la durée d'inactivité du disque diminue pour tomber sous les 10 %, avec pour résultat un serveur qui ne répond plus.</span><span class="sxs-lookup"><span data-stu-id="b1a20-132">This might cause the server’s %Disk Read and Write Times to continue increasing without stabilizing, also the disk’s %Idle time to continue to decrease and become lower than 10%, and this might cause your database server to become unresponsive.</span></span>  
  
 <span data-ttu-id="b1a20-133">En fonction de la quantité d'activités et de la charge utilisée dans votre déploiement BizTalk, s'il arrive que les serveurs de base de données ne répondent plus lors de fortes sollicitations, vous devez envisager de mettre à niveau les composants suivants de vos serveurs de base de données : le nombre d'UC, la quantité de mémoire et la connexion à un SAN.</span><span class="sxs-lookup"><span data-stu-id="b1a20-133">Depending on the amount of activities and load you have on your BizTalk deployment, if you find that you are getting unresponsive database servers during to high loads, you should consider upgrading the following parts in your database servers: number of CPUs, memory, and connecting to a SAN.</span></span> <span data-ttu-id="b1a20-134">Il est bien sûr conseillé de poser le bon diagnostic pour savoir quel composant de votre matériel (mémoire, nombre d'UC, etc.) est à l'origine de l'engorgement et nécessite d'être mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="b1a20-134">Of course, you should do the proper diagnosis to figure out which part (memory, number of CPUs etc.) is the bottleneck that needs to be upgraded in your hardware.</span></span>  
  
##### <a name="sharing-one-server-or-disk-for-more-than-one-group-of-biztalk-databases"></a><span data-ttu-id="b1a20-135">Plusieurs groupes de bases de données BizTalk partageant un même serveur ou un même disque</span><span class="sxs-lookup"><span data-stu-id="b1a20-135">Sharing one server or disk for more than one group of BizTalk databases</span></span>  
 <span data-ttu-id="b1a20-136">Comme cela a été dit plus haut, les bases de données autres que MessageBox, telles que les bases de données des suivis BizTalk (BizTalkDTADb) et BAM, peuvent consommer d'importantes ressources sur le disque physique d'un serveur.</span><span class="sxs-lookup"><span data-stu-id="b1a20-136">As mentioned previously, databases other than MessageBoxes, such as the BizTalk Tracking (BizTalkDTADb) database and BAM databases, might consume high cycles on a server’s physical disk.</span></span> <span data-ttu-id="b1a20-137">De ce fait, si ces bases de données et les bases MessageBox devaient partager le même disque physique, ce dernier risquerait d'être trop sollicité et de ne plus être en mesure de répondre. Les serveurs BizTalk pourraient alors connaître des problèmes de connectivité avec les bases MessageBox et générer une erreur DBNetLib. </span><span class="sxs-lookup"><span data-stu-id="b1a20-137">So, if those databases happen to share the same physical disk with the MessageBox databases, then they might choke the disk and make it unresponsive, which again might cause BizTalk servers to loose connectivity with the MessageBox databases and thus hit DBNetLib.</span></span>  
  
 <span data-ttu-id="b1a20-138">Il est fortement recommandé de séparer toute base de données susceptible d'utiliser d'importantes ressources du disque physique du serveur des bases de données MessageBox, de sorte qu'elles partagent plusieurs disques physiques (ou qu'elles soient placées sur différents serveurs).</span><span class="sxs-lookup"><span data-stu-id="b1a20-138">It is highly recommended that you separate any database expected to have high consumption of the server’s physical disk from the BizTalk MessageBox(s), so they share different physical disks (or separate them on different servers).</span></span> <span data-ttu-id="b1a20-139">Il est conseillé de placer les bases de données BizTalkDTADb et BAM sur des lecteurs/serveurs qui leur sont propres, distincts des bases de données MessageBox. Chaque base de données MessageBox (si vous en utilisez plusieurs) devrait par ailleurs être hébergée de manière séparée, chacune sur son propre disque.</span><span class="sxs-lookup"><span data-stu-id="b1a20-139">It is recommended that you separate the BizTalkDTADb and BAM databases on their own separate drives/servers from the MessageBox(s), and it is also recommended to have each MessageBox database (in the case there is more than one) on it’s own disk.</span></span>  
  
##### <a name="archiving-and-purging"></a><span data-ttu-id="b1a20-140">L'archivage et la purge</span><span class="sxs-lookup"><span data-stu-id="b1a20-140">Archiving and Purging</span></span>  
 <span data-ttu-id="b1a20-141">Si les bases de données BizTalkDTADb et MessageBox partagent le même disque sur le même serveur, vous devez archiver et purger les bases BizTalkDTADb de manière régulière, de façon à éviter que leur volume ne s'accroisse indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="b1a20-141">In the case when you have BizTalkDTADb and MessageBox databases sharing the same disk on the same server, you must archive and purge your BizTalkDTADb databases regularly, otherwise they will grow indefinitely.</span></span>  
  
 <span data-ttu-id="b1a20-142">Le test montre qu'il est conseillé de les archiver et de les purger de manière périodique. Toutefois, en cas de charges plus élevées que la normale, vous pouvez être amené à augmenter la fréquence d'archivage et de purge.</span><span class="sxs-lookup"><span data-stu-id="b1a20-142">Testing indicates that it is good practice to archive and purge periodically, but if you run under higher loads than normal then you might want to consider archiving and purging more frequently.</span></span> <span data-ttu-id="b1a20-143">Sachez que des travaux d'archivage et de purge non effectués régulièrement risquent de prendre beaucoup plus de temps et d'utiliser une grosse partie des ressources disponibles du serveur.</span><span class="sxs-lookup"><span data-stu-id="b1a20-143">If the BizTalkDTADb database growth is not maintained regularly, then when these actions are finally performed they may take considerable time and consume most of the available database server resources while they are running.</span></span>