---
title: "Modèles d’échange pour les adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e505559e-66be-4c32-a2a8-a242cba10000
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cf8f36bb128d82a6d6b2e143320f89408f26680
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exchange-patterns-for-receive-adapters"></a>Remplacement des modèles pour les adaptateurs de réception
Les adaptateurs de réception reçoivent les données au « format câble » et les transmettent sous forme de message à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce processus de soumission peut se faire sur un modèle d'échange de message unidirectionnel ou bidirectionnel.  
  
## <a name="one-way-submit"></a>Soumission unidirectionnelle  
 Pour pouvoir soumettre un message au moteur de messagerie BizTalk, l'adaptateur de réception doit d'abord créer un message BizTalk. L'exemple de code de la rubrique relative à l'interface IBaseMessage montre comment cette création se fait. Le flux que l'adaptateur définit en tant que corps de message doit être un flux de transmission vers l'avant uniquement. Cela signifie que l'adaptateur ne doit pas mettre en cache les données qu'il vient de lire.  
  
 Avant de l’adaptateur envoie le message au moteur, il doit écrire la **InboundTransportLocation** propriété de contexte dans l’espace de noms système sur le message BizTalk. L'extrait de code suivant l'illustre.  
  
 `Assembly References:`  
  
 `Microsoft.XLANGs.BaseTypes.dll`  
  
 `Microsoft.BizTalk.Pipeline.dll`  
  
 `Microsoft.BizTalk.GlobalPropertySchemas.dll`  
  
```  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.XLANGs.BaseTypes;  
  
private static readonly PropertyBase InboundTransportLocationProp =   
new BTS.InboundTransportLocation();  
  
private void StampMsgCtxProps(  
IBaseMessage msg, string uri, string adapterType)  
{  
msg.Context.Write(  
 InboundTransportLocationProp.Name.Name,   
 InboundTransportLocationProperty.Name.Namespace,   
  uri);  
}  
```  
  
 En outre, l'adaptateur peut définir ses propres schémas de propriété et écrire les propriétés de contexte de message associées au point de terminaison par lequel il a reçu le message. Par exemple, un adaptateur HTTP peut écrire les en-têtes HTTP dans le contexte de message et un récepteur SMTP peut écrire le sujet du message dans le contexte de message. Ces informations peuvent être utiles pour intercepter en aval des composants tels que des composants de pipeline, des planifications d'orchestration ou un adaptateur d'envoi.  
  
 Une fois les messages préparés, ils peuvent être soumis au moteur de messagerie. Pour voir comment un adaptateur de réception unidirectionnel peut envoyer un message au moteur, consultez l’exemple de code [SubmitDirect (exemple BizTalk Server)](../core/submitdirect-biztalk-server-sample.md).  
  
## <a name="request-response"></a>Requête-réponse  
 Les adaptateurs de réception bidirectionnels sont généralement utilisés sur des ports de réception unidirectionnels ou bidirectionnels. L'adaptateur détermine si l'emplacement de réception pour lequel il fonctionne est un port unidirectionnel ou bidirectionnel en examinant le jeu de propriétés de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce processus est expliqué dans la **méthode IBTTransportConfig.AddReceiveEndpoint (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 Le diagramme d'interaction d'objets suivant présente le processus d'échange d'un message de type requête-réponse. L’adaptateur demande un nouveau lot du proxy de transport et transmet les références à la **IBTTransmitter** interface via le **SubmitRequestMessage** (méthode). Le moteur de messagerie remet le message de réponse sur cette interface à l’aide de la **TransmitMessage** (méthode).  
  
 Étant donné que le moteur de messagerie traite les messages de façon asynchrone, les configurations suivantes sont possibles :  
  
-   Le **BatchComplete** rappel peut se produire avant **fait** a retourné.  
  
-   L'appel de la méthode TransmitMessage doit être lancé avant le rappel BatchComplete et le renvoi de Done.  
  
 Bien que ces deux scénarios soient rares, il est préférable de protéger l'adaptateur contre de telles éventualités.  
  
 Il vaut mieux que le message de réponse soit transmis à l'aide d'un appel asynchrone sans blocage.  
  
 Le projet BaseAdapter dispose d’une classe utilitaire, **StandardRequestResponseHandler**, qui encapsule la sémantique de requête-réponse expliquée dans cette rubrique.  
  
## <a name="request-response-message-time-outs"></a>Expirations du délai des messages de requête-réponse  
 Lorsqu’un adaptateur envoie un message demande-réponse, il doit spécifier le délai d’expiration du message de demande sur le **méthode IBTTransportBatch.SubmitRequestMessage (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. Un message de réponse n'est ensuite remis à l'adaptateur que dans le délai spécifié. Une fois ce délai expiré, un accusé de réception négatif (NACK) est transmis à l'adaptateur à la place du message de réponse. Si aucun délai d'expiration n'est indiqué pour l'adaptateur, le moteur de messagerie respecte le délai par défaut qui est de 20 minutes.  
  
 Le délai d'expiration par défaut pour les messages de type requête-réponse peut être contrôlé à l'aide de la clé de registre suivante pour les adaptateurs de réception en cours de traitement :  
  
 **DWORD**  
  
 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc {Guid hôte} \MessagingReqRespTTL**  
  
 La clé de registre se trouve à un emplacement différent pour les adaptateurs de réception isolés :  
  
 **DWORD**  
  
 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**  
  
 Les accusés de réception négatifs sont des erreurs SOAP qu'il est possible de traiter de deux façons. En général, l'adaptateur renvoie l'accusé négatif au client pour qu'il le traite. Sinon, le pipeline de transmission qui traite le message de réponse peut être configuré de manière que le contenu du message de réponse soit modifié à l'aide d'un mappage ou d'un composant de pipeline personnalisé.