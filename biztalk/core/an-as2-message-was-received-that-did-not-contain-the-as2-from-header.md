---
title: "Réception d’un message AS2 ne contenant pas AS2-à partir de l’en-tête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 899f9b21-b321-49a3-84bd-a5410c883968
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a63829b8a52088893a595549637f82be67efcd59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-as2-message-was-received-that-did-not-contain-the-as2-from-header"></a><span data-ttu-id="d1e98-102">Un message AS2 ne contenant pas l'en-tête AS2-From a été reçu</span><span class="sxs-lookup"><span data-stu-id="d1e98-102">An AS2 message was received that did not contain the AS2-From header</span></span>
## <a name="details"></a><span data-ttu-id="d1e98-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d1e98-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1e98-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d1e98-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d1e98-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d1e98-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d1e98-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1e98-106">Event ID</span></span>|-|  
|<span data-ttu-id="d1e98-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d1e98-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1e98-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d1e98-108"> EDI</span></span>|  
|<span data-ttu-id="d1e98-109">Composant</span><span class="sxs-lookup"><span data-stu-id="d1e98-109">Component</span></span>|<span data-ttu-id="d1e98-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="d1e98-110">AS2 Engine</span></span>|  
|<span data-ttu-id="d1e98-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d1e98-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="d1e98-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d1e98-112">Message Text</span></span>|<span data-ttu-id="d1e98-113">Un message AS2 ne contenant pas l'en-tête AS2-From a été reçu</span><span class="sxs-lookup"><span data-stu-id="d1e98-113">An AS2 message was received that did not contain the AS2-From header</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1e98-114">Explication</span><span class="sxs-lookup"><span data-stu-id="d1e98-114">Explanation</span></span>  
 <span data-ttu-id="d1e98-115">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu traiter le message AS2 entrant car celui-ci ne contient pas d'en-tête AS2-From indiquant la source du message.</span><span class="sxs-lookup"><span data-stu-id="d1e98-115">This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message did not contain an AS2-From header indicating the source of the message.</span></span> <span data-ttu-id="d1e98-116">Un message AS2 doit posséder un en-tête AS2-From.</span><span class="sxs-lookup"><span data-stu-id="d1e98-116">An AS2 message must have an AS2-From header.</span></span> <span data-ttu-id="d1e98-117">Dans le cas contraire, il est suspendu.</span><span class="sxs-lookup"><span data-stu-id="d1e98-117">The message will be suspended if it does not have an AS2-From header.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1e98-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d1e98-118">User Action</span></span>  
 <span data-ttu-id="d1e98-119">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d1e98-119">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="d1e98-120">Assurez-vous que le tiers expéditeur ajoute un en-tête AS2-To à l'en-tête HTTP, AS2 et MIME du message AS2 avant de l'envoyer.</span><span class="sxs-lookup"><span data-stu-id="d1e98-120">Ensure the sending party adds an AS2-To header to the HTTP, AS2, and MIME header of the AS2 message before sending it.</span></span>