---
title: "L’importation de schémas JD Edwards OneWorld dans des projets BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- importing schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
ms.assetid: 5bcaa276-8c76-4212-b373-de86e3008a69
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b0d7fec5acc991ae6c141f57297b7511281be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects"></a><span data-ttu-id="b62c3-102">Importation de schémas JD Edwards OneWorld dans des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b62c3-102">Importing JD Edwards OneWorld Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="b62c3-103">Cette rubrique traite de la recherche d'un serveur JD Edwards OneWorld et de l'importation des schémas dans un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b62c3-103">This topic discusses browsing a JD Edwards OneWorld server and importing the schemas into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b62c3-104">Vous devez vérifier que vous avez défini le fichier arglist.</span><span class="sxs-lookup"><span data-stu-id="b62c3-104">You must ensure that you set the arglist.</span></span> <span data-ttu-id="b62c3-105">Vous devez également mettre à jour le fichier jdearglist.txt avant de générer les schémas dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b62c3-105">You must update the jdearglist.txt before you generate the schemas in the orchestration.</span></span> <span data-ttu-id="b62c3-106">Pour plus d’informations, consultez [gestion des valeurs de chaîne](../core/handling-string-values1.md).</span><span class="sxs-lookup"><span data-stu-id="b62c3-106">For more information, see [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b62c3-107">Chaque fois que vous modifiez le fichier jdearglist, vous devez régénérer les schémas pour cet objet métier.</span><span class="sxs-lookup"><span data-stu-id="b62c3-107">Each time that you change the jdearglist, you must regenerate the schemas for that business object.</span></span>  
  
 <span data-ttu-id="b62c3-108">Après avoir créé le système logique JD Edwards OneWorld, vous pouvez parcourir JD Edwards OneWorld en ouvrant l'Assistant Adaptateur Microsoft à partir d'un projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b62c3-108">After creating the JD Edwards OneWorld logical system, you can browse JD Edwards OneWorld by opening the Microsoft Adapter Wizard from a BizTalk Server project.</span></span>  
  
### <a name="to-import-schemas"></a><span data-ttu-id="b62c3-109">Pour importer des schémas</span><span class="sxs-lookup"><span data-stu-id="b62c3-109">To import schemas</span></span>  
  
1.  <span data-ttu-id="b62c3-110">Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b62c3-110">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="b62c3-111">Avec le bouton droit le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="b62c3-111">Right-click the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="b62c3-112">Cliquez sur **ajouter un adaptateur**, puis sélectionnez **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="b62c3-112">Click **Add adapter**, and select **Open**.</span></span>  
  
4.  <span data-ttu-id="b62c3-113">Sélectionnez la carte, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b62c3-113">Select the adapter, and click **Next**.</span></span>  
  
     <span data-ttu-id="b62c3-114">Le JD.</span><span class="sxs-lookup"><span data-stu-id="b62c3-114">The JD.</span></span> <span data-ttu-id="b62c3-115">Système d’Edwards OneWorld XE s’affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="b62c3-115">Edwards OneWorld XE system appears in the browser.</span></span>  
  
     ![](../core/media/jdedadapter-04-jdebrowse.gif "JDEdAdapter_04_JDEBrowse")  
  
     <span data-ttu-id="b62c3-116">L'assistant Adaptateur affiche une arborescence de tous les systèmes définis.</span><span class="sxs-lookup"><span data-stu-id="b62c3-116">The Adapter Wizard displays a tree of all of the defined systems.</span></span> <span data-ttu-id="b62c3-117">JD Edwards OneWorld possède un nombre de modules trop important pour tous les afficher dans un seule grande liste.</span><span class="sxs-lookup"><span data-stu-id="b62c3-117">JD Edwards OneWorld has too many modules to show in one long list.</span></span> <span data-ttu-id="b62c3-118">Les modules sont regroupés selon les trois premiers caractères de leur nom.</span><span class="sxs-lookup"><span data-stu-id="b62c3-118">The modules are grouped together according to the first three characters of their name.</span></span>  
  
    -   <span data-ttu-id="b62c3-119">Le premier niveau de la hiérarchie correspond à la liste des préfixes à trois caractères des noms de module.</span><span class="sxs-lookup"><span data-stu-id="b62c3-119">The first level of the hierarchy is the list of all three-character prefixes for the module names.</span></span>  
  
    -   <span data-ttu-id="b62c3-120">Le second niveau inclut les modules qui partagent le même préfixe à trois caractères.</span><span class="sxs-lookup"><span data-stu-id="b62c3-120">The second level lists all the modules that share the same three-character prefix.</span></span>  
  
    -   <span data-ttu-id="b62c3-121">Le dernier niveau répertorie les fonctions commerciales appartenant à un module.</span><span class="sxs-lookup"><span data-stu-id="b62c3-121">The last level lists the business functions belonging to a module.</span></span> <span data-ttu-id="b62c3-122">Lorsque vous développez l'icône des services, vous affichez ses opérations.</span><span class="sxs-lookup"><span data-stu-id="b62c3-122">When you expand the services icon you can view its operations.</span></span>  
  
     <span data-ttu-id="b62c3-123">Le développement d'une opération affiche les arguments d'entrée/de sortie.</span><span class="sxs-lookup"><span data-stu-id="b62c3-123">Expanding an operation displays the input/output arguments.</span></span>  
  
     <span data-ttu-id="b62c3-124">Vous pouvez développer les arguments d'entrée/de sortie pour afficher les types de données des arguments.</span><span class="sxs-lookup"><span data-stu-id="b62c3-124">You can expand the input/output arguments to view the data types of the arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b62c3-125">Si les définitions d'objet serveur sont modifiées, vous devez régénérer le schéma afin d'actualiser les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="b62c3-125">If the server object definitions change, you must regenerate the schema to refresh the data it contains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b62c3-126">Si vous modifiez le fichier jdearglist.txt après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="b62c3-126">If you change jdearglist.txt after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span> <span data-ttu-id="b62c3-127">Pour plus d’informations sur le fichier jdearglist.txt, consultez [gestion des valeurs de chaîne](../core/handling-string-values1.md).</span><span class="sxs-lookup"><span data-stu-id="b62c3-127">For information on jdearglist.txt, see to [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
## <a name="generating-schemas"></a><span data-ttu-id="b62c3-128">Création de schémas</span><span class="sxs-lookup"><span data-stu-id="b62c3-128">Generating Schemas</span></span>  
 <span data-ttu-id="b62c3-129">La procédure suivante permet de générer des schémas.</span><span class="sxs-lookup"><span data-stu-id="b62c3-129">Use the following procedure to generate schemas.</span></span>  
  
#### <a name="to-generate-schemas"></a><span data-ttu-id="b62c3-130">Pour créer des schémas</span><span class="sxs-lookup"><span data-stu-id="b62c3-130">To generate schemas</span></span>  
  
1.  <span data-ttu-id="b62c3-131">Sélectionnez l'élément pour lequel vous souhaitez importer des schémas.</span><span class="sxs-lookup"><span data-stu-id="b62c3-131">Select the item for which you want to import schemas.</span></span>  
  
2.  <span data-ttu-id="b62c3-132">Cliquez sur (ou faites glisser) pour ajouter l’élément à la **transmission** volet (pour un trafic entrant vers JD Edwards OneWorld call).</span><span class="sxs-lookup"><span data-stu-id="b62c3-132">Click (or drag) to add the item to the **Transmit** pane (for an inbound to J. Edwards OneWorld call).</span></span>  
  
3.  <span data-ttu-id="b62c3-133">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b62c3-133">Click **OK**.</span></span>  
  
     <span data-ttu-id="b62c3-134">Les schémas générés pour l'élément JD Edwards OneWorld sélectionné sont importés dans le projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b62c3-134">Schemas generated for the selected JD Edwards OneWorld item are imported into the BizTalk Server project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b62c3-135">Lors de l’utilisation de carnet d’adresses (N0100041) le nom du champ est **cActionCode**.</span><span class="sxs-lookup"><span data-stu-id="b62c3-135">When using AddressBook (N0100041) the field name is **cActionCode**.</span></span> <span data-ttu-id="b62c3-136">L'action fait partie du fichier XML lui-même.</span><span class="sxs-lookup"><span data-stu-id="b62c3-136">The action is part of the XML file itself.</span></span> <span data-ttu-id="b62c3-137">Les codes suivants sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="b62c3-137">The codes are:</span></span>  
>   
>  <span data-ttu-id="b62c3-138">--A pour Ajouter ;</span><span class="sxs-lookup"><span data-stu-id="b62c3-138">--A for Add</span></span>  
>   
>  <span data-ttu-id="b62c3-139">--C pour Modifier ;</span><span class="sxs-lookup"><span data-stu-id="b62c3-139">--C for Change</span></span>  
>   
>  <span data-ttu-id="b62c3-140">--D pour Supprimer ;</span><span class="sxs-lookup"><span data-stu-id="b62c3-140">--D for Delete</span></span>  
>   
>  <span data-ttu-id="b62c3-141">--I pour Requête.</span><span class="sxs-lookup"><span data-stu-id="b62c3-141">--I for Inquiry</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62c3-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b62c3-142">See Also</span></span>  
 [<span data-ttu-id="b62c3-143">Création de gestionnaires de JD Edwards OneWorld envoi</span><span class="sxs-lookup"><span data-stu-id="b62c3-143">Creating JD Edwards OneWorld Send Handlers</span></span>](../core/creating-jd-edwards-oneworld-send-handlers.md)