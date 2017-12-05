---
title: "Comment ajouter des métadonnées de l’adaptateur à un projet BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e439e5bf-94b3-4582-bacc-b058e6eb8e17
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75aea1f23236d448f6efaa451d45663352fb3083
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-adapter-metadata-to-a-biztalk-project"></a><span data-ttu-id="b7c6c-102">Comment ajouter des métadonnées de l’adaptateur à un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="b7c6c-102">How to Add Adapter Metadata to a BizTalk Project</span></span>
<span data-ttu-id="b7c6c-103">L'Assistant Ajouter les métadonnées de l'adaptateur vous permet d'ajouter des métadonnées d'adaptateur à un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-103">The Add Adapter Metadata Wizard enables you to add adapter metadata to a BizTalk project.</span></span> <span data-ttu-id="b7c6c-104">Ces données sont les schémas, types de messages et types de ports requis pour communiquer avec un adaptateur à partir d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-104">This data includes schemas, message types, and port types needed to communicate with an adapter from an orchestration.</span></span> <span data-ttu-id="b7c6c-105">Servez-vous de cet Assistant avec les adaptateurs d'applications, tels que FTP, pour intégrer les schémas correspondant à ces adaptateurs d'applications au système.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-105">Use the Add Adapter Metadata Wizard with application adapters, such as FTP, to pull schemas corresponding to these application adapters into the system.</span></span> <span data-ttu-id="b7c6c-106">Notez que les adaptateurs de transport tels que HTTP n'utilisent généralement pas de schémas.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-106">Note that transport adapters such as HTTP do not typically use schemas.</span></span>  
  
 <span data-ttu-id="b7c6c-107">La procédure ci-dessous présente les étapes requises pour ajouter des métadonnées pour un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-107">The following procedure walks you through the generic steps to add metadata for an adapter.</span></span>  
  
### <a name="to-add-adapter-metadata-to-a-biztalk-project"></a><span data-ttu-id="b7c6c-108">Pour ajouter des métadonnées d'adaptateur à un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="b7c6c-108">To add adapter metadata to a BizTalk project</span></span>  
  
1.  <span data-ttu-id="b7c6c-109">Dans votre [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans l’Explorateur de solutions, cliquez sur votre projet, cliquez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-109">In your [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, in Solution Explorer, right-click your project, click **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="b7c6c-110">Dans le **ajouter les éléments générés - \<**  *nom du projet*  **\>**  boîte de dialogue le **modèles** section, Sélectionnez **ajouter un adaptateur**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-110">In the **Add Generated Items - \<***Project name***\>** dialog box, in the **Templates** section, select **Add Adapter**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="b7c6c-111">Dans l’Assistant Ajout de métadonnées d’adaptateur, sur le **sélectionner un adaptateur** page, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-111">In the Add Adapter Metadata Wizard, on the **Select Adapter** page, do the following.</span></span>  
  
    |<span data-ttu-id="b7c6c-112">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b7c6c-112">Use this</span></span>|<span data-ttu-id="b7c6c-113">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b7c6c-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b7c6c-114">Liste des adaptateurs</span><span class="sxs-lookup"><span data-stu-id="b7c6c-114">Adapter list box</span></span>|<span data-ttu-id="b7c6c-115">Sélectionner l'adaptateur inscrit à ajouter au projet. </span><span class="sxs-lookup"><span data-stu-id="b7c6c-115">Select the registered adapter to add to the project.</span></span>|  
    |<span data-ttu-id="b7c6c-116">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b7c6c-116">SQL Server</span></span>|<span data-ttu-id="b7c6c-117">Entrer le nom du serveur de base de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-117">Enter the BizTalk database server name.</span></span>|  
    |<span data-ttu-id="b7c6c-118">Base de données</span><span class="sxs-lookup"><span data-stu-id="b7c6c-118">Database</span></span>|<span data-ttu-id="b7c6c-119">Affiche la liste des bases de données de gestion BizTalk pour le serveur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-119">Displays the list of BizTalk Management databases for the chosen server.</span></span>|  
    |<span data-ttu-id="b7c6c-120">Port</span><span class="sxs-lookup"><span data-stu-id="b7c6c-120">Port</span></span>|<span data-ttu-id="b7c6c-121">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-121">Optional.</span></span> <span data-ttu-id="b7c6c-122">Afficher la liste des ports créés et enregistrés dans la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-122">Displays the list of ports created and stored in the BizTalk Management database.</span></span> <span data-ttu-id="b7c6c-123">Seuls les ports configurés pour fonctionner avec l'adaptateur sélectionné sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-123">Only ports configured to work with the selected adapter are shown.</span></span>|  
  
     <span data-ttu-id="b7c6c-124">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-124">Click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7c6c-125">Vous essayez d’ajouter des schémas générés qui contiennent des caractères que le **System.XML.XMLConvert** classe ne prend pas en charge les résultats dans une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-125">Attempting to add generated schemas that contain characters that the **System.XML.XMLConvert** class does not support results in a compilation error.</span></span>  
  
4.  <span data-ttu-id="b7c6c-126">Si vous utilisez un adaptateur statique, sur le **sélectionner les Services à importer** page, sélectionnez un ensemble de services disponibles à partir de l’arborescence, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-126">If you are using a static adapter, on the **Select Services to Import** page, select a set of available services from the tree view, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="b7c6c-127">- Ou -</span><span class="sxs-lookup"><span data-stu-id="b7c6c-127">–Or–</span></span>  
  
     <span data-ttu-id="b7c6c-128">Si vous utilisez un adaptateur dynamique, suivez la procédure de l'interface utilisateur personnalisée pour terminer l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-128">If you are using a dynamic adapter, follow the steps in the custom user interface to complete the wizard.</span></span>  
  
 <span data-ttu-id="b7c6c-129">Une fois la procédure terminée, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] affiche les fichiers .odx et .xsd dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="b7c6c-129">After you complete the wizard, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] lists the .odx and .xsd files in Solution Explorer.</span></span>