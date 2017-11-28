---
title: "Comment activer les Services de Notifications sur d’autres ordinateurs dans un groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 571d6b45-b0cc-47f2-bed3-7c6f3e70decc
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b65596e59820258df01a5655ea30adafe439674
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-notifications-services-on-additional-computers-in-a-group"></a><span data-ttu-id="934cb-102">Activation des services de notification sur les autres ordinateurs d'un groupe</span><span class="sxs-lookup"><span data-stu-id="934cb-102">How to Enable Notifications Services on Additional Computers In A Group</span></span>
<span data-ttu-id="934cb-103">Lorsque vous exécutez l'analyse BAM dans un environnement multiserveur, vous devez activer les services Notification Services sur tous les ordinateurs sur lesquels vous envisagez d'exécuter l'utilitaire de gestion de l'analyse BAM afin de déployer une activité.</span><span class="sxs-lookup"><span data-stu-id="934cb-103">When running BAM in a multi-computer environment, you must enable Notification Services on each computer on which you will run the BAM Management Utility to deploy an activity.</span></span>  
  
 <span data-ttu-id="934cb-104">Examinez le cas suivant :</span><span class="sxs-lookup"><span data-stu-id="934cb-104">Consider the following scenario:</span></span>  
  
-   <span data-ttu-id="934cb-105">Le groupe A est composé des ordinateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="934cb-105">Group A consists of the following computers:</span></span>  
  
    -   <span data-ttu-id="934cb-106">L'ordinateur 1 sert à administrer l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="934cb-106">Computer 1 is used as a BAM administration computer.</span></span>  
  
    -   <span data-ttu-id="934cb-107">L'ordinateur 2 héberge les bases de données de schémas en étoile et BAM PIT.</span><span class="sxs-lookup"><span data-stu-id="934cb-107">Computer 2 hosts the BAM PIT and Star Schema database.</span></span>  
  
    -   <span data-ttu-id="934cb-108">L'ordinateur 3 héberge les bases de données d'analyse et d'archives BAM.</span><span class="sxs-lookup"><span data-stu-id="934cb-108">Computer 3 hosts the BAM Archive and Analysis databases.</span></span>  
  
    -   <span data-ttu-id="934cb-109">L'ordinateur 4 héberge les bases de données d'alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="934cb-109">Computer 4 hosts the BAM Alerts database.</span></span>  
  
    -   <span data-ttu-id="934cb-110">L'ordinateur 5 héberge le reste des bases de données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="934cb-110">Computer 5 hosts the rest of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
-   <span data-ttu-id="934cb-111">Groupe B :</span><span class="sxs-lookup"><span data-stu-id="934cb-111">Group B:</span></span>  
  
    -   <span data-ttu-id="934cb-112">L'ordinateur 6 sert à l'administration de l'analyse BAM. Il contient toutes les bases de données partagées avec le groupe A.</span><span class="sxs-lookup"><span data-stu-id="934cb-112">Computer 6 is used as a BAM administration computer on which all the databases are shared with Group A.</span></span>  
  
 <span data-ttu-id="934cb-113">Pour pouvoir déployer une activité dans les bases de données du groupe A à partir de l'ordinateur du groupe B, vous devez commencer par inscrire les services Notification Services avec le serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les hébergeant.</span><span class="sxs-lookup"><span data-stu-id="934cb-113">To be able to deploy an activity to the databases in group A from the computer in group B, you must first register the Notification Services with the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] hosting the notifications services.</span></span> <span data-ttu-id="934cb-114">Si ces services ne sont pas inscrits, vous recevrez le message d'erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="934cb-114">If the Notification Services are not registered, you will receive the following error:</span></span>  
  
 <span data-ttu-id="934cb-115">Déploiement de l'alerte en cours... Erreur : Échec du déploiement de l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="934cb-115">Deploying Alert... ERROR: The BAM deployment failed.</span></span>  
  
 <span data-ttu-id="934cb-116">Les alertes n'ont pas été déployées.</span><span class="sxs-lookup"><span data-stu-id="934cb-116">The alerts were not deployed.</span></span>  
  
 <span data-ttu-id="934cb-117">Une exception a été levée par la cible d'un appel.</span><span class="sxs-lookup"><span data-stu-id="934cb-117">Exception has been thrown by the target of an invocation.</span></span>  
  
 <span data-ttu-id="934cb-118">Les entrées de registre de l'instance spécifiée de Notification Services sont introuvables.</span><span class="sxs-lookup"><span data-stu-id="934cb-118">The registry entries for the specified instance of Notification Services could not be found.</span></span>  
  
### <a name="to-register-notifications-services-additional-computers"></a><span data-ttu-id="934cb-119">Pour inscrire les services Notification Services sur d'autres ordinateurs</span><span class="sxs-lookup"><span data-stu-id="934cb-119">To register notifications services additional computers</span></span>  
  
1.  <span data-ttu-id="934cb-120">Sur l’ordinateur du groupe supplémentaire, cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **invite de commandes de Notification Services**.</span><span class="sxs-lookup"><span data-stu-id="934cb-120">On the computer in the additional group, click **Start**, point to **All Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="934cb-121">À l’invite de commandes, tapez : **nscontrol register - nom \<NS du préfixe de nom choisie au config >-server \<serveur ns db sql >**.</span><span class="sxs-lookup"><span data-stu-id="934cb-121">At the command prompt, type: **nscontrol register -name \<NS Prefix name chosen at config> -server \<ns db sql server>**.</span></span> <span data-ttu-id="934cb-122">Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le registre de l'ordinateur du service).</span><span class="sxs-lookup"><span data-stu-id="934cb-122">This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service machine by nscontrol).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934cb-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="934cb-123">See Also</span></span>  
 <span data-ttu-id="934cb-124">[Modification des paramètres d’exécution BAM](../core/changing-bam-runtime-settings.md) </span><span class="sxs-lookup"><span data-stu-id="934cb-124">[Changing BAM Runtime Settings](../core/changing-bam-runtime-settings.md) </span></span>  
 [<span data-ttu-id="934cb-125">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="934cb-125">BAM Management Utility</span></span>](../core/bam-management-utility.md)