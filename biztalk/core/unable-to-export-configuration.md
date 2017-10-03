---
title: "Impossible d’exporter la configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64f09af4-00a0-47cb-889e-d9aeb7266eb2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd7f27a2779819fff934008cc9924dfe01e6064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-configuration"></a><span data-ttu-id="bd321-102">Impossible d'exporter la configuration</span><span class="sxs-lookup"><span data-stu-id="bd321-102">Unable to export configuration</span></span>
## <a name="details"></a><span data-ttu-id="bd321-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bd321-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd321-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bd321-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bd321-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bd321-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="bd321-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bd321-106">Event ID</span></span>|<span data-ttu-id="bd321-107">0</span><span class="sxs-lookup"><span data-stu-id="bd321-107">0</span></span>|  
|<span data-ttu-id="bd321-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bd321-108">Event Source</span></span>|<span data-ttu-id="bd321-109">0</span><span class="sxs-lookup"><span data-stu-id="bd321-109">0</span></span>|  
|<span data-ttu-id="bd321-110">Composant</span><span class="sxs-lookup"><span data-stu-id="bd321-110">Component</span></span>|<span data-ttu-id="bd321-111">0</span><span class="sxs-lookup"><span data-stu-id="bd321-111">0</span></span>|  
|<span data-ttu-id="bd321-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bd321-112">Symbolic Name</span></span>|<span data-ttu-id="bd321-113">0</span><span class="sxs-lookup"><span data-stu-id="bd321-113">0</span></span>|  
|<span data-ttu-id="bd321-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bd321-114">Message Text</span></span>|<span data-ttu-id="bd321-115">Impossible d'exporter la configuration vers le fichier « {0} ».</span><span class="sxs-lookup"><span data-stu-id="bd321-115">Unable to export configuration to file "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bd321-116">Explication</span><span class="sxs-lookup"><span data-stu-id="bd321-116">Explanation</span></span>  
 <span data-ttu-id="bd321-117">Certaines propriétés requises n'ont pas été correctement spécifiées, par exemple Adresse (URI) et Type de liaison.</span><span class="sxs-lookup"><span data-stu-id="bd321-117">Some required properties were not correctly specified, such as Address (URI) and Binding Type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bd321-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bd321-118">User Action</span></span>  
 <span data-ttu-id="bd321-119">La procédure suivante permet de vérifier que les propriétés sont correctes.</span><span class="sxs-lookup"><span data-stu-id="bd321-119">Use the following procedure to verify properties are correct.</span></span>  
  
#### <a name="to-verify-properties"></a><span data-ttu-id="bd321-120">Pour vérifier les propriétés</span><span class="sxs-lookup"><span data-stu-id="bd321-120">To verify properties</span></span>  
  
1.  <span data-ttu-id="bd321-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bd321-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bd321-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="bd321-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="bd321-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="bd321-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="bd321-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="bd321-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="bd321-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bd321-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="bd321-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="bd321-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="bd321-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bd321-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="bd321-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Import/Export** onglet.</span><span class="sxs-lookup"><span data-stu-id="bd321-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Import/Export** tab.</span></span>  
  
9. <span data-ttu-id="bd321-129">Cliquez sur **Exporter**.</span><span class="sxs-lookup"><span data-stu-id="bd321-129">Click **Export**.</span></span>  
  
10. <span data-ttu-id="bd321-130">Vérifiez que les propriétés requises ont été correctement spécifiées.</span><span class="sxs-lookup"><span data-stu-id="bd321-130">Ensure the required properties have been correctly specified.</span></span> <span data-ttu-id="bd321-131">Le schéma de l'adresse (URI) doit correspondre au type de liaison.</span><span class="sxs-lookup"><span data-stu-id="bd321-131">The scheme of the Address (URI) must correctly match the Binding type.</span></span>