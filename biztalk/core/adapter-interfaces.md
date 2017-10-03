---
title: "Interfaces d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7398aeb-7c1c-400e-a552-d0ab39e55a0b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717adcf5d4a706a7cc072b42b224ab0f9f8cc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-interfaces"></a><span data-ttu-id="3f0d0-102">Interfaces d’adaptateur</span><span class="sxs-lookup"><span data-stu-id="3f0d0-102">Adapter Interfaces</span></span>
<span data-ttu-id="3f0d0-103">Les adaptateurs personnalisés doivent implémenter trois interfaces. Il existe en outre deux interfaces facultatives.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-103">There are three interfaces that custom adapters must implement, and two interfaces that are optional.</span></span>  
  
## <a name="mandatory-interfaces"></a><span data-ttu-id="3f0d0-104">Interfaces obligatoires</span><span class="sxs-lookup"><span data-stu-id="3f0d0-104">Mandatory interfaces</span></span>  
 <span data-ttu-id="3f0d0-105">Tous les adaptateurs doivent implémenter les interfaces suivantes.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-105">All adapters must implement the following interfaces.</span></span>  
  
### <a name="ibasecomponent"></a><span data-ttu-id="3f0d0-106">IBaseComponent</span><span class="sxs-lookup"><span data-stu-id="3f0d0-106">IBaseComponent</span></span>  
 <span data-ttu-id="3f0d0-107">Cette interface détaille le **nom**, **Version**, et **Description** de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-107">This interface details the **Name**, **Version**, and **Description** of the adapter.</span></span>  
  
### <a name="ibttransport"></a><span data-ttu-id="3f0d0-108">IBTTransport</span><span class="sxs-lookup"><span data-stu-id="3f0d0-108">IBTTransport</span></span>  
 <span data-ttu-id="3f0d0-109">Cette interface détaille le **Type de Transport** et **ClassID** de la carte.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-109">This interface details the **Transport Type** and **ClassID** of the adapter.</span></span>  
  
### <a name="ibtbatchcallback"></a><span data-ttu-id="3f0d0-110">IBTBatchCallback</span><span class="sxs-lookup"><span data-stu-id="3f0d0-110">IBTBatchCallback</span></span>  
 <span data-ttu-id="3f0d0-111">Cette interface est une interface de rappel par l'intermédiaire de laquelle l'adaptateur reçoit les informations d'état et d'erreur liées à un lot de messages soumis au moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-111">This interface is a callback interface through which the adapter receives status and error information for a batch of messages it submits to the Messaging Engine.</span></span>  
  
## <a name="optional-interfaces"></a><span data-ttu-id="3f0d0-112">Interfaces facultatives</span><span class="sxs-lookup"><span data-stu-id="3f0d0-112">Optional interfaces</span></span>  
 <span data-ttu-id="3f0d0-113">Les adaptateurs peuvent implémenter les interfaces ci-dessous, si besoin est.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-113">Adapters may or may not implement the following interfaces, depending on their needs.</span></span>  
  
### <a name="ipersistpropertybag"></a><span data-ttu-id="3f0d0-114">IPersistPropertyBag</span><span class="sxs-lookup"><span data-stu-id="3f0d0-114">IPersistPropertyBag</span></span>  
 <span data-ttu-id="3f0d0-115">Il s'agit d'une interface de configuration par le biais de laquelle la configuration du gestionnaire est fournie à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-115">This is a configuration interface through which handler configuration is delivered to the adapter.</span></span> <span data-ttu-id="3f0d0-116">Cette interface est requise uniquement pour les adaptateurs disposant d'informations de configuration de gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-116">This interface is required only for adapters that have handler configuration information.</span></span>  
  
### <a name="ibttransportcontrol"></a><span data-ttu-id="3f0d0-117">IBTTransportControl</span><span class="sxs-lookup"><span data-stu-id="3f0d0-117">IBTTransportControl</span></span>  
 <span data-ttu-id="3f0d0-118">Cette interface permet d'initialiser et d'arrêter un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-118">This interface is used to initialize and terminate an adapter.</span></span> <span data-ttu-id="3f0d0-119">Le proxy de transport de l'adaptateur lui est transmis par l'intermédiaire de cette interface.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-119">The adapter's transport proxy is passed to it through this interface.</span></span> <span data-ttu-id="3f0d0-120">Cette interface n'est pas requise pour les adaptateurs isolés.</span><span class="sxs-lookup"><span data-stu-id="3f0d0-120">This interface is not required for isolated adapters.</span></span>