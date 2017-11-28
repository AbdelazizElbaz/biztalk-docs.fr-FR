---
title: "Configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, sending to an Oracle database
- messages, receiving from an Oracle database
- physical port binding, manually configuring
ms.assetid: 6b118236-e9eb-494e-96b2-969c7064943d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2a64223485cf83fb214055cb1e11b44fb6bc7c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-database-adapter"></a><span data-ttu-id="df012-102">Configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="df012-102">Manually configure a physical port binding to the Oracle Database Adapter</span></span>
<span data-ttu-id="df012-103">Cette section fournit des informations sur la configuration de la [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] en tant que liaison de WCF-Custom ou liaison WCF-OracleDB à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="df012-103">This section provides information about configuring the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] as a WCF-Custom binding or WCF-OracleDB binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="df012-104">Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir de la base de données Oracle à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="df012-104">After deploying the adapter, you will be able to send and receive messages from the Oracle database by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="df012-105">Les étapes de déploiement de l’adaptateur varient en fonction de :</span><span class="sxs-lookup"><span data-stu-id="df012-105">The steps for deploying the adapter vary depending on:</span></span>  
  
-   <span data-ttu-id="df012-106">La direction de communication entre BizTalk Server et [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df012-106">The direction of communication between BizTalk Server and [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="df012-107">Vous pouvez choisir de configurer un envoi, réception, envoi-réception ou un port d’envoi à la réception.</span><span class="sxs-lookup"><span data-stu-id="df012-107">You may choose to configure a send, receive, send-receive, or a receive-send port.</span></span> <span data-ttu-id="df012-108">Les choix disponibles sont résumées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="df012-108">Your choices are summarized in the following table.</span></span>  
  
    |<span data-ttu-id="df012-109">Direction du port</span><span class="sxs-lookup"><span data-stu-id="df012-109">Port direction</span></span>|<span data-ttu-id="df012-110">Modèle de communication</span><span class="sxs-lookup"><span data-stu-id="df012-110">Communication pattern</span></span>|<span data-ttu-id="df012-111">Direction de communication sélectionnables</span><span class="sxs-lookup"><span data-stu-id="df012-111">Direction of communication to choose from</span></span>|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |<span data-ttu-id="df012-112">Send</span><span class="sxs-lookup"><span data-stu-id="df012-112">Send</span></span>|<span data-ttu-id="df012-113">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="df012-113">One-way</span></span>|<span data-ttu-id="df012-114">Toujours envoyer les messages sur ce port.</span><span class="sxs-lookup"><span data-stu-id="df012-114">I will always be sending messages on this port.</span></span>|  
    |<span data-ttu-id="df012-115">Recevoir</span><span class="sxs-lookup"><span data-stu-id="df012-115">Receive</span></span>|<span data-ttu-id="df012-116">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="df012-116">One-way</span></span>|<span data-ttu-id="df012-117">Toujours recevoir les messages sur ce port.</span><span class="sxs-lookup"><span data-stu-id="df012-117">I will always be receiving messages on this port.</span></span>|  
    |<span data-ttu-id="df012-118">Envoi / réception</span><span class="sxs-lookup"><span data-stu-id="df012-118">Send-receive</span></span>|<span data-ttu-id="df012-119">Requête-réponse</span><span class="sxs-lookup"><span data-stu-id="df012-119">Request-response</span></span>|<span data-ttu-id="df012-120">J’ai sera envoyer une requête et recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="df012-120">I will be sending a request and receiving a response.</span></span>|  
    |<span data-ttu-id="df012-121">Envoi de réception</span><span class="sxs-lookup"><span data-stu-id="df012-121">Receive-send</span></span>|<span data-ttu-id="df012-122">Sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="df012-122">Solicit-response</span></span>|<span data-ttu-id="df012-123">Recevoir une requête et envoyer une réponse.</span><span class="sxs-lookup"><span data-stu-id="df012-123">I will be receiving a request and sending a response.</span></span>|  
  
     <span data-ttu-id="df012-124">Pour plus d’informations, consultez [créer un Port d’envoi](../../core/how-to-create-a-send-port2.md), ou [créer un Port de réception](../../core/how-to-create-a-receive-port.md).</span><span class="sxs-lookup"><span data-stu-id="df012-124">For more information, see [Create a Send Port](../../core/how-to-create-a-send-port2.md), or [Create a Receive Port](../../core/how-to-create-a-receive-port.md).</span></span> 
  
-   <span data-ttu-id="df012-125">Indique si l’adaptateur envoie des messages à la base de données Oracle ou reçoit des messages à partir de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="df012-125">Whether the adapter sends messages to the Oracle database or receives messages from the Oracle database.</span></span> <span data-ttu-id="df012-126">Selon que vous souhaitez envoyer ou recevoir des messages, vous créez un envoi ou port de réception, respectivement.</span><span class="sxs-lookup"><span data-stu-id="df012-126">Depending on whether you want to send or receive messages, you will create a send or receive port, respectively.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df012-127">Vous pouvez également configurer l’envoi ou les ports de réception en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="df012-127">You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="df012-128">Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="df012-128">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="df012-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df012-129">See Also</span></span>  
[<span data-ttu-id="df012-130">Développer vos applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="df012-130">Develop your BizTalk applications</span></span>](../../core/develop-your-biztalk-applications.md)