---
title: "AS2 Le Message et état MDN corrélé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48ed0ee3-c844-4cb9-a84d-32b719ab8fab
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ce4aed138f4e32e87cb1d428050999cc2b764a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-message-and-correlated-mdn-status-report"></a>Rapport Message AS2 et état MDN corrélé
Ce rapport affiche les messages AS2 traités par les pipelines d'envoi et de réception AS2, ainsi que les MDN corrélés à ces échanges.  
  
## <a name="fields-in-the-status-report"></a>Champs du rapport État  
 Le rapport Message AS2 et état ACK corrélé indique les informations suivantes relatives aux échanges reçus ou envoyés et aux accusés de réception qui leur sont corrélés :  
  
-   Nom du tiers expéditeur  
  
-   Nom du tiers récepteur  
  
-   AS2 From  
  
-   AS2 To  
  
-   ID du message AS2  
  
-   Date/heure du message AS2  
  
-   Date/heure de réception  
  
-   Rôle du tiers  
  
-   État du MDN  
  
-   État du chiffrement  
  
-   État de la signature  
  
-   État de l'échange EDI  
  
-   Est le Message AS2 en double  
  
-   Nombre de jours pendant lequel rechercher les doublons  
  
-   Nom du fichier  
  
-   Messagerie fiable activée  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>Champs de l'expression de requête du rapport d'état  
 Vous pouvez personnaliser le rapport Message AS2 et état ACK corrélé en modifiant les champs de l'expression de requête qui détermine les données affichées. Les champs suivants sont disponibles :  
  
|||||  
|-|-|-|-|  
|Champ de l'expression de requête|Opérateurs potentiels|Valeurs potentielles|Inclus par défaut ?|  
|Rechercher|Égal à|État AS2/MDN|Oui (requis)|  
|État du message|Égal à<br /><br /> Différent de|Tous<br /><br /> Accusé de réception - Traité<br /><br /> Accusé de réception - Échec<br /><br /> Traité - MDN en attente<br /><br /> Traité - MDN non attendu<br /><br /> Pas d'accusé de réception - Nombre de tentatives de renvoi dépassé<br /><br /> Pas d'accusé de réception - Délai dépassé pour les tentatives de renvoi|Oui|  
|Date/heure du message AS2|Inférieur ou égal à<br /><br /> Supérieur ou égal à|Date/heure spécifique<br /><br /> aujourd'hui<br /><br /> Aujourd'hui - 1|Oui<br /><br /> Remarque : peut être inclus plusieurs fois dans l'expression de requête.|  
|Résultats (nb maximal)|Égal à|Entier (valeur par défaut 50)|Oui|  
|ID du message AS2|Égal à|Tous<br /><br /> ID du message AS2 spécifique|Non|  
|Sens|Égal à|Tous (par défaut)<br /><br /> Recevoir<br /><br /> Send|Non|  
|Nom du tiers récepteur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Non|  
|Nom du tiers expéditeur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Non|  
  
## <a name="additional-as2-message-and-correlated-mdn-status-reports"></a>Autres rapports Message AS2 et état MDN corrélé  
 Cliquez avec le bouton droit sur un message AS2 répertorié dans le rapport Message AS2 et état MDN corrélé pour afficher un des rapports d'état plus détaillés :  
  
|Rapport d'état|État affiché|  
|-------------------|----------------------|  
|État de l'échange/de l'accusé de réception|État de la charge EDI du message AS2|  
|Détails de l'état des renvois|État des renvois du message|  
|Message au format câble|Format câble du message AS2|  
|Message décodé|Format décodé du message AS2|  
|Message MDN|Message MDN corrélé au message AS2|  
  
 Le format des trois derniers messages est identique. Pour plus d’informations, consultez [rapports d’état AS2 Message contenu](../core/as2-message-content-status-reports.md).  
  
## <a name="correlate-an-as2-message-with-its-edi-payload"></a>Mettre en corrélation un Message AS2 avec sa charge EDI  
 La création de rapports d'état AS2 et EDI permet de corréler les entrées d'état d'un message AS2 et sa charge EDI. Si vous avez activé la création de rapports d'état AS2 et EDI, une entrée d'état est consignée dans le rapport d'état AS2 pour le message AS2, de même que dans le rapport d'état pour la charge EDI de ce message AS2. Si vous avez affiché le rapport d’état AS2, vous pouvez afficher l’état de la charge EDI pour un message AS2 en double-cliquant sur l’entrée d’état de message AS2, puis en cliquant **état échange/ACK**. S'il n'y a qu'un seul échange EDI dans le message AS2, cette action indique l'entrée d'état pour cet échange.  
  
 Si le message AS2 contient plusieurs échanges EDI, et que vous essayez d’afficher l’état des échanges EDI dans le message AS2, le dernier échange EDI s’affichera dans le rapport d’état de l’échange/accusé de réception. En outre, le **N° de contrôle d’échange EDI** champ dans le rapport d’état AS2/MDN affiche uniquement le dernier numéro de contrôle d’échange. (Le numéro de contrôle de l'échange met en correspondance le message AS2 et sa charge d'échange EDI.)  
  
 Les données relatives aux échanges EDI dans un message AS2 sont enregistrées dans la base de données de création de rapports d'état. Vous pouvez afficher tous les échanges dans un message AS2 dans le rapport d’état de l’échange/accusé de réception si les **Control ID Equals All** clause est dans la requête de rapport d’état. Les autres échanges non inclus dans le message AS2 sont également affichés. Vous pouvez identifier les échanges EDI associés à un message AS2 spécifique en examinant les autres champs (Tiers expéditeur, Tiers récepteur et Date/heure de l'échange).  
  
 Le **rôle du tiers** champ dans le rapport d’état AS2 et le **Direction** champ dans le rapport d’état EDI sont opposé dans leur signification. Pour un message AS2 entrant avec une charge EDI, le **rôle du tiers** champ pour le message AS2 n’est **expéditeur**, tandis que la **Direction** champ pour l’échange EDI serait **Réception**. En effet, pour un message entrant reçu d'un tiers, celui-ci a le rôle d'expéditeur. Les propriétés de ce tiers lié à un message AS2 qu'il envoie sont celles d'un tiers en tant qu'expéditeur d'un message AS2, telles que définies dans la boîte de dialogue Propriétés AS2 de la gestion des accords de partenariat. Le rôle du tiers AS2 est donc opposé à la direction EDI.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [AS2 Rapports d’état du contenu du Message](../core/as2-message-content-status-reports.md)  
  
-   [Renvoyer le rapport Détails de l’état](../core/resend-status-details-report.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AS2 Le Message et état MDN corrélé](../core/as2-message-and-correlated-mdn-status-report.md)   
