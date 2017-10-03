---
title: "Données stockées pour les rapports d’état de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d55aa0e1-095f-434e-8530-f1a946ad4430
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db9831aafce56845fe7b75e91f5369a8860d8996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-batching-status-reports"></a>Données stockées pour des rapports d'état de traitement par lot
Lorsque le **activer la création de rapports** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke l’état de chaque instance de traitement par lot. Cette propriété est en disponible dans le **propriétés générales** page de la **général** onglet dans le **propriétés de l’accord** boîte de dialogue. Voici les différents états possibles :  
  
-   **Défini**: l’instance de lot est configurée. La date et l'heure d'activation du lot sont postérieures à la date et à l'heure actuelles. Tous les paramètres de lot sont définis, mais le lot n'est pas en cours d'exécution (il n'accepte pas de documents).  
  
-   **Active**: l’instance du lot a été activée et regroupe des documents informatisés. Vous pouvez voir le nombre de documents informatisés acceptés/rejetés.  
  
-   **Publié**: le lot remplies les critères de déclenchement et a été publié dans la MessageBox, mais n’a pas été publié par le pipeline d’envoi ou le lot a été interrompu avant le traitement des messages.  
  
-   **Terminé**: le lot a été envoyé par le pipeline EdiSend.  
  
 Si le lot a été envoyé via le pipeline EdiSend, vous pouvez mettre en corrélation l'enregistrement de lot de l'interface utilisateur et un enregistrement de l'échange Edi envoyé, puis afficher les détails des documents informatisés.  
  
> [!NOTE]
>  De multiples instances de lot peuvent avoir l'état Terminé pour une configuration de lot.  
  
 **Mise en corrélation un échange avec un lot**  
  
 L'activité BAM BusinessMessageJournal permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de mettre en corrélation un échange EDI reçu contenant des documents informatisés et un échange par lot sortant qui contient les mêmes documents informatisés. Pour plus d’informations sur la façon d’implémenter et utiliser ces informations de corrélation, consultez [corréler un document informatisé entrant avec un lot sortant](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Données stockées pour les rapports d’état AS2 et EDI](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [Données stockées pour les rapports d’état EDI](../core/data-stored-for-edi-status-reports.md)   
 [Données stockées pour les rapports d’état AS2](../core/data-stored-for-as2-status-reports.md)