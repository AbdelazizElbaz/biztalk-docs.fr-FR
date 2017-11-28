---
title: "Dépannage des erreurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, troubleshooting
- troubleshooting, errors
ms.assetid: 08cc95a3-4be9-450f-a015-e031011158f7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae7ad99b699da29d4d8680375f88e4d4a74ff66a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-errors"></a><span data-ttu-id="e8b4b-102">Résolution des erreurs</span><span class="sxs-lookup"><span data-stu-id="e8b4b-102">Troubleshooting Errors</span></span>
<span data-ttu-id="e8b4b-103">Cette section traite des problèmes liés à [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] a généré des erreurs.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-103">This section addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generated errors.</span></span>  
  
## <a name="the-mllp-adapter-can-run-only-on-a-single-host-instance"></a><span data-ttu-id="e8b4b-104">L’adaptateur MLLP être exécuté uniquement sur une seule instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="e8b4b-104">The MLLP adapter can run only on a single host instance</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="e8b4b-105">Symptôme</span><span class="sxs-lookup"><span data-stu-id="e8b4b-105">Symptom</span></span>  
 <span data-ttu-id="e8b4b-106">Vous ne pouvez pas activer un emplacement de réception avec un type de transport de MLLP et un gestionnaire de réception différent à un autre emplacement de réception existant.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-106">You cannot enable a receive location with a transport type of MLLP and a different receive handler than another existing receive location.</span></span> <span data-ttu-id="e8b4b-107">En outre, vous ne peut pas inscrire et démarrer un port d’envoi avec un gestionnaire d’envoi différent que le port d’envoi existant un autre.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-107">In addition, you cannot enlist and start a send port with a different send handler than another existing send port.</span></span>  
  
<span data-ttu-id="e8b4b-108">**Cause possible** : vous ne pouvez utiliser un MLLP réception (ou envoi) Gestionnaire sur un seul serveur.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-108">**Possible Cause** : You can only use one MLLP receive (or send) handler on a single server.</span></span> <span data-ttu-id="e8b4b-109">En outre, l’URI est désigné pour l’emplacement de réception (ou le port d’envoi) (le nom d’hôte dans les propriétés de Transport MLLP) doit être « localhost » ou le nom du serveur sur lequel l’ordinateur hôte de l’instance pour le Gestionnaire d’adaptateur de réception (ou d’envoi) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-109">In addition, the URI designated for the receive location (or send port) (the Host name in the MLLP Transport Properties) must either be "localhost" or the server name where the host instance for the receive (or send) adapter handler is running.</span></span>  
  
<span data-ttu-id="e8b4b-110">**Résolution** : désigne le même gestionnaire de réception (ou envoi) pour MLLP tous les emplacements de réception (ou ports d’envoi) sur un serveur unique.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-110">**Resolution** : Designate the same receive (or send) handler for all MLLP receive locations (or send ports) on a single server.</span></span>  
  
## <a name="msh-and-ack-schemas-must-be-added-to-only-one-project"></a><span data-ttu-id="e8b4b-111">Schémas MSH et l’accusé de réception doivent être ajoutés à un seul projet</span><span class="sxs-lookup"><span data-stu-id="e8b4b-111">MSH and ACK schemas must be added to only one project</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="e8b4b-112">Symptôme</span><span class="sxs-lookup"><span data-stu-id="e8b4b-112">Symptom</span></span>  
 <span data-ttu-id="e8b4b-113">Lorsque vous essayez de générer un projet, vous obtenez une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8b4b-113">When you attempt to build a project, you get one of the following errors:</span></span>  
  
`Error: Cannot locate document specification as multiple schemas match the message type "http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF"`
  
`Schema http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF not found`
  
<span data-ttu-id="e8b4b-114">**Cause possible** : schémas MSH l’et l’accusé de réception (MSH_25_GLO_DEF.xsd et ACK_24_GLO_DEF.xsd) ont été déployés dans plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-114">**Possible Cause** : The MSH and ACK schemas (MSH_25_GLO_DEF.xsd and ACK_24_GLO_DEF.xsd) have been deployed in multiple projects.</span></span>  
  
<span data-ttu-id="e8b4b-115">**Résolution** : Vérifiez que MSH_25_GLO_DEF.xsd et ACK_24_GLO_DEF.xsd ont été ajoutées à un seul projet.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-115">**Resolution** : Ensure that MSH_25_GLO_DEF.xsd and ACK_24_GLO_DEF.xsd have been added to only one project.</span></span>  
  
## <a name="exception-of-type-systemoutofmemoryexception-has-thrown-an-error-in-the-event-log"></a><span data-ttu-id="e8b4b-116">Exception de type System.OutOfMemoryException a levé une erreur dans le journal des événements</span><span class="sxs-lookup"><span data-stu-id="e8b4b-116">Exception of type System.OutOfMemoryException has thrown an error in the Event Log</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="e8b4b-117">Symptôme</span><span class="sxs-lookup"><span data-stu-id="e8b4b-117">Symptom</span></span>  
 <span data-ttu-id="e8b4b-118">Vous obtenez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="e8b4b-118">You get the following or similar error in the Event Log:</span></span>  
  
`Exception of type System.OutOfMemoryException has thrown an error.`
  
<span data-ttu-id="e8b4b-119">**Cause possible** : lors du traitement d’un grand nombre de messages, certaines [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] composants de moteur peuvent présenter des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-119">**Possible Cause** : While processing a large number of messages, some [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] engine components may exhibit memory leaks.</span></span>  
  
<span data-ttu-id="e8b4b-120">**Résolution** : redémarrer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8b4b-120">**Resolution** : Restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="header-serialization-generates-an-error-in-the-event-viewer"></a><span data-ttu-id="e8b4b-121">Sérialisation de l’en-tête génère une erreur dans l’Observateur d’événements</span><span class="sxs-lookup"><span data-stu-id="e8b4b-121">Header serialization generates an error in the Event Viewer</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="e8b4b-122">Symptôme</span><span class="sxs-lookup"><span data-stu-id="e8b4b-122">Symptom</span></span>  
 <span data-ttu-id="e8b4b-123">Vous obtenez l’erreur suivante ou similaire dans le journal des événements, même si le message dans l’outil de contrôle d’intégrité et l’activité de suivi du fonctionnement (HAT) indique la réussite :</span><span class="sxs-lookup"><span data-stu-id="e8b4b-123">You get the following or similar error in the Event Log, even though the message in the Health and Activity Tracking (HAT) tool indicates success:</span></span>  
  
`An error happened in the header during serialization.`
  
<span data-ttu-id="e8b4b-124">**Cause possible** : la valeur de transformation d’en-tête de message n’est pas définie correctement [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-124">**Possible Cause** : The message header transformation value is not set correctly in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
<span data-ttu-id="e8b4b-125">**Résolution** : mappage de MSH de vérifier les valeurs dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-125">**Resolution** : Verify MSH map values in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="duplicate-event-id-4133-serializer-errors-are-logged"></a><span data-ttu-id="e8b4b-126">Les erreurs de sérialiseur événement ID 4133 en double sont enregistrées</span><span class="sxs-lookup"><span data-stu-id="e8b4b-126">Duplicate Event ID 4133 serializer errors are logged</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="e8b4b-127">Symptôme</span><span class="sxs-lookup"><span data-stu-id="e8b4b-127">Symptom</span></span>  
 <span data-ttu-id="e8b4b-128">ID d’événement 4133 : « Erreur s’est produite dans l’en-tête pendant la sérialisation » se produit deux fois pour chaque instance d’un message avec une valeur MSH11 qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-128">Event ID 4133 – "Error happened in header during serialization" occurs twice for every instance of a message with a MSH11 value that is not valid.</span></span>  
  
<span data-ttu-id="e8b4b-129">**Cause possible** : une erreur s’est produite lors du traitement de deux accusés de réception (validation et les accusés de réception Application) sans erreurs en double dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-129">**Possible Cause** : An error occurred while processing two acknowledgments (Commit and Application ACKs) without duplicate errors in the Event Log.</span></span> <span data-ttu-id="e8b4b-130">Au lieu de cela, vous recevez un 4133 d’ID d’événement pour chacun des deux accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-130">Instead, you receive one Event ID 4133 for each of the two ACKs.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="e8b4b-131">Crée une entrée de journal pour chaque accusé de réception qu’il génère.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-131"> creates a log entry for each ACK it generates.</span></span>  
  
<span data-ttu-id="e8b4b-132">**Résolution** : Assurez-vous que vos messages ont un champ MSH11 correctement mis en forme et rempli.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-132">**Resolution** : Ensure that your messages have a correctly formatted and populated MSH11 field.</span></span>  
  
## <a name="send-pipeline-generates-an-error-when-using-the-2-way-mllp-adapter"></a><span data-ttu-id="e8b4b-133">Envoyer le pipeline génère une erreur lors de l’utilisation de l’adaptateur MLLP à 2 facteurs</span><span class="sxs-lookup"><span data-stu-id="e8b4b-133">Send pipeline generates an error when using the 2-way MLLP adapter</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="e8b4b-134">Symptôme</span><span class="sxs-lookup"><span data-stu-id="e8b4b-134">Symptom</span></span>  
 <span data-ttu-id="e8b4b-135">Vous obtenez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="e8b4b-135">You get the following or similar error in the Event Log:</span></span>  
  
`There was a failure executing the send pipeline: "[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XPipelines.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XSendPipeline" Source: "[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm" Send Port: "<*host name: port number*>" Reason: Message does not contain a part with name MSHSegment.`
  
<span data-ttu-id="e8b4b-136">**Cause possible** : l’application réceptrice ne répond pas avec un accusé de réception et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] attend une réponse de l’application de réception.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-136">**Possible Cause** : The receiving application does not respond with an Acknowledgment and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is expecting a response from the receiving application.</span></span>  
  
<span data-ttu-id="e8b4b-137">**Résolution** : il s’agit par conception, et vous pouvez ignorer le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e8b4b-137">**Resolution** : This is by design, and you can ignore the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b4b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8b4b-138">See Also</span></span>  
 [<span data-ttu-id="e8b4b-139">Problèmes connus et dépannage dans HL7</span><span class="sxs-lookup"><span data-stu-id="e8b4b-139">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)