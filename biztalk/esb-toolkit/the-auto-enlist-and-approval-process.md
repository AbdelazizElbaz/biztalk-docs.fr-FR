---
title: "Le processus d’approbation et inscription automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd3e72e-e28b-4ee3-bc4a-89ef3f64e6d5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333e1403ffd45f80a98d3eb17f5d3aa2b63c7798
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-auto-enlist-and-approval-process"></a><span data-ttu-id="7c2a2-102">Le processus d’approbation et inscription automatique</span><span class="sxs-lookup"><span data-stu-id="7c2a2-102">The Auto-Enlist and Approval Process</span></span>
<span data-ttu-id="7c2a2-103">Vous pouvez configurer le portail de gestion ESB pour publier des points de terminaison de Microsoft BizTalk Server de deux manières :</span><span class="sxs-lookup"><span data-stu-id="7c2a2-103">You can configure the ESB Management Portal to publish Microsoft BizTalk Server endpoints in two ways:</span></span>  
  
-   <span data-ttu-id="7c2a2-104">Il peut être configuré via le processus d’approbation, où un administrateur doit vérifier et approuver la demande d’inscription.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-104">It can be configured through the approval process, where an administrator must confirm and approve the registration request.</span></span>  
  
-   <span data-ttu-id="7c2a2-105">Il peut être configuré à l’aide de publication automatique, où le portail publie automatiquement la demande dans le Registre Universal Description, Discovery and Integration (UDDI) sans nécessiter d’intervention de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-105">It can be configured by using auto-publish, where the portal automatically publishes the request into the Universal Description, Discovery, and Integration (UDDI) registry without requiring administrator intervention.</span></span>  
  
 <span data-ttu-id="7c2a2-106">Vous pouvez également spécifier d’autres paramètres de fonctionnalités d’intégration d’UDDI du portail, comme décrit dans les deux procédures suivantes.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-106">You can also specify several other settings of the UDDI Integration features of the portal, as described in the following two procedures.</span></span>  
  
### <a name="to-configure-auto-approval-and-publishing-in-the-esb-management-portal"></a><span data-ttu-id="7c2a2-107">Pour configurer l’approbation automatique et la publication dans le portail de gestion ESB</span><span class="sxs-lookup"><span data-stu-id="7c2a2-107">To configure auto-approval and publishing in the ESB Management Portal</span></span>  
  
1.  <span data-ttu-id="7c2a2-108">Assurez-vous que vous vous connectez au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-108">Make sure that you log on to the portal using an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="7c2a2-109">Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **paramètres du Registre** pour ouvrir le portail [Page Paramètres du Registre](../esb-toolkit/registry-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a2-109">Point to the **Admin** tab on the portal main menu, and then click **Registry Settings** to open the portal [Registry Settings Page](../esb-toolkit/registry-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="7c2a2-110">Pour activer l’approbation automatique et la publication, tapez l’URL de votre serveur UDDI dans la zone de texte en haut de la **UDDI détails** section de la page, puis sélectionnez le **qu’elle publie automatiquement** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-110">To enable auto-approval and publishing, type the URL of your UDDI server in the text box at the top of the **UDDI Details** section of the page, and then select the **AutoPublish** check box.</span></span>  
  
4.  <span data-ttu-id="7c2a2-111">Pour désactiver l’approbation automatique et la publication, désactivez le **publication automatique** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-111">To disable auto-approval and publishing, clear the **Auto Publish** check box.</span></span>  
  
### <a name="to-configure-e-mail-and-registry-settings-for-the-uddi-integration-features"></a><span data-ttu-id="7c2a2-112">Pour configurer les paramètres de messagerie et du Registre pour les fonctionnalités d’intégration d’UDDI</span><span class="sxs-lookup"><span data-stu-id="7c2a2-112">To configure e-mail and registry settings for the UDDI Integration features</span></span>  
  
1.  <span data-ttu-id="7c2a2-113">Assurez-vous que vous vous connectez au portail à l’aide d’un compte qui est membre d’un groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-113">Make sure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group.</span></span>  
  
2.  <span data-ttu-id="7c2a2-114">Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **paramètres du Registre** pour ouvrir le portail [Page Paramètres du Registre](../esb-toolkit/registry-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a2-114">Point to the **Admin** tab on the portal main menu, and then click **Registry Settings** to open the portal [Registry Settings Page](../esb-toolkit/registry-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="7c2a2-115">Modifiez l’URL de votre serveur UDDI dans la zone de texte en haut de la **UDDI détails** section de la page.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-115">Edit the URL of your UDDI server in the text box at the top of the **UDDI Details** section of the page.</span></span> <span data-ttu-id="7c2a2-116">Le service UDDI par défaut est le service de Microsoft UDDI local.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-116">The default UDDI service is the local Microsoft UDDI service.</span></span>  
  
4.  <span data-ttu-id="7c2a2-117">Sélectionnez le **anonyme** case à cocher si vous souhaitez que le portail pour l’authentification anonyme lorsque l’accès au serveur UDDI.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-117">Select the **Anonymous** check box if you want the portal to use anonymous authentication when accessing the UDDI server.</span></span>  
  
5.  <span data-ttu-id="7c2a2-118">Si vous souhaitez que le portail pour vous informer par courrier électronique lorsqu’une publication UDDI la demande est en attente d’approbation, sélectionnez le **Notification activée** case à cocher dans la **Notification par courrier électronique** section de la page.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-118">If you want the portal to notify you by e-mail when a UDDI publishing request is awaiting approval, select the **Notification Enabled** check box in the **Email Notification** section of the page.</span></span> <span data-ttu-id="7c2a2-119">Puis entrez les détails de votre serveur de messagerie, l’adresse de livraison des messages électroniques, une adresse de messagerie « from » approprié, l’objet du message et le corps du message.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-119">Then enter the details of your e-mail server, the address for delivery of e-mail messages, an appropriate "from" e-mail address, the message subject, and the message body.</span></span>  
  
6.  <span data-ttu-id="7c2a2-120">Entrez le nom du contact administrateur et l’adresse de messagerie pour la réception de UDDI demander des messages électroniques dans les **les paramètres par défaut** section de la page.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-120">Enter the administrator contact name and e-mail address for the receipt of UDDI request e-mail messages in the **Default Settings** section of the page.</span></span>  
  
### <a name="to-approve-or-decline-a-registration-request-as-an-administrator"></a><span data-ttu-id="7c2a2-121">Pour approuver ou refuser une demande d’enregistrement en tant qu’administrateur</span><span class="sxs-lookup"><span data-stu-id="7c2a2-121">To approve or decline a registration request as an administrator</span></span>  
  
1.  <span data-ttu-id="7c2a2-122">Assurez-vous que vous vous connectez au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-122">Make sure that you log into the portal using an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="7c2a2-123">Pointez sur le **Registre** onglet dans le menu principal de portail, puis cliquez sur **gérer les demandes en attente** pour ouvrir le portail [Page Gestion des demandes en attente](../esb-toolkit/manage-pending-requests-page.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a2-123">Point to the **Registry** tab on the portal main menu, and then click **Manage Pending Requests** to open the portal [Manage Pending Requests Page](../esb-toolkit/manage-pending-requests-page.md).</span></span>  
  
3.  <span data-ttu-id="7c2a2-124">Pour approuver une demande en attente, cliquez sur le **approuver** icône (coche) en regard de cette demande dans la liste.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-124">To approve a pending request, click the **Approve** icon (the check mark) next to that request in the list.</span></span>  
  
4.  <span data-ttu-id="7c2a2-125">Pour refuser une demande en attente, cliquez sur le **rejeter** icône (croix) en regard de cette demande dans la liste.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-125">To reject a pending request, click the **Reject** icon (the cross mark) next to that request in the list.</span></span>  
  
5.  <span data-ttu-id="7c2a2-126">Pour afficher les détails d’une demande en attente, cliquez sur le **afficher les détails** icône (la Loupe) pour ouvrir la [Page Détails du Registre](../esb-toolkit/registry-details-page.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a2-126">To view details of a pending request, click the **View Details** icon (the magnifying glass) to open the [Registry Details Page](../esb-toolkit/registry-details-page.md).</span></span> <span data-ttu-id="7c2a2-127">Vous pouvez publier, supprimer ou mettre à jour de la demande dans cette page.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-127">You can publish, delete, or update the request in this page.</span></span>  
  
6.  <span data-ttu-id="7c2a2-128">Pour consulter l’état des demandes et affiche une liste de demandes précédentes, cliquez sur le **afficher l’historique de demande** lien.</span><span class="sxs-lookup"><span data-stu-id="7c2a2-128">To review the requests status and see a list of previous requests, click the **View Request History** link.</span></span>