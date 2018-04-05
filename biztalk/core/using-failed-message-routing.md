---
title: À l’aide du routage de Message ayant échoué | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.ops.tsroutingfailure
ms.assetid: d081934c-600e-44ce-8ba4-fb646d494589
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af6d006aeebd5e2a5f8625a994c8a6f9b0cb6f6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-failed-message-routing"></a>Utilisation du routage pour les messages ayant échoué
La fonctionnalité de gestion des erreurs permet au concepteur de désigner la gestion automatique des échecs relatifs à la messagerie comme une alternative au comportement traditionnel (par défaut désormais) qui consiste à placer les messages ayant échoué dans la file d'attente des messages interrompus. Cette gestion automatique achemine les messages d'erreur vers n'importe quelle destination de routage abonnée, telle qu'un port d'envoi ou une orchestration. Le message d'erreur est un clone du message d'origine. Les propriétés précédemment promues sont désormais toutes rétrogradées et les propriétés sélectionnées associées à l'échec spécifique de la messagerie sont promues vers le contexte de message.  
  
> [!WARNING]
>  Les messages ayant échoué contiennent une copie du message d'origine. Si le message d'origine contient des informations sensibles, concevez vos processus automatique et manuel de messages ayant échoué de manière à ce qu'une divulgation accidentelle soit évitée.  
  
## <a name="what-does-failed-message-routing-consist-of"></a>En quoi consiste le routage des messages ayant échoué ?  
 Lorsque le routage des messages ayant échoué est activé, BizTalk Server achemine le message au lieu de le suspendre. Le routage des messages ayant échoué peut être activé sur les ports de réception et d'envoi, avec les résultats suivants :  
  
-   Si le routage des messages ayant échoué est activé sur un port de réception et qu'un message échoue dans le pipeline de réception ou pendant le routage, un message ayant échoué est généré. Dans le cas où une erreur se produit pendant ou avant la phase de désassemblage, le message d'erreur est un clone de l'échange d'origine.  
  
-   Si le routage des messages ayant échoué est activé sur un port d'envoi et que le message échoue dans le pipeline d'envoi, un message ayant échoué est généré.  
  
 Lorsqu'un message ayant échoué est généré, BizTalk Server promeut des propriétés de contexte de message de rapport d'erreur et rétrograde des propriétés de contexte de message normal avant de publier le message ayant échoué. Comparez ce comportement à celui par défaut quand le routage des messages ayant échoué n'est pas activé : les messages qui échouent sont suspendus.  
  
## <a name="what-kinds-of-messaging-failures-trigger-an-error-message"></a>Quels types d'échecs de messagerie déclenchent un message d'erreur ?  
 Tout échec survenant lors du traitement de l'adaptateur ou du pipeline, du mappage, ou du routage des messages provoque un message d'erreur si le routage des messages ayant échoué est activé. Lorsqu'une erreur de messagerie se produit au moment où une orchestration reçoit des données d'un port de réception ou envoie des données à un port d'envoi, le message d'erreur qui en résulte est associé aux ports de messagerie auxquels l'orchestration est liée.  
  
## <a name="subscribing-to-an-error-message"></a>Abonnement à un message d'erreur  
 Les messages d'erreur sont remis aux orchestrations ou aux ports d'envoi qui s'y sont abonnés. Un abonnement sélectionne généralement un message d'erreur sur la base du nom du port (un port d'envoi ou de réception) dans lequel l'erreur de messagerie s'est produite. Un abonnement peut également filtrer d'autres propriétés promues vers le contexte de message de l'erreur (par exemple **InboundTransportLocation** ou **FailureCode**).  
  
## <a name="error-message-specification"></a>Spécification de message d'erreur  
 Un message d'erreur est un clone du message d'origine ayant échoué. Les propriétés précédemment promues sont toutes rétrogradées et un ensemble des propriétés propres à l'erreur est promu vers le contexte de message. Les propriétés promues précédemment sont rétrogradées pour éviter toute remise involontaire à des abonnés n'étant pas censés recevoir le message d'erreur. Le message d'erreur est publié afin d'être distribué aux abonnés (orchestrations, ports d'envoi et groupes de ports d'envoi).  
  
 Les propriétés sont promues vers le contexte de message d’erreur qui se trouvent toutes dans le **/errorreport** espace de noms dans BizTalk Server. Il s'agit des propriétés suivantes :  
  
|Nom de la propriété|Type de données|Promue|Description|  
|-------------------|---------------|--------------|-----------------|  
|FailureCode|System.String|Oui|Code d'erreur Il s'agit d'une valeur hexadécimale reportée dans la console Administration de BizTalk Server.|  
|FailureCategory|System.Int32|Oui|Cette propriété n'est pas utilisée. Sa valeur n'est pas définie.|  
|Description|System.String|Non|Description d'erreur. Même texte de diagnostic que celui consigné dans le journal d'événements d'applications en ce qui concerne cet échec de messagerie.|  
|MessageType|System.String|Oui|Type de message ayant échoué, ou vide si le type de message est indéterminé.<br /><br /> BizTalk Server utilise le type de message pour associer des messages à leurs schémas XML. Le type de message est formé en concaténant l'espace de noms du schéma et le nœud racine du schéma : http://mynamespace#rootnode **Remarque :** les Messages qui échouent avant que leur type de message est déterminé ne pas cette propriété est définie.|  
|ReceivePortName|System.String|**Promue** si l'échec s'est produit pendant le traitement entrant (dans un port de réception).<br /><br /> **Non promue** si l'échec s'est produit dans un port d'envoi.|Nom du port de réception où l'échec s'est produit.|  
|InboundTransportLocation|System.String|**Promue** si l'échec s'est produit pendant le traitement entrant (dans un port de réception).<br /><br /> **Non promue** si l'échec s'est produit dans un port d'envoi.|URI de l'emplacement de réception où l'échec s'est produit.|  
|SendPortName|System.String|**Promue** si l'échec s'est produit pendant le traitement sortant (dans un port d'envoi).<br /><br /> **Non promue** si l'échec s'est produit dans un port de réception.|Nom du port d'envoi où l'échec s'est produit.|  
|OutboundTransportLocation|System.String|**Promue** si l'échec s'est produit pendant le traitement sortant (dans un port d'envoi).<br /><br /> **Non promue** si l'échec s'est produit dans un port de réception.|URI de l'emplacement d'envoi où l'échec s'est produit.|  
|ErrorType|System.String|Oui|Indique le type de message que l'erreur contient. Cette propriété contient toujours la valeur **FailedMessage**, ce qui signifie que l'erreur contient le message ayant échoué d'origine.|  
|RoutingFailureReportID|System.String|Oui|Cette propriété fournit l'ID du rapport d'échec de routage généré par BizTalk Server en cas d'échec de routage. Un rapport d'échec de routage est un message spécial que BizTalk Server génère et suspend. Ce message est dépourvu de corps, mais possède le contexte du message ayant échoué. À l'aide de cet ID, une orchestration de gestion des erreurs ou un port d'envoi peuvent interroger la base de données MessageBox et traiter le rapport d'échec de routage. Une orchestration peut par exemple souhaiter mettre fin au rapport d'échec de routage après avoir reçu le message ayant échoué.|  
  
## <a name="handling-error-messages"></a>Gestion des messages d'erreur  
 La gestion des erreurs est spécifiée par un abonnement à une orchestration ou un port d'envoi, abonnement dont le filtre correspond aux propriétés qui ont été promues vers le contexte de message du message d'erreur.  
  
## <a name="security-implications"></a>Incidence sur la sécurité  
 L'identité associée au message d'origine (son identité initiale ou son identité finale déterminée par la phase de résolution de tiers du pipeline de réception) est affectée au message d'erreur.  
  
 Les mécanismes de sécurité qui restreignent la remise de messages aux ports et aux orchestrations abonnés autorisés s'appliquent aussi aux messages d'erreur.  
  
 Un port d'envoi qui s'abonne à un message d'erreur, mais qui n'est pas configuré avec un certificat de déchiffrement approprié, ne reçoit pas de messages d'erreur résultant d'échecs de messagerie durant ou avant l'étape de déchiffrement du pipeline de réception via lequel le message d'origine a pénétré dans BizTalk Server. Au lieu de cela, les messages ayant échoué sont placés dans la file d'attente des messages interrompus.  
  
## <a name="adapter-messaging-failure"></a>Échec de messagerie de l'adaptateur  
 Si un adaptateur suspend un message, un message d'erreur est publié. Aucun message d'erreur n'est généré si le message n'est pas suspendu.  
  
## <a name="transactional-receive-pipelines"></a>Pipelines de réception transactionnels  
 Si un pipeline de réception transactionnel lève une exception (spécifie que la transaction doit être abandonnée), la transaction est abandonnée et un message d'erreur est publié.  
  
 Si un pipeline de réception transactionnel suspend explicitement un message (spécifie que MessageDestination = SuspendQueue), la transaction actuelle est autorisée à se poursuivre (et peut être validée sauf si les étapes suivantes spécifient son abandon) et le message d'erreur résultant est publié.  
  
## <a name="solicit-response-send-ports"></a>Ports d'envoi avec sollicitation-réponse  
 Lorsqu'un message de requête est envoyé à partir d'une orchestration et que sa transmission ou le traitement entrant de sa réponse échoue, l'orchestration obtient une exception, que le message ayant échoué ait été routé ou non.  
  
 Dans le cas où un port d'envoi avec sollicitation-réponse est connecté à un port de réception de requête-réponse, le port de réception reçoit soit un message de réponse (si la transmission réussit), soit un accusé NACK (si la transmission échoue), que le message ayant échoué ait été routé ou non.  
  
## <a name="one-way-send-ports"></a>Ports d'envoi unidirectionnels  
 Lorsqu'un message est envoyé à partir d'une orchestration via un port d'envoi configuré pour les accusés de réception, l'orchestration reçoit un accusé de réception que le message d'erreur ait été routé ou non. Autrement dit, le port d'envoi génère un accusé de réception pour l'orchestration même si le port est confronté à un échec de messagerie pendant le traitement. L'accusé se borne à confirmer la remise faite au port, il ne mentionne pas si le traitement via ce dernier a réussi.  
  
## <a name="resuming-suspended-messages"></a>Reprise des messages suspendus  
 La plupart des messages dont le traitement entrant échoue (autrement dit, le traitement allant de l'adaptateur de réception, ce dernier inclus, à la publication, non comprise, dans la MessageBox) et dont les erreurs ne sont pas gérées sont suspendus et peuvent être repris. Ce n'est en revanche pas le cas des messages de requête issus des ports de réception bidirectionnels, qui sont suspendus et ne peuvent pas être repris.  
  
 Le format des messages suspendus est généralement celui qu'ils avaient à l'origine (avant le traitement de pipeline). Il y a cependant deux exceptions à cette règle :  
  
-   **Messages suspendus par des composants de pipeline.** BizTalk Server suspend ce type de message selon le même format que celui fourni au composant de pipeline défaillant. Dès que le message est repris, il subit un traitement de pipeline depuis le début du même pipeline. Cela signifie qu'un composant de pipeline situé dans une phase de pipeline précédant la phase où la défaillance d'origine a eu lieu doit être préparé à gérer le « même » message dans un format différent du format d'origine dans lequel il a traité ce message.  
  
-   **Le code machine qui provoquant l’échec de routage d’échange de messages restaurable.** BizTalk Server suspend ce type de message selon le même format que celui avec lequel il a été publié. Il s'agit du format qui était celui du message **après** l'exécution du pipeline. Dès que le message est repris, il ignore le traitement de pipeline et est publié directement dans la base de données MessageBox.  
  
## <a name="scenarios-leading-to-suspended-non-resumable-messages"></a>Scénarios générant des messages suspendus (sans reprise possible)  
 Bien que les messages suspendus puissent généralement être repris, certains scénarios génèrent des messages sans reprise possible :  
  
-   Dans un port d'envoi Livraison chronologique des messages pour lequel l'option « Continuer après un échec » est activé, en cas de défaillance au niveau du pipeline, du mappage ou de la transmission  
  
-   Dans un port de réception Livraison chronologique des messages, si l'adaptateur est configuré pour suspendre les messages sans reprise possible en cas d'échec. Par exemple, si le paramètre d'adaptateur MSMQ « En cas d'échec » est défini sur « Suspendre (sans reprise) » ou si pour l'adaptateur MQSeries, l'option « Suspendre sans réponse possible » est activée, les messages ayant échoué seront suspendus sans reprise possible.  
  
-   Dans un port de réception bidirectionnel, en cas d'échec du message de réponse dans le pipeline, le mappage ou la transmission  
  
-   Dans un port de réception bidirectionnel, en cas d'échec de la réception d'un message dans le pipeline, le mappage ou la transmission. Le comportement des adaptateurs individuels peut être différent. Par exemple, par défaut l'adaptateur HTTP ne suspend pas de messages, mais il peut être également configuré pour les suspendre.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs](../core/error-handling.md)   
 [À l’aide des accusés de réception](../core/using-acknowledgments.md)   
 [Livraison chronologique des messages](../core/ordered-delivery-of-messages.md)