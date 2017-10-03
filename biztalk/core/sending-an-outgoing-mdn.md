---
title: "Envoi d’un MDN sortant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dce7620-d354-4b76-bcbc-f97dc93c3fc3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d947751e06e0dc9892ab63e109b417047ad91b59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-outgoing-mdn"></a>Envoi d'une réponse MDN sortante
Un MDN sortant est généré par le pipeline de réception AS2EDIReceive ou AS2Receive et envoyé par le pipeline AS2Send. Cette rubrique explique comment un MDN est envoyé. Pour plus d’informations sur la façon dont un MDN est généré, consultez [générer un MDN sortant](../core/generating-an-outgoing-mdn.md).  
  
> [!NOTE]
>  Le pipeline de réception AS2EDISend ne permet pas d'envoyer un MDN sortant, car l'assembleur EDI de ce pipeline n'est pas utilisé pour traiter un MDN.  
  
## <a name="agreement-resolution-for-an-mdn"></a>Résolution de l'accord pour un MDN  
 Un MDN est acheminé automatiquement. Il contient les informations nécessaires pour être acheminé dans l'accord prévu. Le pipeline d'envoi utilise les propriétés d'accord AS2 pour traiter le MDN sortant. Il n'est cependant pas tenu d'avoir un accord résolu à acheminer vers le tiers.  
  
 Lorsque le pipeline AS2Send traite un MDN sortant, il utilise la valeur AS2-To dans le contexte du message pour obtenir les propriétés d'accord pour traiter le MDN. Il le fait en faisant correspondre AS2-pour la propriété de contexte et AS2-pour la propriété d’accord dans le **identificateurs** page dans l’onglet d’accord unidirectionnel AS2 dans le **propriétés de l’accord** boîte de dialogue. Cette résolution d'accord pour le MDN peut échouer si la valeur AS2-To n'est pas définie pour l'accord. Si l'accord ne peut pas être déterminé, un accord par défaut permet de générer le MDN.  
  
 Dans l'accord par défaut pour un MDN sortant, la vérification de la liste de résolution des certificats est effectuée. Si vous ne voulez pas que cette vérification ait lieu, vérifiez que la propriété AS2-To correcte est définie, de façon que le tiers qui reçoit puisse être résolu et les propriétés d'accord déterminées. Si c'est le cas, l'accord par défaut qui invite à vérifier la liste de résolution des certificats n'est pas utilisé. Vous devez également désactiver la **vérifier la liste de révocation** propriété sur le **Validation** page de l’onglet d’accord unidirectionnel AS2 dans le **propriétés de l’accord** boîte de dialogue.  
  
## <a name="synchronous-and-asynchronous-transmission"></a>Transmissions synchrones et asynchrones  
 Dans le traitement d'AS2 par défaut, un MDN est transmis de façon synchrone. Le MDN est envoyé par l’envoi port associé à un double port de réception. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]envoie le MDN sous la forme d’une réponse HTTP à une requête HTTP POST ou une réponse HTTPS à une requête HTTPS POST sur la même connexion TCP/IP. Le MDN est inclus dans le corps du message de la commande de la réponse HTTP.  
  
 Si le MDN est envoyé de façon asynchrone, le MDN doit être envoyé par un port d’envoi distinct, qui Récupère le MDN à partir de la MessageBox. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]envoie le MDN comme un HTTP Post séparé remis sur une connexion TCP/IP unique, distincte de celle utilisée pour remettre le message AS2 d’origine. Même si le MDN est défini comme HTTP Post séparé, une commande de réponse HTTP est nécessaire pour la publication.  
  
 Un MDN asynchrone est normalement envoyé à l'URL contenue dans l'en-tête Receipt-Delivery-Option du message AS2 d'origine. Toutefois, si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est définie sur le sur le **Validation** page de l’onglet d’accord unidirectionnel AS2 dans le **accord Propriétés** boîte de dialogue, le MDN est envoyé à l’URL qui le **Receipt-Delivery-Option (URL)** a la valeur de propriété d’accord.  
  
## <a name="how-the-send-pipeline-processes-an-outgoing-mdn"></a>Comment le pipeline d'envoi traite un MDN sortant  
 Le pipeline AS2Send traite un MDN sortant comme suit :  
  
-   Effectue le traitement MIME, y compris l’application d’une signature numérique, si activé dans les propriétés d’accord unidirectionnel AS2.  
  
-   Établit des entrées de corrélation dans la base de données de non répudiation (la table  EdiMessageContent de la base de données BizTalkDTADb).  
  
-   Effectue une copie du MDN (au format câble) et le stocke dans la base de données de non-répudiation, si activé dans le **NRR activé pour les MDN sortants** propriété d’accord.  
  
-   Fournit le MDN à l'adaptateur HTTP.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)   
 [AS2 Composants d’envoi](../core/as2-send-components.md)