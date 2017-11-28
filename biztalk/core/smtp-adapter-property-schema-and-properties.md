---
title: "Propriétés et schéma de propriété d’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserName property, SMTP adapters
- EmailBodyTextCharset property [SMTP adapters]
- configuring [SMTP adapters], properties
- Subject property [SMTP adapters]
- EmailBodyFileCharset property [SMTP adapters]
- Attachments property [SMTP adapters]
- SMTP adapters, schemas
- EmailBodyText property [SMTP adapters]
- configuring [SMTP adapters], schemas
- CC property [SMTP adapters]
- ReadReceipt property [SMTP adapters]
- Password property [SMTP adapters]
- ReplyBy property [SMTP adapters]
- DeliveryReceipt property [SMTP adapters]
- SMTP adapters, properties
- SMTPAuthenticate property [SMTP adapters]
- EmailBodyFile property [SMTP adapters]
- schemas, SMTP adapters
- SMTPHost property [SMTP adapters]
- From property [SMTP adapters]
- MessagePartsAttachments property [SMTP adapters]
ms.assetid: 6d062fb6-d728-4525-8f0d-bd3f0f8ff7ca
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09f7dfa67bfad53e43a4a6678ff6ad67705e0e27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-property-schema-and-properties"></a><span data-ttu-id="7e67e-102">Propriétés et schéma de propriété de l'adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="7e67e-102">SMTP Adapter Property Schema and Properties</span></span>
<span data-ttu-id="7e67e-103">Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="7e67e-103">The following table lists the properties in the SMTP adapter property schema.</span></span>  
  
 <span data-ttu-id="7e67e-104">**Namespace :** http://schemas.microsoft.com/BizTalk/2003/smtp-properties</span><span class="sxs-lookup"><span data-stu-id="7e67e-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/smtp-properties</span></span>  
  
|<span data-ttu-id="7e67e-105">Nom</span><span class="sxs-lookup"><span data-stu-id="7e67e-105">Name</span></span>|<span data-ttu-id="7e67e-106">Type</span><span class="sxs-lookup"><span data-stu-id="7e67e-106">Type</span></span>|<span data-ttu-id="7e67e-107"> Description</span><span class="sxs-lookup"><span data-stu-id="7e67e-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="7e67e-108">**Nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="7e67e-108">**Username**</span></span>|<span data-ttu-id="7e67e-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-109">xs:string</span></span>|<span data-ttu-id="7e67e-110">Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="7e67e-110">Specify the user name to use for authentication with the SMTP server.</span></span>|  
|<span data-ttu-id="7e67e-111">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="7e67e-111">**Password**</span></span>|<span data-ttu-id="7e67e-112">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-112">xs:string</span></span>|<span data-ttu-id="7e67e-113">Indiquer le mot de passe nécessaire à l'authentification sur le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="7e67e-113">Specify the password to use for authentication with the SMTP server.</span></span>|  
|<span data-ttu-id="7e67e-114">**SMTPHost**</span><span class="sxs-lookup"><span data-stu-id="7e67e-114">**SMTPHost**</span></span>|<span data-ttu-id="7e67e-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-115">xs:string</span></span>|<span data-ttu-id="7e67e-116">Indiquer le nom du serveur SMTP à utiliser pour l'envoi des messages.</span><span class="sxs-lookup"><span data-stu-id="7e67e-116">Specify the name of the SMTP server to use when sending messages.</span></span>|  
|<span data-ttu-id="7e67e-117">**From**</span><span class="sxs-lookup"><span data-stu-id="7e67e-117">**From**</span></span>|<span data-ttu-id="7e67e-118">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-118">xs:string</span></span>|<span data-ttu-id="7e67e-119">Spécifiez l’adresse de messagerie à placer sur le protocole SMTP **de** en-tête.</span><span class="sxs-lookup"><span data-stu-id="7e67e-119">Specify the e-mail address to place on the SMTP **From** header.</span></span>|  
|<span data-ttu-id="7e67e-120">**CC**</span><span class="sxs-lookup"><span data-stu-id="7e67e-120">**CC**</span></span>|<span data-ttu-id="7e67e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-121">xs:string</span></span>|<span data-ttu-id="7e67e-122">Indique l'adresse de messagerie à laquelle envoyer une copie du message.</span><span class="sxs-lookup"><span data-stu-id="7e67e-122">Specify the e-mail address to send a copy of the message.</span></span>|  
|<span data-ttu-id="7e67e-123">**Subject**</span><span class="sxs-lookup"><span data-stu-id="7e67e-123">**Subject**</span></span>|<span data-ttu-id="7e67e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-124">xs:string</span></span>|<span data-ttu-id="7e67e-125">Indiquer l'en-tête objet du message.</span><span class="sxs-lookup"><span data-stu-id="7e67e-125">Specify the subject header for the message.</span></span>|  
|<span data-ttu-id="7e67e-126">**SMTPAuthenticate**</span><span class="sxs-lookup"><span data-stu-id="7e67e-126">**SMTPAuthenticate**</span></span>|<span data-ttu-id="7e67e-127">xs:int</span><span class="sxs-lookup"><span data-stu-id="7e67e-127">xs:int</span></span>|<span data-ttu-id="7e67e-128">Indique le type d'authentification à utiliser avec le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="7e67e-128">Specify the type of authentication to use with the SMTP server.</span></span>|  
|<span data-ttu-id="7e67e-129">**ReadReceipt**</span><span class="sxs-lookup"><span data-stu-id="7e67e-129">**ReadReceipt**</span></span>|<span data-ttu-id="7e67e-130">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="7e67e-130">xs:boolean</span></span>|<span data-ttu-id="7e67e-131">Indique qu'un message électronique de confirmation doit être envoyé après la lecture du message.</span><span class="sxs-lookup"><span data-stu-id="7e67e-131">Specify whether to send a confirmation e-mail message when the message is read.</span></span>|  
|<span data-ttu-id="7e67e-132">**DeliveryReceipt**</span><span class="sxs-lookup"><span data-stu-id="7e67e-132">**DeliveryReceipt**</span></span>|<span data-ttu-id="7e67e-133">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="7e67e-133">xs:boolean</span></span>|<span data-ttu-id="7e67e-134">Indique qu'un message électronique de confirmation doit être envoyé après la remise du message.</span><span class="sxs-lookup"><span data-stu-id="7e67e-134">Specify whether to send a confirmation e-mail message after delivery of the message.</span></span>|  
|<span data-ttu-id="7e67e-135">**EmailBodyText**</span><span class="sxs-lookup"><span data-stu-id="7e67e-135">**EmailBodyText**</span></span>|<span data-ttu-id="7e67e-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-136">xs:string</span></span>|<span data-ttu-id="7e67e-137">Indiquer le texte à utiliser pour le corps du message électronique à envoyer.</span><span class="sxs-lookup"><span data-stu-id="7e67e-137">Specify text to be used for the body of the e-mail being sent.</span></span>|  
|<span data-ttu-id="7e67e-138">**EmailBodyTextCharset**</span><span class="sxs-lookup"><span data-stu-id="7e67e-138">**EmailBodyTextCharset**</span></span>|<span data-ttu-id="7e67e-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-139">xs:string</span></span>|<span data-ttu-id="7e67e-140">Spécifier le jeu de caractères à utiliser pour coder le corps du message électronique envoyé lorsque la **EmailBodyText** option est utilisée.</span><span class="sxs-lookup"><span data-stu-id="7e67e-140">Specify the character set to use for encoding the body of the e-mail being sent when the **EmailBodyText** option is used.</span></span> <span data-ttu-id="7e67e-141">L’adaptateur SMTP convertit le **EmailBodyText** pour le jeu de caractères spécifié par **EmailBodyTextCharset**.</span><span class="sxs-lookup"><span data-stu-id="7e67e-141">The SMTP adapter will convert the **EmailBodyText** to the character set specified by **EmailBodyTextCharset**.</span></span>|  
|<span data-ttu-id="7e67e-142">**EmailBodyFile**</span><span class="sxs-lookup"><span data-stu-id="7e67e-142">**EmailBodyFile**</span></span>|<span data-ttu-id="7e67e-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-143">xs:string</span></span>|<span data-ttu-id="7e67e-144">Indique que le corps du message électronique à envoyer correspond au contenu d'un fichier, et précise le chemin d'accès à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="7e67e-144">Specifies that the contents of a file will be used for the body of the e-mail being sent and the full path to the file.</span></span> <span data-ttu-id="7e67e-145">Ce chemin d’accès doit être accessible à l’hôte de l’adaptateur SMTP au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7e67e-145">This path must be accessible to the host for the SMTP adapter at run time.</span></span>|  
|<span data-ttu-id="7e67e-146">**EmailBodyFileCharset**</span><span class="sxs-lookup"><span data-stu-id="7e67e-146">**EmailBodyFileCharset**</span></span>|<span data-ttu-id="7e67e-147">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-147">xs:string</span></span>|<span data-ttu-id="7e67e-148">Spécifier le jeu de caractères à utiliser pour coder le corps du message électronique à envoyer si la **EmailBodyFile** est définie.</span><span class="sxs-lookup"><span data-stu-id="7e67e-148">Specify the character set to use for encoding the body of the e-mail being sent if the **EmailBodyFile** property is set.</span></span> <span data-ttu-id="7e67e-149">L'adaptateur SMTP n'effectue aucune conversion du fichier ; celui-ci doit être déjà codé dans ce jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="7e67e-149">The SMTP adapter will not perform any conversion on the file; the file must already be encoded in this character set.</span></span> <span data-ttu-id="7e67e-150">Si le fichier inclut une marque d'ordre de tri, l'adaptateur SMTP la supprime.</span><span class="sxs-lookup"><span data-stu-id="7e67e-150">If the file has a Byte-Order-Mark (BOM), the SMTP adapter will remove it.</span></span>|  
|<span data-ttu-id="7e67e-151">**Pièces jointes**</span><span class="sxs-lookup"><span data-stu-id="7e67e-151">**Attachments**</span></span>|<span data-ttu-id="7e67e-152">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e67e-152">xs:string</span></span>|<span data-ttu-id="7e67e-153">Indique qu'un ou plusieurs fichiers sont joints au message électronique, et précise leur chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="7e67e-153">Specifies that a file or files will be attached to the e-mail message and the full path to the file or files.</span></span> <span data-ttu-id="7e67e-154">L'hôte de l'adaptateur SMTP doit pouvoir y accéder au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7e67e-154">The specified path or paths must be accessible to the host for the SMTP adapter at run time.</span></span>|  
|<span data-ttu-id="7e67e-155">**MessagePartsAttachments**</span><span class="sxs-lookup"><span data-stu-id="7e67e-155">**MessagePartsAttachments**</span></span>|<span data-ttu-id="7e67e-156">xs:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="7e67e-156">xs:unsignedInt</span></span>|<span data-ttu-id="7e67e-157">Indiquer la méthode utilisée pour joindre les parties de message BizTalk à un message électronique.</span><span class="sxs-lookup"><span data-stu-id="7e67e-157">Specify how BizTalk message parts are attached to the e-mail message.</span></span>|  
|<span data-ttu-id="7e67e-158">**ReplyBy**</span><span class="sxs-lookup"><span data-stu-id="7e67e-158">**ReplyBy**</span></span>|<span data-ttu-id="7e67e-159">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="7e67e-159">xs:dateTime</span></span>|<span data-ttu-id="7e67e-160">Spécifiez une valeur dateTime pour le **réponse** en-tête dans le message sortant.</span><span class="sxs-lookup"><span data-stu-id="7e67e-160">Specify a dateTime value for the **Reply-To** header in the outgoing e-mail message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e67e-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e67e-161">See Also</span></span>  
 [<span data-ttu-id="7e67e-162">Configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="7e67e-162">Configuring the SMTP Adapter</span></span>](../core/configuring-the-smtp-adapter.md)