---
title: "Configuration des journaux de BizTalk Server pour les bases de données supplémentaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
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
ms.openlocfilehash: 4b16b1d262b07ecaa62e87456f10bece225b3b34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a><span data-ttu-id="aef7f-102">Configuration des journaux de BizTalk Server pour les bases de données supplémentaires</span><span class="sxs-lookup"><span data-stu-id="aef7f-102">Configuring BizTalk Server Log Shipping for Additional Databases</span></span>
<span data-ttu-id="aef7f-103">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], travaux ajouté à la tâche de sauvegarde de BizTalk Server est automatiquement ajoutés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction.</span><span class="sxs-lookup"><span data-stu-id="aef7f-103">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], jobs added to the Backup BizTalk Server job are automatically added to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping.</span></span> <span data-ttu-id="aef7f-104">Vous n’avez pas à effectuer des étapes supplémentaires pour configurer l’envoi de journaux pour les nouvelles bases de données sont ajoutées à la tâche de sauvegarde de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aef7f-104">You do not have to take additional steps to configure log shipping for new databases added to the Backup BizTalk Server job.</span></span> <span data-ttu-id="aef7f-105">Toutefois, veillez à ajouter des bases de données personnalisées comme approprié sous le \<OtherDatabases > section du fichier SampleUpdateInfo.xml, comme décrit à l’étape 22 de [comment configurer le système de Destination pour l’envoi de journaux](http://go.microsoft.com/fwlink/?LinkId=151402) (http : / / go.microsoft.com/fwlink/ ? LinkId = 151402) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="aef7f-105">However, be sure to add custom databases as appropriate under the \<OtherDatabases> section of the SampleUpdateInfo.xml file as described in step 22 of [How to Configure the Destination System for Log Shipping](http://go.microsoft.com/fwlink/?LinkId=151402) (http://go.microsoft.com/fwlink/?LinkId=151402) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef7f-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aef7f-106">See Also</span></span>  
 [<span data-ttu-id="aef7f-107">Journaux de configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="aef7f-107">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)