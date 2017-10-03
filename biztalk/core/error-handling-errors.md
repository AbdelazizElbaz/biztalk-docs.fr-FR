---
title: Erreur de gestion des erreurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 602be8a5-1f28-457d-8e12-ba06cff65491
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafc64afb24ce8bb7995e7852a778b17a556f018
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-handling-errors"></a><span data-ttu-id="1afe8-102">Erreur en relation avec la gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="1afe8-102">Error Handling Errors</span></span>
<span data-ttu-id="1afe8-103">Informations sur le diagnostic et résolution des erreurs de gestion des erreurs de WCF.</span><span class="sxs-lookup"><span data-stu-id="1afe8-103">Information for diagnosing and resolving WCF Error Handling errors.</span></span>  

## <a name="error-handling-options-disable-location-on-failure-and-suspend-request-message-on-failure-should-not-both-be-set-to-false"></a><span data-ttu-id="1afe8-104">Les options de gestion des erreurs « Désactiver l'emplacement en cas d'échec » « Suspendre le message de requête en cas d'échec » ne doivent pas être toutes deux définies sur False</span><span class="sxs-lookup"><span data-stu-id="1afe8-104">Error handling options "Disable location on failure" and "Suspend request message on failure" should not both be set to false</span></span>    
||<span data-ttu-id="1afe8-105">Détails</span><span class="sxs-lookup"><span data-stu-id="1afe8-105">Details</span></span>|  
|-|-|  
|<span data-ttu-id="1afe8-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1afe8-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1afe8-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1afe8-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="1afe8-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1afe8-108">Event ID</span></span>|<span data-ttu-id="1afe8-109">0</span><span class="sxs-lookup"><span data-stu-id="1afe8-109">0</span></span>|  
|<span data-ttu-id="1afe8-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1afe8-110">Event Source</span></span>|<span data-ttu-id="1afe8-111">0</span><span class="sxs-lookup"><span data-stu-id="1afe8-111">0</span></span>|  
|<span data-ttu-id="1afe8-112">Composant</span><span class="sxs-lookup"><span data-stu-id="1afe8-112">Component</span></span>|<span data-ttu-id="1afe8-113">0</span><span class="sxs-lookup"><span data-stu-id="1afe8-113">0</span></span>|  
|<span data-ttu-id="1afe8-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1afe8-114">Symbolic Name</span></span>|<span data-ttu-id="1afe8-115">0</span><span class="sxs-lookup"><span data-stu-id="1afe8-115">0</span></span>|  
|<span data-ttu-id="1afe8-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1afe8-116">Message Text</span></span>|<span data-ttu-id="1afe8-117">Les options de gestion des erreurs « Désactiver l'emplacement en cas d'échec » « Suspendre le message de requête en cas d'échec » ne doivent pas être toutes deux définies sur False, faute de quoi des messages pourraient être perdus.</span><span class="sxs-lookup"><span data-stu-id="1afe8-117">The error handling options "Disable location on failure" and "Suspend request message on failure" should not both be set to false since message loss may occur.</span></span> <span data-ttu-id="1afe8-118">Définissez l'une d'elles ou les deux sur True.</span><span class="sxs-lookup"><span data-stu-id="1afe8-118">Please set one or both options to true</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1afe8-119">Explication</span><span class="sxs-lookup"><span data-stu-id="1afe8-119">Explanation</span></span>  
 <span data-ttu-id="1afe8-120">Dans l’adaptateur WCF-NetMsmq, les options **désactiver l’emplacement en cas d’échec** et **suspendre le message de demande en cas d’échec** doivent pas être toutes deux sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="1afe8-120">In the WCF-NetMsmq adapter, the options **Disable location on failure** and **Suspend request message on failure** should not both be selected.</span></span> <span data-ttu-id="1afe8-121">Une perte de messages peut se produire si l'emplacement de réception continue à recevoir des messages non valides alors que ceux-ci n'ont pas été suspendus ni stockés dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="1afe8-121">Message loss may occur as the receive location continues to receive invalid messages, while these messages are not suspended and stored in the Message Box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1afe8-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1afe8-122">User Action</span></span>  
 <span data-ttu-id="1afe8-123">La procédure suivante permet de configurer les paramètres de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1afe8-123">Use the following procedure to configure adapter settings.</span></span>    

1. <span data-ttu-id="1afe8-124">Ouvrez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="1afe8-124">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1afe8-125">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="1afe8-125">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="1afe8-126">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="1afe8-126">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="1afe8-127">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="1afe8-127">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="1afe8-128">Sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1afe8-128">Select **Properties**.</span></span>  
  
6.  <span data-ttu-id="1afe8-129">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="1afe8-129">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="1afe8-130">Sélectionnez **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="1afe8-130">Select **Configure**.</span></span>  
  
8.  <span data-ttu-id="1afe8-131">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, sélectionnez le **Messages** onglet.</span><span class="sxs-lookup"><span data-stu-id="1afe8-131">In the **WCF [***transport type***] Transport Properties** dialog box, select the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="1afe8-132">Dans le **gestion des erreurs** section, assurez-vous soit **désactiver l’emplacement en cas d’échec** ou **suspendre le message de demande en cas d’échec** est activée.</span><span class="sxs-lookup"><span data-stu-id="1afe8-132">In the **Error Handling** section, ensure either **Disable location on failure** or **Suspend request message on failure** is checked.</span></span>