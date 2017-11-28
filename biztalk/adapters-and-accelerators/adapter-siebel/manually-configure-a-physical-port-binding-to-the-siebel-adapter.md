---
title: "Configurer manuellement une liaison de port physique à l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- physical port binding, manually configuring
- how to, manually configure adapters for sending messages to a Siebel system
ms.assetid: a1445b8a-440f-45e8-96e9-a13142ca87c6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed94ca9f6a44919684d36a1be931cbb33f746377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-siebel-adapter"></a><span data-ttu-id="8accf-102">Configurer manuellement une liaison de port physique à l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="8accf-102">Manually configure a physical port binding to the Siebel adapter</span></span>
<span data-ttu-id="8accf-103">Cette section fournit des informations sur la configuration de la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] comme une liaison WCF personnalisée à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8accf-103">This section provides information about configuring the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] as a WCF custom binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8accf-104">Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir du système Siebel à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8accf-104">After deploying the adapter, you will be able to send and receive messages from the Siebel system by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="8accf-105">Les étapes de déploiement de l’adaptateur varient en fonction de la direction de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8accf-105">The steps for deploying the adapter vary depending on the direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="8accf-106">Vous pouvez choisir de configurer un envoi ou un port d’envoi / réception.</span><span class="sxs-lookup"><span data-stu-id="8accf-106">You may choose to configure a Send or a Send-Receive port.</span></span> <span data-ttu-id="8accf-107">Les choix que vous avez effectués sont résumés dans le tableau ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="8accf-107">Your choices are summarized in the following table:</span></span>  
  
|<span data-ttu-id="8accf-108">Direction du port</span><span class="sxs-lookup"><span data-stu-id="8accf-108">Port direction</span></span>|<span data-ttu-id="8accf-109">Modèle de communication</span><span class="sxs-lookup"><span data-stu-id="8accf-109">Communication pattern</span></span>|<span data-ttu-id="8accf-110">Direction de communication sélectionnables</span><span class="sxs-lookup"><span data-stu-id="8accf-110">Direction of communication to choose from</span></span>|  
|---|---|---|  
|<span data-ttu-id="8accf-111">Send</span><span class="sxs-lookup"><span data-stu-id="8accf-111">Send</span></span>|<span data-ttu-id="8accf-112">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="8accf-112">One-way</span></span>|<span data-ttu-id="8accf-113">Toujours envoyer les messages sur ce port.</span><span class="sxs-lookup"><span data-stu-id="8accf-113">I will always be sending messages on this port.</span></span>|  
|<span data-ttu-id="8accf-114">Envoi-Réception</span><span class="sxs-lookup"><span data-stu-id="8accf-114">Send-Receive</span></span>|<span data-ttu-id="8accf-115">Requête-réponse</span><span class="sxs-lookup"><span data-stu-id="8accf-115">Request-response</span></span>|<span data-ttu-id="8accf-116">J’ai sera envoyer une requête et recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="8accf-116">I will be sending a request and receiving a response.</span></span>|  
  
 <span data-ttu-id="8accf-117">Pour plus d’informations, consultez [création et configuration des Ports d’envoi](../../core/creating-and-configuring-send-ports.md).</span><span class="sxs-lookup"><span data-stu-id="8accf-117">For more information, see [Creating and Configuring Send Ports](../../core/creating-and-configuring-send-ports.md).</span></span>
  
> [!NOTE]
>  <span data-ttu-id="8accf-118">Recevoir des ports ne sont pas pris en charge, car le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’active pas les opérations entrantes à partir du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="8accf-118">Receive ports are not supported because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not enable inbound operations from the Siebel system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8accf-119">Vous pouvez également configurer les ports d’envoi WCF-Custom en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8accf-119">You can also configure the WCF-Custom send ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="8accf-120">Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="8accf-120">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).</span></span>
  
 
  
## <a name="see-also"></a><span data-ttu-id="8accf-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8accf-121">See Also</span></span>  
[<span data-ttu-id="8accf-122">Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="8accf-122">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)