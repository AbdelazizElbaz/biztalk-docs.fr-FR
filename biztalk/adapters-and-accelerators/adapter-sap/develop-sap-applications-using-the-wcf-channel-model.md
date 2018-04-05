---
title: Développer des applications SAP à l’aide du modèle de canal WCF | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, developing applications by using
ms.assetid: 1ce70c8b-5eeb-4585-97af-b0a7b4398dac
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13015cb042d26c946abfa3c99a4f67034b8d9708
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sap-applications-using-the-wcf-channel-model"></a><span data-ttu-id="a2945-102">Développer des applications SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2945-102">Develop SAP applications using the WCF Channel Model</span></span>
<span data-ttu-id="a2945-103">Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de SAP.</span><span class="sxs-lookup"><span data-stu-id="a2945-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] by sending XML messages directly over a channel instance created with the SAP Binding.</span></span>  
  
 <span data-ttu-id="a2945-104">Un avantage de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes que le modèle de service WCF expose est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="a2945-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the SAP system.</span></span> <span data-ttu-id="a2945-105">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="a2945-105">Why?</span></span> <span data-ttu-id="a2945-106">Dans le modèle de canal WCF vous contrôler directement le contenu des messages que vous envoyez sur le canal.</span><span class="sxs-lookup"><span data-stu-id="a2945-106">In the WCF channel model you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="a2945-107">Un autre avantage clé qui fournit un modèle de canal WCF sur le modèle de service WCF est prise en charge plus complète pour la diffusion en continu de données.</span><span class="sxs-lookup"><span data-stu-id="a2945-107">Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for data streaming.</span></span> <span data-ttu-id="a2945-108">En utilisant le modèle de canal WCF, vous pouvez effectuer :</span><span class="sxs-lookup"><span data-stu-id="a2945-108">By using the WCF channel model you can perform:</span></span>  
  
-   <span data-ttu-id="a2945-109">Nœud de message de diffusion en continu sur tous les messages échangés entre votre code et de la carte.</span><span class="sxs-lookup"><span data-stu-id="a2945-109">Message node streaming on all messages exchanged between your code and the adapter.</span></span>  
  
-   <span data-ttu-id="a2945-110">Message-valeur du nœud de diffusion en continu sur les opérations SendIdoc et ReceiveIdoc.</span><span class="sxs-lookup"><span data-stu-id="a2945-110">Message node-value streaming on the SendIdoc and ReceiveIdoc operations.</span></span>  
  
 <span data-ttu-id="a2945-111">Il s’agit, car dans le modèle de canal WCF vous contrôlez directement comment vous fournir le corps du message sur les messages que vous envoyez à l’adaptateur et comment vous consommez le corps du message sur les messages que vous recevez à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a2945-111">This is because in the WCF channel model you directly control how you provide the message body on messages that you send to the adapter and how you consume the message body on messages that you receive from the adapter.</span></span>  
  
 <span data-ttu-id="a2945-112">En revanche, l’adaptateur ne fournit aucune prise en charge pour la diffusion en continu dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="a2945-112">In contrast, the adapter provides no support for streaming in the WCF service model.</span></span> <span data-ttu-id="a2945-113">Étant donné que, dans le modèle de service WCF, le runtime WCF sérialise et désérialise les messages entre leurs XML et les représentations d’objets du code managé, une copie complète de la mémoire de chaque message que vous échangez avec l’adaptateur est effectuée.</span><span class="sxs-lookup"><span data-stu-id="a2945-113">Because, in the WCF service model, the WCF runtime serializes and deserializes messages between their XML and managed code object representations, a complete in-memory copy of each message that you exchange with the adapter is made.</span></span>  
  
 <span data-ttu-id="a2945-114">Les sections de cette rubrique expliquent comment effectuer les opérations sur les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en utilisant le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="a2945-114">The sections in this topic explain how to perform operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2945-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2945-115">In This Section</span></span>  
  
-   [<span data-ttu-id="a2945-116">Vue d’ensemble du modèle de canal WCF avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="a2945-116">Overview of the WCF Channel Model with the SAP Adapter</span></span>](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-channel-model-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="a2945-117">Créer un canal à l’aide de SAP</span><span class="sxs-lookup"><span data-stu-id="a2945-117">Create a channel using SAP</span></span>](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)  
  
-   [<span data-ttu-id="a2945-118">Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2945-118">Invoking Operations on the SAP System by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="a2945-119">Réception d’opérations entrantes à partir du système SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2945-119">Receiving Inbound Operations from the SAP System by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md) 
  
-   [<span data-ttu-id="a2945-120">Diffusion en continu IDOC de fichier plat dans SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="a2945-120">Streaming Flat-File IDOCs in SAP using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)