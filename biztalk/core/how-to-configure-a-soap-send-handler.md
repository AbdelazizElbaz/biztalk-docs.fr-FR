---
title: "Comment configurer un gestionnaire d’envoi SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, SOAP adapters
- SOAP adapters, denial of service
- denital of service, HTTP adapters
- configuring [SOAP adapters], send handlers
- configuring [SOAP adapters], denial of service
- SOAP adapters, send handlers
- denial of service, SOAP adapters
ms.assetid: fd610a3f-ca10-42e0-b81e-219e07e33830
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65ca116b47e36d754b27839a09225aeb313c9e0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-send-handler"></a><span data-ttu-id="744bd-102">Comment configurer un gestionnaire d’envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="744bd-102">How to Configure a SOAP Send Handler</span></span>
<span data-ttu-id="744bd-103">La procédure suivante permet de configurer le gestionnaire d'envoi SOAP.</span><span class="sxs-lookup"><span data-stu-id="744bd-103">Use the following procedure to configure the SOAP send handler.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="744bd-104">Lorsque vous utilisez des gestionnaires d’adaptateur HTTP ou SOAP, il est recommandé d’installer les instances d’hôte pour ces gestionnaires sur Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="744bd-104">When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]computers.</span></span>  
  
### <a name="to-change-global-variables-for-a-soap-send-handler"></a><span data-ttu-id="744bd-105">Pour modifier des variables globales d'un gestionnaire d'envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="744bd-105">To change global variables for a SOAP send handler</span></span>  
  
1.  <span data-ttu-id="744bd-106">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.</span><span class="sxs-lookup"><span data-stu-id="744bd-106">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="744bd-107">Dans la liste développée des adaptateurs, cliquez sur **SOAP**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="744bd-107">In the expanded adapter list, click **SOAP**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="744bd-108">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="744bd-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="744bd-109">Sur le **Proxy** onglet, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="744bd-109">On the **Proxy** tab, do the following.</span></span>  
  
    |<span data-ttu-id="744bd-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="744bd-110">Use this</span></span>|<span data-ttu-id="744bd-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="744bd-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="744bd-112">**Utiliser le proxy**</span><span class="sxs-lookup"><span data-stu-id="744bd-112">**Use proxy**</span></span>|<span data-ttu-id="744bd-113">Indiquer si le gestionnaire d'envoi SOAP fait appel ou non à un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="744bd-113">Indicate whether the SOAP send handler uses a proxy server.</span></span>|  
    |<span data-ttu-id="744bd-114">**Server**</span><span class="sxs-lookup"><span data-stu-id="744bd-114">**Server**</span></span>|<span data-ttu-id="744bd-115">Indiquer le nom du serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="744bd-115">Specify the name of the proxy server.</span></span><br /><br /> <span data-ttu-id="744bd-116">Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="744bd-116">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="744bd-117">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="744bd-117">Type: String</span></span><br /><br /> <span data-ttu-id="744bd-118">Longueur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="744bd-118">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="744bd-119">Longueur maximale : 256</span><span class="sxs-lookup"><span data-stu-id="744bd-119">Maximum length: 256</span></span>|  
    |<span data-ttu-id="744bd-120">**Port**</span><span class="sxs-lookup"><span data-stu-id="744bd-120">**Port**</span></span>|<span data-ttu-id="744bd-121">Indiquer le port que le gestionnaire d'envoi SOAP utilise.</span><span class="sxs-lookup"><span data-stu-id="744bd-121">Specify the port the SOAP send handler uses.</span></span><br /><br /> <span data-ttu-id="744bd-122">Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="744bd-122">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="744bd-123">Valeur par défaut : 80</span><span class="sxs-lookup"><span data-stu-id="744bd-123">Default Value: 80</span></span><br /><br /> <span data-ttu-id="744bd-124">Type : Long</span><span class="sxs-lookup"><span data-stu-id="744bd-124">Type: Long</span></span><br /><br /> <span data-ttu-id="744bd-125">Valeur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="744bd-125">Minimum value: 0</span></span><br /><br /> <span data-ttu-id="744bd-126">Valeur maximale : 65535</span><span class="sxs-lookup"><span data-stu-id="744bd-126">Maximum value: 65535</span></span>|  
    |<span data-ttu-id="744bd-127">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="744bd-127">**User name**</span></span>|<span data-ttu-id="744bd-128">Indiquer le nom d’utilisateur nécessaire à l’authentification.</span><span class="sxs-lookup"><span data-stu-id="744bd-128">Specify the user name to use for authentication.</span></span><br /><br /> <span data-ttu-id="744bd-129">Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="744bd-129">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="744bd-130">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="744bd-130">Type: String</span></span><br /><br /> <span data-ttu-id="744bd-131">Longueur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="744bd-131">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="744bd-132">Longueur maximale : 256</span><span class="sxs-lookup"><span data-stu-id="744bd-132">Maximum length: 256</span></span>|  
    |<span data-ttu-id="744bd-133">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="744bd-133">**Password**</span></span>|<span data-ttu-id="744bd-134">Indiquer le mot de passe nécessaire à l’authentification.</span><span class="sxs-lookup"><span data-stu-id="744bd-134">Specify the password to use for authentication.</span></span><br /><br /> <span data-ttu-id="744bd-135">Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="744bd-135">This property only requires a value if **Use proxy** is selected.</span></span><br /><br /> <span data-ttu-id="744bd-136">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="744bd-136">Type: String</span></span><br /><br /> <span data-ttu-id="744bd-137">Longueur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="744bd-137">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="744bd-138">Longueur maximale : 256</span><span class="sxs-lookup"><span data-stu-id="744bd-138">Maximum length: 256</span></span>|  
  
5.  <span data-ttu-id="744bd-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="744bd-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744bd-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="744bd-140">See Also</span></span>  
 <span data-ttu-id="744bd-141">[Configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="744bd-141">[Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="744bd-142">Publication de Services Web</span><span class="sxs-lookup"><span data-stu-id="744bd-142">Publishing Web Services</span></span>](../core/publishing-web-services.md)