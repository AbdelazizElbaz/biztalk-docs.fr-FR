---
title: "Rapport d’état détails transactions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d81367c7-c74e-42cb-b856-748962b727ec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6da167ea995fa05d8e35807d8cf26f23b5444a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-details-status-report"></a>Rapport d'état Détails du document informatisé
Ce rapport présente de manière détaillée le contenu des documents informatisés d'un échange EDI spécifique sélectionné à partir du rapport État de l'échange/de l'accusé de réception. Pour afficher ce rapport d’état, cliquez sur un échange répertorié dans le volet de résultats de requête du rapport d’état de l’échange/accusé de réception, puis cliquez sur **détails du document informatisé**.  
  
 Ce rapport est disponible uniquement si vous avez sélectionné le **stocker les transactions/données utiles pour les rapports** propriété dans la Général Page de la boîte de dialogue Propriétés EDI pour le tiers associé.  
  
## <a name="fields-in-the-status-report"></a>Champs du rapport État  
 Le Rapport État détaillé du document informatisé affiche les informations suivantes pour les documents informatisés dans les échanges reçus ou envoyés :  
  
-   ID du jeu de transactions  
  
-   Type de document  
  
-   Alias du tiers expéditeur  
  
-   Expéditeur de l’application  
  
-   Alias du tiers récepteur  
  
-   Application réceptrice  
  
-   Sens  
  
-   Numéro de contrôle d’échange  
  
-   Numéro de contrôle du groupe  
  
-   Numéro de contrôle du document informatisé  
  
-   État du document informatisé  
  
-   Date/heure de l'échange (n'est pas affichée par défaut)  
  
    > [!NOTE]
    >  Pour les documents reçus, si la date spécifiée dans l'échange est au format AAMMJJ et que AA est supérieur ou égal à 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche l'année sous la forme 19AA. Si la date est antérieure à 75, l'année est affichée sous la forme 20AA.  
    >   
    >  Par exemple, si vous recevez un échange contenant la valeur 991113 dans ISA09, la date/heure de l'échange est affichée dans le rapport sous la forme 11/13/1999.  
  
-   Date/heure du traitement (n'est pas affichée par défaut)  
  
-   Date/heure du groupe (n'est pas affichée par défaut)  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>Champs de l'expression de requête du rapport d'état  
 Vous pouvez personnaliser le rapport Échange EDI et état ACK corrélé en modifiant les champs de l'expression de requête qui détermine les données affichées. Les champs suivants sont disponibles :  
  
|||||  
|-|-|-|-|  
|Champ de l'expression de requête|Opérateurs potentiels|Valeurs potentielles|Inclus par défaut ?|  
|Rechercher|Égal à|Détails du document informatisé|Oui (requis)|  
|date/heure de l'échange ;|Inférieur ou égal à<br /><br /> Supérieur ou égal à|Date/heure spécifique<br /><br /> aujourd'hui<br /><br /> Aujourd'hui - 1|Oui<br /><br /> Remarque : peut être inclus plusieurs fois dans l'expression de requête.|  
|Nom du tiers récepteur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Oui|  
|Nom du tiers expéditeur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Oui|  
|Sens|Égal à|Tous (par défaut)<br /><br /> Recevoir<br /><br /> Send|Oui|  
|ID de contrôle|Égal à|ID de contrôle de l'échange|Oui|  
|ID de corrélation du document informatisé|Égal à|Id de corrélation|Oui|  
|Résultats (nb maximal)|Égal à|Entier (valeur par défaut 50)|Oui|  
|État|Égal à<br /><br /> Différent de|Accepté<br /><br /> Accepté avec erreurs<br /><br /> Envoyé<br /><br /> Tous<br /><br /> Accusé de réception attendu<br /><br /> Accusé de réception non attendu<br /><br /> Rejeté|Non|  
|ID du document informatisé|Égal à|ID du document informatisé|Non|  
  
## <a name="additional-reports-displayed-from-this-report"></a>Rapports supplémentaires affichés à partir de ce rapport  
 Vous pouvez afficher les rapports d'état supplémentaires suivants pour un document informatisé affiché dans le rapport Détails du document informatisé :  
  
-   Rapport d'état sur le contenu d'un message. Pour accéder à ce rapport, cliquez avec le bouton droit sur un document informatisé dans les rapports détaillés, puis cliquez sur Afficher le contenu du document informatisé. Pour plus d’informations, consultez [rapport d’état EDI Message contenu](../core/edi-message-content-status-report.md).  
  
-   Rapport État de l'échange/de l'accusé de réception. Ce rapport utilise la même interface utilisateur que le [échange EDI et le rapport d’état ACK corrélé](../core/edi-interchange-and-correlated-ack-status-report.md) qui s’affiche pour les échanges multiples. La différence est que les données de ce rapport ne concernent que l'échange contenant ce document informatisé.  
  
