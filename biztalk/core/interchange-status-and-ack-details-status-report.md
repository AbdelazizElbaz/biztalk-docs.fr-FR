---
title: "État de l’échange et rapport d’état de détails de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebba4af5-6dff-4bb8-9c63-739ef49bbbb8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cc596a99d1a49b01ccc417abccb73d12ed34ad5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interchange-status-and-ack-details-status-report"></a>État de l'échange et rapport Détails de l'accusé de réception
Ce rapport d'état affiche les détails d'un échange, de son accusé de réception d'échange corrélé (technique) et de ses accusés de réception fonctionnels. Afficher ce rapport pour le droit d’un échange dans le rapport d’état de l’échange/accusé de réception, puis en cliquant sur **détails de l’état et l’accusé de réception de l’échange**.  
  
 Ce rapport fournit les vues distinctes suivantes pour l'échange et les accusés de réception corrélés :  
  
## <a name="interchange-status"></a>État de l'échange  
 Cette vue inclut un tableau indiquant les valeurs des champs suivants :  
  
-   ID du tiers expéditeur  
  
-   ID du tiers récepteur  
  
-   ID de contrôle  
  
-   Nom du tiers récepteur  
  
-   Nom du tiers expéditeur  
  
-   Sens  
  
-   date/heure de l'échange ;  
  
    > [!NOTE]
    >  Pour les documents reçus, si la date spécifiée dans l'échange est au format AAMMJJ et que AA est supérieur ou égal à 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche l'année sous la forme 19AA. Si la date est antérieure à 75, l'année est affichée sous la forme 20AA.  
    >   
    >  Par exemple, si vous recevez un échange contenant la valeur 991113 dans ISA09, la date de l'échange est affichée dans le rapport sous la forme 11/13/1999.  
  
-   Nombre de groupes  
  
-   ID de port  
  
-   État de l'échange  
  
-   Type de codage EDI  
  
-   ID de corrélation du document informatisé  
  
 Si un accusé de réception technique est activé pour un tiers en tant que récepteur d'échanges (dans la page Traitement des accusés de réception et paramètres de validation de la boîte de dialogue Propriétés EDI), BizTalk Server attend qu'un accusé de réception technique (d'échange) soit renvoyé en réponse à un échange qu'il envoie. Lorsqu'il crée initialement une entrée d'état d'échange pour un échange sortant, il entre la valeur Accusé de réception attendu dans le champ État de l'échange. Lorsqu'il reçoit un accusé de réception technique et le met en corrélation avec l'échange d'origine, il met à jour le champ État de l'échange pour indiquer qu'il a reçu l'accusé de réception.  
  
## <a name="interchange-ack-status"></a>État de l'accusé de réception d'échange  
 Cette vue affiche les valeurs d'état pour un accusé de réception d'échange (technique) :  
  
-   ID de contrôle de l'échange d'accusé de réception  
  
-   Tiers récepteur  
  
-   Tiers expéditeur  
  
-   Sens  
  
-   Date de l'échange d'accusé de réception  
  
-   Heure de l'échange d'accusé de réception  
  
-   État de l'accusé de réception  
  
-   Code de l'état  
  
-   Code d'accusé de réception 1  
  
-   Code d'accusé de réception 2  
  
## <a name="functional-acks"></a>Ack(s) fonctionnel  
 Cette vue affiche les valeurs d'état d'un accusé de réception fonctionnel :  
  
-   Numéro de contrôle du groupe  
  
-   Tiers récepteur  
  
-   Tiers expéditeur  
  
-   Sens  
  
-   État  
  
-   Code de l'état  
  
-   Code de l'ID fonctionnel  
  
-   Nombre de segments TS  
  
-   ID de contrôle de l'échange d'accusé de réception  
  
-   Date de l'échange d'accusé de réception  
  
-   Heure de l'échange d'accusé de réception  
  
-   Nombre de segments TS transmis  
  
-   Nombre de segments TS acceptés  
  
-   ErrorCode 1  
  
-   Code d’erreur 2  
  
-   Code d’erreur 3  
  
-   Code d’erreur 4  
  
-   Code d’erreur 5  
  
-   Heure de réception