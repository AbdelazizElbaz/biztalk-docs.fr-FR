---
title: "Restrictions relatives à la propriété hôte SMTP | Documents Microsoft"
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
ms.assetid: 6dbdb6dc-0062-4444-a4c8-6e2a7900f533
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 465946f15d11f087995b8000231796c5e204c077
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="restrictions-on-the-smtp-host-property"></a><span data-ttu-id="02977-102">Restrictions relatives à la propriété hôte SMTP</span><span class="sxs-lookup"><span data-stu-id="02977-102">Restrictions on the SMTP Host Property</span></span>
<span data-ttu-id="02977-103">La propriété d'hôte SMTP est une chaîne qui spécifie le serveur SMTP que l'adaptateur utilise pour envoyer des messages à partir du serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="02977-103">The SMTP host property is a string that specifies the SMTP server that the SMTP adapter will use to send messages from the BizTalk server.</span></span>  
  
 <span data-ttu-id="02977-104">Les règles et restrictions suivantes s'appliquent à cette propriété :</span><span class="sxs-lookup"><span data-stu-id="02977-104">The following rules and restrictions apply to this property:</span></span>  
  
-   <span data-ttu-id="02977-105">Cette propriété doit être configurée au niveau du gestionnaire de l'adaptateur, au niveau du point de terminaison ou aux niveaux des deux emplacements.</span><span class="sxs-lookup"><span data-stu-id="02977-105">This property must be configured on the adapter handler level, on the endpoint level, or in both places.</span></span>  
  
-   <span data-ttu-id="02977-106">La propriété du serveur SMTP ne peut pas contenir les caractères suivants : ' ~ !</span><span class="sxs-lookup"><span data-stu-id="02977-106">The SMTP server property cannot contain the following characters: \` ~ !</span></span> <span data-ttu-id="02977-107">@ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;</span><span class="sxs-lookup"><span data-stu-id="02977-107">@ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;</span></span>  
  
-   <span data-ttu-id="02977-108">La longueur du nom du serveur SMTP ne doit pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="02977-108">The length of the SMTP server name must not exceed 256 characters.</span></span>  
  
 <span data-ttu-id="02977-109">Lors de la phase de conception, l'adaptateur SMTP valide toujours le nom d'hôte SMTP en employant les règles mentionnées précédemment.</span><span class="sxs-lookup"><span data-stu-id="02977-109">The SMTP adapter always validates the SMTP host name at design time by using the previously mentioned rules.</span></span> <span data-ttu-id="02977-110">En outre, il valide le nom d'hôte SMTP au moment de l'exécution si un message est envoyé via un port dynamique lui étant associé.</span><span class="sxs-lookup"><span data-stu-id="02977-110">In addition, the SMTP adapter validates the SMTP host name at run time if a message is sent through a dynamic port with the SMTP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02977-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02977-111">See Also</span></span>  
 [<span data-ttu-id="02977-112">Restrictions relatives à la configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="02977-112">Restrictions When Configuring the SMTP Adapter</span></span>](../core/restrictions-when-configuring-the-smtp-adapter.md)