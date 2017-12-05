---
title: "Files d’attente de file d’attente de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MSMQ adapters], queue paths
- naming conventions, MSMQ adapters
- configuring [MSMQ adapters], naming conventions
- messages, queuing
- MSMQ adapters, troubleshooting
- MSMQ adapters, message queues
- configuring [MSMQ adapters], troubleshooting
- troubleshooting, queue paths [MSMQ adapters]
- naming conventions, queue paths [MSMQ adapters]
- configuring [MSMQ adapters], message queues
ms.assetid: b802348e-8543-4b06-a6e4-149b86139fb1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8d2521a8cf434c7a0ea56f749f9df3f032551e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-queuing-queues"></a>Files d’attente de file d’attente
Cette section décrit la spécification de files d'attentes Microsoft Message Queuing (également appelé MSMQ) lors de l'utilisation de l'adaptateur MSMQ. Elle décrit les conventions utilisées lors de la spécification de chemins d'accès ainsi que le rôle joué par les noms de formats dans la conversion de chemins en désignations de file d'attente.  
  
## <a name="queue-path-naming-conventions"></a>Conventions d'affectation de noms aux chemins des files d'attente  
 Lorsque le nom de la file d'attente fait référence à un chemin, utilisez les conventions d'affectation de noms décrites dans le tableau suivant.  
  
|**Type de file d'attente**|**Syntaxe de chemin d’accès**|  
|--------------------|-------------------------|  
|File d'attente publique|*Nom_Ordinateur*\QueueName|  
|File d'attente privée|*Nom_Ordinateur*\Private$\QueueName|  
|File d'attente du journal|*Nom_Ordinateur*\QueueName\Journal$|  
|File d’attente du journal de l’ordinateur **Remarque :** utilisation de la file d’attente de réception uniquement.|*Nom_Ordinateur*\Journal$|  
|File d’attente de lettres mortes ordinateur **Remarque :** utilisation de la file d’attente de réception uniquement.|*Nom_Ordinateur*\Deadletter$|  
|File d’attente de lettres mortes de transaction ordinateur **Remarque :** utilisation de la file d’attente de réception uniquement.|*Nom_Ordinateur*\XactDeadletter$|  
  
> [!NOTE]
>  Le chemin de la file d'attente doit être unique.  
  
 Lorsque le nom de la file d'attente fait référence à un nom de format, il prend la forme d'une chaîne qui indique si la file d'attente est publique ou privée, suivie par un GUID généré pour la file d'attente ainsi que par d'autres identificateurs, selon le besoin. Utilisez les conventions d'affectation de noms décrites dans le tableau suivant.  
  
|**Type de format**|**Syntaxe de nom de format**|  
|---------------------|--------------------------------|  
|Public|*FormatName*: Public = Guidfileattente|  
|Direct|*FormatName*: DIRECT = SPX:NetworkNumber:HostNumber\QueueName<br /><br /> *FormatName*: DIRECT = TCP : adresseip\nomfileattente<br /><br /> *FormatName*: DIRECT = OS : NomOrdinateur\NomFileAttente|  
  
 Si le chemin de la file d'attente du port d'envoi est une liste de distribution, sa syntaxe est la suivante :  
  
 DL=GUIDListeDistribution  
  
 Si le chemin de la file d'attente d'envoi ou de réception est une URL HTTP ou HTTPS, la syntaxe est la suivante :  
  
 NomFormat : direct = http : / /\<nom de client\>/msmq/\<nom de la file d’attente\>  
  
 NomFormat : direct = https : / /\<nom de client\>/msmq/\<nom de la file d’attente\>  
  
> [!NOTE]
>  « msmq » correspond au répertoire virtuel créé par Message Queuing dans IIS (Internet Information Services).  
  
> [!NOTE]
>  Vous pouvez uniquement utiliser le protocole HTTP pour envoyer des messages. Il est impossible de lire des messages dans une file d'attente située sur un ordinateur distant si celle-ci est ouverte à l'aide d'un nom de format direct HTTP. Toutefois, vous pouvez toujours recevoir des messages SOAP (formatés) à partir d'une file d'attente distante à l'aide du chemin de la file d'attente publique ou privée sans le protocole HTTP.  
  
 Si le nom de la file d'attente fait référence à un nom constitué de texte descriptif que l'administrateur a spécifié pour cette file d'attente, la syntaxe du chemin de file d'attente faisant référence à ce nom est la suivante :  
  
 LABEL:MyQueue  
  
> [!NOTE]
>  Les noms ne sont pas toujours uniques. Toutefois, vous recevrez une erreur s'il existe un conflit de noms lorsque vous tentez de vous connecter à une file d'attente spécifique à l'aide de son nom.  
  
> [!NOTE]
>  Le nom est un paramètre de champ de transport obligatoire pour l'adaptateur.  
  
## <a name="role-of-the-format-name"></a>Rôle du nom de format  
 Le nom de format permet à Message Queuing d'identifier une file d'attente et de déterminer la manière d'y accéder. Message Queuing attribue le nom de format à la file d'attente.  
  
 Lorsque vous spécifiez une file d'attente à l'aide de la syntaxe du nom de chemin, par exemple myMachine\myQueue, Message Queuing recherche le chemin pour identifier le nom de format qui lui est associé. Message Queuing utilise ensuite ce nom de format pour accéder à la file d'attente. Lorsque vous spécifiez le nom de format, Message Queuing utilise celui que vous indiquez.  
  
 Pour plus d'informations sur les noms de formats, consultez la rubrique « Propriété MessageQueue.FormatName » dans l'aide de la bibliothèque de classes .NET Framework.  
  
## <a name="troubleshooting-queue-paths"></a>Résolution des problèmes relatifs aux chemins des files d'attente  
  
-   Une exception se produit si la syntaxe du chemin de file d'attente renseigné ne correspond à aucun des formats décrits précédemment dans la partie « Conventions d'affectation de noms aux chemins des files d'attente ».  
  
-   Les caractères suivants sont non valides pour la spécification du nom de l'ordinateur dans le chemin de file d'attente :  
  
     \ ; , + "  
  
     Une exception se produit si le nom d'un ordinateur est un nombre. Par exemple : 234\private$ \queue.  
  
-   Pour la file d'attente des messages non distribués de l'ordinateur, la file d'attente du journal de l'ordinateur et pour la file d'attente des messages non distribués des transactions de l'ordinateur, une exception se produit lorsqu'un utilisateur spécifie l'une des files d'attente du système comme file d'attente de destination pour l'envoi.  
  
-   **System.Messaging.MessageQueue.Exists** ne fonctionne pas pour les files d’attente distantes. Pour plus d'informations, consultez la rubrique « Méthode MessageQueue.Exists » dans l'aide de la bibliothèque de classes .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)