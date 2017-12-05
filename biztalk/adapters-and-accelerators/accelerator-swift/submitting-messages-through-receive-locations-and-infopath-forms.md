---
title: "Envoi de Messages via emplacements de réception et des formulaires InfoPath | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, receive locations
- receive locations, messages
- messages, InfoPath forms
- InfoPath forms, messages
ms.assetid: e8676830-3fbc-423f-82f6-03e6a532075f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4589649be79ce369f0e6756ae7f96615d4a36c0f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="submitting-messages-through-receive-locations-and-infopath-forms"></a><span data-ttu-id="36bd1-102">Envoi de Messages via emplacements de réception et des formulaires InfoPath</span><span class="sxs-lookup"><span data-stu-id="36bd1-102">Submitting Messages Through Receive Locations and InfoPath Forms</span></span>
<span data-ttu-id="36bd1-103">Recevoir des emplacements de recevoir des messages à envoyer dans [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] applications.</span><span class="sxs-lookup"><span data-stu-id="36bd1-103">Receive locations receive messages for submission into [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] applications.</span></span> <span data-ttu-id="36bd1-104">Vous pouvez définir des emplacements de réception en tant que points de terminaison physiques configurés pour recevoir des messages à l’aide d’un protocole de transport spécifié.</span><span class="sxs-lookup"><span data-stu-id="36bd1-104">You can define receive locations as physical endpoints configured to receive messages using a specified transport protocol.</span></span> <span data-ttu-id="36bd1-105">Par exemple, un emplacement de réception peut être configuré pour des fichiers de réception déplacées vers un dossier de système de fichier particulier en utilisant le transport de fichier.</span><span class="sxs-lookup"><span data-stu-id="36bd1-105">For example, a receive location may be configured to receive files dropped to a particular file system folder using the FILE transport.</span></span>  
  
 <span data-ttu-id="36bd1-106">Vous créez des emplacements de réception pour les ports de réception qui logiquement regroupement et gérer les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="36bd1-106">You create receive locations for receive ports that logically group and manage receive locations.</span></span> <span data-ttu-id="36bd1-107">Pour chaque emplacement de réception, vous spécifiez un pipeline de réception, qui effectue le traitement (le décodage, le code machine, validation et ainsi de suite) des messages reçus à cet emplacement de réception particulier.</span><span class="sxs-lookup"><span data-stu-id="36bd1-107">For each receive location you specify a receive pipeline, which does the actual processing (decoding, disassembly, validation, and so on) of messages received at that particular receive location.</span></span> <span data-ttu-id="36bd1-108">Emplacements de réception de réception A4SWIFT lie les ports qui logiquement regroupement et gérer les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="36bd1-108">A4SWIFT binds receive locations to receive ports that logically group and manage receive locations.</span></span>  
  
 <span data-ttu-id="36bd1-109">Pour envoyer un message SWIFT dans une application A4SWIFT via un emplacement de réception, le message doit supprimé à un emplacement de réception configuré, traité par un pipeline de réception à l’aide du désassembleur SWIFT, analyser et de valider par le désassembleur SWIFT, et publié dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="36bd1-109">To submit a SWIFT message into an A4SWIFT application through a receive location, the message must be dropped to a configured receive location, processed by a receive pipeline using the SWIFT disassembler, parsed and validated by the SWIFT disassembler, and published to the MessageBox database.</span></span> <span data-ttu-id="36bd1-110">Une fois que les messages sont publiés dans la base de données MessageBox, autres composants de votre application A4SWIFT de récupérer les messages (à l’aide d’abonnements) pour un traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="36bd1-110">After messages are published to the MessageBox database, other components in your A4SWIFT application retrieve the messages (using subscriptions) for additional processing.</span></span> <span data-ttu-id="36bd1-111">Par exemple, vous pouvez utiliser des ports d’envoi pour le routage finale.</span><span class="sxs-lookup"><span data-stu-id="36bd1-111">For example, you can use send ports for final routing.</span></span>  
  
 <span data-ttu-id="36bd1-112">Pour plus d’informations sur la création et configuration des ports de réception et emplacements de réception, consultez l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="36bd1-112">For more information about creating and configuring receive ports and receive locations, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="36bd1-113">Vous pouvez également envoyer un message via un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran, à l’aide de la fonctionnalité de Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="36bd1-113">You can also submit a new message through an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, using the Message Repair and New Submission feature.</span></span> <span data-ttu-id="36bd1-114">Pour ce faire, vous ouvrez le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour ce message à partir d’un dossier sur le site MRSR.</span><span class="sxs-lookup"><span data-stu-id="36bd1-114">To do so, you open the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for that message from a folder in the MRSR site.</span></span> <span data-ttu-id="36bd1-115">Vous fournissez les données dans le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forment, se connecter à l’aide de votre certificat, puis l’envoyer.</span><span class="sxs-lookup"><span data-stu-id="36bd1-115">You fill in the data in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, sign it using your certificate, and then submit it.</span></span> <span data-ttu-id="36bd1-116">L’orchestration Message Repair et New Submission traite le message.</span><span class="sxs-lookup"><span data-stu-id="36bd1-116">The Message Repair and New Submission orchestration processes the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bd1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36bd1-117">See Also</span></span>  
 [<span data-ttu-id="36bd1-118">Exécution de BizTalk Accelerator pour SWIFT</span><span class="sxs-lookup"><span data-stu-id="36bd1-118">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)