---
title: "Message CONTRL EDIFACT comme accusé de réception fonctionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d3c2be0-0993-4b2d-b6c3-286020117078
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923bc73e6ee778cbf960300902c7f631dc5d9f5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-contrl-message-as-functional-acknowledgment"></a>Message CONTRL EDIFACT comme accusé de réception fonctionnel
Si vous avez choisi de générer une notification de transactions opérationnelles dans les paramètres du profil d'entreprise ou dans l'accord de partenariat commercial (ou dans l'accord de secours si aucun accord n'a été défini entre les deux profils d'entreprise), ou si le champ UNB9 du message est défini sur « 1 », un message CONTRL est généré en tant que notification de transactions opérationnelles. Celle-ci signale les résultats de la vérification de la syntaxe effectuée sur l'échange.  
  
 La notification de transactions opérationnelles CONTRL inclut les segments suivants :  
  
-   L'en-tête de message UNH (obligatoire).  
  
-   Un segment UCI qui identifie l'échange de l'objet, qui indique la réception de l'état de l'échange et qui contient des références aux segments UNA, UNB et UNZ de l'échange reçu (obligatoire). Le segment UCI dispose d'une occurrence maximale de 1 ; par conséquent, il signale la première erreur rencontrée dans l'un des segments de contrôle.  
  
-   Un segment UCF identifiant un segment de groupe (encapsulé par l'en-tête UNG et le code de fin UNE) et indiquant la nature d'une erreur (obligatoire si le segment UNG existe).  
  
-   Un segment UCM identifiant un segment de message (encapsulé par l'en-tête UNH et le code de fin UNT) et indiquant la nature d'une erreur (obligatoire).  
  
-   Un segment UCS identifiant un document informatisé et indiquant la nature d'une erreur (obligatoire).  
  
-   Un segment UCD identifiant un élément de données composites erroné et indiquant la nature d'une erreur (facultatif).  
  
-   Le code de fin UNT (obligatoire).  
  
 Lorsqu'une notification de transactions opérationnelles CONTRL reçue contient uniquement les segments UNH, UCI et UNT, le pipeline EDIReceive traite la notification comme un accusé de réception CONTRL (technique).  
  
 Chaque instance d'un segment d'un niveau de rapport (par exemple, les segments UCI, UCF, UCM, UCS et UCD) ne peut signaler qu'une seule erreur.  
  
> [!NOTE]
>  Le message CONTRL contient plusieurs éléments de données obligatoires qui sont copiés à partir de l'échange reçu. Lorsqu'un élément de données de l'échange est manquant ou syntaxiquement non valide, un message CONTRL valide au niveau de la syntaxe ne peut pas être généré. L'erreur doit alors être signalée autrement que par le biais d'un message CONTRL.  
  
> [!NOTE]
>  Dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], un message CONTRL (accusé de réception, acceptation ou rejet) est envoyé en réponse à un échange reçu contenant un seul ou plusieurs messages CONTRL. En revanche, dans [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)], aucun message CONTRL (accusé de réception, acceptation ou rejet) n’est envoyé en réponse à un échange reçu contenant un seul ou plusieurs messages CONTRL. Les erreurs rencontrées dans les messages CONTRL reçus doivent être signalées autrement que par l'intermédiaire d'un message CONTRL. Lorsqu'un échange contient un ou plusieurs messages CONTRL conjointement avec des messages de données, un message CONTRL généré en réponse à cet échange est créé comme si aucun message CONTRL n'avait été inclus dans l'échange reçu.  
  
 **Boucles SG**  
  
 La notification de transactions opérationnelles CONTRL est structurée différemment selon que l'échange reçu inclut un ou plusieurs groupes. Si l'échange comporte un seul groupe, la notification contient un segment UCF par groupe. Chaque segment UCF contient un segment UCM par message, et chaque segment UCM inclut une série de segments UCS et UCD couplés.  
  
 Le formulaire XML du message ACK inclut un élément SG3Loop qui encapsule les segments UCF, un élément SG4Loop qui encapsule les éléments UCM, ainsi qu'un élément SG5Loop qui encapsule les paires d'éléments UCS et UCD. Les balises d'une boucle SG ne sont pas présentes dans le format EDI natif du message.  
  
 Si l'échange n'inclut aucun groupe, la notification ne contient aucun segment UCF. En revanche, elle contient un segment UCM par message, et chaque segment UCM inclut une série de segments UCS et UCD couplés.  
  
 Le formulaire XML du message ACK inclut un élément SG1Loop qui encapsule les éléments UCM, ainsi qu'un élément SG2Loop qui encapsule les paires d'éléments UCS et UCD. À l'instar des échanges incluant des groupes, les balises SG ne sont pas présentes dans le format natif de la notification.  
  
> [!NOTE]
>  En fonction de leur utilisation par défaut et dans l'industrie, les boucles SG1/SG4 ne sont pas attendues dans les documents informatiques acceptés. Toutefois, pour prendre en charge de la conformité aux normes, vous pouvez forcer la génération de SG1/SG4 en sélectionnant le **générer boucle SG1/SG4 pour les documents informatisés acceptés** case à cocher dans la **accusés de réception** page de la Boîte de dialogue Propriétés de contrat pour un accord entre deux profils d’entreprise (ou le **accusés de réception** page de l’onglet Paramètres EDI pour un profil d’entreprise). Si vous activez cette case à cocher, le pipeline de réception génère des boucles SG1/SG4 que le document informatisé soit accepté ou rejeté. Dans le cas contraire, les boucles sont générées uniquement pour les documents informatisés erronés (pour lesquels UCM5! = 7).  
  
 **Éléments de données**  
  
 La notification de transactions opérationnelles CONTRL inclut les éléments de données suivants :  
  
|Éléments Data|Nom|Utilisation|  
|------------------|----------|-----------|  
|UNH1|Numéro de référence du message|-|  
|UNH2|Sous-composants de l'identificateur de message|Les sous-composants sont :<br /><br /> -1 = CONTRL<br /><br /> - 2 = 4<br /><br /> - 3 = 1<br /><br /> -4 = ANNULATION|  
|UCI1|Numéro de contrôle de l'échange|Mappé à partir du champ UNB5 du message reçu.|  
|UCI2|Expéditeur des échanges|Mappé à partir du champ UNB2 du message reçu. Le premier sous-composant (identification) est obligatoire. Le deuxième sous-composant (qualificateur du code) et le troisième composant (adresse de routage inverse) sont facultatifs.|  
|UCI3|Destinataire de l’échange|Mappé à partir du champ UNB3 du message reçu. Le premier sous-composant (identification) est obligatoire. Le deuxième sous-composant (qualificateur du code) est facultatif.|  
|UCI4|Code d'action|Les codes d'action sont les suivants :<br /><br /> -8 si l’échange est accepté.<br /><br /> -7 si l’échange est accepté mais certains documents informatisés sont rejetées.<br /><br /> -4 si l’échange est rejeté en raison d’une erreur dans le segment UNA ou UNB<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCI5|Code d'erreur de syntaxe|Identifie la condition d'erreur dans la réception de l'échange (le cas échéant). Pour plus d’informations, consultez [Codes d’erreur d’accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment-error-codes.md).<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCI6|Balise de segment de service|Identifie le segment disposant de la condition d'erreur spécifiée dans l'élément de données UCI.5.<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCI7|Identification de l'élément de données|Identifie les éléments de données disposant de la condition d'erreur spécifiée dans l'élément de données UCI.5. Les sous-composants du segment UCI7 sont :<br /><br /> -La position de l’élément de données erroné dans le segment (obligatoire)<br /><br /> -La position de l’élément de données composites erroné dans le segment (caractère facultatif conditionnel)<br /><br /> -L’occurrence de l’élément de données erroné dans le segment (caractère facultatif conditionnel)|  
|UCI8|-|-|  
|UCF1|Numéro de référence du groupe|Mappé à partir du champ UNG5 du message reçu.<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCF2|Identification de l’expéditeur de l’application|Mappé à partir du champ UNG2 du message reçu conjointement avec les sous-composants.<br /><br /> Il s'agit d'un élément de données conditionnel.|  
|UCF3|Identification du destinataire de l’application|Mappé à partir du champ UNG3 du message reçu conjointement avec les sous-composants.<br /><br /> Il s'agit d'un élément de données conditionnel.|  
|UCF4|Action codée|Les codes d'action sont les suivants :<br /><br /> -7 si l’échange est accepté.<br /><br /> -4 si l’échange est rejeté en raison d’une erreur dans le segment UNA ou UNB<br /><br /> Le code s'applique à ce niveau et à tous les niveaux inférieurs.<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCF5|Erreur de syntaxe, codée|Identifie la condition d'erreur dans le groupe (le cas échéant). Pour plus d’informations, consultez [Codes d’erreur d’accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment-error-codes.md).<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCF6|Balise de segment de service|Identifie le segment erroné dans le groupe.<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCF7|Identification de l'élément de données|Identifie les éléments de données disposant de la condition d'erreur spécifiée dans l'élément de données UCF5. Les sous-composants du segment UCF7 sont :<br /><br /> -La position de l’élément de données erroné dans le segment (obligatoire)<br /><br /> -La position de l’élément de données composites erroné dans le segment (caractère facultatif conditionnel)<br /><br /> -L’occurrence de l’élément de données erroné dans le segment (obligatoire)|  
|UCM1|Numéro de référence du message|Mappé à partir du champ UNH1 du message reçu.<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCM2|Identificateur du message|Mappé à partir du champ UNH2 du message reçu conjointement avec les sous-composants.<br /><br /> Il s'agit d'un élément de données conditionnel.|  
|UCM3|Action codée|Les codes d'action sont les suivants :<br /><br /> -7 si l’échange est accepté.<br /><br /> -4 si l’échange est rejeté en raison d’une erreur dans le segment UNA ou UNB<br /><br /> Le code s'applique à ce niveau et à tous les niveaux inférieurs.<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCM4|Erreur de syntaxe, codée|Identifie la condition d'erreur dans le groupe (le cas échéant). Pour plus d’informations, consultez [Codes d’erreur d’accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment-error-codes.md).<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCM5|Balise de segment de service|Identifie le segment UNH ou UNT dans l'erreur.<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCM7|Identification de l'élément de données|Identifie les éléments de données disposant de la condition d'erreur spécifiée dans l'élément de données UCM5. Les sous-composants du segment UCM7 sont :<br /><br /> -La position de l’élément de données erroné dans le segment (obligatoire)<br /><br /> -La position de l’élément de données composites erroné dans le segment (caractère facultatif conditionnel)<br /><br /> -L’occurrence de l’élément de données erroné dans le segment (obligatoire)|  
|UCS1|Position du segment dans le corps du message|Numéro de la position du segment erroné, où UNH représente 1. Dans le signalement d'un segment manquant, il s'agit de la position numérique du dernier segment traité avant celle où est supposé se trouver le segment manquant. Un groupe de segments manquant est identifié en désignant le premier segment du groupe comme manquant.<br /><br /> Il s'agit d'un élément de données obligatoire.|  
|UCS2|Erreur de syntaxe codée|Identifie la condition d'erreur dans le groupe (le cas échéant). Pour plus d’informations, consultez [Codes d’erreur d’accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment-error-codes.md).<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.|  
|UCD1|Erreur de syntaxe codée|Identifie la condition d'erreur dans le groupe (le cas échéant). Pour plus d’informations, consultez [Codes d’erreur d’accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment-error-codes.md).<br /><br /> Cet élément de données possède un caractère facultatif conditionnel.<br /><br /> **Remarque :** si un échec de la validation XSD se produit, l’élément de données UCD1 signale une valeur de code de 12, la valeur non valide.|  
|UCD2|Identification de l'élément de données|Identifie les éléments de données disposant de la condition d'erreur spécifiée dans l'élément de données UCD1. Les sous-composants du segment UCD2 sont :<br /><br /> -La position de l’élément de données erroné dans le segment (obligatoire)<br /><br /> -La position de l’élément de données composites erroné dans le segment (caractère facultatif conditionnel)<br /><br /> -L’occurrence de l’élément de données erroné dans le segment (obligatoire)|  
|UNT1|Nombre de segments|-|  
|UNT2|Numéro de référence du message|-|