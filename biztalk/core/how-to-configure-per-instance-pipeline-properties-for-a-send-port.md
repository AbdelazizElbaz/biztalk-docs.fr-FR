---
title: "Comment configurer les propriétés de Pipeline par Instance pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- managing [pipelines], properties
- configuring, send ports
- configuring, pipelines
- managing [pipelines], configuring
- managing [send ports], pipelines
- managing [send ports], configuring
- send ports, pipelines
- pipelines, configuring
ms.assetid: c58faa9e-0dfb-458b-8f1b-d3c91bce0436
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfb9927dca890a7f84baf372c4fa250a8ced17c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-send-port"></a><span data-ttu-id="b3631-102">Configuration des propriétés de pipeline par instance pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="b3631-102">How to Configure Per-Instance Pipeline Properties for a Send Port</span></span>
<span data-ttu-id="b3631-103">Cette rubrique explique comment configurer les propriétés de pipeline d'un port d'envoi à l'aide de la console Administration de BizTalk Server après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b3631-103">This topic describes how to use the BizTalk Server Administration console to configure pipeline properties for a send port after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="b3631-104">Les modifications que vous effectuez remplacent les propriétés de pipeline par défaut de ce port d'envoi uniquement. Vous pouvez donc configurer différentes propriétés de pipeline pour chacun des ports d'envoi du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b3631-104">Changes that you make overwrite the default pipeline properties for this send port only, so if you want, you can configure different pipeline properties for each send port in the BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b3631-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b3631-105">Prerequisites</span></span>  
 <span data-ttu-id="b3631-106">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b3631-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b3631-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="b3631-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3631-108">Lors de l’utilisation des propriétés de pipeline par instance pour définir la valeur de la **DocumentSpecNames** propriété dans le composant désassembleur XML d’un pipeline, le schéma de document spécifié et le pipeline doit être définie dans le même projet.</span><span class="sxs-lookup"><span data-stu-id="b3631-108">When using per-instance pipeline properties to set the value for the **DocumentSpecNames** property in the XML disassembler component of a pipeline, the specified document schema and the pipeline must be defined in the same project.</span></span>  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-send-port"></a><span data-ttu-id="b3631-109">Pour configurer les propriétés de pipeline par instance d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="b3631-109">To configure per-instance pipeline properties for a send port</span></span>  
  
1.  <span data-ttu-id="b3631-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b3631-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b3631-111">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le port d’envoi pour lequel vous souhaitez configurer les propriétés de pipeline, **Applications**, puis Développez l’application contenant le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="b3631-111">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the send port for which you want to configure pipeline properties, expand **Applications**, and then expand the application containing the send port.</span></span>  
  
3.  <span data-ttu-id="b3631-112">Cliquez sur le **Ports d’envoi** dossier, cliquez sur le port d’envoi, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b3631-112">Click the **Send Ports** folder, right-click the send port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b3631-113">Cliquez sur le bouton de sélection (**...** ) situé à droite de la **Pipeline d’envoi** boîte.</span><span class="sxs-lookup"><span data-stu-id="b3631-113">Click the ellipsis (**…**) button to the right of the **Send Pipeline** box.</span></span>  
  
5.  <span data-ttu-id="b3631-114">Configurer les propriétés de votre choix, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3631-114">Configure the properties you want, and then click **OK**.</span></span> <span data-ttu-id="b3631-115">Cliquez sur **aide** sur la page de propriétés pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="b3631-115">Click **Help** on the properties page for more information.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b3631-116">Assurez-vous que les informations de propriétés que vous entrez sont correctes.</span><span class="sxs-lookup"><span data-stu-id="b3631-116">Make sure that you enter correct information for pipelines properties.</span></span> <span data-ttu-id="b3631-117">Si une des valeurs n'est pas valide, par exemple une chaîne au lieu d'un nombre, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="b3631-117">If you enter an invalid value, for example a string rather than a number, it will generate an error.</span></span>  
  
6.  <span data-ttu-id="b3631-118">S’il s’agit d’un port d’envoi de sollicitation-réponse, cliquez sur le bouton de sélection (**...** ) situé à droite de la **Pipeline de réception** boîte.</span><span class="sxs-lookup"><span data-stu-id="b3631-118">If this is a solicit-response send port, click the ellipsis (**…**) button to the right of the **Receive Pipeline** box.</span></span>  
  
7.  <span data-ttu-id="b3631-119">Configurer les propriétés de votre choix, puis cliquez sur **OK** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="b3631-119">Configure the properties you want, and then click **OK** twice.</span></span> <span data-ttu-id="b3631-120">Cliquez sur **aide** sur la page de propriétés pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="b3631-120">Click **Help** on the properties page for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3631-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3631-121">See Also</span></span>  
 <span data-ttu-id="b3631-122">[Gestion des Pipelines](../core/managing-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="b3631-122">[Managing Pipelines](../core/managing-pipelines.md) </span></span>  
 <span data-ttu-id="b3631-123">[Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="b3631-123">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="b3631-124">La gestion des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="b3631-124">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)