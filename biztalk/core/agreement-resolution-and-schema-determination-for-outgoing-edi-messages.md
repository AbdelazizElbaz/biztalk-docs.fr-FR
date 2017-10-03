---
title: "Résolution de l’accord et détermination du schéma pour les Messages EDI sortants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e37aeb9d-1e95-464d-bb71-73653c1d4674
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d33715d4f1683910269adf7b49965e31bce4840
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-and-schema-determination-for-outgoing-edi-messages"></a>Résolution de l'accord et détermination du schéma pour les messages EDI sortants
Pour générer un message EDI vers un partenaire commercial, le pipeline d'envoi EDI doit effectuer les opérations suivantes :  
  
-   déterminer l'accord correspondant au message ;  
  
-   déterminer le schéma à utiliser pour valider le message.  
  
## <a name="agreement-resolution"></a>Résolution de l'accord  
 Le pipeline d'envoi EDI effectue une recherche d'accord par le biais d'une série d'étapes pour déterminer s'il existe une correspondance entre l'échange sortant et les propriétés d'un accord. Une fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a déterminé l'accord, il identifie le schéma de document qui s'applique à l'échange (voir ci-après). Il utilise les propriétés associées à l'accord correspondant et le schéma pertinent pour générer et valider le message sortant.  
  
 Pour effectuer la résolution de l'accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] procède comme suit :  
  
1.  Résout l'accord en faisant correspondre la propriété de contexte AgreementPartIDForSend à l'ID de l'accord unidirectionnel. Cette propriété doit être un type entier. Vous pouvez la définir dans un composant personnalisé car elle n'est pas définie par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Si l'étape 1 échoue, résout l'accord en mettant en correspondance les trois propriétés de contexte suivantes avec les propriétés d'accord AgreementNameForSend, SenderPartyNameForSend, ReceiverPartyNameForSend. Notez que celles-ci doivent être définies de manière à être correctement associées à un accord. Vous pouvez les définir dans un composant personnalisé car elles ne sont pas définies par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Si l’étape 2 échoue, résout l’accord en faisant correspondre le nom du tiers dans les propriétés de contexte de message avec la propriété DestinationPartyName, qui est défini en tant que programme de résolution d’accord supplémentaire dans le **identificateurs** onglet de propriétés de l’accord.  
  
4.  En cas d'échec de l'étape 3, résout l'accord en mettant en correspondance les propriétés suivantes dans le contexte d'un message avec celles des propriétés d'accord DestinationPartySenderIdentifier, DestinationPartySenderQualifier, DestinationPartyReceiverIdentifier et DestinationPartyReceiverQualifier. Notez que les quatre propriétés doivent être définies afin de résoudre correctement à un accord. Ces propriétés peuvent être définies dans un composant personnalisé ; ils ne sont pas activés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d'informations, consultez les paragraphes ci-après.  
  
    > [!NOTE]
    >  Si l'un des ensembles de propriétés de contexte ci-dessus est promu et que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne parvient pas à trouver un accord associé à ces propriétés de contexte, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suspend le message.  
    >   
    >  Si l'utilisateur écrit intentionnellement un ensemble de propriétés de contexte à des fins de résolution d'accord et si le résolveur ne parvient pas à identifier OnewayAgreement, le message est suspendu. En cas d'échec de la résolution d'un accord en fonction d'un ensemble de propriétés de contexte, un message d'avertissement est généré dans EventLog.  
  
5.  Si l'étape 4 échoue ou qu'aucune des propriétés de contexte ci-dessus n'est promue, le message EDI est mappé à un accord en faisant correspondre le port d'envoi abonné au message au port d'envoi associé à un accord.  
  
    > [!NOTE]
    >  Si le même port d'envoi est associé à plusieurs accords, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère une erreur.  
  
6.  Si aucun accord n'est trouvé lors de l'étape 1, 2, 3 ou 4, le pipeline d'envoi utilise les paramètres d'accord de secours pour générer le message sortant.  
  
 **Résolution de l’accord en mettant en correspondance de l’expéditeur et récepteur les propriétés de contexte**  
  
 Dans l'étape 2 ci-dessus, les quatre propriétés de contexte utilisées dans la correspondance sont les suivantes : EDI.DestinationPartySenderIdentifier, EDI.DestinationPartySenderQualifier, EDI.DestinationPartyReceiverIdentifier et EDI.DestinationPartyReceiverQualifier. L'espace de noms de ces propriétés de contexte est `http://schemas.microsoft.com/Edi/PropertySchema`. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]tente de faire correspondre ces valeurs avec l’expéditeur connexe et les identificateurs du récepteur et les qualificateurs dans les propriétés d’accord unidirectionnel. Pour X12, ces champs sont ISA05, ISA06, ISA07 et ISA08 dans le **identificateurs** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue ; pour EDIFACT, ces champs sont UNB2.1, UNB2.2, UNB3.1 et UNB3.2 dans les **identificateurs** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
 Pour activer la résolution d'accord côté envoi à l'aide des quatre qualificateurs et identificateurs de l'expéditeur et du récepteur, vous devez définir les quatre propriétés de contexte afin d'identifier l'accord de manière unique. L'utilisation de cette méthode de recherche d'accord offre une flexibilité accrue dans le cadre du traitement côté envoi. Par exemple, elle peut vous éviter de créer plusieurs ports d'envoi sous certaines circonstances et de faire appel à des filtres de port d'envoi complexes. Elle vous évite également de devoir définir la propriété OneWayAgreementId (le cas échéant).  
  
 Si les quatre propriétés de contexte ont été définies pour un message et qu'aucune correspondance n'est trouvée entre celles-ci et les propriétés de propriété, le message est suspendu. L'accord est résolu à l'aide du port d'envoi associé à l'accord uniquement si aucune des quatre propriétés de contexte n'a été définie.  
  
> [!NOTE]
>  Un message du pipeline EDI est transmis à l'étape réussie de la résolution d'accord jusqu'à ce qu'il soit résolu et que l'accord soit activé dans l'étape. Par exemple, si le message est résolu dans la première étape de la résolution d'accord mais que l'accord est désactivé, le message est transmis à l'étape réussie à des fins de résolution.  
  
## <a name="schema-determination"></a>Détermination du schéma  
 Le pipeline d'envoi EDI détermine le schéma qui s'applique au message à partir des nom et espace de noms du schéma contenus dans le fichier XML intermédiaire de chaque document informatisé (soit en tant qu'informations de type de document soit dans le nœud racine).  
  
 Pour un échange conservé, le pipeline d'envoi utilise les informations de type de document des documents informatisés spécifiques du fichier XML intermédiaire pour l'échange complet. Il utilise les schémas de segment de contrôle pour le traitement des segments d'enveloppe.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages EDI dans BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)