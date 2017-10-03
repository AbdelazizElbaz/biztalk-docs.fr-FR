---
title: "Envoi d’un accusé de réception EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a036d08-8a65-43ad-b72c-2a246d302792
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a47a3fbe13f4cf054b6114050b8777231c4b217
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-edi-acknowledgment"></a>Envoi d'un accusé de réception EDI
Les accusés de réception indiquent l'état de transmission du message EDI. Une fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a reçu un échange EDI, il renvoie un ou plusieurs accusés de réception à l'expéditeur d'un échange EDI, selon les accusés de réception activés.  
  
 En fonction du niveau de validation, les accusés de réception de message EDI se répartissent en deux types :  
  
-   A **accusé de réception technique** générée en raison de la validation de l’en-tête. L'accusé de réception technique indique l'état du traitement de l'en-tête et du code de fin d'un échange par le récepteur d'adresse.  
  
-   A **accusé de réception fonctionnel** générée en raison de la validation du corps. L'accusé de réception fonctionnel signale chaque erreur rencontrée lors du traitement du document reçu.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut renvoyer des accusés de réception techniques et fonctionnels en réponse à un échange unique. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] renvoie un seul accusé de réception technique par échange. Pour les échanges X12, il renvoie un accusé de réception fonctionnel par groupe reçu. Pour les échanges EDIFACT, il renvoie un accusé de réception fonctionnel par échange, quel que soit le nombre de groupes dans l'échange.  
  
## <a name="x12-acknowledgments"></a>Accusés de réception X12  
 **X12 accusé de réception technique**  
  
 Un accusé de réception TA1 positif est envoyé si l'en-tête ISA et le code de fin IEA d'un message X12 sont valides (indépendamment de tout autre contenu). Pour plus d’informations sur le contenu d’un accusé de réception TA1, consultez [X12 accusé de réception TA1](../core/x12-ta1-acknowledgment.md).  
  
 **X12 accusé de réception fonctionnel**  
  
 Un accusé de réception 997 sert à confirmer la réception d'un échange ou d'un groupe fonctionnel, à accepter ou refuser un ou plusieurs groupes fonctionnels ou une ou plusieurs documents et à vérifier ou signaler la conformité aux standard. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un échange avec plusieurs groupes, il renvoie un accusé de réception par groupe. Si un groupe contient plusieurs documents informatisés, l'accusé de réception pour ce groupe comporte plusieurs boucles AK2, une par document informatisé, selon qu'il convient de générer des boucles AK2 pour les documents informatisés acceptés. Pour plus d’informations sur le contenu d’un accusé de réception 997, consultez [X12 accusé de réception 997](../core/x12-997-acknowledgment.md).  
  
> [!NOTE]
>  Lorsque le pipeline de réception EDI crée le segment En-tête de groupe fonctionnel (GS) pour l'accusé de réception fonctionnel X12, les codes de l'expéditeur de l'application (GS02) et du récepteur de l'application (GS03) proviennent du groupe fonctionnel dont il est accusé réception. Cependant, GS02 sur le message entrant est mappé à GS03 sur l'accusé de réception et GS03 sur le message entrant est mappé à GS02 sur l'accusé de réception.  
  
## <a name="edifact-acknowledgments"></a>Accusés de réception EDIFACT  
 **Accusé de réception technique EDIFACT**  
  
 Pour EDIFACT, un accusé de réception technique distinct n'est pas utilisé, mais des sections de l'accusé de réception fonctionnel ou de l'accusé de réception CONTRL (voir ci-après) sont réutilisées pour l'accusé de réception. Il émule un accusé de réception technique.  
  
 Pour plus d’informations sur l’accusé de réception technique CONTRL, consultez [Message de CONTRL EDIFACT comme accusé de réception technique](../core/edifact-contrl-message-as-technical-acknowledgment.md).  
  
 **Accusé de réception fonctionnel EDIFACT**  
  
 Pour EDIFACT, l'accusé de réception fonctionnel CONTRL sert à confirmer la réception d'un échange, d'un groupe et d'un message reçus, à accepter ou refuser un échange, un groupe et un message reçus, et à répertorier toute erreur syntaxique ou fonctionnalité non prise en charge qu'ils pourraient contenir. L'accusé de réception CONTRL communique les résultats d'une vérification syntaxique de l'échange complet reçu.  
  
 Pour plus d’informations sur l’accusé de réception fonctionnel CONTRL, consultez [Message de CONTRL EDIFACT comme accusé de réception fonctionnel](../core/edifact-contrl-message-as-functional-acknowledgment.md).  
  
## <a name="when-an-acknowledgment-is-generated"></a>Lorsqu'un accusé de réception est généré  
 Le pipeline de réception EDI génère un accusé de réception si l'une des conditions suivantes est remplie :  
  
-   Un élément de données dans l'échange reçu demande l'accusé de réception. Pour les messages X12, le pipeline de réception génère un accusé de réception technique TA1 si l'élément de données ISA12 est défini sur 1. Pour les messages EDIFACT, le pipeline de réception génère un accusé de réception technique CONTRL si l'élément de données UNB9 est défini sur 2 et un accusé de réception fonctionnel CONTRL si l'élément de données UNB9 est défini sur 1.  
  
-   Une propriété d'accord demande l'accusé de réception. Pour les échanges de X12, ces propriétés sont les **TA1 attendu** et **997 attendu** propriétés dans le **accusés de réception** page d’onglets de l’accord bidirectionnel de la **Propriétés de l’accord** boîte de dialogue. Pour les échanges EDIFACT, ces propriétés sont les **réception du message (CONTRL) attendu** et **accusé de réception (CONTRL) attendu** dans les **accusés de réception** page de les onglets d’accord bidirectionnel de la **propriétés de l’accord** boîte de dialogue. Lorsque vous activez un type d'accusé de réception, vous pouvez également indiquer s'il convient de le traiter par lot.  
  
-   Une propriété globale demande l'accusé de réception lorsqu'aucun accord n'est déterminé pour l'échange. Ces propriétés sont les propriétés  
  
    -   **TA1 attendu** et **997 attendu** propriétés dans le **accusés de réception** page de l’onglet d’accord de la **X12 paramètres de secours** boîte de dialogue.  
  
    -   **Réception du message (CONTRL) attendu** et **accusé de réception (CONTRL) attendu** dans les **accusés de réception** page de l’onglet d’accord de la **EDIFACT secours Paramètres** boîte de dialogue.  
  
 Pour EDIFACT, le pipeline de réception EDI renvoie deux accusés de réception CONTRL distincts si un accusé de réception technique et un accusé de réception fonctionnel sont demandés. L'accusé de réception technique CONTRL inclut uniquement des informations de l'accusé de réception. L'accusé de réception fonctionnel CONTRL inclut des informations sur la réception et des informations de l'accusé de réception fonctionnel. Pour plus d’informations, consultez [accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment.md).  
  
## <a name="identifying-an-acknowledgment-with-a-control-number"></a>Identification d'un accusé de réception avec un nombre de contrôle  
 Chaque accusé de réception doit être identifié par un numéro de contrôle du document informatisé pour X12 (élément de données ST2) ou un numéro de référence du document informatisé pour EDIFACT (élément de données UNH1). Si un accord est configuré pour l'accusé de réception sortant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] définit le numéro de contrôle ou le numéro de référence du document informatisé sur la valeur définie pour l'accord, comme suit :  
  
-   **Pour X12 accusés de réception** – (**numéro de contrôle de l’accusé de réception (ST02)** propriété dans **paramètres d’hôte Local** Page (**paramètres du récepteur** section) de l’accord onglet **propriétés de l’accord** boîte de dialogue  
  
-   **Pour les accusés de réception EDIFACT** – (**numéro de contrôle de l’accusé de réception Edifact** propriété dans **paramètres d’hôte Local** Page (**paramètres du récepteur** section) de la onglet d’accord de **propriétés de l’accord** boîte de dialogue  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne détermine pas l’accord pour l’accusé de réception, il utilise les mêmes propriétés comme mentionnées précédemment mais disponibles sous l’onglet d’accord dans le **X12 paramètres de secours** ad **EDIFACT secours Paramètres** boîtes de dialogue. Ce paramétrage s'applique aux accusés de réception techniques et fonctionnels si les deux sont configurés. Cet entier est incrémenté d'une unité pour chaque accusé de réception ou échange généré.  
  
 L'enveloppe d'un accusé de réception est créée à partir des données du message reçu, selon le schéma de contrôle d'accusé de réception.  
  
## <a name="preparing-the-acknowledgment"></a>Préparation de l'accusé de réception  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée l'enveloppe pour un accusé de réception comme il crée une enveloppe pour un message, en examinant les définitions de l'en-tête de contrôle de l'échange et de l'en-tête de groupe fonctionnel. Pour plus d’informations, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
 Pour activer le routage sans problème de l'accusé de réception généré (TA1, 997 ou CONTRL), le Désassembleur EDI renseigne les propriétés `DestinationPartyReceiverQualifier`, `DestinationPartyReceiverIdentifier`, `DestinationPartySenderQualifier` et `DestinationPartySenderIdentifier` sur l'accusé de réception.  
  
## <a name="synchronous-and-asynchronous-acknowledgments"></a>Accusés de réception synchrones et asynchrones  
 Vous pouvez choisir d'envoyer des accusés de réception EDI de manière synchrone ou asynchrone. En mode synchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] route l'accusé de réception directement vers le pipeline d'envoi du port de réception requête-réponse bidirectionnel. En mode asynchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] route l'accusé de réception vers la base de données MessageBox et un port d'envoi s'abonne à ce message.  
  
 Pour spécifier que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie l’accusé de réception de façon synchrone, sélectionnez **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** dans les **paramètres d’hôte Local** page ( **Paramètres du récepteur** section) sous **paramètres de l’échange** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT). Si vous supprimez cette propriété, le pipeline d'envoi du port de réception bidirectionnel doit être configuré pour renvoyer un échange EDI.  
  
 Si un scénario utilise un port de réception requête-réponse et qu'un accusé de réception technique et un accusé de réception fonctionnel sont activés, l'accusé de réception technique est renvoyé de manière synchrone et l'accusé de réception fonctionnel, de manière asynchrone.  
  
 Lors de la réception d'un message EDIINT/AS2 via HTTP/HTTPS, si un MDN est envoyé en réponse à une charge EDI encapsulée dans un MIME (sur le même socket), alors un accusé de réception EDI n'est pas envoyé de manière synchrone. Si, dans ce cas le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** propriété est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ignore la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’accusé de réception EDI](../core/edi-acknowledgment-structure.md)   
 [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md)   
 [X12 accusé de réception TA1](../core/x12-ta1-acknowledgment.md)   
 [X12 accusé de réception 997](../core/x12-997-acknowledgment.md)   
 [Accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment.md)   
 [Message CONTRL EDIFACT comme accusé de réception technique](../core/edifact-contrl-message-as-technical-acknowledgment.md)   
 [Message CONTRL EDIFACT comme accusé de réception fonctionnel](../core/edifact-contrl-message-as-functional-acknowledgment.md)