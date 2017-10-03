---
title: "Générer un MDN sortant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12d7da1c-0d3c-42d4-9388-29f499353d13
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a903cc72a41362f6843449a4d635878706f2ea1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-an-outgoing-mdn"></a>Génération d'une réponse MDN sortante
Les pipelines de réception AS2 génèrent une réponse MDN (Message Disposition Notification) à un message entrant. Cette opération est effectuée par le composant de pipeline du Désassembleur EDI dans le pipeline de réception AS2EDIReceive (en réponse à un message EDI) ou par le composant de pipeline du Désassembleur AS2 dans le pipeline de réception AS2Receive (en réponse à un message non EDI).  
  
## <a name="when-and-how-an-mdn-is-generated"></a>Circonstances provoquant la génération d'un MDN  
 En général, un MDN est généré en fonction des en-têtes AS2 du message AS2 d'origine, de la façon suivante :  
  
-   Si l'en-tête Disposition-Notification-To est présent dans le message AS2, un MDN sera envoyé.  
  
-   Si les en-têtes Disposition-Notification-To et Receipt-Delivery-Option sont présents dans le message, le MDN sera envoyé de manière asynchrone. Il est envoyé à l'URL contenue dans l'en-tête Receipt-Delivery-Option sur une connexion différente de celle du message d'origine.  
  
-   Si l'en-tête Disposition-Notification-To est présent dans le message, mais que l'en-tête Receipt-Delivery-Option ne l'est pas, le MDN est envoyé de manière synchrone sur la même connexion que le message d'origine.  
  
 Le Désassembleur crée l'en-tête AS2-From dans le MDN à partir de l'en-tête AS2-To contenu dans le message AS2 reçu. Il crée également l'en-tête AS2-To dans le MDN à partir de l'en-tête AS2-From contenu dans le message AS2 reçu.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de remplacer ces paramètres en indiquant si un MDN sera généré, et comment il le sera, en fonction des propriétés d'un accord AS2 d'un tiers. Vous remplacer les paramètres d’en-tête AS2 du message à l’aide de la **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété dans l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord**boîte de dialogue. Cette propriété vous permet d'envoyer un MDN même si l'en-tête AS2 n'en appelle pas, ou d'envoyer un MDN de manière asynchrone lorsque l'en-tête AS2 spécifie une connexion synchrone.  
  
 Si vous définissez la **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété, les valeurs dans le **exiger le MDN** section de la **paramètres MDN de l’expéditeur** page dans l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue sera utilisée pour le MDN, comme suit :  
  
-   Un MDN est envoyé si la **exiger le MDN** propriété est sélectionnée.  
  
-   Si le **exiger le MDN** propriété est sélectionnée et le **exiger le MDN asynchrone** propriété est sélectionnée, le MDN est envoyé de façon asynchrone. Le MDN est envoyé à l’URL qui le **Receipt-Delivery-Option (URL)** est définie sur, sur une connexion différente de celle du message d’origine.  
  
-   Si le **exiger le MDN** propriété est sélectionnée, mais la **exiger le MDN asynchrone** propriété n’est pas sélectionnée, le MDN sera envoyé de manière synchrone sur la même connexion que le message d’origine.  
  
 Si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est définie, AS2-à partir de la propriété dans le message d’en-tête sera utilisé pour générer le MDN, mais AS2-pour seront prises dans les propriétés de l’accord, et le pipeline signe le MDN conformément à la **exiger le MDN signé** propriété. Les en-têtes AS2 correspondent aux propriétés de l'accord de la façon suivante :  
  
|Propriétés de l'accord|En-tête AS2 dans le message|  
|------------------------|-------------------------------|  
|Générer un MDN|Disposition-Notification-To|  
|Signer le MDN|Signed-Receipt-Protocol|  
|Receipt-Delivery-Option|Receipt-Delivery-Option|  
  
 Si un MDN est activé, le pipeline de réception promeut les propriétés de contexte suivantes :  
  
-   `EdiIntAS.DispositionMode`  
  
-   `EdiIntAS.DispositionType`  
  
 Ces propriétés de contexte doivent toutes deux être promues pour que le MDN soit généré. Pour plus d’informations sur ces propriétés de contexte, consultez [propriétés de contexte AS2](../core/as2-context-properties.md).  
  
 Si les paramètres de configuration et les en-têtes du message entrant ne sont pas cohérents, le pipeline génère un MDN négatif.  
  
 Si le MDN est exigé dans les propriétés de l'accord, le pipeline de réception tente d'envoyer un MDN même si une erreur se produit dans le traitement AS2.  
  
## <a name="how-the-receive-pipeline-processes-a-generated-mdn"></a>Traitement par le pipeline de réception d'un MDN généré  
 Si un MDN est généré conformément aux règles ci-dessus, le pipeline de réception AS2EDIReceive ou AS2Receive traite le MDN de la manière suivante :  
  
-   Effectue une copie du message MDN (au format câblé) et la stocke dans la base de données de non répudiation, si activé dans les propriétés de l'accord unidirectionnel AS2.  
  
-   Effectue le traitement MIME, y compris l'application d'une signature numérique, si activé dans les propriétés de l'accord unidirectionnel AS2.  
  
-   Calcule le MIC (Message Integrity Check) pour la charge du message AS2 et l'ajoute au champ d'extension Received-content-MIC du MDN. L’algorithme qui sera appliqué au MIC est déterminé par l’en-tête signed-receipt-micalg du message entrant ou **algorithme de signature** propriété sur le **paramètres MDN de l’expéditeur** page de l’unidirectionnel onglet d’accord de la **propriétés de l’accord** boîte de dialogue (lorsque les propriétés de message entrant sont remplacées). Il peut s'agir de SHA1 ou de MD5. La valeur de l'algorithme est également incluse dans le MDN.  
  
-   Crée des entrées de corrélation dans la base de données de non-répudiation.  
  
-   Effectue une copie du message MDN.  
  
-   Si le MDN doit être transmis de manière synchrone, le pipeline définit la propriété `EdiIntAS.IsAS2AsynchronousMDN` sur la valeur False ; s'il doit être transmis de manière asynchrone, le pipeline définit cette propriété sur la valeur True.  
  
-   Si le MDN doit être transmis de manière synchrone, le pipeline d'envoi AS2Send associé au port de réception bidirectionnel récupèrera le MDN en fonction de la propriété `EdiIntAS.IsAS2AsynchronousMDN` (ayant la valeur False) et des jetons de corrélation.  
  
    > [!NOTE]
    >  Vous pouvez également configurer un port d'envoi qui s'abonne au MDN synchrone sortant. Pour cela, définissez le filtre de port d'envoi sur `EdiIntAS.IsAS2MdnResponseMessage==True`.  
  
-   Si le MDN doit être transmis de manière asynchrone, le pipeline de réception achemine le MDN vers la MessageBox. Vous devez configurer un port d'envoi pour qu'il s'abonne au MDN en définissant le filtre de port d'envoi sur la valeur `IsAS2AsynchronousMdn==True`. Le pipeline d'envoi AS2Send récupère le message en fonction de cette propriété et des jetons de corrélation. Si le port d'envoi est dynamique, il achemine le MDN en fonction de l'adresse indiquée sur la ligne Receipt-Delivery-Notification de l'en-tête du message. Si le port d'envoi est statique, il achemine le message en fonction de la propriété Transport - URI du port d'envoi.  
  
## <a name="mdn-generation-rules"></a>Règles de génération d'un MDN  
 Les règles suivantes s'appliquent à la génération de MDN :  
  
-   Lorsque l'expéditeur d'un message exige spécifiquement un accusé de réception signé mais qu'une erreur se produit dans le traitement du contenu du message, le récepteur du message est tenu de renvoyer un accusé de réception signé bien que la transaction elle-même ne soit pas valide. La raison de l'erreur de traitement du contenu du message doit être définie dans disposition-field.  
  
-   Lorsque la requête d'accusé de réception de MDN précise de façon explicite que l'accusé de réception doit être signé, mais que le récepteur du message d'origine ne prend pas en charge le format de protocole demandé ou l'algorithme MIC requis, un accusé de réception signé ou non signé doit être renvoyé.  
  
-   Si une signature n'est pas explicitement exigée, ou que le paramètre de requête d'accusé de réception signé n'est pas reconnu par l'accord du tiers destinataire, le tiers destinataire peut renvoyer un accusé de réception non signé, un accusé de réception signé ou aucun accusé de réception.  
  
## <a name="mic-generation"></a>Génération de MIC  
 Lorsqu'un MDN est exigé, le récepteur du message d'origine génère un MIC (Message Integrity Check) et l'ajoute au MDN. Lorsque l'échange EDI fait partie d'un type de contenu MIME à parties multiples, le MIC doit être calculé sur tout le contenu à parties multiples, y compris sur l'échange EDI et les en-têtes MIME. Pour les messages chiffrés, non signés, le MIC à renvoyer est calculé en fonction de l'en-tête et du contenu MIME déchiffrés. Pour les messages non chiffrés, non signés, le MIC doit être calculé en fonction du contenu du message sans les en-têtes MIME.  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)