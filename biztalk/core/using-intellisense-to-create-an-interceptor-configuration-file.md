---
title: "L’utilisation d’IntelliSense pour créer un fichier de Configuration de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 349ea1bf-a5d1-4464-bf4b-d8746c622377
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7be3f79545db81a0127fc8d004d71c758069a55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-intellisense-to-create-an-interceptor-configuration-file"></a><span data-ttu-id="eb048-102">Utilisation d'IntelliSense pour créer un fichier de configuration d'intercepteur</span><span class="sxs-lookup"><span data-stu-id="eb048-102">Using IntelliSense to Create an Interceptor Configuration File</span></span>
<span data-ttu-id="eb048-103">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], la fonctionnalité IntelliSense et la validation de schéma vous permettent de créer des fichiers de configuration de l'intercepteur valides au niveau du schéma.</span><span class="sxs-lookup"><span data-stu-id="eb048-103">You can use IntelliSense and schema validation in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to help you construct interceptor configuration files that are schematically valid.</span></span> <span data-ttu-id="eb048-104">L'utilitaire de gestion de l'analyse BAM valide un fichier de configuration de l'intercepteur d'après un schéma de configuration de base et, si le fichier n'est pas valide, il n'autorise pas le déploiement de ce schéma.</span><span class="sxs-lookup"><span data-stu-id="eb048-104">The BAM management utility validates your interceptor configuration file against the base interceptor configuration schema and, if the file is not valid, does not deploy the schema.</span></span> <span data-ttu-id="eb048-105">Si un fichier réussit cette validation, il est ensuite soumis à validation au moment de l'exécution sur la base de schémas spécifiques à la technologie, comme les schémas [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] ou [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]. Si des erreurs surviennent, l'interception n'a pas lieu.</span><span class="sxs-lookup"><span data-stu-id="eb048-105">If the file passes validation against the base interceptor configuration schema, it is validated against technology-specific schemas like the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schema or the [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] schema during run time and if errors are encountered, no interception will occur.</span></span> <span data-ttu-id="eb048-106">Ces erreurs peuvent être évitées en utilisant la validation de schéma dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] au moment de la création du fichier de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="eb048-106">You can avoid these errors by using schema validation in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] when constructing your interceptor configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb048-107">Les exemples de fichiers XSD de configuration de l'intercepteur de l'analyse BAM sont installés avec les fichiers du Kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="eb048-107">The sample BAM interceptor configuration XSD files are installed with the SDK files.</span></span> <span data-ttu-id="eb048-108">Ils se trouvent dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs :</span><span class="sxs-lookup"><span data-stu-id="eb048-108">They can be found at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs:</span></span>  
>   
>  -   <span data-ttu-id="eb048-109">CommonInterceptorConfiguration.xsd</span><span class="sxs-lookup"><span data-stu-id="eb048-109">CommonInterceptorConfiguration.xsd</span></span>  
> -   <span data-ttu-id="eb048-110">WcfInterceptorConfiguration.xsd</span><span class="sxs-lookup"><span data-stu-id="eb048-110">WcfInterceptorConfiguration.xsd</span></span>  
> -   <span data-ttu-id="eb048-111">WorkflowInterceptorConfiguration.xsd</span><span class="sxs-lookup"><span data-stu-id="eb048-111">WorkflowInterceptorConfiguration.xsd</span></span>  
  
### <a name="to-obtain-a-copy-of-the-interceptor-schemas"></a><span data-ttu-id="eb048-112">Pour obtenir une copie des schémas de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="eb048-112">To obtain a copy of the interceptor schemas</span></span>  
  
1.  <span data-ttu-id="eb048-113">Ouvrez le Bloc-notes ou un autre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="eb048-113">Open Notepad or another text editor.</span></span>  
  
2.  <span data-ttu-id="eb048-114">Accédez à la [schéma de Configuration de l’intercepteur](../core/interceptor-configuration-schema.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="eb048-114">Navigate to the [Interceptor Configuration Schema](../core/interceptor-configuration-schema.md) topic.</span></span>  
  
3.  <span data-ttu-id="eb048-115">Coller le contenu dans un nouveau document dans l’éditeur de texte ouvert, puis enregistrez le fichier comme un fichier texte en utilisant le nom **CommonInterceptorConfiguration.xsd** (ou un de votre choix) sur votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="eb048-115">Paste the contents into a new document in the open text editor, and then save the file as a text file using the name **CommonInterceptorConfiguration.xsd** (or one of your own choosing) to your hard disk.</span></span>  
  
4.  <span data-ttu-id="eb048-116">Répétez ces étapes pour le [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schéma et [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] rubriques de schéma en utilisant les noms de fichier **WorkflowInterceptorConfiguration.xsd** et **WcfInterceptorConfiguration.xsd** ou des noms de votre choix.</span><span class="sxs-lookup"><span data-stu-id="eb048-116">Repeat these steps for the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schema and [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] schema topics using the file names **WorkflowInterceptorConfiguration.xsd** and **WcfInterceptorConfiguration.xsd** or names of your own choosing.</span></span>  
  
### <a name="to-use-intellisense-with-your-interceptor-configuration-file"></a><span data-ttu-id="eb048-117">Pour utiliser la fonctionnalité IntelliSense avec le fichier de configuration de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="eb048-117">To use IntelliSense with your interceptor configuration file</span></span>  
  
1.  <span data-ttu-id="eb048-118">Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb048-118">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb048-119">Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="eb048-119">Click **File**, click **New**, and then click **File**.</span></span>  
  
3.  <span data-ttu-id="eb048-120">Dans le **nouveau fichier** boîte de dialogue, sélectionnez **fichier XML** puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="eb048-120">In the **New File** dialog box, select **XML File** and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="eb048-121">Afficher le volet Propriétés en cliquant sur le volet d’édition, puis en cliquant **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="eb048-121">View the Properties pane by right-clicking the edit pane, and then clicking **Properties**.</span></span>  
  
5.  <span data-ttu-id="eb048-122">Dans le volet Propriétés, cliquez sur **schémas**, puis cliquez sur le bouton de sélection (**...** ).</span><span class="sxs-lookup"><span data-stu-id="eb048-122">In the Properties pane, click **Schemas**, and then click the ellipsis (**…**).</span></span>  
  
6.  <span data-ttu-id="eb048-123">Dans le **schémas XML** boîte de dialogue, cliquez sur **ajouter** , puis accédez à l’emplacement des schémas et sélectionnez **CommonInterceptorConfiguration.xsd** et  **WcfInterceptorConfiguration.xsd** si vous travaillez avec un [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] fichier de configuration de l’intercepteur, ou **WorkflowInterceptorConfiguration.xsd** si vous travaillez avec un [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] fichier de configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="eb048-123">In the **XML Schemas** dialog box, click **Add** and then navigate to the location of the schemas and select **CommonInterceptorConfiguration.xsd** and **WcfInterceptorConfiguration.xsd** if you are working with a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] interceptor configuration file, or **WorkflowInterceptorConfiguration.xsd** if you are working with a [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor configuration file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb048-124">Si vous avez enregistré ces fichiers sous des noms différents, sélectionnez-les.</span><span class="sxs-lookup"><span data-stu-id="eb048-124">If you saved the files using different names, select those files instead.</span></span>  
  
7.  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="eb048-125"> valide alors le fichier de configuration de l'intercepteur une fois celui-ci ouvert et offre une aide IntelliSense à mesure que vous créez et modifiez le fichier.</span><span class="sxs-lookup"><span data-stu-id="eb048-125"> will now validate your interceptor configuration file when it is opened and supply IntelliSense help as you create and modify the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb048-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb048-126">See Also</span></span>  
 <span data-ttu-id="eb048-127">[Schéma Windows Workflow Foundation](../core/windows-workflow-foundation-schema.md) </span><span class="sxs-lookup"><span data-stu-id="eb048-127">[Windows Workflow Foundation Schema](../core/windows-workflow-foundation-schema.md) </span></span>  
 [<span data-ttu-id="eb048-128">Schéma Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="eb048-128">Windows Communication Foundation Schema</span></span>](../core/windows-communication-foundation-schema.md)