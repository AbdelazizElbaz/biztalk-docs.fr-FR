---
title: "Impossible de créer l’élément de configuration de liaison pour la modification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71853662-5a4a-417e-8160-c93dbcbea336
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5c4387e0cb9287ecc4d491291fdfd1fa6b79ab9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-binding-configuration-element-for-editing"></a><span data-ttu-id="531b9-102">Impossible de créer l'élément de configuration de la liaison pour la modification</span><span class="sxs-lookup"><span data-stu-id="531b9-102">Unable to create binding configuration element for editing</span></span>
## <a name="details"></a><span data-ttu-id="531b9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="531b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="531b9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="531b9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="531b9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="531b9-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="531b9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="531b9-106">Event ID</span></span>|<span data-ttu-id="531b9-107">0</span><span class="sxs-lookup"><span data-stu-id="531b9-107">0</span></span>|  
|<span data-ttu-id="531b9-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="531b9-108">Event Source</span></span>|<span data-ttu-id="531b9-109">0</span><span class="sxs-lookup"><span data-stu-id="531b9-109">0</span></span>|  
|<span data-ttu-id="531b9-110">Composant</span><span class="sxs-lookup"><span data-stu-id="531b9-110">Component</span></span>|<span data-ttu-id="531b9-111">0</span><span class="sxs-lookup"><span data-stu-id="531b9-111">0</span></span>|  
|<span data-ttu-id="531b9-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="531b9-112">Symbolic Name</span></span>|<span data-ttu-id="531b9-113">0</span><span class="sxs-lookup"><span data-stu-id="531b9-113">0</span></span>|  
|<span data-ttu-id="531b9-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="531b9-114">Message Text</span></span>|<span data-ttu-id="531b9-115">Impossible de créer l'élément de configuration de la liaison pour la modification.</span><span class="sxs-lookup"><span data-stu-id="531b9-115">Unable to create binding configuration element for editing.</span></span> <span data-ttu-id="531b9-116">Vérifiez les valeurs des propriétés BindingType et BindingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="531b9-116">Check the values of the BindingType and BindingConfiguration properties.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="531b9-117">Explication</span><span class="sxs-lookup"><span data-stu-id="531b9-117">Explanation</span></span>  
 <span data-ttu-id="531b9-118">Une erreur s'est produite lors du chargement d'un élément de liaison à des fins d'affichage dans l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="531b9-118">There was an error loading a binding element for display in the user interface.</span></span> <span data-ttu-id="531b9-119">Cette erreur se produit généralement avec les liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="531b9-119">This error often occurs with custom binding.</span></span> <span data-ttu-id="531b9-120">L'élément de liaison est probablement manquant dans le fichier de configuration, ce qui explique pourquoi il n'est pas disponible dans la liste déroulante pour la liaison.</span><span class="sxs-lookup"><span data-stu-id="531b9-120">The binding element is probably missing in the configuration file and is therefore not available on the drop-down list for binding.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="531b9-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="531b9-121">User Action</span></span>  
 <span data-ttu-id="531b9-122">Vérifiez les valeurs de la **BindingType** et **BindingConfiguration** propriétés.</span><span class="sxs-lookup"><span data-stu-id="531b9-122">Check the values of the **BindingType** and **BindingConfiguration** properties.</span></span>  
  
 <span data-ttu-id="531b9-123">Pour plus d'informations sur la création des éléments de configuration de liaison, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="531b9-123">For further information on creating binding configuration elements, see the following resource:</span></span>  
  
-   [<span data-ttu-id="531b9-124">Configuration de l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="531b9-124">Configuring the WCF-NetMsmq Adapter</span></span>](../core/configuring-the-wcf-netmsmq-adapter.md)