---
title: "Messages suspendus sont inclus dans le nombre de messages dans le seuil de limitation de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb708bb-6d6d-4494-8b8d-67aa44800a20
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f8ea0643ccf2d6206ba86bc56b5dd54c0d51115
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="suspended-messages-are-included-in-the-message-count-in-database-throttling-threshold"></a><span data-ttu-id="e0176-102">Les messages interrompus sont inclus dans le seuil de limitation Nombre de messages dans la base de données</span><span class="sxs-lookup"><span data-stu-id="e0176-102">Suspended Messages are Included in the Message Count in Database Throttling Threshold</span></span>
<span data-ttu-id="e0176-103">Par défaut, l’hôte **nombre dans la base de données de messages** seuil de limitation est définie à 50 000, ce qui déclenchera une condition de limitation dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0176-103">By default the host **Message count in DB** throttling threshold is set to a value of 50,000, which will trigger a throttling condition under the following circumstances:</span></span>  
  
-   <span data-ttu-id="e0176-104">Le nombre total de messages publiés par l'instance de l'hôte dans les files d'attente de travail, de messages interrompus et d'état des hôtes d'abonnement est supérieur à 50 000.</span><span class="sxs-lookup"><span data-stu-id="e0176-104">The total number of messages published by the host instance to the work, state, and suspended queues of the subscribing hosts exceeds 50,000.</span></span>  
  
-   <span data-ttu-id="e0176-105">Le nombre de messages de la table de mise en file d’attente ou des tables de suivi est supérieur à 500 000.</span><span class="sxs-lookup"><span data-stu-id="e0176-105">The number of messages in the spool table or the tracking tables exceeds 500,000 messages.</span></span>  
  
 <span data-ttu-id="e0176-106">Étant donné que les messages interrompus sont inclus dans le **nombre dans la base de données de messages** calcul, la limitation de publication peut se produire même si le serveur BizTalk server rencontre faible de message ou pas de charge.</span><span class="sxs-lookup"><span data-stu-id="e0176-106">Since suspended messages are included in the **Message count in DB** calculation, throttling of message publishing can occur even if the BizTalk server is experiencing low or no load.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="e0176-107">Recommandations</span><span class="sxs-lookup"><span data-stu-id="e0176-107">Recommendations</span></span>  
  
-   <span data-ttu-id="e0176-108">Si vous pensez que peut avoir un grand nombre de messages suspendus, envisagez d’augmenter la valeur par défaut pour le **nombre dans la base de données de messages** seuil en prenant en compte l’espace requis par le serveur SQL qui contient le Bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e0176-108">If you anticipate that you may have a large number of suspended messages, consider increasing the default value for the **Message count in DB** threshold taking into consideration the space requirements of the SQL server that contains the BizTalk databases.</span></span> <span data-ttu-id="e0176-109">Envisagez également d’augmenter la **multiplicateur de Spool** et **multiplicateur de données de suivi** valeurs pour permettre d’en souffrance dans la table du spouleur.</span><span class="sxs-lookup"><span data-stu-id="e0176-109">Also consider increasing the **Spool multiplier** and **Tracking data multiplier** values to allow additional backlog in the Spool table.</span></span>  
  
     <span data-ttu-id="e0176-110">Pour plus d’informations sur ces valeurs, consultez [comment modifier les ressources de limitation paramètres](../core/how-to-modify-resource-based-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e0176-110">For more information about these values, see [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).</span></span>  
  
-   <span data-ttu-id="e0176-111">Utilisez le **état de limitation de publication de messages** compteur Analyseur de performances associé **BizTalk:MessageAgent** catégorie d’objet de performance pour mesurer l’état de limitation actuel.</span><span class="sxs-lookup"><span data-stu-id="e0176-111">Use the **Message publishing throttling state** Performance Monitor counter associated with **BizTalk:MessageAgent** performance object category to measure the current throttling state.</span></span> <span data-ttu-id="e0176-112">Si ce compteur renvoie la valeur 6, recherchez les instances interrompues et reprenez ou mettez fin à celles-ci, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="e0176-112">If this counter returns a value of 6, then check for suspended instances and terminate or resume suspended instances as needed.</span></span>  
  
     <span data-ttu-id="e0176-113">Pour plus d’informations sur la limitation des compteurs de performance de l’hôte, consultez [hôte la limitation des compteurs de Performance](../core/host-throttling-performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="e0176-113">For more information about the host throttling performance counters, see [Host Throttling Performance Counters](../core/host-throttling-performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0176-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0176-114">See Also</span></span>  
 [<span data-ttu-id="e0176-115">Limitation des recommandations sur la conception</span><span class="sxs-lookup"><span data-stu-id="e0176-115">Throttling Design Recommendations</span></span>](../core/throttling-design-recommendations.md)