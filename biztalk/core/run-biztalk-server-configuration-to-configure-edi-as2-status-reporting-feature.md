---
title: "Pour activer le rapport d’état, exécuter &#39; Configuration de BizTalk Server &#39; et configurer la fonctionnalité de rapport d’état EDI-AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf125919-80ab-4cb8-b1f5-0f2616cc6f5c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 334e77ed58d460aea3ca37f73c1165d62da0f10b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="to-enable-status-reporting-run-39biztalk-server-configuration39-and-configure-edi-as2-status-reporting-feature"></a>Pour activer le rapport d’état, exécuter &#39; Configuration de BizTalk Server &#39; et configurer la fonctionnalité de rapport d’état EDI-AS2
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|0|  
|Texte du message|Pour activer la création de rapports d'état, exécutez la configuration de BizTalk Server et configurez la fonctionnalité de création de rapports d'état EDI/AS2.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que la création de rapports d'état EDI/AS2 ne fonctionne pas car cette fonctionnalité n'a pas été configurée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
1.  Exécutez l'Assistant Configuration de BizTalk Server. Cliquez sur le nœud Moteur d'exécution EDI/AS2 BizTalk, puis activez la propriété « Activer le rapport d'état EDI/AS2 BizTalk pour ce groupe BizTalk ». Vous devez configurer l'analyse BAM afin de configurer la création de rapports d'état EDI/AS2.  
  
2.  Dans la console Administration de BizTalk Server, activez la création de rapports d'état EDI pour le tiers en cliquant sur la propriété « Activer la création de rapports EDI » dans la page Général de la boîte de dialogue Propriétés EDI. Activez la création de rapports d'état AS2 pour le tiers en cliquant sur la propriété « Activer la création de rapports AS2 » dans la page Général de la boîte de dialogue Propriétés AS2. Vous devez redémarrer le service BizTalk après l'activation de la création de rapports d'état EDI ou AS2.