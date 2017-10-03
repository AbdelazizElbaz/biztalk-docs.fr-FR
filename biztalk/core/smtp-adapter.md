---
title: Adaptateur SMTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, about SMTP adapters
- SMTP adapters, authenticating
- send adapters, SMTP adapters
- authenticating, SMTP adapters
- SMTP adapters
- SMTP adapters, send adapters
ms.assetid: b712f76d-3ce4-4780-9627-951e5951bd8a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0d0d16bf266d0b636aa9955b5c25b37d9ab54d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter"></a><span data-ttu-id="365d1-102">Adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="365d1-102">SMTP Adapter</span></span>
<span data-ttu-id="365d1-103">L'adaptateur SMTP permet d'échanger des informations entre un serveur exécutant Microsoft BizTalk Server et d'autres applications via le protocole SMTP (Simple Mail Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="365d1-103">You use the Simple Mail Transfer Protocol (SMTP) adapter to exchange information between a server running Microsoft BizTalk Server and other applications by means of the SMTP protocol.</span></span> <span data-ttu-id="365d1-104">BizTalk Server peut envoyer des messages à d'autres applications en créant un message électronique qu'il remet à une adresse de messagerie spécifiée.</span><span class="sxs-lookup"><span data-stu-id="365d1-104">BizTalk Server can send messages to other applications by creating an e-mail message and delivering it to a specified e-mail address.</span></span> <span data-ttu-id="365d1-105">L'adaptateur d'envoi SMTP crée en interne un message électronique SMTP et l'envoie à une adresse de messagerie cible.</span><span class="sxs-lookup"><span data-stu-id="365d1-105">Internally, the SMTP send adapter creates an SMTP-based e-mail message and sends it to a target e-mail address.</span></span> <span data-ttu-id="365d1-106">L'adresse de messagerie cible est une propriété de l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="365d1-106">The target e-mail address is a property of the SMTP adapter.</span></span> <span data-ttu-id="365d1-107">L'Explorateur BizTalk expose cette propriété lors de la configuration du port d'envoi SMTP.</span><span class="sxs-lookup"><span data-stu-id="365d1-107">BizTalk Explorer exposes this property when you configure the SMTP send port.</span></span>  
  
 <span data-ttu-id="365d1-108">L’adaptateur SMTP prend en charge les caractères génériques dans le **à**, **FROM**, **CC** et **sujet** propriétés et les résout à leur réelle valeurs.</span><span class="sxs-lookup"><span data-stu-id="365d1-108">The SMTP adapter supports wildcard characters in the **TO**, **FROM**, **CC** and **SUBJECT** properties, and resolves them to their actual values.</span></span> <span data-ttu-id="365d1-109">Si les caractères génériques dans le **à**, **FROM**, et **CC** ne peuvent pas être résolu, le transport SMTP consigne une erreur et place le message dans la file d’attente suspendue ou redirige le message vers le transport secondaire.</span><span class="sxs-lookup"><span data-stu-id="365d1-109">If wildcard characters in the **TO**, **FROM**, and **CC** properties cannot be resolved, the SMTP transport logs an error and puts the message into the suspended queue or redirects the message to the backup transport.</span></span> <span data-ttu-id="365d1-110">Si les caractères génériques ne peuvent pas être résolues dans le **sujet** propriété, le message est envoyé avec la **objet** propriété spécifiée exactement comme dans la propriété (par exemple, « Message MessageID % »).</span><span class="sxs-lookup"><span data-stu-id="365d1-110">If the wildcard characters cannot be resolved in the **SUBJECT** property, the message is sent with the **SUBJECT** property specified exactly as in the property (for example, "Message %MessageID%").</span></span>  
  
 <span data-ttu-id="365d1-111">Par défaut, le texte des messages SMTP est au format Texte brut.</span><span class="sxs-lookup"><span data-stu-id="365d1-111">By default, the message text of SMTP messages is plain text.</span></span> <span data-ttu-id="365d1-112">Pour utiliser le format HTML dans le corps des messages, vous pouvez configurer l'adaptateur pour qu'il utilise le contenu d'un fichier HTML pour le texte du message.</span><span class="sxs-lookup"><span data-stu-id="365d1-112">To use HTML in message bodies, you can configure the adapter to use the contents of an HTML file for the message text.</span></span>  
  
 <span data-ttu-id="365d1-113">Pour plus d’informations sur les problèmes de sécurité SMTP, consultez [recommandations de sécurité de l’adaptateur SMTP](../core/smtp-adapter-security-recommendations.md).</span><span class="sxs-lookup"><span data-stu-id="365d1-113">For more information about SMTP security issues, see [SMTP Adapter Security Recommendations](../core/smtp-adapter-security-recommendations.md).</span></span>  
  
 <span data-ttu-id="365d1-114">L'adaptateur SMTP est constitué d'un seul adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="365d1-114">The SMTP adapter consists of only one adapter, a send adapter.</span></span> <span data-ttu-id="365d1-115">L'adaptateur d'envoi contrôle les ports d'envoi qui utilisent l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="365d1-115">The send adapter controls the send ports that use the SMTP adapter.</span></span>  
  
 <span data-ttu-id="365d1-116">Cette rubrique décrit le flux d'un message via l'adaptateur d'envoi SMTP.</span><span class="sxs-lookup"><span data-stu-id="365d1-116">This topic discusses the flow of a message through the SMTP send adapter.</span></span>  
  
 <span data-ttu-id="365d1-117">**Adaptateur d’envoi SMTP**</span><span class="sxs-lookup"><span data-stu-id="365d1-117">**SMTP Send Adapter**</span></span>  
  
 <span data-ttu-id="365d1-118">L'adaptateur d'envoi SMTP récupère les messages auprès du serveur avant de les publier sur un serveur SMTP qui les envoie aux destinataires des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="365d1-118">The SMTP send adapter gets messages from the server and posts them to an SMTP server that sends them to e-mail recipients.</span></span> <span data-ttu-id="365d1-119">L'adaptateur d'envoi SMTP récupère le contenu du message à partir du corps de l'objet message BizTalk, d'un fichier spécifié ou d'un texte entré dans une boîte de dialogue affichée lors de la configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="365d1-119">The SMTP send adapter gets the message content from the body part of the BizTalk Message object, from a specified file, or from a text entered into a dialog box that is available when configuring the adapter.</span></span>  
  
 <span data-ttu-id="365d1-120">Une fois que l'adaptateur d'envoi SMTP a publié un message sur le serveur SMTP, il supprime le message de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="365d1-120">After the SMTP send adapter successfully posts a message onto the SMTP server, the SMTP send adapter deletes the message from the MessageBox database.</span></span>  
  
 <span data-ttu-id="365d1-121">Pour chaque message qu'il envoie, l'adaptateur d'envoi SMTP peut demander un accusé de réception et une confirmation de lecture.</span><span class="sxs-lookup"><span data-stu-id="365d1-121">The SMTP send adapter can request delivery notification and read receipts for messages sent over the SMTP send adapter.</span></span> <span data-ttu-id="365d1-122">L’adaptateur SMTP remet l’accusé de réception de notification et les informations à l’adresse spécifiée sur le protocole SMTP **de** en-tête.</span><span class="sxs-lookup"><span data-stu-id="365d1-122">The SMTP adapter delivers the notification and read receipt to the address specified on the SMTP **From** header.</span></span>  
  
 <span data-ttu-id="365d1-123">**Authentification avec le serveur SMTP**</span><span class="sxs-lookup"><span data-stu-id="365d1-123">**Authentication with SMTP Server**</span></span>  
  
 <span data-ttu-id="365d1-124">Si l'authentification du serveur SMTP est requise, l'adaptateur SMTP utilise l'un des types d'authentifications suivants :</span><span class="sxs-lookup"><span data-stu-id="365d1-124">If you require SMTP server authentication, the SMTP send adapter uses one of the following authentication types:</span></span>  
  
-   <span data-ttu-id="365d1-125">**De base.**</span><span class="sxs-lookup"><span data-stu-id="365d1-125">**Basic.**</span></span> <span data-ttu-id="365d1-126">Le serveur SMTP utilise les informations d'identification fournies par l'utilisateur à des fins d'authentification.</span><span class="sxs-lookup"><span data-stu-id="365d1-126">The SMTP server uses user-provided credentials for authentication.</span></span>  
  
-   <span data-ttu-id="365d1-127">**Compte du processus (NTLM).**</span><span class="sxs-lookup"><span data-stu-id="365d1-127">**Process account (NTLM).**</span></span> <span data-ttu-id="365d1-128">Le serveur SMTP utilise les informations d'identification du processus actuel à des fins d'authentification.</span><span class="sxs-lookup"><span data-stu-id="365d1-128">The SMTP server uses current process credentials for authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="365d1-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="365d1-129">In This Section</span></span>  
  
-   [<span data-ttu-id="365d1-130">Configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="365d1-130">Configuring the SMTP Adapter</span></span>](../core/configuring-the-smtp-adapter.md)  
  
-   [<span data-ttu-id="365d1-131">Restrictions relatives à la configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="365d1-131">Restrictions When Configuring the SMTP Adapter</span></span>](../core/restrictions-when-configuring-the-smtp-adapter.md)  
  
-   [<span data-ttu-id="365d1-132">Recommandations de sécurité de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="365d1-132">SMTP Adapter Security Recommendations</span></span>](../core/smtp-adapter-security-recommendations.md)