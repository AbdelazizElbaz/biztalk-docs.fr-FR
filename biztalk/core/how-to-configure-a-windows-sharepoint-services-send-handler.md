---
title: "Comment faire pour configurer Windows SharePoint Services de gestionnaire d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], send handlers
- send handlers, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, send handlers
ms.assetid: 457767d9-6e39-4553-9bbe-212fcb7c04bc
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8e110fb2a671fc839fb96cfdc2ad03169649e6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-windows-sharepoint-services-send-handler"></a><span data-ttu-id="943e5-102">Configuration d'un gestionnaire d'envoi Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="943e5-102">How to Configure a Windows SharePoint Services Send Handler</span></span>
<span data-ttu-id="943e5-103">La procédure suivante permet de modifier l'hôte auquel le gestionnaire d'envoi Windows SharePoint Services est associé.</span><span class="sxs-lookup"><span data-stu-id="943e5-103">Use the following procedure to change the host with which the Windows SharePoint Services send handler is associated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="943e5-104">Un seul gestionnaire d'envoi peut être associé à chaque hôte.</span><span class="sxs-lookup"><span data-stu-id="943e5-104">Each host can have only one send handler associated with it.</span></span>  
  
### <a name="to-change-global-variables-for-a-windows-sharepoint-services-send-handler"></a><span data-ttu-id="943e5-105">Pour modifier les variables globales d'un gestionnaire d'envoi Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="943e5-105">To change global variables for a Windows SharePoint Services send handler</span></span>  
  
1.  <span data-ttu-id="943e5-106">Dans la console Administration de BizTalk Server, cliquez pour développer [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, puis cliquez pour développer **groupe BizTalk [\<nom_serveur\>:\< base de données de gestion\>]**, cliquez pour développer **paramètres de plateforme**, puis cliquez pour développer **cartes**.</span><span class="sxs-lookup"><span data-stu-id="943e5-106">In the BizTalk Server Administration console, click to expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, and then click to expand **BizTalk Group [\<servername\>:\<management database\>]**, click to expand **Platform Settings**, and then click to expand **Adapters**.</span></span> <span data-ttu-id="943e5-107">La liste des adaptateurs est affichée dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="943e5-107">The list of adapters appears under the folder.</span></span>  
  
2.  <span data-ttu-id="943e5-108">Cliquez sur **Windows SharePoint Services**, dans le volet droit, cliquez sur le Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="943e5-108">Click **Windows SharePoint Services**, and in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="943e5-109">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="943e5-109">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.</span></span>  
  
4.  <span data-ttu-id="943e5-110">Sur le **général** , cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="943e5-110">On the **General** tab, click **Properties**.</span></span>  
  
5.  <span data-ttu-id="943e5-111">Dans le **propriétés du Transport Windows SharePoint Services** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="943e5-111">In the **Windows SharePoint Services Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="943e5-112">Utiliser</span><span class="sxs-lookup"><span data-stu-id="943e5-112">Use this</span></span>|<span data-ttu-id="943e5-113">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="943e5-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="943e5-114">Taille du lot d'envoi</span><span class="sxs-lookup"><span data-stu-id="943e5-114">Send Batch Size</span></span>|<span data-ttu-id="943e5-115">Nombre maximal de documents que le service Web Windows SharePoint Services va traiter en un seul lot.</span><span class="sxs-lookup"><span data-stu-id="943e5-115">The maximum number of documents that the Windows SharePoint Services Web service will process as a batch.</span></span> <span data-ttu-id="943e5-116">La valeur par défaut est 20.</span><span class="sxs-lookup"><span data-stu-id="943e5-116">The default is 20.</span></span> <span data-ttu-id="943e5-117">**Remarque :** la valeur minimale est 1.</span><span class="sxs-lookup"><span data-stu-id="943e5-117">**Note:**  The minimum value is 1.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="943e5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="943e5-118">See Also</span></span>  
 <span data-ttu-id="943e5-119">[Pour configurer Windows SharePoint Services emplacement de réception](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md) </span><span class="sxs-lookup"><span data-stu-id="943e5-119">[How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md) </span></span>  
 <span data-ttu-id="943e5-120">[Comment configurer un Port d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="943e5-120">[How to Configure a Windows SharePoint Services Send Port](../core/how-to-configure-a-windows-sharepoint-services-send-port.md) </span></span>  
 <span data-ttu-id="943e5-121">[Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md) </span><span class="sxs-lookup"><span data-stu-id="943e5-121">[How to Create a Send Port](../core/how-to-create-a-send-port2.md) </span></span>  
 <span data-ttu-id="943e5-122">[Référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="943e5-122">[Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md) </span></span>  
 <span data-ttu-id="943e5-123">[Expressions de l’adaptateur de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="943e5-123">[Windows SharePoint Services Adapter Expressions](../core/windows-sharepoint-services-adapter-expressions.md) </span></span>  
 [<span data-ttu-id="943e5-124">Types de colonnes Windows SharePoint Services pris en charge</span><span class="sxs-lookup"><span data-stu-id="943e5-124">Supported Windows SharePoint Services Column Types</span></span>](../core/supported-windows-sharepoint-services-column-types.md)