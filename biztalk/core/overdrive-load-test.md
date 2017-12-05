---
title: "Dépassement de Test de charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d16d0a8-4255-4f5a-86a2-26cc11bb9a70
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cff4592c58dd165a85d63666958721231cfcbd4c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="overdrive-load-test"></a><span data-ttu-id="bf962-102">Test Overdrive de chargement</span><span class="sxs-lookup"><span data-stu-id="bf962-102">Overdrive Load Test</span></span>
<span data-ttu-id="bf962-103">Les informations contenues dans cette rubrique fait référence aux tests décrits dans [des scénarios de Test pour mesurer le débit maximal acceptable du moteur de](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span><span class="sxs-lookup"><span data-stu-id="bf962-103">The information in this topic refers to the tests explained in [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span></span>  
  
 <span data-ttu-id="bf962-104">L'outil de génération de charge, LoadGen 2007, vous permet de simuler de lourdes charges sur un système BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bf962-104">The Load Generation tool, LoadGen 2007, enables you to simulate heavy loads on a BizTalk Server system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf962-105">Télécharger [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925).</span><span class="sxs-lookup"><span data-stu-id="bf962-105">Download [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925).</span></span> <span data-ttu-id="bf962-106">La version précédente de cet outil, l’outil de génération de charge de BizTalk Server 2004 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999).</span><span class="sxs-lookup"><span data-stu-id="bf962-106">The previous version of this tool, the BizTalk Server 2004 Load Generation Tool is available for download at [http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999).</span></span>  
  
 <span data-ttu-id="bf962-107">Pour simuler un système fonctionnant en permanence au-delà de ses capacités, LoadGen 2007 a été configuré de sorte à envoyer environ 410 msgs/s, à savoir 120 msgs/s de plus que le débit maximal acceptable mesuré.</span><span class="sxs-lookup"><span data-stu-id="bf962-107">To simulate a continuously overdriven system, LoadGen 2007 was configured to send about 410 msgs/sec, 120 msgs/sec more than the measured maximum sustainable throughput.</span></span>  
  
 <span data-ttu-id="bf962-108">Ce test a été conçu non seulement pour dépasser le système, mais aussi pour savoir combien de temps cela prendrait pour le récupérer après une accumulation d'une profondeur de mise en file d'attente d'environ 2 millions d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="bf962-108">The test was designed not only to overdrive the system, but also to get an idea of how long it would take to recover from a spool backlog depth of around 2 million records.</span></span>  
  
 <span data-ttu-id="bf962-109">Pour ce faire, le système a été poussé à la vitesse supérieure jusqu'à ce que la profondeur de mise en file d'attente atteigne environ 2 millions d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="bf962-109">To accomplish this, the system was driven at the increased rate until the spool depth was around 2 million records.</span></span> <span data-ttu-id="bf962-110">Lorsque cette profondeur a atteint le niveau désiré, aucune autre charge n'est générée.</span><span class="sxs-lookup"><span data-stu-id="bf962-110">Once the spool depth reached the desired level then no further load was generated.</span></span>  
  
 <span data-ttu-id="bf962-111">Pour vous assurer que le mécanisme de limitation BizTalk ne pas limiter l’hôte de réception, ce qui empêcherait l’accumulation d’un backlog de la table spool, le **nombre dans la base de données de messages** seuil de limitation de l’hôte de réception a été modifié à partir de la valeur par défaut 50000 à 2000000.</span><span class="sxs-lookup"><span data-stu-id="bf962-111">To ensure that the BizTalk throttling mechanism did not throttle the receive host, which would prevent the accumulation of a spool table backlog, the **Message count in DB** throttling threshold for the receive host was changed from the default value of 50000 to 2000000.</span></span> <span data-ttu-id="bf962-112">Pour plus d’informations sur la modification de la **nombre dans la base de données de messages** seuil de limitation, consultez [comment modifier les ressources de limitation paramètres](../core/how-to-modify-resource-based-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="bf962-112">For information on changing the **Message count in DB** throttling threshold, see [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).</span></span> <span data-ttu-id="bf962-113">Pour plus d’informations sur l’hôte par défaut de paramètres de limitation, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="bf962-113">For information about the default host throttling settings, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span></span>  
  
 <span data-ttu-id="bf962-114">Le graphique suivant présente les mêmes indicateurs que le graphique ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="bf962-114">The following graph shows the same indicators as in the graph above.</span></span>  
  
 <span data-ttu-id="bf962-115">**Profil de charge du test de surcharge**</span><span class="sxs-lookup"><span data-stu-id="bf962-115">**Load profile of overdrive load test**</span></span>  
  
 <span data-ttu-id="bf962-116">![Affichage dans l’Analyseur de performances de la surcharge](../core/media/bts06-overdrive-load.gif "BTS06_Overdrive_Load")</span><span class="sxs-lookup"><span data-stu-id="bf962-116">![Performance montor display of overdrive load](../core/media/bts06-overdrive-load.gif "BTS06_Overdrive_Load")</span></span>  
  
 <span data-ttu-id="bf962-117">Comme le montre le graphique, la profondeur de mise en file d'attente a commencé à augmenter immédiatement pour atteindre jusqu'à 2 millions d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="bf962-117">As can be seen from the graph, the spool depth started building up immediately, peaking at just above 2 million records.</span></span> <span data-ttu-id="bf962-118">À ce taux, il a fallu environ 2 heures et demi pour atteindre l'accumulation de messages prévue de 2 millions d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="bf962-118">At this rate, it took just about 2.5 hours to get to the targeted 2 million record backlog.</span></span> <span data-ttu-id="bf962-119">Une fois la charge arrêtée, il a fallu environ 8 heures pour que les fonctions de nettoyage récupèrent de l'accumulation de messages.</span><span class="sxs-lookup"><span data-stu-id="bf962-119">After the load was stopped, it took around 8 hours for the cleanup jobs to recover from the backlog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf962-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf962-120">See Also</span></span>  
 <span data-ttu-id="bf962-121">[Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="bf962-121">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 <span data-ttu-id="bf962-122">[À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span><span class="sxs-lookup"><span data-stu-id="bf962-122">[Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span></span>  
 [<span data-ttu-id="bf962-123">Test de charge maximale</span><span class="sxs-lookup"><span data-stu-id="bf962-123">Sustainable Load Test</span></span>](../core/sustainable-load-test.md)