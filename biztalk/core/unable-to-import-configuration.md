---
title: "Impossible d’importer la configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2887da50-4f74-4259-a7d6-c87bc9b9fc58
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e565b466e4f9ce8af3745948952b4318a029ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-configuration"></a><span data-ttu-id="7ece1-102">Impossible d'importer la configuration</span><span class="sxs-lookup"><span data-stu-id="7ece1-102">Unable to import configuration</span></span>
## <a name="details"></a><span data-ttu-id="7ece1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7ece1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ece1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7ece1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7ece1-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7ece1-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="7ece1-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7ece1-106">Event ID</span></span>|<span data-ttu-id="7ece1-107">0</span><span class="sxs-lookup"><span data-stu-id="7ece1-107">0</span></span>|  
|<span data-ttu-id="7ece1-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7ece1-108">Event Source</span></span>|<span data-ttu-id="7ece1-109">0</span><span class="sxs-lookup"><span data-stu-id="7ece1-109">0</span></span>|  
|<span data-ttu-id="7ece1-110">Composant</span><span class="sxs-lookup"><span data-stu-id="7ece1-110">Component</span></span>|<span data-ttu-id="7ece1-111">0</span><span class="sxs-lookup"><span data-stu-id="7ece1-111">0</span></span>|  
|<span data-ttu-id="7ece1-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7ece1-112">Symbolic Name</span></span>|<span data-ttu-id="7ece1-113">0</span><span class="sxs-lookup"><span data-stu-id="7ece1-113">0</span></span>|  
|<span data-ttu-id="7ece1-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7ece1-114">Message Text</span></span>|<span data-ttu-id="7ece1-115">Impossible d'importer la configuration à partir du fichier « {0} »</span><span class="sxs-lookup"><span data-stu-id="7ece1-115">Unable to import configuration from file "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ece1-116">Explication</span><span class="sxs-lookup"><span data-stu-id="7ece1-116">Explanation</span></span>  
 <span data-ttu-id="7ece1-117">Plusieurs raisons peuvent expliquer cette erreur :</span><span class="sxs-lookup"><span data-stu-id="7ece1-117">There could be multiple reasons for this error:</span></span>  
  
-   <span data-ttu-id="7ece1-118">Le fichier de configuration peut contenir des caractères non valides par rapport au codage donné.</span><span class="sxs-lookup"><span data-stu-id="7ece1-118">The configuration file may contain invalid character in the given encoding.</span></span>  
  
-   <span data-ttu-id="7ece1-119">L'élément racine est peut-être manquant.</span><span class="sxs-lookup"><span data-stu-id="7ece1-119">The root element may be missing.</span></span>  
  
-   <span data-ttu-id="7ece1-120">Les données au niveau racine sont peut-être non valides.</span><span class="sxs-lookup"><span data-stu-id="7ece1-120">The data at the root level may be invalid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ece1-121">Cette situation et l'action de l'utilisateur s'appliquent uniquement aux adaptateurs WCF-Custom et WCF-CustomIsolate.</span><span class="sxs-lookup"><span data-stu-id="7ece1-121">This situation, and the user action, applies only to WCF-Custom and WCF-CustomIsolate adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ece1-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7ece1-122">User Action</span></span>  
 <span data-ttu-id="7ece1-123">La procédure suivante permet d'importer un fichier de configuration valide.</span><span class="sxs-lookup"><span data-stu-id="7ece1-123">Use the following procedure to import a valid configuration file.</span></span>  
  
#### <a name="to-import-a-valid-configuration-file"></a><span data-ttu-id="7ece1-124">Pour importer un fichier de configuration valide</span><span class="sxs-lookup"><span data-stu-id="7ece1-124">To import a valid configuration file</span></span>  
  
1.  <span data-ttu-id="7ece1-125">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7ece1-125">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7ece1-126">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="7ece1-126">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="7ece1-127">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="7ece1-127">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="7ece1-128">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="7ece1-128">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="7ece1-129">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7ece1-129">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="7ece1-130">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="7ece1-130">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="7ece1-131">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="7ece1-131">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="7ece1-132">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Import/Export** onglet.</span><span class="sxs-lookup"><span data-stu-id="7ece1-132">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Import/Export** tab.</span></span>  
  
9. <span data-ttu-id="7ece1-133">Cliquez sur **Importer**.</span><span class="sxs-lookup"><span data-stu-id="7ece1-133">Click **Import**.</span></span> <span data-ttu-id="7ece1-134">Importez un fichier de configuration valide et complet.</span><span class="sxs-lookup"><span data-stu-id="7ece1-134">Import a valid and complete configuration file.</span></span>  
  
 <span data-ttu-id="7ece1-135">Vous pouvez également vérifier la validité du fichier de configuration en l’ouvrant avec l’éditeur de Configuration de Service **(Démarrer > tous les programmes > Kit de développement)** (cette étape suppose que vous avez installé le kit SDK Windows.) Ouvrez **svcConfigEditor.exe** et vérifiez chaque propriété du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7ece1-135">You can also verify the validity of the configuration file by opening it with the Service Configuration Editor **(Start > All Programs > Windows SDK)** (this step assumes you have the Windows SDK installed.) Open **svcConfigEditor.exe** and verify each property of the configuration file.</span></span>