---
title: "POP3 L’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- POP3 adapters, about POP3 adapters
- authenticating, POP3 adapters
- POP3 adapters
- POP3 adapters, receive adapters
- POP3 adapters, authenticating
- receive adapters, POP3 adapters
ms.assetid: 008f7fa7-60c3-4ea3-b90d-821e4029a04c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbe21a3cf0e611a690cf22c88b1344926fa72744
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter"></a><span data-ttu-id="99550-102">Adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="99550-102">POP3 Adapter</span></span>
<span data-ttu-id="99550-103">Vous utilisez l'adaptateur POP3 (Post Office Protocol 3) pour extraire les données d'un serveur sur lequel résident des boîtes aux lettres POP3 vers un serveur exécutant Microsoft BizTalk Server via le protocole POP3.</span><span class="sxs-lookup"><span data-stu-id="99550-103">You use the Post Office Protocol 3 (POP3) adapter to retrieve data from a server that houses POP3 mailboxes into a server running Microsoft BizTalk Server by means of the POP3 protocol.</span></span>  
  
 <span data-ttu-id="99550-104">L'adaptateur POP3 est constitué d'un seul adaptateur de réception.</span><span class="sxs-lookup"><span data-stu-id="99550-104">The POP3 adapter consists of only one adapter, a receive adapter.</span></span> <span data-ttu-id="99550-105">Ce dernier contrôle les emplacements de réception qui utilisent l'adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="99550-105">The receive adapter controls the receive locations that use the POP3 adapter.</span></span>  
  
 <span data-ttu-id="99550-106">Cette rubrique traite du flux de travail de l'adaptateur de réception POP3.</span><span class="sxs-lookup"><span data-stu-id="99550-106">This topic discusses the workflow of the POP3 receive adapter.</span></span>  
  
 <span data-ttu-id="99550-107">**POP3 Adaptateur de réception**</span><span class="sxs-lookup"><span data-stu-id="99550-107">**POP3 Receive Adapter**</span></span>  
  
 <span data-ttu-id="99550-108">L'adaptateur de réception POP3 extrait les messages électroniques d'une boîte aux lettres spécifiée située sur un serveur POP3 donné.</span><span class="sxs-lookup"><span data-stu-id="99550-108">The POP3 receive adapter retrieves e-mail from a specified mailbox on a specified POP3 server.</span></span> <span data-ttu-id="99550-109">Par défaut, il applique un traitement MIME aux messages électroniques téléchargés et soumet ces derniers à BizTalk Server en tant que messages BizTalk à parties multiples.</span><span class="sxs-lookup"><span data-stu-id="99550-109">By default, the POP3 receive adapter applies MIME processing to the e-mail messages that it downloads and submits these messages to BizTalk Server as multipart BizTalk messages.</span></span> <span data-ttu-id="99550-110">Il peut recevoir et traiter des messages électroniques dans les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="99550-110">The POP3 receive adapter can receive and process e-mail in the following formats:</span></span>  
  
-   <span data-ttu-id="99550-111">Texte brut</span><span class="sxs-lookup"><span data-stu-id="99550-111">Plain text</span></span>  
  
-   <span data-ttu-id="99550-112">MIME codé</span><span class="sxs-lookup"><span data-stu-id="99550-112">MIME encoded</span></span>  
  
-   <span data-ttu-id="99550-113">MIME chiffré</span><span class="sxs-lookup"><span data-stu-id="99550-113">MIME encrypted</span></span>  
  
-   <span data-ttu-id="99550-114">MIME codé et signé</span><span class="sxs-lookup"><span data-stu-id="99550-114">MIME encoded and signed</span></span>  
  
-   <span data-ttu-id="99550-115">MIME chiffré et signé</span><span class="sxs-lookup"><span data-stu-id="99550-115">MIME encrypted and signed</span></span>  
  
 <span data-ttu-id="99550-116">**Prise en charge de traitement par lot pour l’adaptateur de réception POP3**</span><span class="sxs-lookup"><span data-stu-id="99550-116">**Batching Support for the POP3 Receive Adapter**</span></span>  
  
 <span data-ttu-id="99550-117">L'adaptateur de réception POP3 ne prend pas en charge le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="99550-117">The POP3 receive adapter does not support batching.</span></span>  
  
 <span data-ttu-id="99550-118">**Authentification avec le serveur POP3**</span><span class="sxs-lookup"><span data-stu-id="99550-118">**Authentication with POP3 Server**</span></span>  
  
 <span data-ttu-id="99550-119">Les méthodes d'authentification suivantes sont prises en charge par l'adaptateur POP3 :</span><span class="sxs-lookup"><span data-stu-id="99550-119">The following authentication methods are supported for use with the POP3 adapter:</span></span>  
  
-   <span data-ttu-id="99550-120">**De base.**</span><span class="sxs-lookup"><span data-stu-id="99550-120">**Basic.**</span></span> <span data-ttu-id="99550-121">Le serveur POP3 utilise les informations d'identification fournies par l'utilisateur à des fins d'authentification.</span><span class="sxs-lookup"><span data-stu-id="99550-121">The POP3 server uses user provided credentials for authentication.</span></span>  <span data-ttu-id="99550-122">Celles-ci sont envoyées en texte clair.</span><span class="sxs-lookup"><span data-stu-id="99550-122">These credentials are sent in clear text.</span></span>  
  
-   <span data-ttu-id="99550-123">**Digest (APOP).**</span><span class="sxs-lookup"><span data-stu-id="99550-123">**Digest (APOP).**</span></span> <span data-ttu-id="99550-124">Le serveur POP3 utilise une chaîne Digest à des fins d'authentification.</span><span class="sxs-lookup"><span data-stu-id="99550-124">The POP3 server uses a digest string for authentication.</span></span>  
  
-   <span data-ttu-id="99550-125">**Authentification du mot de passe sécurisé (SPA).**</span><span class="sxs-lookup"><span data-stu-id="99550-125">**Secure Password Authentication (SPA).**</span></span> <span data-ttu-id="99550-126">Le serveur POP3 utilise les informations d'identification du processus actuel à des fins d'authentification.</span><span class="sxs-lookup"><span data-stu-id="99550-126">The POP3 server uses current process credentials for authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99550-127">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="99550-127">In This Section</span></span>  
  
-   [<span data-ttu-id="99550-128">Nouveautés de l’adaptateur POP3 ?</span><span class="sxs-lookup"><span data-stu-id="99550-128">What Is the POP3 Adapter?</span></span>](../core/what-is-the-pop3-adapter.md)  
  
-   [<span data-ttu-id="99550-129">Configuration de l’adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="99550-129">Configuring the POP3 Adapter</span></span>](../core/configuring-the-pop3-adapter.md)  
  
-   [<span data-ttu-id="99550-130">Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="99550-130">Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter</span></span>](../core/walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter.md)  
  
-   [<span data-ttu-id="99550-131">Traitement des Messages à parties multiples avec l’adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="99550-131">Processing Multi Part Messages with the POP3 Adapter</span></span>](../core/processing-multi-part-messages-with-the-pop3-adapter.md)