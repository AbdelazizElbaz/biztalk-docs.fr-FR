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
ms.openlocfilehash: 42173fa0ccb01b3ced42965af74e1fcc01d12aba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-smtp-host-property"></a><span data-ttu-id="b8ce7-102">Restrictions relatives à la propriété hôte SMTP</span><span class="sxs-lookup"><span data-stu-id="b8ce7-102">Restrictions on the SMTP Host Property</span></span>
<span data-ttu-id="b8ce7-103">La propriété d'hôte SMTP est une chaîne qui spécifie le serveur SMTP que l'adaptateur utilise pour envoyer des messages à partir du serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b8ce7-103">The SMTP host property is a string that specifies the SMTP server that the SMTP adapter will use to send messages from the BizTalk server.</span></span>  
  
 <span data-ttu-id="b8ce7-104">Les règles et restrictions suivantes s'appliquent à cette propriété :</span><span class="sxs-lookup"><span data-stu-id="b8ce7-104">The following rules and restrictions apply to this property:</span></span>  
  
-   <span data-ttu-id="b8ce7-105">Cette propriété doit être configurée au niveau du gestionnaire de l'adaptateur, au niveau du point de terminaison ou aux niveaux des deux emplacements.</span><span class="sxs-lookup"><span data-stu-id="b8ce7-105">This property must be configured on the adapter handler level, on the endpoint level, or in both places.</span></span>  
  
-   <span data-ttu-id="b8ce7-106">La propriété du serveur SMTP ne peut pas contenir les caractères suivants : ' ~ !</span><span class="sxs-lookup"><span data-stu-id="b8ce7-106">The SMTP server property cannot contain the following characters: \` ~ !</span></span> <span data-ttu-id="b8ce7-107">@ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< > /, ?;</span><span class="sxs-lookup"><span data-stu-id="b8ce7-107">@ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< > /, ?;</span></span>  
  
-   <span data-ttu-id="b8ce7-108">La longueur du nom du serveur SMTP ne doit pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="b8ce7-108">The length of the SMTP server name must not exceed 256 characters.</span></span>  
  
 <span data-ttu-id="b8ce7-109">Lors de la phase de conception, l'adaptateur SMTP valide toujours le nom d'hôte SMTP en employant les règles mentionnées précédemment.</span><span class="sxs-lookup"><span data-stu-id="b8ce7-109">The SMTP adapter always validates the SMTP host name at design time by using the previously mentioned rules.</span></span> <span data-ttu-id="b8ce7-110">En outre, il valide le nom d'hôte SMTP au moment de l'exécution si un message est envoyé via un port dynamique lui étant associé.</span><span class="sxs-lookup"><span data-stu-id="b8ce7-110">In addition, the SMTP adapter validates the SMTP host name at run time if a message is sent through a dynamic port with the SMTP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ce7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8ce7-111">See Also</span></span>  
 [<span data-ttu-id="b8ce7-112">Restrictions relatives à la configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="b8ce7-112">Restrictions When Configuring the SMTP Adapter</span></span>](../core/restrictions-when-configuring-the-smtp-adapter.md)