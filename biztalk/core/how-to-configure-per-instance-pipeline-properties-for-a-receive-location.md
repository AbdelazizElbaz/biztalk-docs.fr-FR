---
title: "Comment configurer les propriétés de Pipeline par instance d’un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- receive locations, configuring
- managing [pipelines], properties
- managing [pipelines], receive locations
- managing [receive locations], pipelines
- managing [pipelines], configuring
- pipelines, receive locations
- pipelines, configuring
- receive locations, pipelines
- managing [receive locations], configuring
ms.assetid: e1ed3b10-2f39-479b-a3e6-22b4b2872192
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e14483c5d17d968fc79126c65506720b501b6da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-receive-location"></a><span data-ttu-id="ef68d-102">Configuration des propriétés de pipeline par instance pour un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="ef68d-102">How to Configure Per-instance Pipeline Properties for a Receive Location</span></span>
<span data-ttu-id="ef68d-103">Cette rubrique explique comment configurer les propriétés de pipeline d'un port de réception à l'aide de la console Administration de BizTalk Server après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ef68d-103">This topic describes how to use the BizTalk Server Administration console to configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="ef68d-104">Les modifications que vous effectuez remplacent les propriétés de pipeline par défaut de cet emplacement de réception uniquement. Vous pouvez donc configurer différentes propriétés de pipeline pour chacun des emplacements de réception du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ef68d-104">Changes that you make overwrite the default pipeline properties for this receive location only, so if you want, you can configure different pipeline properties for each receive location in the BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef68d-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ef68d-105">Prerequisites</span></span>  
 <span data-ttu-id="ef68d-106">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ef68d-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ef68d-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ef68d-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef68d-108">Lors de l’utilisation des propriétés de pipeline par instance pour définir la valeur de la **DocumentSpecNames** propriété dans le composant désassembleur XML d’un pipeline, le schéma de document spécifié et le pipeline doit être définie dans le même projet.</span><span class="sxs-lookup"><span data-stu-id="ef68d-108">When using per-instance pipeline properties to set the value for the **DocumentSpecNames** property in the XML disassembler component of a pipeline, the specified document schema and the pipeline must be defined in the same project.</span></span>  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-receive-location"></a><span data-ttu-id="ef68d-109">Pour configurer les propriétés de pipeline par instance d'un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="ef68d-109">To configure per-instance pipeline properties for a receive location</span></span>  
  
1.  <span data-ttu-id="ef68d-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ef68d-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ef68d-111">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant l’emplacement de réception pour lequel configurer les propriétés de pipeline, **Applications**, puis Développez l’application contenant l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="ef68d-111">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the receive location for which to configure pipeline properties, expand **Applications**, and then expand the application containing the receive location.</span></span>  
  
3.  <span data-ttu-id="ef68d-112">Cliquez sur le **emplacements de réception** dossier, cliquez sur l’emplacement de réception, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ef68d-112">Click the **Receive Locations** folder, right-click the receive location, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="ef68d-113">Cliquez sur les points de suspension (...) à droite de la **Pipeline de réception** boîte.</span><span class="sxs-lookup"><span data-stu-id="ef68d-113">Click the ellipsis (…) to the right of the **Receive Pipeline** box.</span></span>  
  
5.  <span data-ttu-id="ef68d-114">Configurer les propriétés de votre choix, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef68d-114">Configure the properties you want, and then click **OK**.</span></span> <span data-ttu-id="ef68d-115">Pour plus d’informations, cliquez sur **aide** sur la page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="ef68d-115">For more information, click **Help** on the properties page.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ef68d-116">Assurez-vous que les informations de propriétés que vous entrez sont correctes.</span><span class="sxs-lookup"><span data-stu-id="ef68d-116">Make sure that you enter correct information for pipelines properties.</span></span> <span data-ttu-id="ef68d-117">Si une des valeurs n'est pas valide, par exemple une chaîne au lieu d'un nombre, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="ef68d-117">If you enter an invalid value, for example a string rather than a number, it will generate an error.</span></span>  
  
6.  <span data-ttu-id="ef68d-118">S’il s’agit d’une requête-réponse emplacement de réception, cliquez sur les points de suspension (...) à droite de la **Pipeline d’envoi** boîte.</span><span class="sxs-lookup"><span data-stu-id="ef68d-118">If this is a request-response receive location, click the ellipsis (…) to the right of the **Send Pipeline** box.</span></span>  
  
7.  <span data-ttu-id="ef68d-119">Configurer les propriétés de votre choix, puis cliquez sur **OK** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="ef68d-119">Configure the properties you want, and then click **OK** twice.</span></span> <span data-ttu-id="ef68d-120">Pour plus d’informations, cliquez sur **aide** sur la page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="ef68d-120">For more information, click **Help** on the properties page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef68d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef68d-121">See Also</span></span>  
 <span data-ttu-id="ef68d-122">[Gestion des Pipelines](../core/managing-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="ef68d-122">[Managing Pipelines](../core/managing-pipelines.md) </span></span>  
 <span data-ttu-id="ef68d-123">[Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="ef68d-123">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="ef68d-124">La gestion des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="ef68d-124">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)