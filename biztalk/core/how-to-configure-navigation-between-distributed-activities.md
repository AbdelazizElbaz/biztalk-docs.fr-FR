---
title: "Comment configurer la Navigation entre Distributed activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f8faf0a-eb06-4383-932d-4106306d6cf3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ab210f5ab728134b406b5c4bdaf25a1ec6db1c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-navigation-between-distributed-activities"></a><span data-ttu-id="296ac-102">Configuration de la navigation entre les activités distribuées</span><span class="sxs-lookup"><span data-stu-id="296ac-102">How to Configure Navigation Between Distributed Activities</span></span>
<span data-ttu-id="296ac-103">La navigation distribuée permet aux utilisateurs d'afficher les activités qui existent dans des déploiements BAM distants.</span><span class="sxs-lookup"><span data-stu-id="296ac-103">Distributed navigation allows users to view activities that exist in remote BAM deployments.</span></span> <span data-ttu-id="296ac-104">Lorsque vous activez la navigation distribuée, les personnes qui utilisent le portail BAM sur un ordinateur peuvent afficher les activités sur le portail BAM dans un autre déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="296ac-104">When you enable distributed navigation, users of the BAM portal on one computer will be able to view activities in the BAM portal on another deployment of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="296ac-105">La procédure de cette rubrique décrit l'activation de la navigation distribuée dans le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="296ac-105">The procedure in this topic describes how to enable distributed navigation in the following scenario:</span></span>  
  
-   <span data-ttu-id="296ac-106">Un service commercial avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déployé sur l'ordinateur 1.</span><span class="sxs-lookup"><span data-stu-id="296ac-106">A sales department with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployed on computer 1.</span></span>  
  
-   <span data-ttu-id="296ac-107">Un service d'expédition avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déployé sur l'ordinateur 2 (computer2).</span><span class="sxs-lookup"><span data-stu-id="296ac-107">A shipping department with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployed on computer 2.</span></span>  
  
-   <span data-ttu-id="296ac-108">Une vue nommée myBusinessView avec une activité nommée Sales Data déployée sur l'ordinateur 1.</span><span class="sxs-lookup"><span data-stu-id="296ac-108">A view called myBusinessView with an activity called Sales Data deployed on computer 1.</span></span>  
  
-   <span data-ttu-id="296ac-109">Une vue nommée myBusinessView avec une activité nommée Shipping Data installée sur l'ordinateur 2 (computer2).</span><span class="sxs-lookup"><span data-stu-id="296ac-109">A view called myBusinessView with an activity called Shipping Data installed on computer 2.</span></span>  
  
-   <span data-ttu-id="296ac-110">Un utilisateur des activités dans le service commercial ayant besoin d'afficher les activités sur les deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="296ac-110">A business user in the sales department with a business need to see the activities on both computers.</span></span>  
  
### <a name="how-to-set-up-distributed-navigation-for-remote-activities"></a><span data-ttu-id="296ac-111">Configuration de la navigation distribuée pour les activités distantes</span><span class="sxs-lookup"><span data-stu-id="296ac-111">How to set up distributed navigation for remote activities</span></span>  
  
1.  <span data-ttu-id="296ac-112">L’administrateur de l’ordinateur 1 accorde les activités utilisateur l’accès à la vue myBusinessView sur l’ordinateur 1.</span><span class="sxs-lookup"><span data-stu-id="296ac-112">The administrator of computer 1 grants the business user access to the myBusinessView view on computer 1.</span></span> <span data-ttu-id="296ac-113">Vous utilisez la commande bm.exe, comme suit : **ajouter-account - AccountName :\<nom de compte\> -View :** myBusinessView</span><span class="sxs-lookup"><span data-stu-id="296ac-113">You use the bm.exe command, as follows: **add-account -AccountName:\<account name\> -View:** myBusinessView</span></span>  
  
2.  <span data-ttu-id="296ac-114">L’administrateur de l’ordinateur 1 active la navigation distribuée en exécutant la commande enable-reference, comme suit : **bm.exe enable-reference - TargetServer :** Ordinateur2 **- TargetDatabase :\<cible base de données\>**</span><span class="sxs-lookup"><span data-stu-id="296ac-114">The administrator on computer 1 enables distributed navigation by running the enable reference command, as follows: **bm.exe enable-reference -TargetServer:** computer2 **-TargetDatabase:\<target database\>**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="296ac-115">En général, le compte utilisé entre les services pour l'accès aux services Web BAM diffère selon l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="296ac-115">Typically the account used between departments for BAM Web services access will be different on different computers.</span></span> <span data-ttu-id="296ac-116">Par conséquent, dans ce scénario, l’administrateur de l’ordinateur 1 doit ajouter le compte d’emprunt d’identité de services Web de l’ordinateur 1 au rôle BAM_ManagementWS de la base de données d’importation principale BAM pour l’ordinateur 2.</span><span class="sxs-lookup"><span data-stu-id="296ac-116">Therefore, in this scenario the administrator of computer 1 must add the Web services Impersonation account of computer 1 to the BAM_ManagementWS role of the BAM Primary Import database for computer 2.</span></span> <span data-ttu-id="296ac-117">Pour plus d’informations, consultez « Affichage et modification des appartenances au rôle » à [http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990).</span><span class="sxs-lookup"><span data-stu-id="296ac-117">For more information, see "Viewing and Modifying Role Memberships" at [http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="296ac-118">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="296ac-118">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
3.  <span data-ttu-id="296ac-119">L'administrateur de l'ordinateur 2 accorde à l'utilisateur des activités l'accès à la vue myBusinessView sur l'ordinateur 2 à l'aide de la commande BM.exe, comme cela est indiqué à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="296ac-119">The administrator of computer 2 grants the business user access to the myBusinessView view on computer 2 using the BM.exe command as noted in step 1.</span></span>  
  
## <a name="results-of-setting-up-distributed-navigation"></a><span data-ttu-id="296ac-120">Résultats de la configuration de la navigation distribuée</span><span class="sxs-lookup"><span data-stu-id="296ac-120">Results of Setting Up Distributed Navigation</span></span>  
 <span data-ttu-id="296ac-121">Lorsque la navigation distribuée est activée, les utilisateurs ajoutés aux vues sur les deux ordinateurs voient les activités des vues déployées sur les deux ordinateurs dans le volet Mes vues de leur portail de base.</span><span class="sxs-lookup"><span data-stu-id="296ac-121">When distributed navigation is enabled the users added to the views on both computers will see the activities for the views deployed on both computers in the My Views pane of their home portal.</span></span> <span data-ttu-id="296ac-122">Lorsque ces utilisateurs cliquent sur une activité qui est hébergée sur un déploiement à distance, il est redirigé en toute transparence au portail sur lequel qu’activité est hébergée, et ils sont en mesure d’afficher l’activité comme s’il se trouvait sur leur portail par défaut.</span><span class="sxs-lookup"><span data-stu-id="296ac-122">When these users click an activity that is hosted on a remote deployment, they are seamlessly directed to the portal on which that activity is hosted and they are able to view the activity as if it were on their default portal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="296ac-123">La navigation distribuée peut être activée dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="296ac-123">Distributed navigation can be enabled in both directions.</span></span> <span data-ttu-id="296ac-124">Suivez la procédure ci-dessus sur les deux ordinateurs qui partagent les activités distantes pour permettre aux utilisateurs des activités des portails de l'un des ordinateurs d'utiliser la navigation distribuée.</span><span class="sxs-lookup"><span data-stu-id="296ac-124">Following the procedure above on both computers that are sharing remote activities enables business users of the portals on either computer to use distributed navigation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296ac-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="296ac-125">See Also</span></span>  
 <span data-ttu-id="296ac-126">[Gestion de la Navigation distribuée des activités distantes](../core/managing-distributed-navigation-of-remote-activities.md) </span><span class="sxs-lookup"><span data-stu-id="296ac-126">[Managing Distributed Navigation of Remote Activities](../core/managing-distributed-navigation-of-remote-activities.md) </span></span>  
 [<span data-ttu-id="296ac-127">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="296ac-127">BAM Portal</span></span>](../core/bam-portal.md)