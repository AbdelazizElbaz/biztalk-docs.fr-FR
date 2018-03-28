---
title: Restrictions sur la propriété URL de Destination | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [HTTP adapters], restrictions
- HTTP adapters, restrictions
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f7966fccca324a1453f0ea84e79cd7d9d3d55ad
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="restrictions-on-the-destination-url-property"></a><span data-ttu-id="53cba-102">Restrictions sur la propriété URL de Destination</span><span class="sxs-lookup"><span data-stu-id="53cba-102">Restrictions on the Destination URL Property</span></span>
<span data-ttu-id="53cba-103">L'URL de destination est une chaîne qui indique l'adresse du serveur HTTP auquel vous souhaitez envoyer des messages à l'aide du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="53cba-103">The destination URL is a string that specifies the address of the HTTP server where you want to send messages using the HTTP protocol.</span></span>  
  
 <span data-ttu-id="53cba-104">Les règles et restrictions suivantes s'appliquent à la propriété URL de destination :</span><span class="sxs-lookup"><span data-stu-id="53cba-104">The following rules and restrictions apply to the destination URL property:</span></span>  
  
-   <span data-ttu-id="53cba-105">Vous devez toujours indiquer la propriété URL de destination selon le format suivant :</span><span class="sxs-lookup"><span data-stu-id="53cba-105">You must always specify the destination URL property in the following format:</span></span>  
  
     <span data-ttu-id="53cba-106">http[s]://\<host\>[:\<port\>][/\<path\>[/\<file\>[?\<query-string\>]]]</span><span class="sxs-lookup"><span data-stu-id="53cba-106">http[s]://\<host\>[:\<port\>][/\<path\>[/\<file\>[?\<query-string\>]]]</span></span>  
  
-   <span data-ttu-id="53cba-107">L'intégralité de la chaîne doit ou ne doit pas être un codage URI.</span><span class="sxs-lookup"><span data-stu-id="53cba-107">The whole string may or may not be URI encoded.</span></span>  
  
-   <span data-ttu-id="53cba-108">La chaîne entière, à l’exception de la chaîne de requête ne peut pas contenir les caractères suivants : \< \> : \ &#124; » ?</span><span class="sxs-lookup"><span data-stu-id="53cba-108">The whole string, except the query string, cannot contain any of the following characters: \< \> : \ &#124; " ?</span></span> <span data-ttu-id="53cba-109">\*.</span><span class="sxs-lookup"><span data-stu-id="53cba-109">\*.</span></span>  
  
-   <span data-ttu-id="53cba-110">Cette propriété ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="53cba-110">The property is not case-sensitive.</span></span>  
  
-   <span data-ttu-id="53cba-111">La longueur de la chaîne ne doit pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="53cba-111">The length of the string must not exceed 256 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53cba-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53cba-112">See Also</span></span>  
 [<span data-ttu-id="53cba-113">Configuration d’un port d’envoi HTTP</span><span class="sxs-lookup"><span data-stu-id="53cba-113">Configuring an HTTP Send Port</span></span>](../core/configuring-an-http-send-port.md)