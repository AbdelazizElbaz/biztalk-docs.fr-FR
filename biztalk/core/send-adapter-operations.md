---
title: "Opérations de l’adaptateur d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4e0430-e3dc-4884-8411-bbcb579bd21e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444cf4ab7958b0d44838a8331b4b9e6a467baedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-adapter-operations"></a>Opérations de l'adaptateur d'envoi
Les adaptateurs d'envoi peuvent effectuer les opérations suivantes :  
  
-   **Soumettez à nouveau : annulation de renvoi (IBaseMessage msg, DateTime timeStamp).** Après un échec de transmission d'un message, l'adaptateur le renvoie s'il y a lieu. Il s'agit d'une base par message. Si un lot de messages a été envoyé sans succès, l’adaptateur doit déterminer les messages à l’origine de l’échec et renvoie ceux qui n’a pas provoqué d’échec dans des appels séparés à **renvoyer**. Il existe plus d’informations sur la façon de conserver les valeurs de propriété de contexte de message lorsque vous appelez à la fin de cette rubrique **renvoyer**.  
  
-   **Déplacer vers le Transport suivant : void MoveToNextTransport (IBaseMessage msg).** Si un message échoue au cours d'un envoi et que le nombre de tentatives de renvois est atteint, l'adaptateur peut envoyer le message au transport configuré suivant pour qu'il soit transmis.  
  
-   **Suspendre : void MoveToSuspendQ (IBaseMessage msg).** L'adaptateur déplace un message d'envoi qui a échoué dans la file d'attente des messages interrompus si aucun autre transport secondaire n'est configuré. Il existe plus d’informations sur la façon de conserver les valeurs de propriété de contexte de message lorsque vous appelez à la fin de cette rubrique **Suspend**.  
  
-   **Suppression : void DeleteMessage (IBaseMessage msg).** L'adaptateur supprime un message une fois que BizTalk Server l'a informé qu'il a été correctement transmis. La suppression d'un message indique à BizTalk Server que l'adaptateur a fini d'utiliser le message. En règle générale le **SubmitResponse** opération est effectuée dans le même lot que qui lui est associée **supprimer** opération.  
  
-   **Envoyer la réponse : void SubmitResponseMessage (IBaseMessage solicitMsgSent, IBaseMessage responseMsgToSubmit).** L'adaptateur envoie une réponse au lot à renvoyer à BizTalk Server. Cette opération inclut le message d'origine dans l'appel avec la réponse afin que BizTalk Server puisse les mettre en corrélation.  
  
-   **Réponse de l’annuler : void CancelResponseMessages (string correlationToken).** Si l’envoi d’un message de réponse doit être annulé avant que le lot est soumis, la **CancelResponseMessages** méthode est utilisée, transmettant le jeton de corrélation pour le message de réponse associé à supprimer.  
  
 Lors de l’appel **renvoyer** ou **Suspend** sur un message que vous souhaitez conserver les valeurs de certaines propriétés de contexte de message. Vous pouvez enregistrer ces valeurs de propriétés au format XML. Lorsque le message est renvoyé ou suspendu, les propriétés correspondantes restent disponibles dans le contexte du message.  
  
 La chaîne XML suivante décrit le format auquel les informations sont enregistrées :  
  
```  
<PropertiesToUpdate>  
<Property name="StringProperty" nameSpace="http://MyNamespace1" vt="8">SomeString</Property>  
<Property name="IntProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="3">4</Property>  
<Property name="BoolProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="11">0</Property>  
</PropertiesToUpdate>  
```  
  
 La chaîne XML est générée par le code suivant :  
  
```  
private string GetPropsToUpdateXml(int nextRetryAttempt)  
{  
string result = "<PropertiesToUpdate><Property name=\"RetryAttempts\" nameSpace=\"http://schemas.microsoft.com/BizTalk/2005/test-properties\" vt=\"3\">" + nextRetryAttempt.ToString() + "</Property></PropertiesToUpdate>";  
return result;  
}  
```  
  
 Cette chaîne est ensuite enregistrée dans le contexte du message à l'aide du code suivant :  
  
```  
Message.Context.Write("PropertiesToUpdate", "http://schemas.microsoft.com/BizTalk/2003/system-properties", GetPropsToUpdateXml(++retryAttempt));  
```  
  
 Lorsque le message est renvoyé, l'adaptateur peut lire cette propriété à l'aide de la ligne de code suivante :  
  
```  
propValue = inmsg.Context.Read("RetryAttempts", "http://schemas.microsoft.com/BizTalk/2005/test-properties");  
```