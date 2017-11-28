---
title: Comment actualiser une ressource | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [resources], refreshing
- refreshing resources
- resources, refreshing
ms.assetid: d6ff7c9d-8aaf-42a4-b1a3-00c05f6ac869
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bee05b9f137bbec92eccfa217084b66f1e5bf8ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-refresh-a-resource"></a><span data-ttu-id="b4b61-102">Actualisation d'une ressource</span><span class="sxs-lookup"><span data-stu-id="b4b61-102">How to Refresh a Resource</span></span>
<span data-ttu-id="b4b61-103">La présente rubrique explique comment actualiser un artefact de ressource à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b4b61-103">This topic describes how to use the BizTalk Server Administration console to refresh a resource artifact.</span></span> <span data-ttu-id="b4b61-104">Cette opération permet de mettre à jour les informations liées à l'artefact dans la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b4b61-104">This updates the artifact information in the BizTalk Management database.</span></span> <span data-ttu-id="b4b61-105">Une autre façon de procéder consiste à ajouter l’artefact à l’application à l’aide de l’outil BTSTask [commande AddResource](../core/addresource-command.md) avec l’option de remplacement.</span><span class="sxs-lookup"><span data-stu-id="b4b61-105">Another way to do this is by adding the artifact to the application using the BTSTask [AddResource Command](../core/addresource-command.md) with the overwrite option.</span></span>  
  
 <span data-ttu-id="b4b61-106">Les artefacts de ressource se trouvent dans le dossier Ressources de l'application.</span><span class="sxs-lookup"><span data-stu-id="b4b61-106">Resource artifacts are contained in an application's Resources folder.</span></span> <span data-ttu-id="b4b61-107">Vous pouvez actualiser un artefact de ressource lorsque vous modifiez le fichier source et que vous souhaitez remplacer ce fichier par le nouveau dans l'application.</span><span class="sxs-lookup"><span data-stu-id="b4b61-107">You might want to refresh a resource artifact if you make changes to the source file and want to replace the file in the application with the updated file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b4b61-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b4b61-108">Prerequisites</span></span>  
 <span data-ttu-id="b4b61-109">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b4b61-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b4b61-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="b4b61-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-refresh-a-resource-artifact"></a><span data-ttu-id="b4b61-111">Pour actualiser un artefact de ressource</span><span class="sxs-lookup"><span data-stu-id="b4b61-111">To refresh a resource artifact</span></span>  
  
1.  <span data-ttu-id="b4b61-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b4b61-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b4b61-113">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant l’artefact de ressource à actualiser, puis développez l’application contenant l’artefact.</span><span class="sxs-lookup"><span data-stu-id="b4b61-113">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the resource artifact to refresh, and then expand the application containing the artifact.</span></span>  
  
3.  <span data-ttu-id="b4b61-114">Cliquez sur le **ressources** dossier, avec le bouton droit le fichier à actualiser, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="b4b61-114">Click the **Resources** folder, right-click the file to refresh, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="b4b61-115">Dans le **modifier les ressources** boîte de dialogue, sélectionnez le fichier à actualiser, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="b4b61-115">In the **Modify Resources** dialog box, select the file to refresh, and then click **Refresh**.</span></span>  
  
5.  <span data-ttu-id="b4b61-116">Accédez au fichier mis à jour avec lequel vous souhaitez remplacer le fichier actuel, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4b61-116">Browse to the updated file with which you want to replace the current file, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b4b61-117">Le fichier existant est remplacé par le fichier mis à jour.</span><span class="sxs-lookup"><span data-stu-id="b4b61-117">The current file is replaced with the updated file.</span></span> <span data-ttu-id="b4b61-118">En outre, la configuration, les paramètres affichés sur la **Options** onglet de la **modifier les ressources** boîte de dialogue sont appliquées au fichier actualisé.</span><span class="sxs-lookup"><span data-stu-id="b4b61-118">In addition, the configuration, settings displayed on the **Options** tab of the **Modify Resources** dialog box are applied to the refreshed file.</span></span> <span data-ttu-id="b4b61-119">Pour plus d’informations sur la modification de ces paramètres, cliquez sur **aide** dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b4b61-119">For more information about changing these settings, click **Help** in the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b61-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4b61-120">See Also</span></span>  
 <span data-ttu-id="b4b61-121">[Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md) </span><span class="sxs-lookup"><span data-stu-id="b4b61-121">[Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md) </span></span>  
 <span data-ttu-id="b4b61-122">[La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span><span class="sxs-lookup"><span data-stu-id="b4b61-122">[Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span></span>  
 [<span data-ttu-id="b4b61-123">La gestion des ressources</span><span class="sxs-lookup"><span data-stu-id="b4b61-123">Managing Resources</span></span>](../core/managing-resources.md)