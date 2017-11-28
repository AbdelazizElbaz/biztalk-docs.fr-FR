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
ms.openlocfilehash: 0788b693027fb803b121b1b732cb3ee126897e7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-destination-url-property"></a><span data-ttu-id="72a1a-102">Restrictions sur la propriété URL de Destination</span><span class="sxs-lookup"><span data-stu-id="72a1a-102">Restrictions on the Destination URL Property</span></span>
<span data-ttu-id="72a1a-103">L'URL de destination est une chaîne qui indique l'adresse du serveur HTTP auquel vous souhaitez envoyer des messages à l'aide du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="72a1a-103">The destination URL is a string that specifies the address of the HTTP server where you want to send messages using the HTTP protocol.</span></span>  
  
 <span data-ttu-id="72a1a-104">Les règles et restrictions suivantes s'appliquent à la propriété URL de destination :</span><span class="sxs-lookup"><span data-stu-id="72a1a-104">The following rules and restrictions apply to the destination URL property:</span></span>  
  
-   <span data-ttu-id="72a1a-105">Vous devez toujours indiquer la propriété URL de destination selon le format suivant :</span><span class="sxs-lookup"><span data-stu-id="72a1a-105">You must always specify the destination URL property in the following format:</span></span>  
  
     <span data-ttu-id="72a1a-106">http [s]  ://\<hôte > [ :\<port >] [/\<chemin d’accès > [/\<fichier > [ ?\< chaîne de requête >]]]</span><span class="sxs-lookup"><span data-stu-id="72a1a-106">http[s]://\<host>[:\<port>][/\<path>[/\<file>[?\<query-string>]]]</span></span>  
  
-   <span data-ttu-id="72a1a-107">L'intégralité de la chaîne doit ou ne doit pas être un codage URI.</span><span class="sxs-lookup"><span data-stu-id="72a1a-107">The whole string may or may not be URI encoded.</span></span>  
  
-   <span data-ttu-id="72a1a-108">La chaîne entière, à l’exception de la chaîne de requête ne peut pas contenir les caractères suivants : \< > : \ &#124; " ?</span><span class="sxs-lookup"><span data-stu-id="72a1a-108">The whole string, except the query string, cannot contain any of the following characters: \< > : \ &#124; " ?</span></span> <span data-ttu-id="72a1a-109">*.</span><span class="sxs-lookup"><span data-stu-id="72a1a-109">*.</span></span>  
  
-   <span data-ttu-id="72a1a-110">Cette propriété ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="72a1a-110">The property is not case-sensitive.</span></span>  
  
-   <span data-ttu-id="72a1a-111">La longueur de la chaîne ne doit pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="72a1a-111">The length of the string must not exceed 256 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a1a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72a1a-112">See Also</span></span>  
 [<span data-ttu-id="72a1a-113">Configuration d’un Port d’envoi HTTP</span><span class="sxs-lookup"><span data-stu-id="72a1a-113">Configuring an HTTP Send Port</span></span>](../core/configuring-an-http-send-port.md)