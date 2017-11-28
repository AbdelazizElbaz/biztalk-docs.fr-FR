---
title: "Procédure : configurer des bases de données BAM à l’aide de l’utilitaire de gestion BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801338f4-b363-4f8e-b248-9c628065ded2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9343cf9bd33f5880c564e2ec0dce72ece520ff01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-up-the-bam-databases-using-the-bam-management-utility"></a><span data-ttu-id="600e5-102">Configuration des bases de données BAM à l'aide de l'utilitaire de gestion de l'analyse BAM [BTS06]</span><span class="sxs-lookup"><span data-stu-id="600e5-102">How to Set Up the BAM Databases Using the BAM Management Utility</span></span>
<span data-ttu-id="600e5-103">Pour configurer les bases de données BAM, les administrateurs utilisent généralement l'utilitaire de configuration BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="600e5-103">Administrators typically use the BizTalk Server configuration utility to set up the BAM databases.</span></span> <span data-ttu-id="600e5-104">L'utilitaire de gestion de l'analyse BAM (bm.exe) constitue toutefois un autre moyen de configurer les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="600e5-104">You can use the BAM Management utility (bm.exe) as an alternate method to set up the databases.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="600e5-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="600e5-105">Prerequisites</span></span>  
 <span data-ttu-id="600e5-106">La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="600e5-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="600e5-107">Vous devez disposer des autorisations d'administrateur sur le serveur SQL hébergeant les bases de données BAMPrimaryImport, BAMStarSchema et BAMArchive.</span><span class="sxs-lookup"><span data-stu-id="600e5-107">You must have administrator permissions on the SQL server hosting the BAMPrimaryImport, BAMStarSchema, and BAMArchive databases.</span></span>  
  
-   <span data-ttu-id="600e5-108">Pour configurer les bases de données des services de notification SQL, vous devez disposer de l'autorisation d'administrateur et être membre du groupe des administrateurs locaux et de tout autre groupe d'administrateur ayant été configuré, par exemple le groupe des administrateurs BTS.</span><span class="sxs-lookup"><span data-stu-id="600e5-108">To set up the SQL Notification Services databases, you must have administrator permission and be a member of the local administrators group, as well as be a member of any additional administrator groups that have been configured, such as the BTS Admins group.</span></span>  
  
-   <span data-ttu-id="600e5-109">Vous devez avoir un fichier de configuration BAM contenant des données XML à partir desquelles configurer les bases de données.</span><span class="sxs-lookup"><span data-stu-id="600e5-109">You must have a BAM configuration file containing XML data from which to set up the databases.</span></span>  
  
### <a name="to-set-up-the-bam-databases-using-the-bam-management-utility"></a><span data-ttu-id="600e5-110">Pour configurer les bases de données BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="600e5-110">To set up the BAM databases using the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="600e5-111">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="600e5-111">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="600e5-112">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="600e5-112">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="600e5-113">Tapez la commande suivante à l’invite de ligne de commande : **bm le programme d’installation-bases de données - ConfigFile :\<fichier de configuration >**, où \< *fichier de configuration*> est remplacé par le nom de votre fichier de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="600e5-113">Type the following at the command line prompt: **bm setup-databases -ConfigFile:\<configuration file>**, where \<*configuration file*> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="600e5-114">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="600e5-114">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600e5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="600e5-115">See Also</span></span>  
 [<span data-ttu-id="600e5-116">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="600e5-116">BAM Management Utility</span></span>](../core/bam-management-utility.md)