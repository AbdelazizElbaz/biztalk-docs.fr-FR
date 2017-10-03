---
title: "Comment créer un modèle de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, creating
- creating, tracking profiles
ms.assetid: 676ae7e8-f3eb-45f1-ad2e-807b434c0bf9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f5d6cbb210cb292cd8ae7d0e2f4ff811984377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="a0d17-102">Création d'un modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="a0d17-102">How to Create a Tracking Profile</span></span>
<span data-ttu-id="a0d17-103">La création de modèles de suivi vous permet de lier des définitions d'activités BAM à des assemblys déployés et à des propriétés de messagerie BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a0d17-103">You create tracking profiles to link BAM activity definitions to deployed assemblies and BizTalk Server messaging properties.</span></span> <span data-ttu-id="a0d17-104">Lorsque vous ouvrez l’éditeur de modèle de suivi, vous pouvez créer un modèle de suivi en cliquant sur le lien de l’activité importation ou de l’élément de menu d’importation.</span><span class="sxs-lookup"><span data-stu-id="a0d17-104">When you open the Tracking Profile Editor, you can create a new tracking profile by either clicking the import activity link or the import menu item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a0d17-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a0d17-105">Prerequisites</span></span>  
 <span data-ttu-id="a0d17-106">La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a0d17-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="a0d17-107">une base de données de gestion BizTalk existante pour laquelle vous disposez d'autorisations d'accès ;</span><span class="sxs-lookup"><span data-stu-id="a0d17-107">An existing BizTalk Management database to which you have permissions.</span></span>  
  
-   <span data-ttu-id="a0d17-108">un Éditeur de modèle de suivi configuré de manière à pouvoir utiliser la base de données de gestion BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="a0d17-108">The TPE configured to use the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="a0d17-109">une définition d'activité BAM existante dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="a0d17-109">An existing BAM activity definition in the BAM Primary Import database.</span></span>  
  
### <a name="to-create-a-tracking-profile"></a><span data-ttu-id="a0d17-110">Pour créer un modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="a0d17-110">To create a tracking profile</span></span>  
  
1.  <span data-ttu-id="a0d17-111">Sur l’ou les ordinateurs que vous avez identifiés en tant que le système source, ouvrez le **éditeur**.</span><span class="sxs-lookup"><span data-stu-id="a0d17-111">On the computer or computers that you have identified as the source system, open the **Tracking Profile Editor**.</span></span> <span data-ttu-id="a0d17-112">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **BTSTrkEditor.exe**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a0d17-112">To do this, click **Start**, click **Run**, type **BTSTrkEditor.exe**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0d17-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a0d17-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="a0d17-114">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="a0d17-114">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="a0d17-115">Au milieu du volet gauche de l’éditeur, cliquez sur **cliquez ici pour importer une définition d’activité BAM** lien.</span><span class="sxs-lookup"><span data-stu-id="a0d17-115">In the middle of the left pane of the TPE, click **Click here to import a BAM Activity Definition** link.</span></span> <span data-ttu-id="a0d17-116">Cette opération ouvre le **importer une définition d’activité BAM** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a0d17-116">This opens the **Import BAM Activity Definition** dialog box.</span></span>  
  
3.  <span data-ttu-id="a0d17-117">À partir de la **le nom de définition d’activité BAM** zone de liste Sélectionnez l’activité sur laquelle baser le suivi.</span><span class="sxs-lookup"><span data-stu-id="a0d17-117">From the **BAM Activity Definition Name** list box select the activity on which to base the tracking.</span></span> <span data-ttu-id="a0d17-118">Si votre liste contient plusieurs activités déployées, vous pouvez taper une partie du nom de l’activité dans le **dans la chaîne** zone de texte et cliquez sur le **recherche** bouton.</span><span class="sxs-lookup"><span data-stu-id="a0d17-118">If your list contains many deployed activities, you can type part of the activity name in the **In String** text box and click the **Search** button.</span></span> <span data-ttu-id="a0d17-119">Cela permet de limiter la liste aux seules activités dont le nom contient une partie de la chaîne entrée.</span><span class="sxs-lookup"><span data-stu-id="a0d17-119">This limits the list of activities displayed to those whose names contain the partial name entered.</span></span>  
  
4.  <span data-ttu-id="a0d17-120">Une fois que vous avez sélectionné l’activité, cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="a0d17-120">Once you have selected the activity, click the **OK** button.</span></span> <span data-ttu-id="a0d17-121">Un nouveau modèle de suivi basé sur l'activité sélectionnée s'affiche tandis que le modèle apparaît dans le volet gauche de l'Éditeur.</span><span class="sxs-lookup"><span data-stu-id="a0d17-121">This opens a new tracking profile based on the activity selected and displays the profile in the left pane of the TPE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d17-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0d17-122">See Also</span></span>  
 [<span data-ttu-id="a0d17-123">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="a0d17-123">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)