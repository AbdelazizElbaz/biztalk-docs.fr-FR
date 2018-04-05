---
title: Comment se connecter à un groupe existant | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.connecttogroup
helpviewer_keywords:
- groups, existing
- groups, connecting
- managing [groups], connecting
ms.assetid: 1eedbcd5-f3f1-4da5-b91c-67377131f889
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 942093faa4a556f31d090de97b3feff4eb7a9a45
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-connect-to-an-existing-group"></a><span data-ttu-id="841d2-102">Connexion à un groupe existant</span><span class="sxs-lookup"><span data-stu-id="841d2-102">How to Connect to an Existing Group</span></span>
<span data-ttu-id="841d2-103">Vous pouvez utiliser la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration sur n’importe quel ordinateur dans votre entreprise pour gérer à distance un ou plusieurs groupes BizTalk Server au sein de votre entreprise, tant que ces groupes se trouvent sur des ordinateurs au sein du même domaine ou dans des domaines approuvés.</span><span class="sxs-lookup"><span data-stu-id="841d2-103">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console on any computer in your enterprise to remotely manage one or more BizTalk Server groups within your enterprise, as long as these groups are located on computers within the same domain or within trusted domains.</span></span>  
  
 <span data-ttu-id="841d2-104">Le nœud Administration de BizTalk Server dans la console Administration de BizTalk Server est le nœud de niveau supérieur pour tous les groupes BizTalk et le niveau que vous utilisez lors de l’ajout d’un groupe BizTalk Server existant dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="841d2-104">The BizTalk Server Administration node in the BizTalk Server Administration console is the highest-level node for all BizTalk groups, and is the level that you use when adding an existing BizTalk Server group to the BizTalk Server Administration console.</span></span> <span data-ttu-id="841d2-105">Lorsque vous ajoutez un groupe, vous devez spécifier un serveur et une base de données de gestion BizTalk existants auxquels vous connecter.</span><span class="sxs-lookup"><span data-stu-id="841d2-105">When you add a group, you must specify an existing server and BizTalk Management database to which you want to connect.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="841d2-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="841d2-106">Prerequisites</span></span>  
 <span data-ttu-id="841d2-107">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="841d2-107">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group or as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-connect-to-an-existing-group"></a><span data-ttu-id="841d2-108">Pour se connecter à un groupe existant</span><span class="sxs-lookup"><span data-stu-id="841d2-108">To connect to an existing group</span></span>  
  
1.  <span data-ttu-id="841d2-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="841d2-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="841d2-110">Dans l’arborescence de la console, cliquez sur **Administration de BizTalk Server**, puis cliquez sur **se connecter au groupe existant**.</span><span class="sxs-lookup"><span data-stu-id="841d2-110">In the console tree, right-click **BizTalk Server Administration**, and then click **Connect to Existing Group**.</span></span>  
  
3.  <span data-ttu-id="841d2-111">Dans le **se connecter à la base de Configuration BizTalk existante** boîte de dialogue le **nom SQL Server** liste déroulante, sélectionnez le nom de l’instance de Microsoft SQL Server qui héberge la BizTalk Base de données de gestion (également appelée la base de données de Configuration).</span><span class="sxs-lookup"><span data-stu-id="841d2-111">In the **Connect to Existing BizTalk Server Configuration Database** dialog box, in the **SQL Server name** drop-down list box, select the name of the Microsoft SQL Server instance that hosts the BizTalk Management database (also referred to as the Configuration database).</span></span> <span data-ttu-id="841d2-112">Lorsque vous sélectionnez l'instance de SQL Server, BizTalk Server tente automatiquement de détecter les bases de données BizTalk Server sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="841d2-112">When you select the instance of SQL Server, BizTalk Server automatically attempts to detect BizTalk Server databases on that computer.</span></span>  
  
4.  <span data-ttu-id="841d2-113">Dans le **nom de la base de données** liste déroulante, sélectionnez la base de données de gestion BizTalk Server (**BizTalkMgmtDb**) à laquelle vous souhaitez vous connecter, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="841d2-113">In the **Database name** drop-down list box, select the BizTalk Server Management database (**BizTalkMgmtDb**) to which you want to connect, and then click **OK**.</span></span>  
  
     <span data-ttu-id="841d2-114">La console Administration de BizTalk Server ajoute le groupe BizTalk Server à l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="841d2-114">The BizTalk Server Administration console adds the BizTalk Server group to the console tree.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="841d2-115">Si la base de données de gestion BizTalk Server est hébergée sur un cluster SQL Server et si ce cluster est en train de basculer, il se peut qu'une erreur similaire à l'erreur suivante se produise lorsque vous tentez de vous connecter à la base de données de gestion :</span><span class="sxs-lookup"><span data-stu-id="841d2-115">If the BizTalk Server Management database is housed on a SQL Server cluster and the cluster is in the process of failing over then you may receive an error similar to the following when you attempt to connect to the Management database:</span></span>  
    >   
    >  <span data-ttu-id="841d2-116">Échec du chargement du groupe [\<nom_serveur\>:\<base de données de gestion\>] fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="841d2-116">Failed to load Group [\<servername\>:\<management database\>] data providers.</span></span>  
    >   
    >  <span data-ttu-id="841d2-117">And</span><span class="sxs-lookup"><span data-stu-id="841d2-117">And</span></span>  
    >   
    >  <span data-ttu-id="841d2-118">INFORMATIONS SUPPLÉMENTAIRES :</span><span class="sxs-lookup"><span data-stu-id="841d2-118">ADDITIONAL INFORMATION:</span></span>  
    >   
    >  <span data-ttu-id="841d2-119">Impossible de trouver l'instance de la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="841d2-119">Instance of the WMI class is not found.</span></span> <span data-ttu-id="841d2-120">(WinMgmt)</span><span class="sxs-lookup"><span data-stu-id="841d2-120">(WinMgmt)</span></span>  
    >   
    >  <span data-ttu-id="841d2-121">Cette erreur peut être due au fait que les bases de données BizTalk ne sont pas disponibles au moment où elles font l'objet d'un basculement.</span><span class="sxs-lookup"><span data-stu-id="841d2-121">This error can occur because the BizTalk databases are not available while they are being failed over.</span></span> <span data-ttu-id="841d2-122">Pour contourner ce problème, patientez jusqu'à ce que l’instance en cluster de SQL Server est en ligne avant d’essayer de vous y connecter avec la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="841d2-122">To workaround this issue, wait until after the clustered instance of SQL Server is online before attempting to connect to it with the BizTalk Server Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841d2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="841d2-123">See Also</span></span>  
 <span data-ttu-id="841d2-124">[Gestion des groupes](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="841d2-124">[Managing Groups](../core/managing-groups.md) </span></span>  
 [<span data-ttu-id="841d2-125">Groupes BizTalk</span><span class="sxs-lookup"><span data-stu-id="841d2-125">BizTalk Groups</span></span>](../core/biztalk-groups.md)