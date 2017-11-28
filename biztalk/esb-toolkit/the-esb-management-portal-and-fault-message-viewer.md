---
title: Le portail de gestion ESB et erreur Message visionneuse | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4a1636c-2e45-4ee5-92c2-81c976582da3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9a6e7272e7b707b6ba7650cfb93506c3a54a00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-management-portal-and-fault-message-viewer"></a><span data-ttu-id="57559-102">Le portail de gestion ESB et l’Afficheur des messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="57559-102">The ESB Management Portal and Fault Message Viewer</span></span>
<span data-ttu-id="57559-103">Un composant majeur de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est basé sur un Web portail qui fournit un large éventail d’exception fonctionnalités de notification d’alerte et de gestion ; en outre, il joue le rôle de gestion de la configuration utile (Universal Description, Discovery and Integration Interface d’inscription UDDI).</span><span class="sxs-lookup"><span data-stu-id="57559-103">A major component of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is a Web-based portal that provides a wide range of exception management and alert notification features; in addition, it acts as a useful configuration management and Universal Description, Discovery, and Integration (UDDI) registration interface.</span></span> <span data-ttu-id="57559-104">Figure 1 montre la page d’accueil du portail, qui fournit une vue d’ensemble de l’intégrité des applications en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="57559-104">Figure 1 shows the home page of the portal, which provides an overview of the health of the currently running applications.</span></span>  
  
 <span data-ttu-id="57559-105">![Page d’accueil du portail](../esb-toolkit/media/portalhomepage.gif "PortalHomePage")</span><span class="sxs-lookup"><span data-stu-id="57559-105">![Portal Home Page](../esb-toolkit/media/portalhomepage.gif "PortalHomePage")</span></span>  
  
 <span data-ttu-id="57559-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="57559-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="57559-107">**La page d’accueil du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="57559-107">**The home page of the ESB Management Portal**</span></span>  
  
 <span data-ttu-id="57559-108">Les utilisateurs peuvent sélectionner un message d’erreur affiché dans le portail de gestion ESB pour afficher les propriétés ambiantes et statiques de l’erreur et une liste des messages d’origine contenues dans le message d’erreur, comme indiqué dans la Figure 2.</span><span class="sxs-lookup"><span data-stu-id="57559-108">Users can select a fault message displayed in the ESB Management Portal to view the ambient and static properties of the fault and a list of the original messages contained in the fault message, as shown in Figure 2.</span></span>  
  
 <span data-ttu-id="57559-109">![Page Afficheur des erreurs](../esb-toolkit/media/ch4-faultviewerpage.gif "FaultViewerPage de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="57559-109">![Faul tViewer Page](../esb-toolkit/media/ch4-faultviewerpage.gif "Ch4-FaultViewerPage")</span></span>  
  
 <span data-ttu-id="57559-110">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="57559-110">**Figure 2**</span></span>  
  
 <span data-ttu-id="57559-111">**La page de la visionneuse de pannes ESB du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="57559-111">**The ESB Fault Viewer page of the ESB Management Portal**</span></span>  
  
 <span data-ttu-id="57559-112">Les messages d’erreur de ESB affichées dans le portail de gestion ESB peuvent être le résultat d’une erreur dans les valeurs du message d’origine lorsque envoyé pour traitement.</span><span class="sxs-lookup"><span data-stu-id="57559-112">ESB Fault messages displayed in the ESB Management Portal may be the result of an error in the values of the original message when submitted for processing.</span></span> <span data-ttu-id="57559-113">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge la fonctionnalité « Réparer et soumettez à nouveau », ce qui permet aux administrateurs ou utilisateurs de modifier les messages ayant échoué et les soumettre à une rampe d’entrée pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="57559-113">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports "repair and resubmit" functionality, which allows administrators or users to edit failed messages and to submit them to an on-ramp for processing.</span></span>  
  
 <span data-ttu-id="57559-114">Sélectionnant une de la relation contenant-contenu des messages permet d’ouvrir la page en mode de Message dans la vue des détails du Message, comme indiqué dans la Figure 3.</span><span class="sxs-lookup"><span data-stu-id="57559-114">Selecting one of the contained messages opens the Message View page in Message Details view, as shown in Figure 3.</span></span> <span data-ttu-id="57559-115">Dans cette vue, les utilisateurs peuvent voir le message de contenu, téléchargez le message ou cliquez sur **modifier** pour basculer en mode édition, où ils peuvent réparer et renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="57559-115">In this view, users can see the message content, download the message, or click **Edit** to switch to Edit view, where they can repair and resubmit the message.</span></span>  
  
 <span data-ttu-id="57559-116">![Page Afficheur de messages](../esb-toolkit/media/ch4-messageviewerpage.gif "MessageViewerPage de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="57559-116">![Message Viewer Page](../esb-toolkit/media/ch4-messageviewerpage.gif "Ch4-MessageViewerPage")</span></span>  
  
 <span data-ttu-id="57559-117">**Figure 3**</span><span class="sxs-lookup"><span data-stu-id="57559-117">**Figure 3**</span></span>  
  
 <span data-ttu-id="57559-118">**L’Afficheur des messages ESB affichant la vue des détails de l’erreur**</span><span class="sxs-lookup"><span data-stu-id="57559-118">**The ESB Message Viewer showing the Fault Details view**</span></span>  
  
 <span data-ttu-id="57559-119">Pour obtenir une description complète et les options d’utilisation du portail de gestion ESB, y compris la visionneuse de l’erreur, le processus de nouvelle soumission de messages et les techniques utilisées pour la liste, le tri et l’analyse des erreurs, consultez [Administration avec le BizTalk ESB Kit de ressources](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md).</span><span class="sxs-lookup"><span data-stu-id="57559-119">For a complete description and usage options of the ESB Management Portal, including the Fault Viewer, the message resubmission process, and the techniques used for listing, sorting, and analyzing faults, see [Administration with the BizTalk ESB Toolkit](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md).</span></span>