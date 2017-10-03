---
title: "Le composant de répartiteur ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe377221034637eab23b70c50ccf48a8454a23bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-dispatcher-component"></a><span data-ttu-id="61333-102">Le composant de répartiteur ESB</span><span class="sxs-lookup"><span data-stu-id="61333-102">The ESB Dispatcher Component</span></span>
<span data-ttu-id="61333-103">Services d’itinéraire basés sur la messagerie sont exécutées dans le composant du répartiteur d’ESB.</span><span class="sxs-lookup"><span data-stu-id="61333-103">Messaging-based itinerary services are executed inside the ESB Dispatcher component.</span></span> <span data-ttu-id="61333-104">Le composant de répartiteur peut définir également dynamiquement les propriétés d’emplacement de point de terminaison pour les messages sortants et transformer dynamiquement des messages.</span><span class="sxs-lookup"><span data-stu-id="61333-104">The Dispatcher component can also dynamically set endpoint location properties for outbound messages and dynamically transform messages.</span></span>  
  
## <a name="component-properties"></a><span data-ttu-id="61333-105">Propriétés du composant</span><span class="sxs-lookup"><span data-stu-id="61333-105">Component Properties</span></span>  
 <span data-ttu-id="61333-106">Le composant de répartiteur a six propriétés :</span><span class="sxs-lookup"><span data-stu-id="61333-106">The Dispatcher component has six properties:</span></span>  
  
-   <span data-ttu-id="61333-107">**RoutingServiceName**.</span><span class="sxs-lookup"><span data-stu-id="61333-107">**RoutingServiceName**.</span></span> <span data-ttu-id="61333-108">Cette propriété spécifie le nom enregistré pour le service de routage basé sur la messagerie.</span><span class="sxs-lookup"><span data-stu-id="61333-108">This property specifies the registered name for the messaging-based routing service.</span></span> <span data-ttu-id="61333-109">La valeur par défaut est **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="61333-109">The default value is **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
-   <span data-ttu-id="61333-110">**TransformServiceName**.</span><span class="sxs-lookup"><span data-stu-id="61333-110">**TransformServiceName**.</span></span> <span data-ttu-id="61333-111">Cette propriété spécifie le nom inscrit pour le service de messagerie-en fonction de transformation.</span><span class="sxs-lookup"><span data-stu-id="61333-111">This property specifies the registered name for the messaging-based transform service.</span></span> <span data-ttu-id="61333-112">La valeur par défaut est **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="61333-112">The default value is **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
-   <span data-ttu-id="61333-113">**Valider**.</span><span class="sxs-lookup"><span data-stu-id="61333-113">**Validate**.</span></span> <span data-ttu-id="61333-114">Cette propriété spécifie si un message doit être validée.</span><span class="sxs-lookup"><span data-stu-id="61333-114">This property specifies whether a message needs to be validated.</span></span>  
  
-   <span data-ttu-id="61333-115">**Activé**.</span><span class="sxs-lookup"><span data-stu-id="61333-115">**Enabled**.</span></span> <span data-ttu-id="61333-116">Cette propriété Active ou désactive le composant.</span><span class="sxs-lookup"><span data-stu-id="61333-116">This property enables or disables the component.</span></span>  
  
-   <span data-ttu-id="61333-117">**Point de terminaison**.</span><span class="sxs-lookup"><span data-stu-id="61333-117">**Endpoint**.</span></span> <span data-ttu-id="61333-118">Cette propriété est une chaîne de connexion de programme de résolution dans un format enregistré avec BizTalk ESB Toolkit.</span><span class="sxs-lookup"><span data-stu-id="61333-118">This property is a resolver connection string in a format registered with BizTalk ESB Toolkit.</span></span>  
  
-   <span data-ttu-id="61333-119">**Nom de mappage**.</span><span class="sxs-lookup"><span data-stu-id="61333-119">**Map Name**.</span></span> <span data-ttu-id="61333-120">Cette propriété est le nom qualifié complet d’un mappage ou un format de chaîne de connexion est inscrite avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="61333-120">This property is either the fully qualified name of a map or a connection string format registered with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:</span></span>  
  
    -   <span data-ttu-id="61333-121">Voici un exemple d’un nom de mappage :</span><span class="sxs-lookup"><span data-stu-id="61333-121">The following is an example of a map name:</span></span>  
  
        ```  
        GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
        ```