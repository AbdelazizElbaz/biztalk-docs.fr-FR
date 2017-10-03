---
title: Le traitement EDI dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdc60423-24b6-4920-a870-520f575085ed
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a91afb8542284b5c83b19886a417350aebbc0ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-processing-in-biztalk-server"></a>Traitement EDI dans BizTalk Server
Cette rubrique offre un aperçu du traitement des messages EDI côté réception et côté envoi et décrit l'application de la messagerie EDI grâce aux accords de partenariat commercial.  
  
## <a name="trading-partner-agreements-for-edi-processing"></a>Accords de partenariat commercial pour le traitement EDI  
 Ce type d'accord joue un rôle important dans la prise en charge EDI dans [!INCLUDE[prague](../includes/prague-md.md)]. La plupart des fonctions de configuration et d'administration liées au traitement EDI dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont exécutées via la configuration des accords de partenariat commercial entre des profils commerciaux. Les accords combinent les propriétés de traitement des messages bidirectionnelles à partir des profils commerciaux spécifiques des deux partenaires. Les accords reposent sur les paramètres de protocole définis pour chaque profil commercial. Un accord de partenariat commercial entre deux profils commerciaux est appliqué via la définition des propriétés des profils commerciaux impliqués dans l'échange de messages. Les propriétés des profils commerciaux sont définies sous la forme d'un récepteur des échanges et d'un expéditeur des échanges. Pour traiter un message entrant ou générer un message sortant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit connaître l'accord en vertu duquel est effectuée la résolution, et le schéma qui s'applique au message. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'arrive pas à déterminer l'accord, il utilisera les propriétés définies dans l'interface TPM pour l'accord de partenariat commercial de secours.  
  
 Il existe deux ensembles principaux de paramètres du protocole de codage dans TPM : un pour les propriétés EDIFACT et un pour les propriétés X12. Les deux ensembles de propriétés fonctionnent en parallèle. Pour plus d’informations sur les paramètres de protocole, consultez [paramètres de protocole](../core/protocol-settings.md). Pour plus d’informations sur les contrats, consultez [accord de partenariat commercial](../core/trading-partner-agreement.md). Vous définissez les paramètres de protocole et l'accord de partenariat commercial dans l'interface utilisateur de gestion des partenaires commerciaux (GPC). Les écrans du module de plateforme sécurisée se trouvent dans le **Parties** nœud de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Il n'est pas nécessaire d'être un développeur pour configurer le traitement EDI dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour plus d’informations sur les accords de partenariat commercial comment lors du traitement EDI, consultez [rôle des accords dans le traitement EDI](../core/the-role-of-agreements-in-edi-processing.md).  
  
## <a name="edi-receive-side-processing"></a>Traitement EDI côté réception  
 Les messages EDI reçus par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont traités via le pipeline de réception EDI. Le pipeline de réception effectue les opérations de gestion de base suivantes :  
  
-   recherche de l'accord de partenariat commercial et détermination du schéma.  
  
    > [!NOTE]
    >  Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les définitions de tiers incluaient également la définition d'accord. Dans le cadre de la recherche des propriétés d'un tiers, le pipeline de réception effectuait une recherche interne de la définition d'accord au sein de la définition de tiers, puis traitait les messages en conséquence. Dans [!INCLUDE[prague](../includes/prague-md.md)], le tiers (ou partenaire commercial) étant distinct de l'accord de partenariat commercial, le pipeline de réception recherche spécifiquement l'accord de partenariat commercial.  
  
    > [!NOTE]
    >  Si tous les accords en fonction desquels un message effectue la résolution sont désactivés, le message sera suspendu. Un événement est également consigné dans le journal des événements.  
  
-   Si un message EDI unique contient plusieurs échanges, divise les échanges et traite chaque échange séparément (si activé). Pour plus d’informations, consultez [l’activation de la réception de plusieurs échanges dans un seul Message](../core/enabling-the-receiving-of-multiple-interchanges-in-a-single-message.md).  
  
-   Analyse chaque échange EDI et convertit les données X12 ou EDIFACT en document XML.  
  
-   Valide l'enveloppe et son message selon les normes EDI, l'accord commercial et les schémas de message.  
  
-   Si l'échange est traité par lot, le fractionne, génère un fichier XML pour chaque document informatisé et promeut les propriétés nécessaires au traitement du lot, ou conserve l'échange.  
  
-   Génère un accusé de réception.  
  
-   Convertit l'enveloppe EDI en propriétés du contexte et promeut d'autres propriétés pour le traitement EDI.  
  
-   Promeut les propriétés qui contrôlent le traitement par lot. Ceci peut inclure l'envoi de documents informatisés non traités par lot à différents tiers.  
  
 Vous devez tenir compte des considérations suivantes dans le cadre de l'utilisation du traitement EDI côté réception :  
  
-   L'emplacement de réception peut utiliser n'importe quel type de transport.  
  
-   Pour plus d’informations sur le traitement EDI côté réception, consultez [comment BizTalk Server reçoit les Messages EDI](../core/how-biztalk-server-receives-edi-messages.md).  
  
-   Pour plus d’informations sur le traitement spécifique effectué par le désassembleur EDI dans le pipeline de réception, consultez [EDI désassembleur fonctionnement](../core/how-the-edi-disassembler-works.md).  
  
## <a name="edi-batch-processing"></a>Traitement par lot EDI  
 Si le message entrant est un lot, le pipeline de réception EDI fractionnera le lot en documents informatisés qui le composent, ou conservera l'échange traité par lot, en fonction de la configuration. Le pipeline EDIReceive utilise le composant de pipeline BatchMarker pour acheminer tous les échanges devant être traités par lot vers l'orchestration de traitement par lot ou l'orchestration de routage.  
  
 A l'issue du traitement côté réception, les documents informatisés qui doivent être traités par lot avant d'être envoyés seront traités par l'orchestration de traitement par lot. L'orchestration de traitement par lot créera un lot basé sur les critères de filtre, une plage d'activation et des critères de déclenchement.  
  
 Si les documents informatisés EDI doivent être envoyés vers des lots, ils seront traités par une orchestration de routage. Une copie du document informatisé sera créée pour chaque lot correspondant.  
  
 Pour plus d’informations sur le traitement spécifique effectué dans le traitement par lots, consultez [le traitement des lots entrants](../core/processing-incoming-batches.md) ou [le traitement par lot les Messages EDI sortants](../core/batching-outgoing-edi-messages.md).  
  
## <a name="edi-send-side-processing"></a>Traitement EDI côté envoi  
 Les messages EDI sortants générés et envoyés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont traités via le pipeline d'envoi EDI. Le pipeline d'envoi effectue les opérations de gestion de base suivantes :  
  
-   recherche de l'accord de partenariat commercial et détermination du schéma.  
  
    > [!NOTE]
    >  Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les définitions de tiers incluaient également la définition d'accord. Dans le cadre de la recherche des propriétés d'un tiers, le pipeline d'envoi effectuait une recherche interne de la définition d'accord au sein de la définition de tiers, puis traitait les messages en conséquence. Dans [!INCLUDE[prague](../includes/prague-md.md)], le tiers (ou partenaire commercial) étant distinct de l'accord de partenariat commercial, le pipeline d'envoi recherche spécifiquement l'accord de partenariat commercial.  
  
    > [!NOTE]
    >  Si tous les accords en fonction desquels un message effectue la résolution sont désactivés, le message sera suspendu.  Un événement est également consigné dans le journal des événements.  
  
-   Sérialise le message EDI et convertit le document XML en données X12 ou EDIFACT.  
  
-   Si les données du message contiennent des caractères également configurés comme des séparateurs X12, le pipeline d'envoi peut remplacer les caractères de la charge par un autre caractère.  
  
-   Si le message EDI est un échange traité par lot, le pipeline d'envoi récupère l'échange de BizTalk MessageBox après que l'orchestration de traitement par lot eut créé le traitement par lot.  
  
-   Valide le message sortant.  
  
-   Crée l'enveloppe EDI en fonction des propriétés des tiers ou des propriétés d'enveloppe EDI spécifiées lors de l'exécution.  
  
-   Traite les accusés de réception reçus.  
  
 Vous devez tenir compte des considérations suivantes dans le cadre de l'utilisation du traitement EDI côté envoi :  
  
-   Le port d'envoi peut utiliser n'importe quel type de transport.  
  
-   Pour plus d’informations sur le traitement EDI côté envoi, consultez [comment BizTalk Server envoie les Messages EDI](../core/how-biztalk-server-sends-edi-messages.md).  
  
-   Pour plus d’informations sur le traitement spécifique effectué dans le pipeline d’envoi, consultez [EDI assembleur fonctionnement](../core/how-the-edi-assembler-works.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge EDI dans BizTalk Server](../core/edi-support-in-biztalk-server1.md)   
 [Problèmes de prise en charge EDI](../core/edi-support-issues.md)   
 [Le rôle des accords dans le traitement EDI](../core/the-role-of-agreements-in-edi-processing.md)   
 [Réception des Messages EDI dans BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)   
 [Envoi des Messages EDI dans BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)   
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)