---
title: "Nouveautés de l’adaptateur FileAct ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05ec8f1e-57f9-4e2d-ab8b-22b5c4b28055
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62b83fc723bbebce857eb442384b14179c1072ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-fileact-adapter"></a><span data-ttu-id="d8417-103">Nouveautés de l’adaptateur FileAct ?</span><span class="sxs-lookup"><span data-stu-id="d8417-103">What Is the FileAct Adapter?</span></span>
<span data-ttu-id="d8417-104">L’adaptateur FileAct pour SWIFTNet assure la connectivité entre BizTalk Server et de la société de télécommunication financières Interbank (SWIFT) dans le monde Secure IP réseau (SIPN) pour le transfert de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d8417-104">The FileAct adapter for SWIFTNet provides connectivity between BizTalk Server and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) Secure IP Network (SIPN) for the transfer of files.</span></span> <span data-ttu-id="d8417-105">Le SIPN transfère des messages et des fichiers sur un réseau privé sécurisé qui connecte les établissements financiers, les infrastructures financiers et les clients.</span><span class="sxs-lookup"><span data-stu-id="d8417-105">The SIPN transfers messages and files over a secure private network which connects financial institutions, financial industry infrastructures, and customers.</span></span> <span data-ttu-id="d8417-106">L’adaptateur FileAct utilise l’interface de programmation d’application (API) s pour se connecter à la SIPN SWIFTNet lien (SNL).</span><span class="sxs-lookup"><span data-stu-id="d8417-106">The FileAct adapter uses the SWIFTNet Link (SNL) application programming interface (API)s to connect to the SIPN.</span></span>  
  
 <span data-ttu-id="d8417-107">L’adaptateur FileAct fournit un mécanisme pour SWIFT aux participants de manière sécurisée et fiable échanger des fichiers et les informations relatives à ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="d8417-107">The FileAct adapter provides a mechanism for SWIFT participants to securely and reliably exchange files and information pertaining to those files.</span></span> <span data-ttu-id="d8417-108">Il prend en charge les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8417-108">It supports the following functionality:</span></span>  
  
-   <span data-ttu-id="d8417-109">Envoi de fichiers à un utilisateur SWIFTNet</span><span class="sxs-lookup"><span data-stu-id="d8417-109">Sending files to a SWIFTNet User</span></span>  
  
-   <span data-ttu-id="d8417-110">La récupération de fichiers à partir d’un utilisateur SWIFTNet</span><span class="sxs-lookup"><span data-stu-id="d8417-110">Retrieving files from a SWIFTNet User</span></span>  
  
-   <span data-ttu-id="d8417-111">Confirmer la réception du fichier par un récepteur de notification de remise</span><span class="sxs-lookup"><span data-stu-id="d8417-111">Delivery notification confirming file receipt by a receiver</span></span>  
  
-   <span data-ttu-id="d8417-112">Abandon des transferts en cours</span><span class="sxs-lookup"><span data-stu-id="d8417-112">Abort of transfers in progress</span></span>  
  
-   <span data-ttu-id="d8417-113">Analyse d’état du transfert de fichiers</span><span class="sxs-lookup"><span data-stu-id="d8417-113">File transfer state monitoring</span></span>  
  
-   <span data-ttu-id="d8417-114">Transferts de fichiers simultanés</span><span class="sxs-lookup"><span data-stu-id="d8417-114">Concurrent file transfers</span></span>  
  
-   <span data-ttu-id="d8417-115">Garantie de l’authenticité des données et l’intégrité</span><span class="sxs-lookup"><span data-stu-id="d8417-115">Assurance of data authenticity and integrity</span></span>  
  
-   <span data-ttu-id="d8417-116">Confidentialité des données de fichier en transit</span><span class="sxs-lookup"><span data-stu-id="d8417-116">Confidentiality of file data in transit</span></span>  
  
-   <span data-ttu-id="d8417-117">Non répudiation de transferts de fichiers</span><span class="sxs-lookup"><span data-stu-id="d8417-117">Non-repudiation of file transfers</span></span>  
  
-   <span data-ttu-id="d8417-118">Horodatage</span><span class="sxs-lookup"><span data-stu-id="d8417-118">Time-stamping</span></span>  
  
## <a name="the-fileact-service"></a><span data-ttu-id="d8417-119">Le Service de FileAct</span><span class="sxs-lookup"><span data-stu-id="d8417-119">The FileAct Service</span></span>  
 <span data-ttu-id="d8417-120">L’adaptateur FileAct pour SWIFTNet fournit un transfert fiable et sécurisé de fichiers, tels que les lots de messages financiers structurés ou des rapports volumineux.</span><span class="sxs-lookup"><span data-stu-id="d8417-120">The FileAct adapter for SWIFTNet provides secure and reliable transfer of files, such as batches of structured financial messages or large reports.</span></span> <span data-ttu-id="d8417-121">Les applications classiques incluent des virements répétitives, telles que retraite ou paiements de salaire, informations de courtage à valeur ajoutée et des rapports et reporting réglementaire.</span><span class="sxs-lookup"><span data-stu-id="d8417-121">Typical applications include repetitive credit transfers such as pension or salary payments, securities value-added information and reporting, and regulatory reporting.</span></span> <span data-ttu-id="d8417-122">SWIFTNet FileAct offre une variété de modes de messagerie :</span><span class="sxs-lookup"><span data-stu-id="d8417-122">SWIFTNet FileAct offers a variety of messaging modes:</span></span>  
  
-   <span data-ttu-id="d8417-123">**Transfert de fichiers de stockage et de transfert.**</span><span class="sxs-lookup"><span data-stu-id="d8417-123">**Store-and-forward file transfer.**</span></span> <span data-ttu-id="d8417-124">Capacité de stockage et transfert de SWIFTNet FileAct supprime l’incertitude et les problèmes de préoccuper ou non vos correspondants sont en ligne au moment de que vous transmettez le fichier.</span><span class="sxs-lookup"><span data-stu-id="d8417-124">SWIFTNet FileAct’s store-and-forward capability removes the uncertainty and inconvenience of worrying about whether or not your correspondents are online at the time you transmit the file.</span></span> <span data-ttu-id="d8417-125">Le fichier est remis dès que le destinataire est prêt à le recevoir.</span><span class="sxs-lookup"><span data-stu-id="d8417-125">The file is delivered as soon as the recipient is ready to receive it.</span></span> <span data-ttu-id="d8417-126">Par conséquent, il fournit un moyen idéal pour envoyer des fichiers à un grand nombre de correspondants, dont certaines peuvent être dans des fuseaux horaires différents.</span><span class="sxs-lookup"><span data-stu-id="d8417-126">As a result, it provides an ideal way to send files to large numbers of correspondents, some of which may be in different time zones.</span></span>  
  
-   <span data-ttu-id="d8417-127">**Transfert de fichiers en temps réel.**</span><span class="sxs-lookup"><span data-stu-id="d8417-127">**Real-time file transfer.**</span></span> <span data-ttu-id="d8417-128">Messagerie en temps réel offre une solution économique pour stocker et transférer des fichiers qui sont destinés à correspondants qui sont en ligne au moment de la transmission.</span><span class="sxs-lookup"><span data-stu-id="d8417-128">Real-time messaging offers a lower-cost alternative to store and forward for files that are destined for correspondents that are online at the time of transmission.</span></span> <span data-ttu-id="d8417-129">Par conséquent, il est idéal pour l’envoi de fichiers à quelques correspondants volumineux ou des infrastructures de marché.</span><span class="sxs-lookup"><span data-stu-id="d8417-129">As a result it is ideal for sending files to a few large correspondents or market infrastructures.</span></span>  
  
-   <span data-ttu-id="d8417-130">**Récupération de fichiers en temps réel.**</span><span class="sxs-lookup"><span data-stu-id="d8417-130">**Real-time file retrieval.**</span></span> <span data-ttu-id="d8417-131">Il s’agit d’un service interactif généralement utilisé pour récupérer des fichiers dans le contexte de systèmes basés sur une station de travail et souvent conjointement avec SWIFTNet Parcourir.</span><span class="sxs-lookup"><span data-stu-id="d8417-131">This is an interactive service typically used to retrieve files in the context of workstation-based systems and often in conjunction with SWIFTNet Browse.</span></span> <span data-ttu-id="d8417-132">Nous prendrons en charge ce mode.</span><span class="sxs-lookup"><span data-stu-id="d8417-132">We will support this mode.</span></span>  
  
 <span data-ttu-id="d8417-133">Les fonctionnalités facultatives de SWIFTNet FileAct (sur une base par fichier) sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8417-133">The optional SWIFTNet FileAct features (on a file by file basis) include:</span></span>  
  
-   <span data-ttu-id="d8417-134">**Priorité du message.**</span><span class="sxs-lookup"><span data-stu-id="d8417-134">**Message priority.**</span></span> <span data-ttu-id="d8417-135">Transferts de fichiers peuvent être marquées comme « Urgente » dans le message afin de permettre approprié de traitement par vos correspondants.</span><span class="sxs-lookup"><span data-stu-id="d8417-135">File transfers can be flagged as “Urgent” in the message, to allow for appropriate processing by your correspondents.</span></span>  
  
-   <span data-ttu-id="d8417-136">**Accusé de réception (modes de stockage et transmission et en temps réel).**</span><span class="sxs-lookup"><span data-stu-id="d8417-136">**Delivery notification (real-time and store-and-forward modes).**</span></span> <span data-ttu-id="d8417-137">Fournit la confirmation que votre correspondant votre fichier.</span><span class="sxs-lookup"><span data-stu-id="d8417-137">Provides confirmation that your correspondent received your file.</span></span>  
  
-   <span data-ttu-id="d8417-138">**Non-répudiation de réception et d’émission.**</span><span class="sxs-lookup"><span data-stu-id="d8417-138">**Non-repudiation of emission and reception.**</span></span> <span data-ttu-id="d8417-139">En cas de litige, permet de SWIFT confirmer que le transfert de fichiers n’a eu lieu comme demandé.</span><span class="sxs-lookup"><span data-stu-id="d8417-139">In case of dispute, allows SWIFT to confirm that the file transfer did take place as claimed.</span></span>  
  
 <span data-ttu-id="d8417-140">Les fonctionnalités de SWIFTNet FileAct standards incluent la sécurité de SWIFTNet PKI**.**</span><span class="sxs-lookup"><span data-stu-id="d8417-140">The standard SWIFTNet FileAct features include SWIFTNet PKI security**.**</span></span> <span data-ttu-id="d8417-141">SWIFTNet FileAct est sécurisé avec SWIFTNet PKI et offre l’authentification des messages et contrôle d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="d8417-141">SWIFTNet FileAct is secured with SWIFTNet PKI and offers message authentication and integrity control.</span></span>  
  
 <span data-ttu-id="d8417-142">Tous les messages et les fichiers échangés sur SWIFTNet subissent un ensemble commun de contrôles pour s’assurer qu’aucun utilisateur ne peut contourner la sécurité, de validation et de règles de routage de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="d8417-142">All messages and files exchanged on SWIFTNet undergo a common set of checks to ensure that no user can bypass the security, validation and routing rules of the platform.</span></span> <span data-ttu-id="d8417-143">Ces vérifications sont effectuées par l’application de la passerelle SWIFTAlliance (trous).</span><span class="sxs-lookup"><span data-stu-id="d8417-143">These checks are performed by the SWIFTAlliance Gateway (SAG) application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8417-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8417-144">See Also</span></span>  
 <span data-ttu-id="d8417-145">[Mise en route avec l’Adaptateurs FileAct et interagir de cartes](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="d8417-145">[Getting Started with the FileAct and InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span></span>  
 <span data-ttu-id="d8417-146">[Qu’est SWIFTNet ?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span><span class="sxs-lookup"><span data-stu-id="d8417-146">[What Is SWIFTNet?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span></span>  
 [<span data-ttu-id="d8417-147">Quelle est l’interagir adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="d8417-147">What Is the InterAct Adapter?</span></span>](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)