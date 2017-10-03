---
title: "Débogage des erreurs d’exécution d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7be9ee5a-b9fa-428b-8b92-0fa0f801c724
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36e881f8449e7aaac7aeade12c36c3c6d942ef12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-orchestration-runtime-errors"></a>Débogage des erreurs d'exécution d'une orchestration
Cette section présente un certain nombre de questions et réponses conçues pour vous aider à résoudre les problèmes d'exécution liés aux orchestrations.  
  
## <a name="why-do-i-get-intermittent-subscription-errors-when-sending-to-a-child-orchestration-that-was-just-started-by-the-parent"></a>Pourquoi est-ce que j'obtiens des erreurs d'abonnement intermittentes lors de l'envoi vers une orchestration enfant venant juste d'être démarrée par le parent ?  
 L'erreur d'abonnement « abonnement introuvable » résulte d'une condition d'engorgement. Une condition d'engorgement se produit lorsque le résultat d'un traitement dépend de l'ordre spécifique dans lequel est effectué le traitement. Dans ce cas, la condition se produit lorsque l'orchestration enfant n'a pas été démarrée à temps pour recevoir le message envoyé par le parent.  
  
 Pour éviter ce problème, l'orchestration enfant peut renvoyer un message au parent une fois qu'elle est démarrée et prête à recevoir un message. Ainsi, l'orchestration parent l'ayant lancée sait qu'il existe un destinataire avant d'envoyer un message.  
  
## <a name="why-do-i-get-errors-when-i-attach-a-dynamic-send-port-to-a-logical-port"></a>Pourquoi est-ce que j'obtiens des erreurs lorsque j'associe un port d'envoi dynamique à un port logique ?  
 La conception d'un port dynamique ne lui permet pas d'hériter de tous les attributs et caractéristiques du port qui lui est associé. Un port dynamique obtient uniquement une adresse, il n'hérite pas des autres informations associées au port logique.  
  
 Par exemple, si vous associez un port d'envoi dynamique à un port logique avec Accusé de réception = Transmis, le composant d'exécution ne renverra pas d'accusé de réception. Le composant d'exécution XLANG recherche un accusé de réception uniquement si le port a été configuré à cet effet de manière statique.  
  
> [!NOTE]
>  Dans les XLANG, les ports se comporteront uniquement comme s'ils avaient été configurés de manière statique.  
  
## <a name="when-i-try-to-run-my-application-after-deploying-an-orchestration-with-custom-components-why-do-i-get-the-error-file-or-assembly-name-or-one-of-its-dependencies-not-found"></a>Lorsque je tente d'exécuter mon application après avoir déployé une orchestration avec des composants personnalisés, pourquoi est-ce que j'obtiens l'erreur « Nom de fichier ou d'assembly ou une de ses dépendances introuvable »?  
 Cette erreur signifie généralement que le moteur d'orchestration BizTalk  ne trouve pas le composant personnalisé. Vous devez installer tous les assemblys inclus dans une application BizTalk dans le GAC de l'ordinateur hébergeant l'application.  
  
## <a name="an-assemblyname-context-property-was-not-valid-error-occurs-when-submitting-a-document-to-a-web-service-via-an-orchestration"></a>Une erreur « Propriété de contexte AssemblyName non valide » se produit lors de la soumission d'un document à un service Web via une orchestration  
  
### <a name="problem"></a>Problème  
 La soumission d'un document à un service Web via une orchestration entraîne une erreur « Propriété de contexte AssemblyName non valide ».  
  
### <a name="cause"></a>Cause  
 L'application BizTalk a été conçue à l'origine avec une approche « messagerie », sans intervention d'une orchestration. Ce type de solution utilise un filtre sur le port d'envoi pour lier le port de réception et le port d'envoi de sorte que le document est transféré au port d'envoi à réception. Par la suite, la solution a été modifiée afin d'inclure une orchestration liée au port d'envoi.  
  
### <a name="resolution"></a>Résolution  
 Supprimez le filtre sur le port d'envoi. Si vous appliquez un filtre à un port d'envoi lié à une orchestration, les messages vont souvent contourner l'orchestration et provoquer l'erreur de propriété de contexte.  
  
## <a name="a-wrongbodypartexception-occurs-when-handling-a-multipart-mime-message-in-an-orchestration"></a>Une erreur « WrongBodyPartException » se produit lors du traitement d'un message MIME en plusieurs parties dans une orchestration  
  
### <a name="problem"></a>Problème  
 Réception d’un message MIME à parties multiples dans une orchestration entraîne une **WrongBodyPartException** exception.  
  
### <a name="cause"></a>Cause  
 Cette erreur peut survenir si l'ordre des parties est spécifié de manière incorrecte ou si les messages ne respectent pas les positions des parties que vous avez spécifiées. Par exemple, si vous avez indiqué que la troisième partie correspond au corps du message, mais que les messages comportent une partie en-tête en troisième position.  
  
### <a name="resolution"></a>Résolution  
 Vérifiez que le paramètre d'indexation des parties est correct et assurez-vous que tous les messages arrivant par le biais de cet adaptateur sont conformes au paramètre. Vous pouvez étudier le contenu des messages MIME ayant échoué dans une orchestration en arrêtant l'orchestration (tout en la gardant inscrite) ; cela aura pour effet de forcer la publication du message et vous pourrez le consulter en utilisant la console Administration et vérifier ainsi l'ordre des parties.  
  
## <a name="multipart-mime-message-part-cannot-be-found"></a>Une partie d'un message MIME à plusieurs parties est introuvable  
  
### <a name="problem"></a>Problème  
 Tente de récupérer un MIME du message partie avec une valeur d’index supérieure à 0 entraîne l’exécution de BizTalk Server qui lève une erreur semblable à « Impossible de trouver le message à parties multiples avec index = \<valeur > ».  
  
### <a name="cause"></a>Cause  
 Les principales causes de cette erreur sont les suivantes :  
  
-   Le message MIME compte moins de parties que prévu.  
  
-   Le message MIME n'a pas pu être analysé complètement.  
  
### <a name="resolution"></a>Résolution  
 Vous pouvez résoudre ce problème en vous assurant que votre code n'extrait que les parties de message comprises dans la plage attendue à partir de la source du message. Dans le cas d'un problème d'analyse, vérifiez que la structure du message MIME d'origine est correcte et qu'il est construit de manière appropriée. Si vous prévoyez des erreurs d'analyse occasionnelles, assurez-vous que votre orchestration dispose des gestionnaires d'exception appropriés.  
  
## <a name="you-receive-a-the-file-send-adapter-cannot-open-file-for-writing-error-when-sending-using-a-dynamic-send-port"></a>Vous recevez l'erreur « L'adaptateur d'envoi FILE ne peut pas ouvrir le fichier pour écriture » lors d'un envoi à l'aide d'un port d'envoi dynamique  
  
### <a name="problem"></a>Problème  
 Vous recevez un « l’adaptateur d’envoi de fichier ne peut pas ouvrir le fichier  *\<filename >* en écriture « erreur dans le journal des événements BizTalk Server lors de l’envoi à l’aide d’un dynamique un port d’envoi.  
  
 Ce problème se produit lorsque le **BTS. OutBoundTransportLocation** propriété est définie dans une expression d’orchestration et le transport de fichier est spécifié, par exemple les expressions suivantes provoquent cette erreur lors de l’exécution :  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file:///c:/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
 \-Ou -  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file://mymachine/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
### <a name="cause"></a>Cause  
 Ce problème se produit parce que lors de l’exécution, le moteur d’orchestration supprime le texte «**file:// «** à partir de l’URL spécifiée. Dans les exemples précédents, "file:///c:/test/out" est évaluée comme \c:\test\out et "file://mymachine/test/out" est évaluée comme mymachine\test\out.  
  
### <a name="resolution"></a>Résolution  
 Lorsque vous spécifiez l’URL pour le **BTS. OutBoundTransportLocation** propriété dans une expression, ajouter ou supprimer des caractères « / » en fonction des besoins. Les exemples précédents le **BTS. OutBoundTransportLocation** propriété doit être définie en tant que « file://c:/test/out », qui est évalué sur c:\test\out ou « file:///mymachine/test/out », qui est évalué sur \\\mymachine\test\out.