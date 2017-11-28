---
title: "La réparation et la soumettre à nouveau un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccd720b4-44a2-4c44-bf6e-8cf5e9ded1aa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e524ffca1b79032dce55f74e195032d14ec1bf9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-and-resubmitting-a-message"></a><span data-ttu-id="71f1d-102">La réparation et la soumettre à nouveau un Message</span><span class="sxs-lookup"><span data-stu-id="71f1d-102">Repairing and Resubmitting a Message</span></span>
<span data-ttu-id="71f1d-103">Pour réparer et renvoyer un message ayant échoué, utilisez la page d’erreurs du portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="71f1d-103">To repair and resubmit a failed message, use the Faults page of the ESB Management Portal.</span></span>  
  
### <a name="to-repair-and-resubmit-a-message-for-processing"></a><span data-ttu-id="71f1d-104">Réparer et de renvoyer un message pour le traitement</span><span class="sxs-lookup"><span data-stu-id="71f1d-104">To repair and resubmit a message for processing</span></span>  
  
1.  <span data-ttu-id="71f1d-105">Recherchez le message d’erreur souhaité sur le [portail défauts de Page](../esb-toolkit/portal-faults-page.md) page du portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="71f1d-105">Locate the desired fault message on the [Portal Faults Page](../esb-toolkit/portal-faults-page.md) page of the ESB Management Portal.</span></span> <span data-ttu-id="71f1d-106">Utilisez les fonctionnalités de filtrage dans la page d’erreurs pour rechercher un message spécifique.</span><span class="sxs-lookup"><span data-stu-id="71f1d-106">Use the filtering capabilities on the Faults page to search for a specific message.</span></span> <span data-ttu-id="71f1d-107">Renseignez les contrôles pour récupérer tous les messages.</span><span class="sxs-lookup"><span data-stu-id="71f1d-107">Leave any of the controls empty to retrieve all messages.</span></span> <span data-ttu-id="71f1d-108">Notez que le filtrage sur une base de données de l’erreur très volumineux peut prendre plusieurs secondes pour afficher les résultats appropriés.</span><span class="sxs-lookup"><span data-stu-id="71f1d-108">Note that filtering on a very large fault database may take several seconds to display the appropriate results.</span></span> <span data-ttu-id="71f1d-109">La figure 1 illustre la page d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="71f1d-109">Figure 1 illustrates the Faults page.</span></span>  
  
     <span data-ttu-id="71f1d-110">![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")</span><span class="sxs-lookup"><span data-stu-id="71f1d-110">![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")</span></span>  
  
     <span data-ttu-id="71f1d-111">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="71f1d-111">**Figure 1**</span></span>  
  
     <span data-ttu-id="71f1d-112">**La page d’erreurs du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="71f1d-112">**The Faults page of the ESB Management Portal**</span></span>  
  
2.  <span data-ttu-id="71f1d-113">Cliquez n’importe où dans la ligne du message d’erreur souhaité pour ouvrir la [Afficheur des messages d’erreur Portal](../esb-toolkit/portal-fault-message-viewer.md) page [vue des détails d’erreur](../esb-toolkit/fault-details-view.md).</span><span class="sxs-lookup"><span data-stu-id="71f1d-113">Click anywhere in the row of the desired fault message to open the [Portal Fault Message Viewer](../esb-toolkit/portal-fault-message-viewer.md) page in [Fault Details View](../esb-toolkit/fault-details-view.md).</span></span>  
  
3.  <span data-ttu-id="71f1d-114">Faites défiler vers le bas de la vue Détails de l’erreur à la liste des messages contenus dans le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="71f1d-114">Scroll to the bottom of the Fault Details view to the list of messages contained within the fault message.</span></span> <span data-ttu-id="71f1d-115">La figure 2 illustre les **Messages** section de la page de la visionneuse de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="71f1d-115">Figure 2 illustrates the **Messages** section of the Fault Viewer page.</span></span>  
  
     <span data-ttu-id="71f1d-116">![Section des messages](../esb-toolkit/media/ch8-messagessection.gif "Ch8-MessagesSection")</span><span class="sxs-lookup"><span data-stu-id="71f1d-116">![Messages Section](../esb-toolkit/media/ch8-messagessection.gif "Ch8-MessagesSection")</span></span>  
  
     <span data-ttu-id="71f1d-117">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="71f1d-117">**Figure 2**</span></span>  
  
     <span data-ttu-id="71f1d-118">**La section des Messages de la page de la visionneuse de l’erreur du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="71f1d-118">**The Messages section of the Fault Viewer page of the ESB Management Portal**</span></span>  
  
4.  <span data-ttu-id="71f1d-119">Cliquez sur l’identificateur de message du message que vous souhaitez soumettre à nouveau.</span><span class="sxs-lookup"><span data-stu-id="71f1d-119">Click the message identifier of the message you want to resubmit.</span></span> <span data-ttu-id="71f1d-120">Cette opération ouvre le message dans [affichage Détails](../esb-toolkit/message-details-view.md), qui affiche les détails du message individuel et le contenu du message, comme illustré dans la Figure 3.</span><span class="sxs-lookup"><span data-stu-id="71f1d-120">This opens the message in [Message Details View](../esb-toolkit/message-details-view.md), which shows details of the individual message and the message content, as illustrated in Figure 3.</span></span>  
  
     <span data-ttu-id="71f1d-121">![Afficheur de messages](../esb-toolkit/media/ch8-messageviewer.gif "Ch8-MessageViewer")</span><span class="sxs-lookup"><span data-stu-id="71f1d-121">![Message Viewer](../esb-toolkit/media/ch8-messageviewer.gif "Ch8-MessageViewer")</span></span>  
  
     <span data-ttu-id="71f1d-122">**Figure 3**</span><span class="sxs-lookup"><span data-stu-id="71f1d-122">**Figure 3**</span></span>  
  
     <span data-ttu-id="71f1d-123">**La page de l’Afficheur des messages du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="71f1d-123">**The Message Viewer page of the ESB Management Portal**</span></span>  
  
5.  <span data-ttu-id="71f1d-124">Cliquez sur le **modifier** lien situé sous la zone de texte qui contient le contenu du message pour basculer en mode édition, puis modifier le contenu du message en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="71f1d-124">Click the **Edit** link under the text box that contains the message content to switch to edit mode, and then edit the message contents as required.</span></span> <span data-ttu-id="71f1d-125">Par exemple, vous devrez peut-être modifier les paramètres d’appels de méthode de service contenues dans le message.</span><span class="sxs-lookup"><span data-stu-id="71f1d-125">For example, you may need to change the parameters for service method invocations contained within the message.</span></span> <span data-ttu-id="71f1d-126">Notez que vous devez respecter le style document natif (par exemple, XML ou le format de fichier plat) pour empêcher les refus du message lorsque renvoyé.</span><span class="sxs-lookup"><span data-stu-id="71f1d-126">Note that you must adhere to the native document style (such as XML or flat file format) to prevent rejection of the message when resubmitted.</span></span> <span data-ttu-id="71f1d-127">La figure 4 illustre les **détails du Message** section de la page de l’éditeur de Message.</span><span class="sxs-lookup"><span data-stu-id="71f1d-127">Figure 4 illustrates the **Message Details** section of the Message Editor page.</span></span>  
  
     <span data-ttu-id="71f1d-128">![Les détails du message](../esb-toolkit/media/ch8-messagedetails.gif "Ch8-MessageDetails")</span><span class="sxs-lookup"><span data-stu-id="71f1d-128">![Message Details](../esb-toolkit/media/ch8-messagedetails.gif "Ch8-MessageDetails")</span></span>  
  
     <span data-ttu-id="71f1d-129">**Figure 4**</span><span class="sxs-lookup"><span data-stu-id="71f1d-129">**Figure 4**</span></span>  
  
     <span data-ttu-id="71f1d-130">**La section Détails du Message de la page de l’Afficheur des messages du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="71f1d-130">**The Message Details section of the Message Viewer page of the ESB Management Portal**</span></span>  
  
6.  <span data-ttu-id="71f1d-131">Après avoir modifié le message, sélectionnez un emplacement de la nouvelle soumission dans la liste déroulante sous la zone de texte du message.</span><span class="sxs-lookup"><span data-stu-id="71f1d-131">After editing the message, select a resubmission location in the drop-down list under the message text box.</span></span> <span data-ttu-id="71f1d-132">Cette liste montre la liste récupérée dynamiquement des points de terminaison disponibles.</span><span class="sxs-lookup"><span data-stu-id="71f1d-132">This list shows the dynamically retrieved list of available endpoints.</span></span> <span data-ttu-id="71f1d-133">Vous devez sélectionner un point de terminaison configuré comme un point de terminaison renvoyés.</span><span class="sxs-lookup"><span data-stu-id="71f1d-133">You must select an endpoint configured as a resubmission endpoint.</span></span> <span data-ttu-id="71f1d-134">Les points de terminaison suivants conviennent pour la nouvelle soumission :</span><span class="sxs-lookup"><span data-stu-id="71f1d-134">The following endpoints are suitable for resubmission:</span></span>  
  
    -   <span data-ttu-id="71f1d-135">**WCF rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-135">**WCF On-Ramp**.</span></span> <span data-ttu-id="71f1d-136">Ce point de terminaison est ESB itinéraire Services WCF rampe et est disponible uniquement pour les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="71f1d-136">This endpoint is the ESB Itinerary Services WCF on-ramp and is available only for XML files.</span></span> <span data-ttu-id="71f1d-137">Le fichier Web.config du portail définit l’URL pour cette rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="71f1d-137">The portal Web.config file defines the URL for this on-ramp.</span></span>  
  
    -   <span data-ttu-id="71f1d-138">**SOAP-démarrage**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-138">**SOAP On-Ramp**.</span></span> <span data-ttu-id="71f1d-139">Ce point de terminaison est ESB itinéraire Services ASMX rampe et est disponible uniquement pour les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="71f1d-139">This endpoint is the ESB Itinerary Services ASMX on-ramp and is available only for XML files.</span></span> <span data-ttu-id="71f1d-140">Le fichier Web.config du portail définit l’URL pour cette rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="71f1d-140">The portal Web.config file defines the URL for this on-ramp.</span></span>  
  
    -   <span data-ttu-id="71f1d-141">**Un emplacement à l’aide de l’adaptateur HTTP BizTalk de réception**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-141">**Any receive location using the BizTalk HTTP adapter**.</span></span> <span data-ttu-id="71f1d-142">Cette option est disponible pour les fichiers XML et les fichiers plats.</span><span class="sxs-lookup"><span data-stu-id="71f1d-142">This option is available for XML files and flat files.</span></span>  
  
7.  <span data-ttu-id="71f1d-143">Cliquez sur le **renvoyer** lien pour renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="71f1d-143">Click the **Resubmit** link to resubmit the message.</span></span> <span data-ttu-id="71f1d-144">Un message indiquant le **état de la nouvelle soumission** s’affiche sous la zone de texte du contenu du message.</span><span class="sxs-lookup"><span data-stu-id="71f1d-144">A message indicating the **Resubmission Status** appears under the message content text box.</span></span>  
  
8.  <span data-ttu-id="71f1d-145">Si nécessaire, ouvrez le [Page du journal d’Audit](../esb-toolkit/audit-log-page.md) à partir de la **Admin** onglet pour confirmer la nouvelle soumission de message, comme illustré dans la Figure 5.</span><span class="sxs-lookup"><span data-stu-id="71f1d-145">If required, open the [Audit Log Page](../esb-toolkit/audit-log-page.md) from the **Admin** tab to confirm message resubmission, as illustrated in Figure 5.</span></span>  
  
     <span data-ttu-id="71f1d-146">![La page AuditLog](../esb-toolkit/media/ch8-auditlogpagesmallview.gif "Ch8-AuditLogPageSmallView")</span><span class="sxs-lookup"><span data-stu-id="71f1d-146">![AuditLog Page Small View](../esb-toolkit/media/ch8-auditlogpagesmallview.gif "Ch8-AuditLogPageSmallView")</span></span>  
  
     <span data-ttu-id="71f1d-147">**Figure 5**</span><span class="sxs-lookup"><span data-stu-id="71f1d-147">**Figure 5**</span></span>  
  
     <span data-ttu-id="71f1d-148">**La page journal d’Audit du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="71f1d-148">**The Audit Log page of the ESB Management Portal**</span></span>