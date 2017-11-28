---
title: "Ne peut pas créer de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbe1bd54-6031-4f90-a445-c1647b382a1a
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 227addce4f5a5c1d6d18b7e21646e5276732a28f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-create-binding"></a><span data-ttu-id="5447e-102">Impossible de créer la liaison</span><span class="sxs-lookup"><span data-stu-id="5447e-102">Cannot create binding</span></span>
## <a name="details"></a><span data-ttu-id="5447e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5447e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5447e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5447e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5447e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5447e-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="5447e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5447e-106">Event ID</span></span>|<span data-ttu-id="5447e-107">0</span><span class="sxs-lookup"><span data-stu-id="5447e-107">0</span></span>|  
|<span data-ttu-id="5447e-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5447e-108">Event Source</span></span>|<span data-ttu-id="5447e-109">0</span><span class="sxs-lookup"><span data-stu-id="5447e-109">0</span></span>|  
|<span data-ttu-id="5447e-110">Composant</span><span class="sxs-lookup"><span data-stu-id="5447e-110">Component</span></span>|<span data-ttu-id="5447e-111">0</span><span class="sxs-lookup"><span data-stu-id="5447e-111">0</span></span>|  
|<span data-ttu-id="5447e-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5447e-112">Symbolic Name</span></span>|<span data-ttu-id="5447e-113">0</span><span class="sxs-lookup"><span data-stu-id="5447e-113">0</span></span>|  
|<span data-ttu-id="5447e-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5447e-114">Message Text</span></span>|<span data-ttu-id="5447e-115">Impossible de créer la liaison car le type de liaison n'est pas indiqué.</span><span class="sxs-lookup"><span data-stu-id="5447e-115">Cannot create binding since binding type was not specified.</span></span> <span data-ttu-id="5447e-116">Spécifiez un type de liaison tel que « basicHttpBinding », « wsHttpBinding » ou « customBinding »</span><span class="sxs-lookup"><span data-stu-id="5447e-116">Specify a binding type like "basicHttpBinding", "wsHttpBinding", or "customBinding</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5447e-117">Explication</span><span class="sxs-lookup"><span data-stu-id="5447e-117">Explanation</span></span>  
 <span data-ttu-id="5447e-118">Vous n'avez pas défini la propriété BindingType dans le code après la configuration d'un transport WCF-Custom ou WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="5447e-118">You did not set the BindingType property in the code after configuring a WCF-Custom or a WCF-CustomIsolated transport.</span></span> <span data-ttu-id="5447e-119">Le problème peut également provenir d'autres chemins d'accès au code.</span><span class="sxs-lookup"><span data-stu-id="5447e-119">Or the problem could be in other code paths.</span></span> <span data-ttu-id="5447e-120">Le paramètre de liaison doit être associé à une valeur dans l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5447e-120">You must have a value in the user interface for binding setting.</span></span> <span data-ttu-id="5447e-121">Vérifiez votre configuration et assurez-vous qu'un type de liaison a été choisi dans la liste déroulante de la zone Propriétés de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="5447e-121">Review your configuration and ensure that a binding type was chosen from the drop-down list in the receive location Properties area.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5447e-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5447e-122">User Action</span></span>  
 <span data-ttu-id="5447e-123">Pour résoudre cette erreur, vérifiez le code de configuration du transport WCF-Custom ou WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="5447e-123">To resolve this error, review the code configuring the WCF-Custom or WCF-CustomIsolated transport.</span></span> <span data-ttu-id="5447e-124">Vérifiez que le **BindingType** propriété dans les données XML pour le **TransportTypeData** propriété de l’interface ITransportInfo est définie correctement.</span><span class="sxs-lookup"><span data-stu-id="5447e-124">Ensure that the **BindingType** property in the XML data for the **TransportTypeData** property of the ITransportInfo interface is set properly.</span></span>  
  
 <span data-ttu-id="5447e-125">En outre, spécifiez un type de liaison **basicHttpBinding**, **wsHttpBinding**, ou **customBinding**.</span><span class="sxs-lookup"><span data-stu-id="5447e-125">Also, specify a binding type like **basicHttpBinding**, **wsHttpBinding**, or **customBinding**.</span></span>  
  
1.  <span data-ttu-id="5447e-126">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5447e-126">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5447e-127">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="5447e-127">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="5447e-128">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="5447e-128">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="5447e-129">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="5447e-129">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="5447e-130">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5447e-130">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="5447e-131">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="5447e-131">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="5447e-132">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="5447e-132">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="5447e-133">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="5447e-133">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="5447e-134">Vérifiez qu’une valeur est spécifiée dans le **Type de liaison** liste.</span><span class="sxs-lookup"><span data-stu-id="5447e-134">Ensure that a value is specified in the **Binding Type** list.</span></span>  
  
 <span data-ttu-id="5447e-135">Pour plus d'informations sur la configuration des liaisons, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="5447e-135">For additional information on configuring binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="5447e-136">Pour configurer les emplacement de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="5447e-136">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="5447e-137">Pour configurer les emplacement de réception WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="5447e-137">How to Configure a WCF-Custom Receive Location</span></span>](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [<span data-ttu-id="5447e-138">Comment configurer un Port d’envoi WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="5447e-138">How to Configure a WCF-Custom Send Port</span></span>](../core/how-to-configure-a-wcf-custom-send-port.md)