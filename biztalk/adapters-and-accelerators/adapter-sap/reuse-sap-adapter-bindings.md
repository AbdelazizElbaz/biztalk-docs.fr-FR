---
title: "Réutiliser les liaisons de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding file, definition
- adapter bindings, reusing
ms.assetid: 5748c22f-20a2-4eb9-ad45-a1bef7290802
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df4c878f8eb6a5e1fd52dfe749b10d1d89716679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reuse-sap-adapter-bindings"></a><span data-ttu-id="bd87b-102">Réutiliser les liaisons de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="bd87b-102">Reuse SAP adapter bindings</span></span>
<span data-ttu-id="bd87b-103">Une liaison crée un mappage entre un point de terminaison logique (par exemple, un port d’orchestration ou un lien de rôle) et un point de terminaison physique (par exemple un envoi et le port de réception).</span><span class="sxs-lookup"><span data-stu-id="bd87b-103">A binding creates a mapping between a logical endpoint (such as an orchestration port or a role link) and a physical endpoint (such as a send and receive port).</span></span> <span data-ttu-id="bd87b-104">Elle permet aux différents composants d'une solution d'entreprise BizTalk de communiquer.</span><span class="sxs-lookup"><span data-stu-id="bd87b-104">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="bd87b-105">Vous pouvez créer des liaisons dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bd87b-105">You can create bindings by using the BizTalk Server Administration console.</span></span>  
  
## <a name="what-is-a-binding-file"></a><span data-ttu-id="bd87b-106">Qu’est un fichier de liaison ?</span><span class="sxs-lookup"><span data-stu-id="bd87b-106">What is a Binding File?</span></span>  
 <span data-ttu-id="bd87b-107">Un fichier de liaison est un fichier XML qui contient des informations de liaison pour chaque orchestration BizTalk dans l’étendue d’un assembly BizTalk, une application ou un groupe.</span><span class="sxs-lookup"><span data-stu-id="bd87b-107">A binding file is an XML file that contains binding information for each BizTalk orchestration in the scope of a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="bd87b-108">Le fichier de liaison décrit :</span><span class="sxs-lookup"><span data-stu-id="bd87b-108">The binding file describes:</span></span>  
  
-   <span data-ttu-id="bd87b-109">L’hôte auquel est liée chaque orchestration</span><span class="sxs-lookup"><span data-stu-id="bd87b-109">The host to which each orchestration is bound</span></span>
  
-   <span data-ttu-id="bd87b-110">Le niveau de confiance de l’hôte</span><span class="sxs-lookup"><span data-stu-id="bd87b-110">The trust level of the host</span></span>
  
-   <span data-ttu-id="bd87b-111">Les paramètres pour chaque port d’envoi, port de réception, emplacement de réception et tiers qui a été configuré</span><span class="sxs-lookup"><span data-stu-id="bd87b-111">The settings for each send port, receive port, receive location, and party that has been configured</span></span>
  
 <span data-ttu-id="bd87b-112">Vous pouvez générer des fichiers de liaison, puis appliquez les liaisons qu’ils contiennent à un assembly, une application ou un groupe.</span><span class="sxs-lookup"><span data-stu-id="bd87b-112">You can generate binding files and then apply the bindings they contain to an assembly, application, or group.</span></span> <span data-ttu-id="bd87b-113">Cela évite d’avoir à configurer manuellement les liaisons dans différents environnements de déploiement et accélère le déploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="bd87b-113">This prevents having to manually configure bindings in different deployment environments and speeds up application deployment.</span></span>  
  
<span data-ttu-id="bd87b-114">Un fichier de liaison n’est pas généré automatiquement pour un assembly, une application ou un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bd87b-114">A binding file is not automatically generated for a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="bd87b-115">Toutefois, vous pouvez générer un fichier de liaison en exportant des liaisons.</span><span class="sxs-lookup"><span data-stu-id="bd87b-115">However, you can generate a binding file by exporting bindings.</span></span> <span data-ttu-id="bd87b-116">Vous pouvez ensuite importer le fichier de liaison dans une application ou un groupe.</span><span class="sxs-lookup"><span data-stu-id="bd87b-116">You can then import the binding file into an application or group.</span></span>  
  
<span data-ttu-id="bd87b-117">Pour plus d’informations sur les liaisons et les fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../../core/binding-files-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="bd87b-117">For more information about bindings and about binding files, see [Binding Files and Application Deployment](../../core/binding-files-and-application-deployment.md).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="bd87b-118">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bd87b-118">Prerequisites</span></span>  
<span data-ttu-id="bd87b-119">Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bd87b-119">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="bd87b-120">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="bd87b-120">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>
 
## <a name="export-bindings"></a><span data-ttu-id="bd87b-121">Exporter les liaisons</span><span class="sxs-lookup"><span data-stu-id="bd87b-121">Export bindings</span></span>
<span data-ttu-id="bd87b-122">Cette section décrit comment exporter des liaisons pour une application BizTalk dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="bd87b-122">This section describes how to export bindings for a BizTalk application into an XML file.</span></span> <span data-ttu-id="bd87b-123">Vous pouvez ensuite importer les liaisons à partir du fichier XML dans une autre application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bd87b-123">You can then import the bindings from the XML file into another BizTalk application.</span></span> <span data-ttu-id="bd87b-124">Importation des liaisons remplace les liaisons existantes portant le même nom dans l’application.</span><span class="sxs-lookup"><span data-stu-id="bd87b-124">Importing bindings overwrites any existing bindings of the same name in the application.</span></span> <span data-ttu-id="bd87b-125">Vous pouvez aussi ajouter des liaisons à une application, ce qui n'écrase pas les liaisons existantes.</span><span class="sxs-lookup"><span data-stu-id="bd87b-125">You can also add bindings to an application, which does not overwrite existing bindings.</span></span> <span data-ttu-id="bd87b-126">Les liaisons ajoutées ne prennent effet qu'une fois l'application importée.</span><span class="sxs-lookup"><span data-stu-id="bd87b-126">The bindings that you add do not take effect until you import the application.</span></span>  
  
1.  <span data-ttu-id="bd87b-127">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="bd87b-127">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="bd87b-128">Développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="bd87b-128">Expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="bd87b-129">Cliquez sur l’application dont les liaisons à exporter, sélectionnez **exporter**, puis sélectionnez **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="bd87b-129">Right-click the application whose bindings you want to export, select **Export**, and then select **Bindings**.</span></span>  
  
4.  <span data-ttu-id="bd87b-130">Sur le **exporter les liaisons** page **exportation vers le fichier**, tapez le chemin d’accès absolu du fichier XML vers lequel exporter les liaisons.</span><span class="sxs-lookup"><span data-stu-id="bd87b-130">On the **Export Bindings** page, in **Export to file**, type the absolute path of the XML file to which to export the bindings.</span></span>  
  
     <span data-ttu-id="bd87b-131">Par exemple, entrez`C:\Bindings\Application1Bindings.Binding1.xml`</span><span class="sxs-lookup"><span data-stu-id="bd87b-131">For example, enter `C:\Bindings\Application1Bindings.Binding1.xml`</span></span>  
  
5.  <span data-ttu-id="bd87b-132">Vérifiez que **exporter toutes les liaisons à partir de l’application actuelle** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bd87b-132">Confirm that **Export all bindings from the current application** is selected.</span></span>  
  
6.  <span data-ttu-id="bd87b-133">Pour exporter toutes les informations de tiers pour le groupe, sélectionnez le **informations d’exportation de tiers Global** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="bd87b-133">To export all party information for the group, select the **Export Global Party information** check box.</span></span>  
  
7.  <span data-ttu-id="bd87b-134">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="bd87b-134">Select **OK**.</span></span> <span data-ttu-id="bd87b-135">Les liaisons sont exportées dans un fichier XML à l’emplacement que vous avez spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd87b-135">The bindings are exported into an XML file in the location that you specified.</span></span>  

## <a name="import-bindings"></a><span data-ttu-id="bd87b-136">Importer les liaisons</span><span class="sxs-lookup"><span data-stu-id="bd87b-136">Import bindings</span></span>
<span data-ttu-id="bd87b-137">Importer des liaisons à l’aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bd87b-137">Import bindings using the BizTalk Server Administration console.</span></span>
  
1.  <span data-ttu-id="bd87b-138">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="bd87b-138">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="bd87b-139">Développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="bd87b-139">Expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="bd87b-140">Cliquez sur l’application dans laquelle vous souhaitez importer des liaisons, sélectionnez **importer**, puis sélectionnez **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="bd87b-140">Right-click the application into which you want to import bindings, select **Import**, and then select **Bindings**.</span></span>  
  
4.  <span data-ttu-id="bd87b-141">Sélectionnez le fichier de liaison, puis **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="bd87b-141">Select the binding file, and then select **Open**.</span></span>  
  
<span data-ttu-id="bd87b-142">Les artefacts du fichier de liaison sont écrits dans l'application.</span><span class="sxs-lookup"><span data-stu-id="bd87b-142">The artifacts in the binding file are written to the application.</span></span> <span data-ttu-id="bd87b-143">Ils s'affichent dans les dossiers appropriés de l'application.</span><span class="sxs-lookup"><span data-stu-id="bd87b-143">They display in appropriate folders of the application.</span></span> <span data-ttu-id="bd87b-144">Par exemple, les ports d’envoi importés dans le cadre de l’affichage de liaisons sous le **Ports d’envoi** dossier.</span><span class="sxs-lookup"><span data-stu-id="bd87b-144">For example, the send ports imported as part of the bindings display under the **Send Ports** folder.</span></span>  

## <a name="passwords-are-removed"></a><span data-ttu-id="bd87b-145">Les mots de passe sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="bd87b-145">Passwords are removed</span></span>  
<span data-ttu-id="bd87b-146">Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprime les mots de passe pour les liaisons du fichier.</span><span class="sxs-lookup"><span data-stu-id="bd87b-146">For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="bd87b-147">Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="bd87b-147">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="bd87b-148">Vous configurez les mots de passe dans la boîte de dialogue Propriétés du Transport de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] l’Administration de la console pour le port d’envoi ou emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="bd87b-148">You configure passwords in the Transport Properties dialog box of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console for the send port or receive location.</span></span> 

<span data-ttu-id="bd87b-149">Pour plus d’informations sur la spécification du nom d’utilisateur et mots de passe, consultez [configurer l’authentification dans les informations d’identification pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="bd87b-149">For information about specifying user name and passwords, see [Configure the sign in credentials for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd87b-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd87b-150">See also</span></span>
[<span data-ttu-id="bd87b-151">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="bd87b-151">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)