---
title: "Importer des schémas PeopleSoft dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6af82459f8b51f3dfa73a52593db18d25365c2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="import-peoplesoft-schemas-into-biztalk-server-projects"></a><span data-ttu-id="1fe1b-102">Importer des schémas PeopleSoft dans des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1fe1b-102">Import PeopleSoft Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="1fe1b-103">Après avoir créé le système PeopleSoft Enterprise, vous pouvez accéder au serveur qui lui est associé et importer des schémas dans un projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-103">When you have created the PeopleSoft Enterprise system, you can browse the server and import schemas into a BizTalk Server project.</span></span>  
  
## <a name="browse-a-peoplesoft-server-system"></a><span data-ttu-id="1fe1b-104">Accéder à un système de serveur de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="1fe1b-104">Browse a PeopleSoft Server System</span></span>  
  
1.  <span data-ttu-id="1fe1b-105">Cliquez avec le bouton droit sur un projet BizTalk Server, puis sélectionnez l'une des options suivantes.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-105">Right-click a BizTalk Server project, and select one of the following options.</span></span>  
  
    -   <span data-ttu-id="1fe1b-106">Si vous avez déjà un schéma généré pour votre objet, sélectionnez **ajouter**, cliquez sur **ajouter un schéma,** , puis sélectionnez le schéma existant à ajouter à votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-106">If you already have a schema generated for your object, select **Add**, click **Add Schema,** and then select the existing schema to add to your orchestration,.</span></span>  
  
    -   <span data-ttu-id="1fe1b-107">Si vous ne disposez pas d’un schéma généré pour votre objet, sélectionnez **ajouter**, puis cliquez sur **ajouter les éléments générés**, puis sélectionnez la carte.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-107">If you do not have a schema generated for your object, select **Add**, then click **Add Generated Items**, and then select the adapter.</span></span> <span data-ttu-id="1fe1b-108">Ceci est le même nom que celui entré dans le **AdapterProperties** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-108">This is the same name entered in the **AdapterProperties** dialog box.</span></span> <span data-ttu-id="1fe1b-109">Pour plus d'informations, consultez la rubrique « Boîte de dialogue Propriétés de l'adaptateur » dans l'aide principale de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-109">For more information, see "Adapter Properties Dialog Box" in the main BizTalk help.</span></span>  
  
2.  <span data-ttu-id="1fe1b-110">Cliquez sur Suivant.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-110">Click Next.</span></span>  
  
     <span data-ttu-id="1fe1b-111">Le système PeopleSoft Enterprise s'affiche dans l'Explorateur.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-111">The PeopleSoft Enterprise system appears in the browser.</span></span>  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a><span data-ttu-id="1fe1b-112">Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="1fe1b-112">Component Interfaces</span></span>  
 <span data-ttu-id="1fe1b-113">Dans le **Interfaces de composant** (CI), dossier, vous pouvez afficher toutes les interfaces de composant disponible dans le système.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-113">In the **Component Interfaces** (CI) folder, you can view all the available component interfaces in the system.</span></span> <span data-ttu-id="1fe1b-114">Une interface de composant déclare l'ensemble des méthodes et des propriétés qu'elle prend en charge.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-114">A component interface declares the set of methods and properties that it supports.</span></span> <span data-ttu-id="1fe1b-115">Elle n'implémente aucun comportement ni propriété.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-115">A component interface does not implement behavior or properties.</span></span> <span data-ttu-id="1fe1b-116">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise expose des méthodes standard (par exemple, CreateEx, DeleteOnly, Find, Get et UpdateEx).</span><span class="sxs-lookup"><span data-stu-id="1fe1b-116">Microsoft BizTalk Adapter for PeopleSoft Enterprise exposes standard methods, for example, CreateEx, DeleteOnly, Find, Get, and UpdateEx.</span></span> <span data-ttu-id="1fe1b-117">Pour obtenir une description de ces méthodes, consultez [annexe a : composant Interface méthodes](../core/appendix-a-component-interface-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1fe1b-117">For a description of these methods, see [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md).</span></span>  
  
## <a name="generate-schemas"></a><span data-ttu-id="1fe1b-118">Générer des schémas</span><span class="sxs-lookup"><span data-stu-id="1fe1b-118">Generate Schemas</span></span>  
  
<span data-ttu-id="1fe1b-119">Sélectionnez l’élément pour lequel vous souhaitez importer des schémas : un **Message**, **requête**, ou **Interface de composant**.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-119">Select the item for which you want to import schemas: a **Message**, **Query**, or **Component Interface**.</span></span>  <span data-ttu-id="1fe1b-120">BizTalk Server génère les schémas pour l'élément sélectionné et les importe dans un projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-120">BizTalk Server generates the schemas for the selected item and imports them into a BizTalk Server project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fe1b-121">Si les définitions de l'objet serveur sont modifiées, vous devez recréer le schéma afin de mettre à jour les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-121">If the server object definitions change, you must regenerate the schema to update the data it contains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe1b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fe1b-122">See Also</span></span>  
 [<span data-ttu-id="1fe1b-123">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="1fe1b-123">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)