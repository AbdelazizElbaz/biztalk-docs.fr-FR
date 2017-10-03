---
title: "Configurer manuellement une liaison de port physique à l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, sending messages to the SAP system
- physical port binding, manually configuring
- deploying, receiving messages from the SAP system
ms.assetid: c4f547aa-5514-4ca9-809b-d8d395de419c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 725a26eed4502e0a3d1eca8ed5f1429988590614
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-sap-adapter"></a><span data-ttu-id="ca5fa-102">Configurer manuellement une liaison de port physique à l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="ca5fa-102">Manually configure a physical port binding to the SAP adapter</span></span>
<span data-ttu-id="ca5fa-103">Configurer le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] comme une liaison WCF personnalisée à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-103">Configure the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as a WCF custom binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> 

## <a name="port-overview"></a><span data-ttu-id="ca5fa-104">Vue d’ensemble du port</span><span class="sxs-lookup"><span data-stu-id="ca5fa-104">Port overview</span></span>
<span data-ttu-id="ca5fa-105">Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir du système SAP à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-105">After deploying the adapter, you will be able to send and receive messages from the SAP system by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ca5fa-106">Les étapes de déploiement de l’adaptateur varient en fonction de :</span><span class="sxs-lookup"><span data-stu-id="ca5fa-106">The steps for deploying the adapter vary depending on:</span></span>  
  
-   <span data-ttu-id="ca5fa-107">La direction de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca5fa-107">The direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="ca5fa-108">Vous pouvez choisir de configurer un envoi, réception, envoi-réception ou un port d’envoi à la réception.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-108">You may choose to configure a Send, Receive, Send-Receive, or a Receive-Send port.</span></span> <span data-ttu-id="ca5fa-109">Les choix que vous avez effectués sont résumés dans le tableau ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ca5fa-109">Your choices are summarized in the following table:</span></span>  
  
    |<span data-ttu-id="ca5fa-110">Direction du port</span><span class="sxs-lookup"><span data-stu-id="ca5fa-110">Port direction</span></span>|<span data-ttu-id="ca5fa-111">Modèle de communication</span><span class="sxs-lookup"><span data-stu-id="ca5fa-111">Communication pattern</span></span>|<span data-ttu-id="ca5fa-112">Direction de communication sélectionnables</span><span class="sxs-lookup"><span data-stu-id="ca5fa-112">Direction of communication to choose from</span></span>|  
    |---|---|---|  
    |<span data-ttu-id="ca5fa-113">Send</span><span class="sxs-lookup"><span data-stu-id="ca5fa-113">Send</span></span>|<span data-ttu-id="ca5fa-114">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="ca5fa-114">One-way</span></span>|<span data-ttu-id="ca5fa-115">Toujours envoyer les messages sur ce port.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-115">I will always be sending messages on this port.</span></span>|  
    |<span data-ttu-id="ca5fa-116">Recevoir</span><span class="sxs-lookup"><span data-stu-id="ca5fa-116">Receive</span></span>|<span data-ttu-id="ca5fa-117">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="ca5fa-117">One-way</span></span>|<span data-ttu-id="ca5fa-118">Toujours recevoir les messages sur ce port.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-118">I will always be receiving messages on this port.</span></span>|  
    |<span data-ttu-id="ca5fa-119">Envoi-Réception</span><span class="sxs-lookup"><span data-stu-id="ca5fa-119">Send-Receive</span></span>|<span data-ttu-id="ca5fa-120">Requête-réponse</span><span class="sxs-lookup"><span data-stu-id="ca5fa-120">Request-response</span></span>|<span data-ttu-id="ca5fa-121">J’ai sera envoyer une requête et recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-121">I will be sending a request and receiving a response.</span></span>|  
    |<span data-ttu-id="ca5fa-122">Réception-envoi</span><span class="sxs-lookup"><span data-stu-id="ca5fa-122">Receive-Send</span></span>|<span data-ttu-id="ca5fa-123">Sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="ca5fa-123">Solicit-response</span></span>|<span data-ttu-id="ca5fa-124">Recevoir une requête et envoyer une réponse.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-124">I will be receiving a request and sending a response.</span></span>|  
  
     <span data-ttu-id="ca5fa-125">Pour plus d’informations, consultez [créer un Port d’envoi](../../core/how-to-create-a-send-port2.md), ou [créer un Port de réception](../../core/how-to-create-a-receive-port.md).</span><span class="sxs-lookup"><span data-stu-id="ca5fa-125">For more information, see [Create a Send Port](../../core/how-to-create-a-send-port2.md), or [Create a Receive Port](../../core/how-to-create-a-receive-port.md).</span></span>
  
-   <span data-ttu-id="ca5fa-126">Indique si l’adaptateur envoie des messages au système SAP ou reçoit des messages à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-126">Whether the adapter sends messages to the SAP system or receives messages from the SAP system.</span></span> <span data-ttu-id="ca5fa-127">Selon que vous souhaitez envoyer ou recevoir des messages, vous créez un envoi ou port de réception.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-127">Depending on whether you want to send or receive messages, you will create a send or receive port.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca5fa-128">Vous pouvez également configurer l’envoi ou les ports de réception en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ca5fa-128">You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="ca5fa-129">Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).</span><span class="sxs-lookup"><span data-stu-id="ca5fa-129">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="ca5fa-130">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="ca5fa-130">In this section</span></span>  
  
-   [<span data-ttu-id="ca5fa-131">Configurer un port à l’aide de l’adaptateur de base de données Oracle et un adaptateur WCF-custom</span><span class="sxs-lookup"><span data-stu-id="ca5fa-131">Configure a port using the WCF-custom adapter and Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter.md)  
  
-   [<span data-ttu-id="ca5fa-132">Configurer un port à l’aide de l’adaptateur WCF-SAP</span><span class="sxs-lookup"><span data-stu-id="ca5fa-132">Configure a port using the WCF-SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/configure-a-port-using-the-wcf-sap-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="ca5fa-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca5fa-133">See Also</span></span>  
[<span data-ttu-id="ca5fa-134">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="ca5fa-134">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)