---
title: "Gérer (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, examples
- utilities, SSOMANAGE
- examples, SSO
- SSOMANAGE command line utility
ms.assetid: f738e344-4d81-4557-b399-68b59c413245
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15a94bf916550d9a2eada9b8f354432b4c154ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-server-sample"></a><span data-ttu-id="18cd8-102">Gérer (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="18cd8-102">Manage (BizTalk Server Sample)</span></span>
<span data-ttu-id="18cd8-103">L'exemple de gestion de l'authentification unique (Manage Single Sign-On) illustre la génération de fichiers .xml que vous pouvez utiliser avec l'utilitaire de ligne de commande ssomanage.exe pour effectuer les types d'opérations d'administration suivants :</span><span class="sxs-lookup"><span data-stu-id="18cd8-103">The Manage Single Sign-On (SSO) sample demonstrates how to construct .xml files that you can use with the ssomanage.exe command-line utility to perform the following types of administration operations:</span></span>  
  
-   <span data-ttu-id="18cd8-104">mise à jour des informations globales au niveau du système d'authentification unique ;</span><span class="sxs-lookup"><span data-stu-id="18cd8-104">Update global information at the SSO system level</span></span>  
  
-   <span data-ttu-id="18cd8-105">création d'applications associées ;</span><span class="sxs-lookup"><span data-stu-id="18cd8-105">Create affiliate applications</span></span>  
  
-   <span data-ttu-id="18cd8-106">création de mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="18cd8-106">Create user mappings</span></span>  
  
 <span data-ttu-id="18cd8-107">Pour obtenir des informations conceptuelles sur Enterprise Single Sign-On, consultez [à l’aide de l’authentification unique](../core/using-sso.md).</span><span class="sxs-lookup"><span data-stu-id="18cd8-107">For conceptual information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).</span></span>  
  
 <span data-ttu-id="18cd8-108">Pour voir un exemple qui montre comment configurer par programme l’authentification unique, telles que la création d’applications associées et des mappages utilisateur, [HTTPSSO (exemple BizTalk Server)](../core/httpsso-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="18cd8-108">For a sample that shows how to programmatically configure SSO, such as creating affiliate applications and user mappings, see [HTTPSSO (BizTalk Server Sample)](../core/httpsso-biztalk-server-sample.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="18cd8-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="18cd8-109">What This Sample Does</span></span>  
 <span data-ttu-id="18cd8-110">Cet exemple inclut des paires de fichiers XSD et fichiers .xml d'exemple pour chacun des types d'opérations mentionnés plus haut.</span><span class="sxs-lookup"><span data-stu-id="18cd8-110">This sample includes pairs of XSD and sample .xml files for each of these types of operations.</span></span> <span data-ttu-id="18cd8-111">Les valeurs des fichiers .xml d'exemple ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="18cd8-111">The values in the sample .xml files are not valid.</span></span> <span data-ttu-id="18cd8-112">Vous devez les modifier sur des valeurs adaptées à vos besoins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="18cd8-112">You must make changes to the values that are appropriate to your specific requirements.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="18cd8-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="18cd8-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="18cd8-114">*\<Exemples de chemin d’accès >*\SSO\Manage\\</span><span class="sxs-lookup"><span data-stu-id="18cd8-114">*\<Samples Path>*\SSO\Manage\\</span></span>  
  
 <span data-ttu-id="18cd8-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="18cd8-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="18cd8-116">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="18cd8-116">File(s)</span></span>|<span data-ttu-id="18cd8-117"> Description</span><span class="sxs-lookup"><span data-stu-id="18cd8-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18cd8-118">AffiliateApplication.xml, GlobalInfo.xml, UserMapping.xml</span><span class="sxs-lookup"><span data-stu-id="18cd8-118">AffiliateApplication.xml, GlobalInfo.xml, UserMapping.xml</span></span>|<span data-ttu-id="18cd8-119">Fichiers .xml d'exemple que vous pouvez, après modification, transmettre sous forme d'arguments à l'utilitaire de ligne de commande ssomanage.exe.</span><span class="sxs-lookup"><span data-stu-id="18cd8-119">Sample .xml files that you can, after modification, pass as arguments to the command-line utility ssomanage.exe.</span></span>|  
|<span data-ttu-id="18cd8-120">AffiliateApplication.xsd, GlobalInfo.xsd, UserMapping.xsd</span><span class="sxs-lookup"><span data-stu-id="18cd8-120">AffiliateApplication.xsd, GlobalInfo.xsd, UserMapping.xsd</span></span>|<span data-ttu-id="18cd8-121">Fichiers de schéma pour les fichiers .xml correspondants, qui fournissent une description complète de leurs éléments et attributs possibles.</span><span class="sxs-lookup"><span data-stu-id="18cd8-121">Schema files for the corresponding .xml files, providing complete descriptions of their possible elements and attributes.</span></span> <span data-ttu-id="18cd8-122">Vous pouvez utiliser ces fichiers pour valider les fichiers .xml correspondants reçus d'autres sources.</span><span class="sxs-lookup"><span data-stu-id="18cd8-122">You can use these files to validate corresponding .xml files received from other sources.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="18cd8-123">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="18cd8-123">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="18cd8-124">Comme cet exemple est constitué de fichiers XSD (XML Schema definition language) et de fichiers .xml uniquement, ces derniers pouvant être modifiés avant d'être transmis à l'utilitaire de ligne de commande ssomanage.exe, il n'y a pas d'étape de création dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="18cd8-124">Because this sample consists of only XML Schema definition language (XSD) and .xml files, the latter of which you can modify and then pass to the command-line utility ssomanage.exe, there is nothing to build in this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="18cd8-125">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="18cd8-125">Running This Sample</span></span>  
 <span data-ttu-id="18cd8-126">Cet exemple inclut des fichiers .xml d'exemple pour l'exécution de l'utilitaire de ligne de commande ssomanage.exe dans les trois modes suivants :</span><span class="sxs-lookup"><span data-stu-id="18cd8-126">This sample includes sample .xml files for running the command-line utility ssomanage.exe in the following three different modes:</span></span>  
  
-   <span data-ttu-id="18cd8-127">**Mettre à jour des informations globales au niveau du système d’authentification unique.**</span><span class="sxs-lookup"><span data-stu-id="18cd8-127">**Update global information at the SSO system level.**</span></span> <span data-ttu-id="18cd8-128">. Pour effectuer ce type d'opération, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="18cd8-128">To perform this type of operation, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="18cd8-129">Vous devez modifier le fichier GlobalInfo.xml en utilisant des valeurs adaptées à votre configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="18cd8-129">Edit the file GlobalInfo.xml as required for your specific configuration.</span></span>  
  
    2.  <span data-ttu-id="18cd8-130">Exécutez l'utilitaire de ligne de commande ssomanage.exe à l'aide des arguments appropriés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="18cd8-130">Run the ssomanage.exe command-line utility with the appropriate arguments, as follows:</span></span>  
  
        ```  
        ssomanage –updatedb GlobalInfo.xml  
        ```  
  
     <span data-ttu-id="18cd8-131">Veillez à modifier les valeurs du fichier GlobalInfo.xml sur des valeurs adaptées à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="18cd8-131">Ensure that you edit the values in the file GlobalInfo.xml to match your environment.</span></span> <span data-ttu-id="18cd8-132">Par exemple, le compte d'administrateur de l'authentification unique doit être un compte Windows valide.</span><span class="sxs-lookup"><span data-stu-id="18cd8-132">For example, the SSO Admin account must be a valid Windows account.</span></span> <span data-ttu-id="18cd8-133">Le compte d'administrateur de l'authentification unique et le compte d'administrateur d'applications associées à authentification unique doivent être des comptes de groupe global de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="18cd8-133">Both the SSO Admin account and SSO Affiliate Admin account must be Windows Global Domain Group accounts.</span></span>  
  
-   <span data-ttu-id="18cd8-134">**Création d’applications associées.**</span><span class="sxs-lookup"><span data-stu-id="18cd8-134">**Create affiliate applications.**</span></span> <span data-ttu-id="18cd8-135">. Pour effectuer ce type d'opération, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="18cd8-135">To perform this type of operation, perform the following steps:</span></span>  
  
-   <span data-ttu-id="18cd8-136">Modifiez le fichier AffiliateApplication.xml en utilisant des valeurs adaptées à votre configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="18cd8-136">Edit the file AffiliateApplication.xml as required for your specific configuration.</span></span>  
  
    -   <span data-ttu-id="18cd8-137">Exécutez l’utilitaire de ligne de commande ssomanage.exe avec les arguments appropriés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="18cd8-137">Run the command-line utility ssomanage.exe with the appropriate arguments, as follows:</span></span>  
  
        ```  
        ssomanage –createapps AffiliateApplication.xml  
        ```  
  
     <span data-ttu-id="18cd8-138">Vous pouvez créer plusieurs applications associées simultanément.</span><span class="sxs-lookup"><span data-stu-id="18cd8-138">You can create more than one affiliate application at the same time.</span></span>  
  
-   <span data-ttu-id="18cd8-139">**Créer des mappages utilisateur.**</span><span class="sxs-lookup"><span data-stu-id="18cd8-139">**Create user mappings.**</span></span> <span data-ttu-id="18cd8-140">. Pour effectuer ce type d'opération, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="18cd8-140">To perform this type of operation, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="18cd8-141">Modifiez le fichier UserMapping.xml en utilisant des valeurs adaptées à votre configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="18cd8-141">Edit the file UserMapping.xmlas required for your specific configuration.</span></span>  
  
    2.  <span data-ttu-id="18cd8-142">Exécutez l’utilitaire de ligne de commande ssomanage.exe avec les arguments appropriés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="18cd8-142">Run the command-line utility ssomanage.exe with the appropriate arguments, as follows:</span></span>  
  
        ```  
        ssomanage –createmappings UserMapping.xml  
        ```  
  
     <span data-ttu-id="18cd8-143">Vous pouvez créer plusieurs mappages pour une ou plusieurs applications associées simultanément.</span><span class="sxs-lookup"><span data-stu-id="18cd8-143">You can create more than one mapping for one or more affiliate applications at the same time.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="18cd8-144">Commentaires</span><span class="sxs-lookup"><span data-stu-id="18cd8-144">Comments</span></span>  
 <span data-ttu-id="18cd8-145">Une fois les fichiers .xml fournis avec cet exemple modifiés, notamment lorsque les modifications impliquent l'intégration d'informations sensibles aux fichiers, assurez-vous que ces fichiers sont correctement protégés dans votre système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="18cd8-145">After making changes to the sample .xml files provided with this sample, especially where such changes involve including sensitive information in the files, ensure that these files are well protected in your file system.</span></span> <span data-ttu-id="18cd8-146">Par exemple, vérifiez qu'ils ne sont pas placés par inadvertance dans un dossier partagé.</span><span class="sxs-lookup"><span data-stu-id="18cd8-146">For example, ensure that they are not inadvertently placed in a folder that is shared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18cd8-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18cd8-147">See Also</span></span>  
 [<span data-ttu-id="18cd8-148">Authentification unique (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="18cd8-148">SSO (BizTalk Server Samples Folder)</span></span>](../core/sso-biztalk-server-samples-folder.md)