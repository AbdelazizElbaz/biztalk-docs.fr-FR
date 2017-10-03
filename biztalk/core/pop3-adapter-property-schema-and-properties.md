---
title: "POP3 Propriétés et le schéma de propriété de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, POP3 adapters
- Subject properties [POP3 adapters]
- Date properties [POP3 adapters]
- From properties [POP3 adapters]
- To properties [POP3 adapters]
- POP3 adapters, properties
- configuring [POP3 adapters], schemas
- configuring [POP3 adapters], properties
- CC properties [POP3 adapters]
- Headers properties [POP3 adapters]
- ReplyTo properties [POP3 adapters]
- DispositionNotificationTo properties [POP3 adapters]
ms.assetid: 7a10ae1f-dbcf-4c05-9a50-2503895960f9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b976aba7161272ebdc65da2b5bcd2067c8cd3a5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-property-schema-and-properties"></a><span data-ttu-id="2c92e-102">POP3 Propriétés et le schéma de propriété de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="2c92e-102">POP3 Adapter Property Schema and Properties</span></span>
<span data-ttu-id="2c92e-103">Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="2c92e-103">The following table lists the properties in the POP3 adapter property schema.</span></span>  
  
 <span data-ttu-id="2c92e-104">**Namespace :** http://schemas.microsoft.com/BizTalk/2003/pop3-properties</span><span class="sxs-lookup"><span data-stu-id="2c92e-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/pop3-properties</span></span>  
  
|<span data-ttu-id="2c92e-105">**Nom**</span><span class="sxs-lookup"><span data-stu-id="2c92e-105">**Name**</span></span>|<span data-ttu-id="2c92e-106">**Type**</span><span class="sxs-lookup"><span data-stu-id="2c92e-106">**Type**</span></span>|<span data-ttu-id="2c92e-107">**Description**</span><span class="sxs-lookup"><span data-stu-id="2c92e-107">**Description**</span></span>|  
|--------------|--------------|---------------------|  
|<span data-ttu-id="2c92e-108">**Subject**</span><span class="sxs-lookup"><span data-stu-id="2c92e-108">**Subject**</span></span>|<span data-ttu-id="2c92e-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-109">xs:string</span></span>|<span data-ttu-id="2c92e-110">Spécifie le contenu inséré dans le **sujet** en-tête du message</span><span class="sxs-lookup"><span data-stu-id="2c92e-110">Specifies the content placed on the **Subject** header for the message</span></span>|  
|<span data-ttu-id="2c92e-111">**From**</span><span class="sxs-lookup"><span data-stu-id="2c92e-111">**From**</span></span>|<span data-ttu-id="2c92e-112">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-112">xs:string</span></span>|<span data-ttu-id="2c92e-113">Spécifie l’adresse de messagerie placé sur le **de** champ d’en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-113">Specifies the e-mail address placed on the **From** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="2c92e-114">**Pour**</span><span class="sxs-lookup"><span data-stu-id="2c92e-114">**To**</span></span>|<span data-ttu-id="2c92e-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-115">xs:string</span></span>|<span data-ttu-id="2c92e-116">Spécifie l’adresse de messagerie ou les adresses placés sur le **à** champ d’en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-116">Specifies the e-mail address or addresses placed on the **To** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="2c92e-117">**ReplyTo**</span><span class="sxs-lookup"><span data-stu-id="2c92e-117">**ReplyTo**</span></span>|<span data-ttu-id="2c92e-118">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-118">xs:string</span></span>|<span data-ttu-id="2c92e-119">Spécifie l’adresse de messagerie placé sur le **ReplyTo** champ d’en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-119">Specifies the e-mail address placed on the **ReplyTo** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="2c92e-120">**CC**</span><span class="sxs-lookup"><span data-stu-id="2c92e-120">**CC**</span></span>|<span data-ttu-id="2c92e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-121">xs:string</span></span>|<span data-ttu-id="2c92e-122">Spécifie l’adresse de messagerie ou les adresses placés sur le **CC** champ d’en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-122">Specifies the e-mail address or addresses placed on the **CC** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="2c92e-123">**Date**</span><span class="sxs-lookup"><span data-stu-id="2c92e-123">**Date**</span></span>|<span data-ttu-id="2c92e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-124">xs:string</span></span>|<span data-ttu-id="2c92e-125">Spécifie le contenu inséré dans le **Date** champ d’en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-125">Specifies the content placed on the **Date** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="2c92e-126">**DispositionNotificationTo**</span><span class="sxs-lookup"><span data-stu-id="2c92e-126">**DispositionNotificationTo**</span></span>|<span data-ttu-id="2c92e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-127">xs:string</span></span>|<span data-ttu-id="2c92e-128">Spécifie le contenu inséré dans le **DispositionNotificationTo** champ d’en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-128">Specifies the content placed on the **DispositionNotificationTo** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="2c92e-129">**En-têtes**</span><span class="sxs-lookup"><span data-stu-id="2c92e-129">**Headers**</span></span>|<span data-ttu-id="2c92e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c92e-130">xs:string</span></span>|<span data-ttu-id="2c92e-131">Spécifie le contenu de tous les champs d'en-tête du message électronique.</span><span class="sxs-lookup"><span data-stu-id="2c92e-131">Specifies the content of all of the header fields of the e-mail message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c92e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c92e-132">See Also</span></span>  
 [<span data-ttu-id="2c92e-133">Configuration de l’adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="2c92e-133">Configuring the POP3 Adapter</span></span>](../core/configuring-the-pop3-adapter.md)