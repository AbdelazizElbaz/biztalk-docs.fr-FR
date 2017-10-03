---
title: "Importation des schémas PeopleSoft dans des projets BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
- component interfaces
- BizTalk Server, schemas [PeopleSoft]
- importing schemas into BizTalk Server
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4946b438adc0d1e4d360b35207ff69e85b4e2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-peoplesoft-schemas-into-biztalk-server-projects"></a><span data-ttu-id="f86e1-102">Importation des schémas PeopleSoft dans des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f86e1-102">Importing PeopleSoft Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="f86e1-103">Après avoir créé le système PeopleSoft Enterprise, vous pouvez accéder au serveur qui lui est associé et importer des schémas dans un projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f86e1-103">When you have created the PeopleSoft Enterprise system, you can browse the server and import schemas into a BizTalk Server project.</span></span>  
  
## <a name="browsing-a-peoplesoft-server-system"></a><span data-ttu-id="f86e1-104">Accès à un système serveur de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="f86e1-104">Browsing a PeopleSoft Server System</span></span>  
 <span data-ttu-id="f86e1-105">L'Assistant Adaptateur permet d'accéder à un serveur de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="f86e1-105">Use the Adapter Wizard to browse a PeopleSoft server.</span></span>  
  
#### <a name="to-browse-a-peoplesoft-server-system"></a><span data-ttu-id="f86e1-106">Pour accéder à un système serveur de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="f86e1-106">To browse a PeopleSoft server system</span></span>  
  
1.  <span data-ttu-id="f86e1-107">Cliquez avec le bouton droit sur un projet BizTalk Server, puis sélectionnez l'une des options suivantes.</span><span class="sxs-lookup"><span data-stu-id="f86e1-107">Right-click a BizTalk Server project, and select one of the following options.</span></span>  
  
    -   <span data-ttu-id="f86e1-108">Si vous avez déjà un schéma généré pour votre objet, sélectionnez **ajouter**, cliquez sur **ajouter un schéma,** , puis sélectionnez le schéma existant à ajouter à votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="f86e1-108">If you already have a schema generated for your object, select **Add**, click **Add Schema,** and then select the existing schema to add to your orchestration,.</span></span>  
  
    -   <span data-ttu-id="f86e1-109">Si vous ne disposez pas d’un schéma généré pour votre objet, sélectionnez **ajouter**, puis cliquez sur **ajouter les éléments générés**, puis sélectionnez la carte.</span><span class="sxs-lookup"><span data-stu-id="f86e1-109">If you do not have a schema generated for your object, select **Add**, then click **Add Generated Items**, and then select the adapter.</span></span> <span data-ttu-id="f86e1-110">Ceci est le même nom que celui entré dans le **AdapterProperties** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f86e1-110">This is the same name entered in the **AdapterProperties** dialog box.</span></span> <span data-ttu-id="f86e1-111">Pour plus d'informations, consultez la rubrique « Boîte de dialogue Propriétés de l'adaptateur » dans l'aide principale de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f86e1-111">For more information, see "Adapter Properties Dialog Box" in the main BizTalk help.</span></span>  
  
2.  <span data-ttu-id="f86e1-112">Cliquez sur Suivant.</span><span class="sxs-lookup"><span data-stu-id="f86e1-112">Click Next.</span></span>  
  
     <span data-ttu-id="f86e1-113">Le système PeopleSoft Enterprise s'affiche dans l'Explorateur.</span><span class="sxs-lookup"><span data-stu-id="f86e1-113">The PeopleSoft Enterprise system appears in the browser.</span></span>  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a><span data-ttu-id="f86e1-114">Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="f86e1-114">Component Interfaces</span></span>  
 <span data-ttu-id="f86e1-115">Dans le **Interfaces de composant** (CI), dossier, vous pouvez afficher toutes les interfaces de composant disponible dans le système.</span><span class="sxs-lookup"><span data-stu-id="f86e1-115">In the **Component Interfaces** (CI) folder, you can view all the available component interfaces in the system.</span></span> <span data-ttu-id="f86e1-116">Une interface de composant déclare l'ensemble des méthodes et des propriétés qu'elle prend en charge.</span><span class="sxs-lookup"><span data-stu-id="f86e1-116">A component interface declares the set of methods and properties that it supports.</span></span> <span data-ttu-id="f86e1-117">Elle n'implémente aucun comportement ni propriété.</span><span class="sxs-lookup"><span data-stu-id="f86e1-117">A component interface does not implement behavior or properties.</span></span> <span data-ttu-id="f86e1-118">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise expose des méthodes standard (par exemple, CreateEx, DeleteOnly, Find, Get et UpdateEx).</span><span class="sxs-lookup"><span data-stu-id="f86e1-118">Microsoft BizTalk Adapter for PeopleSoft Enterprise exposes standard methods, for example, CreateEx, DeleteOnly, Find, Get, and UpdateEx.</span></span> <span data-ttu-id="f86e1-119">Pour obtenir une description de ces méthodes, consultez [annexe a : composant Interface méthodes](../core/appendix-a-component-interface-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f86e1-119">For a description of these methods, see [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md).</span></span>  
  
## <a name="generating-schemas"></a><span data-ttu-id="f86e1-120">Création de schémas</span><span class="sxs-lookup"><span data-stu-id="f86e1-120">Generating Schemas</span></span>  
 <span data-ttu-id="f86e1-121">Effectuez ces étapes pour générer des schémas.</span><span class="sxs-lookup"><span data-stu-id="f86e1-121">Follow these steps to generate schemas.</span></span>  
  
#### <a name="to-generate-the-schemas"></a><span data-ttu-id="f86e1-122">Pour créer les schémas</span><span class="sxs-lookup"><span data-stu-id="f86e1-122">To generate the schemas</span></span>  
  
-   <span data-ttu-id="f86e1-123">Sélectionnez l’élément pour lequel vous souhaitez importer des schémas : un **Message**, **requête**, ou **Interface de composant**.</span><span class="sxs-lookup"><span data-stu-id="f86e1-123">Select the item for which you want to import schemas: a **Message**, **Query**, or **Component Interface**.</span></span>  
  
     <span data-ttu-id="f86e1-124">BizTalk Server génère les schémas pour l'élément sélectionné et les importe dans un projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f86e1-124">BizTalk Server generates the schemas for the selected item and imports them into a BizTalk Server project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f86e1-125">Si les définitions de l'objet serveur sont modifiées, vous devez recréer le schéma afin de mettre à jour les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="f86e1-125">If the server object definitions change, you must regenerate the schema to update the data it contains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86e1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f86e1-126">See Also</span></span>  
 [<span data-ttu-id="f86e1-127">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="f86e1-127">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)