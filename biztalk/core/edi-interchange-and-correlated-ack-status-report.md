---
title: "Échange EDI et état ACK corrélé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a112cc3d-d34c-4652-a8ee-3355a31d4a03
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5f4268badf9907eb90b090abe34a8355b3ab8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-interchange-and-correlated-ack-status-report"></a>Rapport d'échange EDI et d'état de l'accusé de réception corrélé
Ce rapport affiche les échanges EDI traités par les pipelines d'envoi et de réception EDI, ainsi que les accusés de réception corrélés à ces échanges.  
  
## <a name="fields-in-the-status-report"></a>Champs du rapport État  
 Le rapport Échange EDI et état ACK corrélé indique les informations suivantes relatives aux échanges reçus ou envoyés et aux accusés de réception qui leur sont corrélés :  
  
-   Tiers expéditeur  
  
    > [!NOTE]
    >  Le tiers expéditeur est déterminé comme suit :  
    >   
    >  -   Si le nom du tiers dans l'échange correspond au nom configuré dans les propriétés EDI d'un tiers, le nom configuré s'affiche.  
    > -   Si le nom du tiers dans l'échange ne correspond à aucune des propriétés EDI configurées pour les tiers existants, le nom du tiers spécifié dans l'échange s'affiche.  
  
-   Tiers récepteur  
  
    > [!NOTE]
    >  Le nom du tiers récepteur est déterminé comme suit :  
    >   
    >  -   Si le nom du tiers dans l'échange correspond au nom configuré dans les propriétés EDI d'un tiers, le nom configuré s'affiche.  
    > -   Si le nom du tiers dans l'échange ne correspond à aucune des propriétés EDI configurées pour les tiers existants, le nom du tiers spécifié dans l'échange s'affiche.  
  
-   ID de contrôle  
  
-   Sens  
  
-   date/heure de l'échange ;  
  
-   Type de codage EDI  
  
-   État de l'échange  
  
-   Nombre de groupes  
  
-   ID de port  
  
-   Alias du tiers expéditeur  
  
-   Alias du tiers récepteur  
  
-   ID de corrélation du document informatisé  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>Champs de l'expression de requête du rapport d'état  
 Vous pouvez personnaliser le rapport Échange EDI et état ACK corrélé en modifiant les champs de l'expression de requête qui détermine les données affichées. Les champs suivants sont disponibles :  
  
|||||  
|-|-|-|-|  
|Champ de l'expression de requête|Opérateurs potentiels|Valeurs potentielles|Inclus par défaut ?|  
|Rechercher|Égal à|État de l'échange/de l'accusé de réception|Oui (requis)|  
|État|Égal à<br /><br /> Différent de|Accepté<br /><br /> Accepté avec erreurs<br /><br /> Envoyé<br /><br /> Tous<br /><br /> Accusé de réception attendu<br /><br /> Accusé de réception non attendu<br /><br /> Rejeté<br /><br /> (Ces valeurs sont définies ci-dessous.)|Oui|  
|date/heure de l'échange ;|Inférieur ou égal à<br /><br /> Supérieur ou égal à|Date/heure spécifique<br /><br /> aujourd'hui<br /><br /> Aujourd'hui - 1|Oui<br /><br /> Remarque : peut être inclus plusieurs fois dans l'expression de requête.|  
|Résultats (nb maximal)|Égal à|Entier (valeur par défaut 50)|Oui|  
|ID de contrôle|Égal à|ID de contrôle de l'échange|Non|  
|Sens|Égal à|Tous (par défaut)<br /><br /> Recevoir<br /><br /> Send|Non|  
|Tiers récepteur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Non|  
|Tiers expéditeur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Non|  
  
## <a name="status-definitions"></a>Définitions d'état  
 Les valeurs d'état utilisées dans les rapports d'état EDI ont les définitions suivantes :  
  
-   Accepté : échange valide.  
  
-   Accepté avec erreurs : des erreurs ont été notées dans les segments.  
  
-   Envoyé : l'échange a été envoyé avec succès.  
  
-   Tout : affiche un message avec toute autre valeur.  
  
-   Accusé de réception attendu  
  
    > [!NOTE]
    >  Le champ État de l'échange dans le rapport d'état État de l'échange et détails de l'accusé de réception sera défini à Accusé de réception attendu pour un message sortant lorsque le message est envoyé si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attend un accusé de réception technique. Cela se produit si le **TA1 attendu** propriété est définie dans **accusés de réception** page d’onglet d’accord unidirectionnel. L'état passe à Accepté lorsque l'accusé de réception technique est reçu et validé. Notez que cela se produit uniquement pour un accusé de réception technique, et non pas pour un accusé de réception fonctionnel.  
  
-   Accusé de réception non attendu  
  
-   Rejeté : l'échange n'est pas valide en raison d'erreurs.  
  
## <a name="additional-reports-displayed-from-this-report"></a>Rapports supplémentaires affichés à partir de ce rapport  
 Vous pouvez afficher les rapports d'état supplémentaires suivants pour un document informatisé affiché dans le rapport Détails du document informatisé. Pour accéder aux rapports, cliquez avec le bouton droit sur un échange ou un accusé de réception figurant dans le rapport Échange EDI et état ACK corrélé, puis cliquez sur la commande appropriée :  
  
-   [État de l’échange et rapport d’état de détails de l’accusé de réception](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [Rapport d’état détails transaction](../core/transaction-set-details-status-report.md)  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [État de l’échange et rapport d’état de détails de l’accusé de réception](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [Rapport d’état détails transaction](../core/transaction-set-details-status-report.md)  
  
-   [Rapport d’état du contenu du Message EDI](../core/edi-message-content-status-report.md)  
  
