---
title: "Données stockées pour les rapports d’état EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec66e4d7-2694-499f-a60c-2f80fe643e12
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3b84bf68e89478d4f3d82dfdaf47e38c0aef90b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-edi-status-reports"></a>Données stockées pour les rapports d'état EDI
Deux niveaux de création de rapports sont disponibles dans le rapport d’état EDI : le premier si les **activer la création de rapports** propriété est sélectionnée pour un accord et le deuxième si la **magasin transaction/données utiles reporting** propriété est sélectionnée pour un accord. Ces propriétés sont disponibles dans le **propriétés générales** page de la **général** onglet dans le **propriétés de l’accord** boîte de dialogue.  
  
## <a name="data-stored-if-edi-reporting-is-activated"></a>Les données sont stockées si la création de rapports EDI a été activée  
 Si le **activer la création de rapports** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve un enregistrement de tous les échanges envoyés ou reçus, les accusés de réception techniques et les accusés de réception fonctionnels.  
  
 Dans le cas d'un échange reçu, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les informations suivantes :  
  
-   Un enregistrement de tous les échanges reçus. C'est la première information qui s'affiche dans l'interface utilisateur du rapport d'état EDI.  
  
-   Un enregistrement de tous les documents informatisés contenus dans l'échange. Cela ne comprend pas tous les détails enregistrés lorsque le stockage des documents informatisés est activé.  
  
-   Un enregistrement de tous les accusés de réception techniques présents dans l'échange reçu.  
  
-   Un enregistrement de tous les accusés de réception fonctionnels présents dans l'échange reçu.  
  
    > [!NOTE]
    >  Si un échange comprend plusieurs groupes fonctionnels, plusieurs accusés de réception fonctionnels seront enregistrés dans l'interface utilisateur du rapport d'état. Toutefois, si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit des accusés de réception fonctionnels en double pour un groupe, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera uniquement le dernier accusé de réception fonctionnel dans l'interface utilisateur du rapport d'état.  
  
-   Si un accusé de réception technique doit être généré pour l'échange reçu  
  
-   Si des accusés de réception fonctionnels doivent être générés pour les documents informatisés reçus  
  
 Dans le cas d'un échange envoyé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les informations suivantes :  
  
-   Un enregistrement de l'échange envoyé  
  
-   Un enregistrement de tous les documents informatisés contenus dans l'échange  
  
-   Un enregistrement de tous les accusés de réception techniques présents dans l'échange envoyé  
  
-   Un enregistrement de tous les accusés de réception fonctionnels présents dans l'échange envoyé  
  
 L'interface utilisateur du rapport d'état EDI met en correspondance ces enregistrements pour afficher des informations complètes. Par exemple, si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un échange et qu'un accusé de réception technique et un accusé de réception fonctionnel doivent être envoyés à l'expéditeur du message d'origine, vous pouvez facilement retrouver cette information dans  l'interface utilisateur du rapport d'état.  
  
## <a name="data-stored-if-transaction-set-storage-is-enabled"></a>Les données sont stockées si le stockage des documents informatisés est activé  
 Si le **stocker la charge de message de création de rapports** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke les détails de tous les documents informatisés trouvés dans un échange envoyé ou reçu. Ce niveau de rapport d'état implémente tous les rapports de premier niveau exécutés si la création de rapports EDI est activée, en plus d'informations spécifiques aux documents informatisés. EDI pipeline de réception et envoi pipeline créent des entrées dans la base de données BAM pour chaque entrants et sortants groupe ou document informatisé (alors que le «**reporting de charge utile de message Store** propriété est sélectionnée). Si l'échange est rejeté, aucune entrée n'est créée.  
  
 Dans le cas d'un échange envoyé ou reçu, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les informations suivantes :  
  
-   Le contenu du document informatisé. Dans l'interface utilisateur du rapport d'état, vous pouvez consulter les documents informatisés contenus dans un échange, puis afficher le contenu réel du document informatisé.  
  
-   Informations plus détaillées sur un document informatisé, dont :  
  
|||  
|-|-|  
|Informations|Champ ou Valeur|  
|Application émettrice|(GS02 ou \<UNG2.1(UNG2.2) >|  
|Application réceptrice|GS03 ou \<ung3.1 (ung3.2) >|  
|GroupDate|GS04 ou UNG2.4|  
|GroupTime|GS05 ou UNG2.5|  
|TransactionSetId|ST01 ou UNH2.1 (chaîne)|  
|InterchangeControlNo|ISA13|  
|GroupControlNo|GS06|  
|BtsDocType|NameSpace + Nom du nœud racine|  
|TransactionSetControlID|ST02 ou UNH1|  
|TransactionSetStatus|Accepté, Accepté avec erreur ou Rejeté|  
|Sens|Envoi ou Réception|  
|BtsProcessingTime|Du côté réception : BTSReceiveTime (heure locale) tel que marqué dans le pipeline<br /><br /> Du côté envoi : BTSReceiveTime (heure locale) tel que marqué sur l'enveloppe par le composant ASM|  
|BTS.MessageId|Du côté réception : BTSMessageId extrait des propriétés du message<br /><br /> Du côté envoi :<br /><br /> Pour un document informatisé unique : BTSMessageId<br /><br /> Pour un lot sortant : TransactionSet BTSMessageId pour chaque message du lot (et non le BTSMessageId pour le message du lot) **Remarque :** stockage seulement – affichera pas dans l’interface utilisateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Données stockées pour les rapports d’état AS2 et EDI](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [Données stockées pour les rapports d’état de traitement par lot](../core/data-stored-for-batching-status-reports.md)   
 [Données stockées pour les rapports d’état AS2](../core/data-stored-for-as2-status-reports.md)