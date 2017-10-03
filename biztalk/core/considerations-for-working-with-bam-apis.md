---
title: "Considérations pour l’utilisation des API BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd8ccf63-6989-4ad6-a193-cf3043e9a466
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b00eb00013fefde42e1972b89a661d0a2ba0de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-working-with-bam-apis"></a><span data-ttu-id="9a833-102">Éléments à prendre en compte pour travailler avec les API de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="9a833-102">Considerations for Working with BAM APIs</span></span>
<span data-ttu-id="9a833-103">Lors de l'utilisation d'un objet « Microsoft.BizTalk.Bam.EventObservation.EventStream » tel que DirectEventStream, BufferedEventStream, MessagingEventStream ou OrchestrationEventStream, l'analyse BAM capture des étapes majeures de sorte qu'elles sont automatiquement enregistrées au format UTC (Coordinated Universal Time, également appelé Greenwich Mean Time, ou heure du méridien de Greenwich).</span><span class="sxs-lookup"><span data-stu-id="9a833-103">When using an  "Microsoft.BizTalk.Bam.EventObservation.EventStream" object, such as DirectEventStream, BufferedEventStream, MessagingEventStream, or OrchestrationEventStream, BAM captures milestones such that they are automatically recorded in Coordinated Universal Time (UTC) format (this is also referred to as Greenwich Mean Time).</span></span> <span data-ttu-id="9a833-104">Lorsque vous envoyez des dates et des heures à l'analyse BAM à l'aide des API, elles sont reçues au format envoyé et ne sont pas converties au format UTC.</span><span class="sxs-lookup"><span data-stu-id="9a833-104">When you send date/times to BAM using the APIs they are received in the format sent with no conversion to UTC format.</span></span> <span data-ttu-id="9a833-105">Veuillez tenir compte des considérations suivantes lorsque vous développez vos solutions d'analyse BAM :</span><span class="sxs-lookup"><span data-stu-id="9a833-105">You should take the following considerations into account when you are developing your BAM solutions:</span></span>  
  
-   <span data-ttu-id="9a833-106">Les données suivies à partir de BizTalk Server sont reçues au format UTC.</span><span class="sxs-lookup"><span data-stu-id="9a833-106">Data traced from BizTalk Server is received in UTC format.</span></span> <span data-ttu-id="9a833-107">Il se peut qu'elles diffèrent des autres données issues du flux d'événements.</span><span class="sxs-lookup"><span data-stu-id="9a833-107">This could be inconsistent with other data that comes from the event stream.</span></span>  
  
-   <span data-ttu-id="9a833-108">Si vous utilisez les API de flux d'événements pour fournir des données de suivi de date et d'heure au format d'heure locale, les données figurant dans le portail BAM seront incorrectes, car toutes les dates et les heures des données BAM sont censées être au format UTC.</span><span class="sxs-lookup"><span data-stu-id="9a833-108">If you use the event stream APIs to provide date and time tracking data in local time format, the data in the BAM portal will be incorrect as the expectation is that all times in BAM data are in UTC format.</span></span>  
  
 <span data-ttu-id="9a833-109">Si certaines de vos applications utilisent l'heure locale, que vous effectuez une mise à niveau et envisagez d'utiliser le portail BAM, vous devez modifier vos données afin de les rendre conformes au format UTC.</span><span class="sxs-lookup"><span data-stu-id="9a833-109">If you have existing applications that use local time, and you are now upgrading and planning to use the BAM portal, you must modify your data to make it conform to UTC format.</span></span> <span data-ttu-id="9a833-110">Vous devez également modifier votre application personnalisée afin de la convertir au format UTC.</span><span class="sxs-lookup"><span data-stu-id="9a833-110">You also need to modify your custom application to convert to UTC format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a833-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a833-111">See Also</span></span>  
 [<span data-ttu-id="9a833-112">Implémentation de Solutions BAM</span><span class="sxs-lookup"><span data-stu-id="9a833-112">Implementing BAM Solutions</span></span>](../core/implementing-bam-solutions.md)