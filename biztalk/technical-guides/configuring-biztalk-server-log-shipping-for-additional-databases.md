---
title: "Configurer les journaux de BizTalk pour les bases de données supplémentaires | Documents Microsoft"
description: "Ajouter des bases de données personnalisées à la tâche de sauvegarde de BizTalk Server et pour l’envoi de journaux de BizTalk Server"
ms.custom: 
ms.date: 11/01/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc2ae67-5cb9-4d53-9bf7-c88f84914960
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1ceb760a5f842f8c24a372d793e0074114b81f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a><span data-ttu-id="2b5aa-103">Configuration des journaux de BizTalk Server pour les bases de données supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2b5aa-103">Configuring BizTalk Server Log Shipping for Additional Databases</span></span>

## <a name="overview"></a><span data-ttu-id="2b5aa-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2b5aa-104">Overview</span></span>
<span data-ttu-id="2b5aa-105">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], travaux ajouté à la tâche de sauvegarde de BizTalk Server est automatiquement ajoutés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction.</span><span class="sxs-lookup"><span data-stu-id="2b5aa-105">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], jobs added to the Backup BizTalk Server job are automatically added to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping.</span></span> <span data-ttu-id="2b5aa-106">Vous n’avez pas à effectuer des étapes supplémentaires pour configurer l’envoi de journaux pour les nouvelles bases de données sont ajoutées à la tâche de sauvegarde de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2b5aa-106">You do not have to take additional steps to configure log shipping for new databases added to the Backup BizTalk Server job.</span></span> <span data-ttu-id="2b5aa-107">Toutefois, veillez à ajouter des bases de données personnalisées comme approprié sous le \<OtherDatabases\> section du fichier SampleUpdateInfo.xml.</span><span class="sxs-lookup"><span data-stu-id="2b5aa-107">However, be sure to add custom databases as appropriate under the \<OtherDatabases\> section of the SampleUpdateInfo.xml file.</span></span> <span data-ttu-id="2b5aa-108">[Configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md) et [sauvegarde des personnalisé bases de données](../core/how-to-back-up-custom-databases.md) fournit quelques conseils.</span><span class="sxs-lookup"><span data-stu-id="2b5aa-108">[Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) and [Back Up Custom Databases](../core/how-to-back-up-custom-databases.md) provides some guidance.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2b5aa-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b5aa-109">See Also</span></span>  
 [<span data-ttu-id="2b5aa-110">Configuration de la copie des journaux de transaction BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2b5aa-110">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)