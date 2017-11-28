---
title: "Le serveur Web sur le port d’hôte introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dce09ce00a169ad14bbc8ae2ab28fe70c039c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="web-server-on-host-port-not-found"></a><span data-ttu-id="508b3-102">Serveur Web introuvable sur le port de l'hôte</span><span class="sxs-lookup"><span data-stu-id="508b3-102">Web server on host port not found</span></span>
## <a name="details"></a><span data-ttu-id="508b3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="508b3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="508b3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="508b3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="508b3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="508b3-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="508b3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="508b3-106">Event ID</span></span>|<span data-ttu-id="508b3-107">0</span><span class="sxs-lookup"><span data-stu-id="508b3-107">0</span></span>|  
|<span data-ttu-id="508b3-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="508b3-108">Event Source</span></span>|<span data-ttu-id="508b3-109">0</span><span class="sxs-lookup"><span data-stu-id="508b3-109">0</span></span>|  
|<span data-ttu-id="508b3-110">Composant</span><span class="sxs-lookup"><span data-stu-id="508b3-110">Component</span></span>|<span data-ttu-id="508b3-111">0</span><span class="sxs-lookup"><span data-stu-id="508b3-111">0</span></span>|  
|<span data-ttu-id="508b3-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="508b3-112">Symbolic Name</span></span>|<span data-ttu-id="508b3-113">0</span><span class="sxs-lookup"><span data-stu-id="508b3-113">0</span></span>|  
|<span data-ttu-id="508b3-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="508b3-114">Message Text</span></span>|<span data-ttu-id="508b3-115">Serveur Web sur l’hôte « {0} » {{1} de port introuvable</span><span class="sxs-lookup"><span data-stu-id="508b3-115">Web server on host "{0}" port {1} not found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="508b3-116">Explication</span><span class="sxs-lookup"><span data-stu-id="508b3-116">Explanation</span></span>  
 <span data-ttu-id="508b3-117">Cette erreur indique que le service World Wide Web n'est pas en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="508b3-117">This error indicates the World Wide Web (WWW) service is not running.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="508b3-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="508b3-118">User Action</span></span>  
 <span data-ttu-id="508b3-119">La procédure suivante permet de démarrer le service World Wide Web.</span><span class="sxs-lookup"><span data-stu-id="508b3-119">Use the following procedure to start the World Wide Web service.</span></span>  
  
#### <a name="to-start-the-world-wide-web-service"></a><span data-ttu-id="508b3-120">Pour démarrer le service World Wide Web</span><span class="sxs-lookup"><span data-stu-id="508b3-120">To start the World Wide Web service</span></span>  
  
1.  <span data-ttu-id="508b3-121">Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, double-cliquez sur **outils d’administration**, double-cliquez sur **Services.**</span><span class="sxs-lookup"><span data-stu-id="508b3-121">Click **Start**, click **Control Panel**, double-click **Administrative Tools**, and double-click **Services.**</span></span>  
  
2.  <span data-ttu-id="508b3-122">Dans la colonne nom, recherchez **World Wide Web Publishing**.</span><span class="sxs-lookup"><span data-stu-id="508b3-122">In the Name column, locate **World Wide Web Publishing**.</span></span> <span data-ttu-id="508b3-123">Vérifiez que l’état est **démarré**.</span><span class="sxs-lookup"><span data-stu-id="508b3-123">Ensure that the status is **Started**.</span></span>  
  
3.  <span data-ttu-id="508b3-124">Retour à la **outils d’administration** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="508b3-124">Return to the **Administrative Tools** window.</span></span> <span data-ttu-id="508b3-125">Double-cliquez sur **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="508b3-125">Double-click **Internet Information Services**.</span></span>  
  
4.  <span data-ttu-id="508b3-126">Développez la zone du dossier et recherchez le site Web.</span><span class="sxs-lookup"><span data-stu-id="508b3-126">Expand the folder area and locate the web site.</span></span>  
  
5.  <span data-ttu-id="508b3-127">Vérifiez que l’état est **démarré**.</span><span class="sxs-lookup"><span data-stu-id="508b3-127">Ensure that the status is **Started**.</span></span>