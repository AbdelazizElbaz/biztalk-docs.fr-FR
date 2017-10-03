---
title: "Single Sign-On : Événement 10512 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edf0512-112d-40b8-9e29-7dd67f999b6d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a586af2b280e9d968b87a7cb3e7680a17457ca0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10512"></a><span data-ttu-id="c688d-102">Single Sign-On : Événement 10512</span><span class="sxs-lookup"><span data-stu-id="c688d-102">Single Sign-On: Event 10512</span></span>
## <a name="details"></a><span data-ttu-id="c688d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c688d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c688d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c688d-104">Product Name</span></span>|<span data-ttu-id="c688d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c688d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c688d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c688d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c688d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c688d-107">Event ID</span></span>|<span data-ttu-id="c688d-108">10512</span><span class="sxs-lookup"><span data-stu-id="c688d-108">10512</span></span>|  
|<span data-ttu-id="c688d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c688d-109">Event Source</span></span>|<span data-ttu-id="c688d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c688d-110">ENTSSO</span></span>|  
|<span data-ttu-id="c688d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c688d-111">Component</span></span>|<span data-ttu-id="c688d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c688d-112">N\A</span></span>|  
|<span data-ttu-id="c688d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c688d-113">Symbolic Name</span></span>|<span data-ttu-id="c688d-114">SSO_ERROR_LOADLIBRARY</span><span class="sxs-lookup"><span data-stu-id="c688d-114">SSO_ERROR_LOADLIBRARY</span></span>|  
|<span data-ttu-id="c688d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c688d-115">Message Text</span></span>|<span data-ttu-id="c688d-116">Impossible de charger %1%r</span><span class="sxs-lookup"><span data-stu-id="c688d-116">Failed to load %1%r</span></span><br /><br /> <span data-ttu-id="c688d-117">Code d’erreur : %2.</span><span class="sxs-lookup"><span data-stu-id="c688d-117">Error code: %2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c688d-118">Explication</span><span class="sxs-lookup"><span data-stu-id="c688d-118">Explanation</span></span>  
 <span data-ttu-id="c688d-119">Cet événement d'erreur indique que le fichier DLL (Dynamic Link Library) n'a pas pu être chargé dans le processus de serveur SSO.</span><span class="sxs-lookup"><span data-stu-id="c688d-119">This Error event indicates that the specified Dynamic Link Library (DLL) could not be loaded into the SSO server process.</span></span> <span data-ttu-id="c688d-120">L'absence du fichier DLL dans le répertoire d'installation de l'authentification unique (généralement, C:\Program Files\Common Files\Enterprise Single Sign-On) peut indiquer que le programme d'installation n'a pas été correctement exécuté ou que le fichier DLL a été supprimé après l'exécution du programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="c688d-120">If the DLL is missing in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On, it may indicate that setup was not completed correctly, or that the DLL was deleted after setup was completed.</span></span> <span data-ttu-id="c688d-121">Si le fichier DLL est présent, il se peut qu'il y ait un problème dans le cadre de la résolution du chemin d'accès correct au fichier DLL par le service d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="c688d-121">If the DLL is present, then there could be a problem with the SSO service resolving the correct path to the DLL.</span></span> <span data-ttu-id="c688d-122">Il se peut également que le fichier DLL soit lui-même endommagé.</span><span class="sxs-lookup"><span data-stu-id="c688d-122">Additionally, the DLL itself could be corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c688d-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c688d-123">User Action</span></span>  
 <span data-ttu-id="c688d-124">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="c688d-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="c688d-125">Si une défaillance du programme d'installation est suspectée, il peut être nécessaire de désinstaller, puis de réinstaller le produit.</span><span class="sxs-lookup"><span data-stu-id="c688d-125">If a wider failure of setup is suspected it may be necessary to uninstall and reinstall the product.</span></span>  
  
-   <span data-ttu-id="c688d-126">Si le fichier DLL est manquant ou endommagé, remplacez-le, puis redémarrez le service.</span><span class="sxs-lookup"><span data-stu-id="c688d-126">If the single DLL is missing or corrupted, attempt to replace it and then restart the service.</span></span>  
  
 <span data-ttu-id="c688d-127">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="c688d-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="c688d-128">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c688d-128">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)