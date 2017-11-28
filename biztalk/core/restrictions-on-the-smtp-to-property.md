---
title: "Restrictions sur la propriété To SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- SMTP adapters, restrictions
ms.assetid: c876d30e-44ab-462d-8c98-64416ed6dd1f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b59495ac94b3591801101607533eb9c7dba158fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-smtp-to-property"></a><span data-ttu-id="e2c13-102">Restrictions sur la propriété To SMTP</span><span class="sxs-lookup"><span data-stu-id="e2c13-102">Restrictions on the SMTP To Property</span></span>
<span data-ttu-id="e2c13-103">Le **à** propriété est une chaîne qui spécifie l’adresse SMTP du destinataire du message.</span><span class="sxs-lookup"><span data-stu-id="e2c13-103">The **To** property is a string that specifies the SMTP address of the recipient of the message.</span></span> <span data-ttu-id="e2c13-104">Vous pouvez répertorier plusieurs adresses avec un séparateur pris en charge par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="e2c13-104">You can list several addresses with a separator that SMTP server supports.</span></span>  
  
 <span data-ttu-id="e2c13-105">Aucune restriction particulière ne s'applique au format d'une adresse SMTP.</span><span class="sxs-lookup"><span data-stu-id="e2c13-105">There are no specific restrictions for the format of an SMTP address.</span></span> <span data-ttu-id="e2c13-106">Cela signifie que l'adaptateur accepte tout format pris en charge par un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="e2c13-106">This means that the adapter will accept any format that an SMTP server supports.</span></span> <span data-ttu-id="e2c13-107">Si un utilisateur renseigne des adresses non valides, l'opération d'envoi échouera et l'adaptateur d'envoi SMTP signalera une erreur.</span><span class="sxs-lookup"><span data-stu-id="e2c13-107">If a user provides addresses that are not valid, the send operation will fail and the SMTP send adapter will report an error.</span></span>  
  
 <span data-ttu-id="e2c13-108">Toutefois, cette propriété ne peut pas être vide et sa taille ne doit pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="e2c13-108">The only restrictions for this property are that it must not be empty and its size must not exceed 256 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c13-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2c13-109">See Also</span></span>  
 [<span data-ttu-id="e2c13-110">Restrictions relatives à la configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="e2c13-110">Restrictions When Configuring the SMTP Adapter</span></span>](../core/restrictions-when-configuring-the-smtp-adapter.md)