---
title: "Configuration d’EDI et AS2 le rapport d’état | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c7fa76d-0d03-4b74-9a3a-60f4bd0534ff
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051a03b735f3714910b415d5418ff84089c57940
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-of-edi-and-as2-status-reporting"></a>Configuration de la création de rapports d'état EDI et AS2
Cette rubrique décrit l'activation des rapports d'état EDI et AS2, ainsi que la configuration des filtres de rapport d'état et des colonnes d'affichage pour les rapports d'état EDI, de traitement par lot et AS2.  
  
## <a name="enabling-status-reporting"></a>Activation des rapports d'état  
 Les rapports d'état EDI ne sont disponibles sur un serveur que si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les sous-systèmes EDI et BAM sont installés sur ce serveur. Les rapports d'état EDI/AS2 ne peuvent pas être activés si l'infrastructure BAM n'est pas installée. Le serveur doit également être membre du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de traitement EDI afin qu'il puisse accéder au magasin de données de rapports d'état EDI.  
  
 Entrées de messages EDI sont saisies pour les échanges tiers dans le rapport d’état de l’interface utilisateur si le **activer le rapport d’état** propriété est sélectionnée dans le **propriétés générales** page de la **général** onglet dans le **propriétés de l’accord** boîte de dialogue. Si le tiers envoyant ou en cours envoyé échanges n’est pas déterminé, entrées de messages EDI sont saisies pour ces échanges uniquement si le **création de rapports EDI d’activer** propriété est sélectionnée dans l’accord de secours pour X12 et EDIFACT. Cela s'applique au rapport Échange EDI et état ACK corrélé. Le rapport d’état du lot est activé uniquement si un accord a été déterminé et **activer le rapport d’état** propriété est sélectionnée dans **propriétés générales** page de la **général** onglet dans le **propriétés de l’accord** boîte de dialogue.  
  
 Documents informatisés seront stockées dans la base de données de suivi si le **stocker la charge de message de création de rapports** propriété est sélectionnée dans **propriétés générales** page de la **général** onglet dans le **propriétés de l’accord** boîte de dialogue ou **stocker les transactions/données utiles pour les rapports** propriété est définie dans les propriétés de l’accord de secours. Les rapports d'état de détails du document informatisé et de contenu du message ne sont disponibles que si cette propriété est sélectionnée.  
  
 Les entrées de messages AS2 seront saisies dans le rapport d’état de l’interface utilisateur si le **activer le rapport d’état** propriété est sélectionnée dans le **propriétés générales** page de la **général** onglet dans le  **Propriétés de l’accord** boîte de dialogue. Pour stocker le message AS2 ou MDN dans la base de données de non-répudiation, vous devez sélectionner la propriété appropriée dans le **expéditeur Non répudiation** ou **récepteur de non-répudiation** pages de l’accord AS2 unidirectionnel onglet dans le **propriétés de l’accord** boîte de dialogue. Ces propriétés activent le rapport Message AS2 et état MDN corrélé.  
  
 Le rapport d’état de messagerie fiable sera disponible si le **renvoyer le message AS2 si MDN non reçu** propriété est activée sur **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la **Propriétés de l’accord** boîte de dialogue.  
  
 Pour plus d’informations sur l’activation des rapports d’état, consultez [l’activation de rapports EDI et AS2 état](../core/enabling-edi-and-as2-status-reports.md).  
  
## <a name="status-report-filters-and-display-columns"></a>Filtres de rapport d'état et colonnes d'affichage  
 Les rapports d'état EDI et AS2 vous permettent de personnaliser la plage des données qui sont enregistrées pour le rapport d'état. Vous effectuez cette opération dans le **Hub du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Une fois que vous avez affiché le volet de rapport d'état pour l'un des rapports d'état, vous avez la possibilité de sélectionner la plage de données que vous souhaitez afficher dans le rapport. Pour ce faire, sélectionnez les valeurs de filtre à inclure dans l'expression de requête de rapport d'état.  
  
 Vous pouvez également personnaliser le type de données affichées dans le rapport d'état.  
  
> [!NOTE]
>  À chaque fois que les rapports d'état sont activés, tous les états seront enregistrés dans le stockage. En personnalisant l'expression de requête ou les colonnes d'état, vous définissez quelles données enregistrées sont affichées.  
  
 Pour plus d’informations, consultez [configuration d’un EDI et le rapport d’état AS2](../core/configuring-an-edi-and-as2-status-report.md).  
  
## <a name="see-also"></a>Voir aussi  
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)   
 [Échange EDI et état ACK corrélé](../core/edi-interchange-and-correlated-ack-status-report.md)   
 [Rapport état du lot](../core/batch-status-report.md)   
 [Rapport d’agrégation de l’échange](../core/interchange-aggregation-report.md)   
 [Rapport d’agrégation du document informatisé](../core/transaction-set-aggregation-report.md)   
 [AS2 Le Message et état MDN corrélé](../core/as2-message-and-correlated-mdn-status-report.md)