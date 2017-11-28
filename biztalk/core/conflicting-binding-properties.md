---
title: "Conflit de propriétés de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b08c317e-a617-464b-9ee4-007fb41d99b2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6202385127a676d1f2714b2c3644d135a3d6a7a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conflicting-binding-properties"></a><span data-ttu-id="5f27d-102">Propriétés de liaison en conflit</span><span class="sxs-lookup"><span data-stu-id="5f27d-102">Conflicting binding properties</span></span>
## <a name="details"></a><span data-ttu-id="5f27d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5f27d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f27d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5f27d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5f27d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5f27d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="5f27d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f27d-106">Event ID</span></span>|<span data-ttu-id="5f27d-107">0</span><span class="sxs-lookup"><span data-stu-id="5f27d-107">0</span></span>|  
|<span data-ttu-id="5f27d-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5f27d-108">Event Source</span></span>|<span data-ttu-id="5f27d-109">0</span><span class="sxs-lookup"><span data-stu-id="5f27d-109">0</span></span>|  
|<span data-ttu-id="5f27d-110">Composant</span><span class="sxs-lookup"><span data-stu-id="5f27d-110">Component</span></span>|<span data-ttu-id="5f27d-111">0</span><span class="sxs-lookup"><span data-stu-id="5f27d-111">0</span></span>|  
|<span data-ttu-id="5f27d-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5f27d-112">Symbolic Name</span></span>|<span data-ttu-id="5f27d-113">0</span><span class="sxs-lookup"><span data-stu-id="5f27d-113">0</span></span>|  
|<span data-ttu-id="5f27d-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5f27d-114">Message Text</span></span>|<span data-ttu-id="5f27d-115">Conflit de propriétés de liaison : MsmqAuthenticationMode = {0} et MsmqProtectionLevel = \ {1\\} n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="5f27d-115">Conflicting binding properties: MsmqAuthenticationMode={0} and MsmqProtectionLevel={1} is invalid.</span></span> <span data-ttu-id="5f27d-116">Modifiez l'une des propriétés pour résoudre le conflit</span><span class="sxs-lookup"><span data-stu-id="5f27d-116">Change one of the properties to resolve the conflict</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f27d-117">Explication</span><span class="sxs-lookup"><span data-stu-id="5f27d-117">Explanation</span></span>  
 <span data-ttu-id="5f27d-118">La valeur de la propriété de niveau de protection MSMQ d’un transport WCF-NetMsmq **signe** ou **EncryptAndSign** pour le mode d’authentification MSMQ aucun.</span><span class="sxs-lookup"><span data-stu-id="5f27d-118">The MSMQ protection level property of a WCF-NetMsmq transport was set to **Sign** or **EncryptAndSign** for the None MSMQ authentication mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f27d-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5f27d-119">User Action</span></span>  
 <span data-ttu-id="5f27d-120">Modifiez le niveau de protection MSMQ ou la propriété de mode d'authentification MSMQ pour obtenir une cohérence avec la propriété de niveau de protection MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5f27d-120">Change the MSMQ protection level or the MSMQ authentication mode property to be consistent with the MSMQ protection level property.</span></span>  
  
1.  <span data-ttu-id="5f27d-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5f27d-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5f27d-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="5f27d-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="5f27d-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="5f27d-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="5f27d-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="5f27d-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="5f27d-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5f27d-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="5f27d-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="5f27d-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="5f27d-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="5f27d-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="5f27d-128">Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="5f27d-128">In the **WCF-NetMsmq Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="5f27d-129">Vérifiez les valeurs dans MSMQ **mode d’authentification** liste et **niveau de protection MSMQ** liste.</span><span class="sxs-lookup"><span data-stu-id="5f27d-129">Check the values in the MSMQ **authentication mode** list and the **MSMQ protection level** list.</span></span>  
  
 <span data-ttu-id="5f27d-130">Pour plus d’informations, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :</span><span class="sxs-lookup"><span data-stu-id="5f27d-130">For further information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="5f27d-131">Comment configurer un Port d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="5f27d-131">How to Configure a WCF-NetMsmq Send Port</span></span>](../core/how-to-configure-a-wcf-netmsmq-send-port.md)  
  
-   [<span data-ttu-id="5f27d-132">Pour configurer les emplacement de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="5f27d-132">How to Configure a WCF-NetMsmq Receive Location</span></span>](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)