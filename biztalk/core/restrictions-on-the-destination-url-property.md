---
title: "Restrictions sur la propriété URL de Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [HTTP adapters], restrictions
- HTTP adapters, restrictions
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f7966fccca324a1453f0ea84e79cd7d9d3d55ad
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="restrictions-on-the-destination-url-property"></a><span data-ttu-id="985a3-102">Restrictions sur la propriété URL de Destination</span><span class="sxs-lookup"><span data-stu-id="985a3-102">Restrictions on the Destination URL Property</span></span>
<span data-ttu-id="985a3-103">L'URL de destination est une chaîne qui indique l'adresse du serveur HTTP auquel vous souhaitez envoyer des messages à l'aide du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="985a3-103">The destination URL is a string that specifies the address of the HTTP server where you want to send messages using the HTTP protocol.</span></span>  
  
 <span data-ttu-id="985a3-104">Les règles et restrictions suivantes s'appliquent à la propriété URL de destination :</span><span class="sxs-lookup"><span data-stu-id="985a3-104">The following rules and restrictions apply to the destination URL property:</span></span>  
  
-   <span data-ttu-id="985a3-105">Vous devez toujours indiquer la propriété URL de destination selon le format suivant :</span><span class="sxs-lookup"><span data-stu-id="985a3-105">You must always specify the destination URL property in the following format:</span></span>  
  
     <span data-ttu-id="985a3-106">http [s]  ://\<hôte\>[ :\<port\>] [/\<chemin d’accès\>[/\<fichier\>[ ?\< chaîne de requête\>]]]</span><span class="sxs-lookup"><span data-stu-id="985a3-106">http[s]://\<host\>[:\<port\>][/\<path\>[/\<file\>[?\<query-string\>]]]</span></span>  
  
-   <span data-ttu-id="985a3-107">L'intégralité de la chaîne doit ou ne doit pas être un codage URI.</span><span class="sxs-lookup"><span data-stu-id="985a3-107">The whole string may or may not be URI encoded.</span></span>  
  
-   <span data-ttu-id="985a3-108">La chaîne entière, à l’exception de la chaîne de requête ne peut pas contenir les caractères suivants : \< \> : \ &#124; " ?</span><span class="sxs-lookup"><span data-stu-id="985a3-108">The whole string, except the query string, cannot contain any of the following characters: \< \> : \ &#124; " ?</span></span> <span data-ttu-id="985a3-109">*.</span><span class="sxs-lookup"><span data-stu-id="985a3-109">*.</span></span>  
  
-   <span data-ttu-id="985a3-110">Cette propriété ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="985a3-110">The property is not case-sensitive.</span></span>  
  
-   <span data-ttu-id="985a3-111">La longueur de la chaîne ne doit pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="985a3-111">The length of the string must not exceed 256 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985a3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="985a3-112">See Also</span></span>  
 [<span data-ttu-id="985a3-113">Configuration d’un port d’envoi HTTP</span><span class="sxs-lookup"><span data-stu-id="985a3-113">Configuring an HTTP Send Port</span></span>](../core/configuring-an-http-send-port.md)