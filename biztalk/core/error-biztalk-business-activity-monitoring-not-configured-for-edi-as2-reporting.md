---
title: "BizTalk Business Activity Monitoring n’a pas été configuré pour le rapport d’état EDI-AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f46c1c8-2771-4b16-8fb1-71952792ac4a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e84301e55cd6fbdcb74467758c7e338e61b727f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-business-activity-monitoring-has-not-been-configured-for-edi-as2-status-reporting"></a>BizTalk Business Activity Monitoring n’a pas été configuré pour le rapport d’état EDI-AS2
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|BizTalk Business Activity Monitoring n’a pas été configuré pour le rapport d’état EDI/AS2. La fonction de création de rapports d'état va donc être désactivée.|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement, erreur ou information indique que la création de rapports d'état EDI/AS2 n'est pas activée car l'analyse BAM (Business Activity Monitoring) n'a pas été configurée via l'Assistant Configuration de BizTalk. L'infrastructure BAM est une condition préalable à la création de rapports d'état EDI/AS2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exécutez l'Assistant Configuration de BizTalk et configurez l'analyse BAM (Business Activity Monitoring).