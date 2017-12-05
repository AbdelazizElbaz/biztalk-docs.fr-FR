---
title: "L’importation d’un PIP basé sur XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, importing
- XSD-based PIPs
- PIPs, XSD-based PIPs
ms.assetid: d12441d4-79bf-4c24-9360-4b78c1da0d34
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d8865d7a75bdb06895b963b8269ed457cd5804f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="importing-an-xsd-based-pip"></a><span data-ttu-id="df902-102">Importation d'un PIP basé sur XSD</span><span class="sxs-lookup"><span data-stu-id="df902-102">Importing an XSD-based PIP</span></span>
<span data-ttu-id="df902-103">Alors que la majorité des PIP fournis par RosettaNet.org est basée sur DTD, les PIP les plus récents sont basés sur XSD.</span><span class="sxs-lookup"><span data-stu-id="df902-103">While the majority of PIPS provided by RosettaNet.org are DTD-based, newer PIPS are XSD-based.</span></span> <span data-ttu-id="df902-104">La procédure suivante montre comment importer des PIP basés sur XSD.</span><span class="sxs-lookup"><span data-stu-id="df902-104">The following procedure describes how to import XSD-based PIPS.</span></span>  
  
### <a name="to-import-an-xsd-based-pip"></a><span data-ttu-id="df902-105">Pour importer un PIP basé sur XSD</span><span class="sxs-lookup"><span data-stu-id="df902-105">To import an XSD-based PIP</span></span>  
  
1.  <span data-ttu-id="df902-106">Téléchargez le fichier .zip du PIP basé sur XSD à partir de RosettaNet.org à l'adresse [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859) ou à partir de CIDX.org à l'adresse [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361).</span><span class="sxs-lookup"><span data-stu-id="df902-106">Download the XSD-based PIP .zip file from RosettaNet.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859) or from CIDX.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361).</span></span> <span data-ttu-id="df902-107">Extrayez les fichiers du fichier .zip.</span><span class="sxs-lookup"><span data-stu-id="df902-107">Extract the files from the .zip file.</span></span> <span data-ttu-id="df902-108">Les fichiers dont vous avez besoin se trouvent dans les sous-dossiers du dossier XML.</span><span class="sxs-lookup"><span data-stu-id="df902-108">The files that you need will be in the subfolders of the XML folder.</span></span>  
  
2.  <span data-ttu-id="df902-109">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df902-109">Open Visual Studio.</span></span> <span data-ttu-id="df902-110">Créez un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="df902-110">Create a new BizTalk project.</span></span>  
  
3.  <span data-ttu-id="df902-111">Ouvrez l'Explorateur Windows, puis accédez au dossier XML extrait à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="df902-111">Open Windows Explorer, and move to the XML folder extracted in step 1.</span></span> <span data-ttu-id="df902-112">Sélectionnez le premier dossier sous le dossier XML, faites-le glisser vers l'Explorateur de solutions dans Visual Studio, puis déposez-le dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="df902-112">Select the first folder under the XML folder, drag it to Solutions Explorer in Visual Studio, and drop it into your project.</span></span> <span data-ttu-id="df902-113">Répétez l'opération pour chacun des sous-dossiers du dossier XML, en créant la même structure de dossier dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="df902-113">Repeat for each of the subfolders in the XML folder, creating the same folder structure in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df902-114">Pour un PIP PIP7c7, ces dossiers incluent les dossiers Domain, Interchange, System et Universal.</span><span class="sxs-lookup"><span data-stu-id="df902-114">For a PIP7c7 PIP these folders would include the Domain, Interchange, System, and Universal folders.</span></span> <span data-ttu-id="df902-115">Pour ce PIP, votre projet doit contenir les dossiers Domain, Interchange, System et Universal, ainsi que leur contenu.</span><span class="sxs-lookup"><span data-stu-id="df902-115">For this PIP, your project should contain Domain, Interchange, System, and Universal folders and their contents.</span></span>  
  
4.  <span data-ttu-id="df902-116">Si le dossier système contient un fichier .xsd, sélectionnez ce fichier dans l'Explorateur de solutions et modifiez l'espace de noms répertorié dans la page de propriétés de façon à ce qu'il ne contienne pas la chaîne « .System ».</span><span class="sxs-lookup"><span data-stu-id="df902-116">If there is an .xsd file in the System folder, select it in Solution Explorer and change the namespace listed in the property page so that it does not contain the string ".System".</span></span> <span data-ttu-id="df902-117">Par exemple, pour le PIP PIP7c7, vous pouvez modifier l'espace de noms pour obtenir « PIP7c7._System ».</span><span class="sxs-lookup"><span data-stu-id="df902-117">For example, for PIP7c7 PIP, you could change the namespace to be "PIP7c7._System".</span></span> <span data-ttu-id="df902-118">Répétez l'opération pour chaque fichier .xsd situé dans le dossier System.</span><span class="sxs-lookup"><span data-stu-id="df902-118">Repeat for each .xsd file in the System folder.</span></span> <span data-ttu-id="df902-119">Si vous ne modifiez pas l'espace de noms, vous recevrez l'erreur suivante ou une erreur similaire :</span><span class="sxs-lookup"><span data-stu-id="df902-119">If you do not change the namespace, you will receive the following or a similar error:</span></span>  
  
    ```  
    The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'PIP7C7.System'.  
    ```  
  
5.  <span data-ttu-id="df902-120">Passez en revue tous les fichiers .xsd pour vous assurer que le \<schéma\> type du nœud racine et le nom de type ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="df902-120">Review all .xsd files to ensure that the \<schema\> TypeName and root node TypeName are not identical.</span></span> <span data-ttu-id="df902-121">Par exemple, pour un PIP pip7c7, le fichier partneridentification.xsd situé dans le dossier Universal a le nom de « PartnerIdentification » à la fois pour le \<schéma\> (lorsque PartnerIdentification.xsd est sélectionné dans l’Explorateur de solutions) et également le Nœud de racine PartnerIdentification.</span><span class="sxs-lookup"><span data-stu-id="df902-121">For example, for a PIP7C7 PIP the PartnerIdentification.xsd in the Universal folder has the TypeName of 'PartnerIdentification' for both the \<schema\> (when PartnerIdentification.xsd is selected in Solution Explorer) and also the PartnerIdentification root node.</span></span> <span data-ttu-id="df902-122">Pour corriger ce problème, sélectionnez PartnerIdentification.xsd dans l'Explorateur de solutions, puis, dans la page de propriété, modifiez la propriété TypeName afin qu'elle ne contienne pas le même nom de type que le nœud racine PartnerIdentification.</span><span class="sxs-lookup"><span data-stu-id="df902-122">To correct this, select PartnerIdentification.xsd in Solution Explorer, and then in the property page change the TypeName property so that it does not contain the same TypeName as the PartnerIdentification root node.</span></span> <span data-ttu-id="df902-123">Par exemple, remplacez le nom de type pour qu'il soit « _PartnerIdentification ».</span><span class="sxs-lookup"><span data-stu-id="df902-123">For example, change the TypeName to be "_PartnerIdentification".</span></span> <span data-ttu-id="df902-124">Si vous n'effectuez pas cette étape, vous recevez l'erreur suivante lorsque vous essayez de générer le projet :</span><span class="sxs-lookup"><span data-stu-id="df902-124">If you do not take this step, you will receive the following error when you try to build the project:</span></span>  
  
    ```  
    Node "<Schema>" - This schema file has a TypeName that collides with the RootNode TypeName of one of its root Nodes. Make sure that they are different.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="df902-125">La colonne File dans la liste d'erreurs indique quels fichiers subissent ce problème.</span><span class="sxs-lookup"><span data-stu-id="df902-125">The File column in the error list will indicate which files have this problem.</span></span>  
  
6.  <span data-ttu-id="df902-126">Générez et déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="df902-126">Build and then deploy the project.</span></span>