---
title: "Stockage des données des Messages EDI entrants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8cbcb96-c0af-4f41-b844-f0e684a4af7c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60cc8743cd945ad231f3a42f9cbd4f0e76b418d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-data-is-stored-for-inbound-edi-messages"></a>Stockage des données des messages EDI entrants
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue les opérations suivantes pour générer une entrée de rapport d'état pour un échange entrant et l'accusé de réception envoyé en réponse :  
  
1.  Lorsque le pipeline de réception EDI envoie un message entrant au format XML à la base de données MessageBox, il crée les entrées suivantes dans le magasin de données de création de rapports d'état avec les valeurs suivantes :  
  
    -   une entrée de rapport d'état pour chaque échange reçu, avec l'état défini sur Accepté/Partiellement accepté/Rejeté ;  
  
    -   une entrée de rapport d'état pour chaque accusé de réception (d'échange) technique : un par échange, avec l'état défini sur Généré ;  
  
    -   une entrée de rapport d'état pour chaque accusé de réception fonctionnel : un par groupe dans X12 et un pour tous les groupes dans EDIFACT, avec l'état défini sur Généré.  
  
2.  Une fois que le pipeline d'envoi EDI a envoyé les accusés de réception au partenaire commercial, il met à jour les entrées relatives à l'état des accusés de réception d'échange et fonctionnels en les définissant sur Envoyé. Aucune modification n'est apportée à l'entrée relative à l'état de l'échange.  
  
## <a name="data-stored-by-the-receive-pipeline-for-inbound-interchanges"></a>Données stockées par le pipeline de réception pour les échanges entrants  
 Le pipeline de réception crée un enregistrement dans le magasin de données de création de rapports d'état pour chaque échange reçu. Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'échange  
  
-   Direction de l'échange = réception  
  
-   Récepteur de l'échange = données mises à jour  
  
-   Expéditeur de l'échange = données mises à jour  
  
-   Date de l'échange = données mises à jour  
  
-   Heure de l'échange = données mises à jour  
  
-   ID de contrôle de l'échange = données mises à jour  
  
-   État de l'échange = Données de mise à jour  
  
-   Nombre de groupes d'un échange = données mises à jour (dans EDIFACT, les groupes sont facultatifs ; s'ils sont absents, la valeur définie est Non applicable)  
  
-   ID du port de réception de l'échange = données mises à jour  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-technical-acknowledgment-generated-in-response-to-an-inbound-interchange"></a>Données stockées par le pipeline de réception pour chaque accusé de réception technique généré en réponse à un échange entrant  
 Le pipeline d'envoi crée un enregistrement dans le magasin de données de création de rapports d'état pour chaque accusé de réception technique envoyé. L'accusé de réception technique est TA1 pour X12 et le message CONTRL avec uniquement le segment UCI pour EDIFACT. La plupart des données requises pour l'entrée sont disponibles dans les segments de code de fin et d'en-tête de l'échange (ISA/IEA ou UNB/UNZ). Les autres données sont disponibles dans les propriétés du port d'envoi. Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'échange/de l'accusé de réception  
  
-   Direction de l'accusé de réception d'échange = réception  
  
-   Récepteur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Expéditeur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Date de l'échange = données mises à jour  
  
-   ID de contrôle de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   État de l’accusé de réception de l’échange = \< attendu ou non Applicable >. Si l'accusé de réception technique est configuré ou qu'une valeur lui est attribuée dans l'échange entrant, l'état est défini sur Attendu. Sinon, il est défini sur Non applicable.  
  
-   ID de contrôle de l’accusé de réception de l’échange = \<aucune valeur >  
  
-   Date de l’accusé de réception de l’échange = \<aucune valeur >  
  
-   Heure de l’accusé de réception de l’échange = \<aucune valeur >  
  
-   L’accusé de réception/Code d’Action = \<aucune valeur >  
  
-   Code de Note de l’accusé de réception = \<aucune valeur >  
  
## <a name="data-updated-by-the-send-pipeline-for-each-technical-acknowledgment-generated-in-response-to-inbound-interchanges"></a>Données mises à jour par le pipeline d'envoi pour chaque accusé de réception technique généré en réponse aux échanges entrants  
 Pour chaque accusé de réception technique qu'il envoie, le pipeline d'envoi met à jour l'entrée de rapport d'état pour chaque échange reçu corrélé. La source des données sont les enveloppes d'échange créées par le pipeline d'envoi.  
  
 L'Assembleur EDI recherche les enregistrements dans le magasin de données à l'aide des données des segments UCI et TA1 de l'accusé de réception entrant, comme suit :  
  
|Champs de l'accusé de réception|Champs du magasin de données|Commentaire|  
|-------------------|--------------------------|-------------|  
|ID de l'expéditeur de l'échange|Récepteur de l'échange|-|  
|ID du récepteur de l'échange|Expéditeur de l'échange|-|  
|-|Date de l'échange|-|  
|Numéro de contrôle d’échange|ID de contrôle de l'échange|-|  
|-|Direction de l'échange = réception|Requis dans les scénarios incluant des échanges conservés à des fins d'unicité|  
|Type d'enregistrement|État de l’accusé de réception de l’échange|-|  
  
 Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'échange/de l'accusé de réception  
  
-   Direction de l'accusé de réception d'échange = envoi - données existantes  
  
-   État de l'échange/de l'accusé de réception = Traité ou Envoyé - Données mises à jour  
  
-   Récepteur de l'échange = données existantes  
  
-   Expéditeur de l'échange = données existantes  
  
-   Date de l'échange = données existantes  
  
-   ID de contrôle de l'échange = données existantes  
  
-   ID de contrôle de l'accusé de réception de l'échange = données mises à jour  
  
-   Date de l'accusé de réception de l'échange = données mises à jour  
  
-   Heure de l'accusé de réception de l'échange = données mises à jour  
  
-   Accusé de réception/code d'action = données existantes  
  
-   Code de note de l'accusé de réception = données existantes  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-functional-acknowledgment-generated-in-response-to-an-inbound-interchange"></a>Données stockées par le pipeline de réception pour chaque accusé de réception fonctionnel généré en réponse à un échange entrant  
 Le pipeline d'envoi crée un enregistrement dans le magasin de données de création de rapports d'état pour chaque accusé de réception fonctionnel envoyé. Le pipeline d'envoi crée un enregistrement de chaque accusé de réception fonctionnel envoyé (en réponse à un échange reçu) dans le magasin de données de création de rapports d'état. Si aucun groupe n'est présent dans EDIFACT, un seul accusé de réception fonctionnel est créé. L'entrée de rapport d'état de l'accusé de réception fonctionnel est renseignée à partir du code de fin et de l'en-tête du groupe fonctionnel (GS/GE ou UNG/UNE). L'accusé de réception technique est 997 pour X12 et le message CONTRL complet pour EDIFACT. Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'accusé de réception fonctionnel  
  
-   Direction de l'accusé de réception fonctionnel = réception  
  
-   État de l’accusé de réception fonctionnel = \< attendu ou non Applicable >. Si l'onglet d'accusé de réception fonctionnel dans le Gestionnaire d'accords partenaires est sélectionné, l'état est défini sur Attendu. Dans le cas contraire, l’état est défini à non Applicable.  
  
-   Récepteur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Expéditeur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Date de l'échange = données mises à jour  
  
-   ID de contrôle de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Numéro de contrôle du groupe = données mises à jour (requises à des fins de corrélation. Dans EDIFACT, si aucun segment de groupe n'est présent, ce champ est renseigné à l'aide de UNH.1)  
  
-   Code de l'ID fonctionnel = données mises à jour (aucune valeur dans EDIFACT si aucun groupe n'est présent)  
  
-   Nombre de documents informatisés = données (dans EDIFACT, ceci est mappé à UNE.1 si des segments UNG/UNE sont présents ou à UNZ.1 si aucun segment de groupe n'est présent)  
  
-   ID de contrôle de l’échange de l’accusé de réception fonctionnel = \<aucune valeur >  
  
-   Date de l’échange de l’accusé de réception fonctionnel = \<aucune valeur >  
  
-   Heure de l’échange des accusés de réception fonctionnel = \<aucune valeur >  
  
-   Nombre de documents informatisés remis = \<aucune valeur >  
  
-   Nombre de documents informatisés acceptés = \<aucune valeur >  
  
-   L’accusé de réception/Code d’Action = \<aucune valeur >  
  
-   Syntaxe de l’erreur/Code d’erreur = \<aucune valeur >  
  
-   X12 supplémentaires Code d’erreur l’accusé de réception 2 = \<aucune valeur >  
  
-   X12 supplémentaires l’accusé de réception Code d’erreur 3 = \<aucune valeur >  
  
-   X12 supplémentaires l’accusé de réception Code d’erreur 4 = \<aucune valeur >  
  
-   X12 supplémentaires l’accusé de réception Code d’erreur 5 = \<aucune valeur >  
  
## <a name="data-updated-by-the-send-pipeline-for-each-functional-acknowledgment-generated-in-response-to-inbound-interchanges"></a>Données mises à jour par le pipeline d'envoi pour chaque accusé de réception fonctionnel généré en réponse aux échanges entrants  
 Pour chaque accusé de réception fonctionnel qu'il envoie, le pipeline d'envoi met à jour l'entrée de rapport d'état pour chaque échange reçu corrélé. La source des données sont les enveloppes d'échange créées par le pipeline d'envoi.  
  
 L'Assembleur EDI recherche les enregistrements dans le magasin de données à l'aide des données de l'échange et des segments de l'en-tête de groupe de l'accusé de réception entrant, comme suit :  
  
|Champs de l'accusé de réception|Champs du magasin de données|Commentaire|  
|-------------------|--------------------------|-------------|  
|ID de l'expéditeur de l'échange|Récepteur de l'échange|-|  
|ID du récepteur de l'échange|Expéditeur de l'échange|-|  
|Date de l'échange|Date de l'échange|-|  
|Numéro de contrôle d’échange|ID de contrôle de l'échange|-|  
|Numéro de contrôle du groupe|Numéro de contrôle du groupe|Facultatif dans EDIFACT|  
|-|Direction de l'échange = réception|Requis dans les scénarios incluant des échanges conservés à des fins d'unicité|  
|Type d'enregistrement|État de l'accusé de réception fonctionnel|-|  
  
 Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'accusé de réception fonctionnel  
  
-   Direction de l'accusé de réception fonctionnel = envoi - données existantes  
  
-   État de l'accusé de réception fonctionnel = Envoyé/Traité - Données mises à jour  
  
-   Récepteur de l’échange = données existantes  
  
-   Expéditeur de l'échange = données existantes  
  
-   Date de l'échange = données existantes  
  
-   ID de contrôle de l'échange = données existantes  
  
-   Numéro de contrôle du groupe = données existantes  
  
-   Code de l'ID fonctionnel = données existantes  
  
-   Nombre de documents informatisés = données existantes  
  
-   Accusé de réception fonctionnel pour l'ID de contrôle de l'échange = données mises à jour  
  
-   Accusé de réception fonctionnel pour la date de l'échange = données mises à jour  
  
-   Accusé de réception fonctionnel pour l'heure de l'échange = données mises à jour  
  
-   Nombre de documents informatisés reçus = données existantes  
  
-   Nombre de documents informatisés acceptés = données existantes  
  
-   Accusé de réception/code d'action = données existantes  
  
-   Erreur/code d'erreur de syntaxe = données existantes  
  
-   Code d'erreur 2 de l'accusé de réception X12 supplémentaire = données existantes  
  
-   X12 supplémentaires Code d’erreur de l’accusé de réception 3 = données existantes  
  
-   X12 supplémentaires Code d’erreur de l’accusé de réception 4 = données existantes  
  
-   X12 supplémentaires Code d’erreur de l’accusé de réception 5 = données existantes  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage des données pour les rapports d’état AS2 et EDI](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [Stockage des données pour les Messages EDI sortants](../core/how-data-is-stored-for-outbound-edi-messages.md)