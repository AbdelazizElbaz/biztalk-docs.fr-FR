---
title: Livraison chronologique des Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, message order
- file transport, message order
- Messaging Engine, transports
- messages, performance
- dynamic send ports, message order
- BTS.SuspendAsNonResumable message context property
- performance, message order
- Messaging Engine, performance
- Messaging Engine, message order
- MessageBox database, message order
- messages, sorting
- backing up, backup transports
- adapters, custom receive adapters
- adapters, messages
- customizing, receive adapters
ms.assetid: 39e0bba6-81f5-4ae0-af92-837b225bc801
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abfb0b78065d4eb3aee022d141cc833399fc1496
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages"></a>Livraison chronologique des Messages
La livraison chronologique des messages garantit que les messages publiés dans la base de données MessageBox dans un ordre indiqué sont remis à chaque abonné correspondant dans le même ordre que celui dans lequel ils ont été publiés dans la base MessageBox.  
  
## <a name="configuring-ordered-message-delivery"></a>Configuration de la livraison chronologique des messages  
 La livraison chronologique des messages peut être configurée aux deux emplacements suivants :  
  
-   **Réception** forme dans une orchestration  
  
-   Port d'envoi  
  
## <a name="ordered-delivery-with-existing-transports"></a>Livraison chronologique des messages avec transports existants  
 Les protocoles sous-jacents de certains transports tels que FILE et HTTP ne sont pas cohérents avec la notion de livraison chronologique des messages. Toutefois, même avec de tels transports, si le port lié au transport est programmé pour une livraison chronologique des messages, BizTalk Server applique la livraison chronologique de force en faisant en sorte que le transport ne reçoive pas le message sortant suivant tant que l'envoi du message en cours n'a pas abouti. Pour y parvenir, BizTalk Server transmet chaque message à l’adaptateur de transport dans un lot unique et attend que l’adaptateur ait supprimé le message de la base MessageBox avant de lui transmettre le message suivant, dans un lot différent.  
  
### <a name="ordered-delivery-for-custom-adapters"></a>Livraison chronologique des messages pour des adaptateurs personnalisés  
 Les adaptateurs de réception personnalisés font l’objet de considérations particulières. Si vous écrivez un adaptateur personnalisé prenant en charge la livraison chronologique des messages à la réception, l’adaptateur doit effectuer les opérations suivantes :  
  
-   Après avoir soumis un lot de messages, recevoir votre carte doit attendre le **BatchComplete** rappel à partir de BizTalk Server avant de soumettre le lot suivant. Pour plus d’informations, consultez [Interfaces pour un adaptateur de réception Batch-Supported](../core/interfaces-for-a-batch-supported-receive-adapter.md).  
  
-   Si un message est en échec dans le pipeline, il doit être suspendu, de préférence d'une manière qui ne lui permet pas d’être repris. Utilisez le **BTS. SuspendAsNonResumable** propriété de contexte dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour marquer le message de manière appropriée.  
  
> [!NOTE]
>  La chronologie des messages peut être rompue si un message suspendu est repris plus tard. Si vous ne souhaitez pas que cela se produise, suspendez les messages ayant échoué d'une manière qui ne leur permette pas d’être repris.  
  
 Pour plus d’informations sur la création d’un adaptateur personnalisé, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).  
  
## <a name="conditions-for-end-to-end-ordered-message-processing"></a>Conditions pour le traitement d’une chronologie des messages de bout en bout  
 Pour garantir une livraison chronologique des messages de bout en bout, les conditions ci-dessous doivent être remplies :  
  
-   Les messages doivent être reçus avec un adaptateur qui conserve leur ordre d'arrivée lors de leur envoi à BizTalk Server. MSMQ et MQSeries sont des exemples de ces adaptateurs dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En outre, les adaptateurs HTTP ou SOAP permettent de soumettre des messages dans l'ordre, mais dans ce cas, le client HTTP ou SOAP doit appliquer l’ordre de force en soumettant les messages un par un.  
  
-   Vous devez vous abonner à ces messages avec un port d’envoi de la **livraison chronologique des messages** option définie sur `True`.  
  
-   Si une orchestration permet de traiter les messages, une seule instance de l’orchestration doivent être utilisés, l’orchestration doit être configurée pour utiliser un convoi séquentiel et la **livraison chronologique des messages** propriété de la port de réception de l’orchestration doit être défini sur `True`.  
  
## <a name="restrictions"></a>Restrictions  
 La livraison chronologique des messages n'est pas prise en charge dans les cas suivants :  
  
-   Ports d’envoi dynamique de [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] et les versions précédentes

- Ports d’envoi dynamique de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] (et les versions plus récentes) pour ceux les types de carte qui **ne** prise en charge de la livraison sur les ports d’envoi statiques chronologique
  
-   Transports secondaires  

  
## <a name="interactions"></a>Interactions  
 Lorsque la livraison chronologique est configurée pour un port d’envoi, soyez conscient des interactions possibles suivantes avec d’autres comportements configurés dans BizTalk Server :  
  
-   Pour le paramètre « Arrêter d'envoyer des messages supplémentaires en cas d'échec du message actuel » sur le même port d'envoi :  
  
    -   **La valeur est false.** seul le message ayant échoué est suspendu (d’une façon qui ne lui permet pas d’être repris) et tous les messages suivants continuent d’être traités. Cela préserve la chronologie des messages n’ayant pas échoué, mais peut provoquer l’apparition d’intervalles dans la séquence. Par exemple, si les commandes 101, 102 et 103 sont reçues et que la commande 102 est interrompue, les commandes 101 et 103 continueront à être traitées dans l'ordre.  
  
    -   **La valeur est true.** l'instance de port d'envoi est suspendue si le traitement d'un message échoue. Il en résulte la suspension de tous les messages suivants de l'ensemble chronologique de messages. La chronologie des messages est ainsi préservée puisque la livraison des messages suivants est interrompue jusqu'à livraison du message ayant échoué.  
  
-   Si le port d’envoi avec sollicitation-réponse est caractérisé par la propriété « Arrêter d'envoyer des messages supplémentaires en cas d'échec du message actuel » définie sur `true`, et que le traitement des échanges récupérables est configuré pour l’étape de désassemblage du pipeline de réception pour la réponse, le port d’envoi n’interrompt pas l’envoi des messages (c’est-à-dire que l’instance n’est pas suspendue) s’il existe une erreur récupérable lors du désassemblage de la réponse.  
  
-   Avant de supprimer un port d’envoi chronologique, assurez-vous qu’aucune instance ne lui est associée. Si des instances lui sont associées, elles doivent être terminées avant que vous ne puissiez supprimer le port d'envoi.  
  
## <a name="ordered-delivery-to-file-transport"></a>Livraison chronologique des messages pour le transport FILE  
 Les messages arrivent à l’adaptateur FILE dans l'ordre. L'adaptateur FILE peut ajouter des messages à un seul fichier ou écrire une séquence de fichiers, ce qui donne les résultats suivants :  
  
-   Si les données de message sont ajoutées à un fichier unique, des messages individuels sont ajoutés dans l’ordre. L'option de livraison chronologique sur un port d'envoi qui utilise l'adaptateur FILE est pertinente uniquement si le transport d'envoi fonctionne en mode Append.  
  
-   Si des messages sont écrits dans des fichiers individuels, l'ordre transparaît dans les noms de fichier, nommés séquentiellement. Dans ce cas, pour les fichiers écrits par l’adaptateur, les propriétés système du fichier relatives à la chronologie (par exemple l'heure de création ou de modification d'un fichier) ne reflètent pas obligatoirement la séquence d’arrivée du message.  
  
## <a name="performance-impact-of-ordered-delivery"></a>Impact de la livraison chronologique des messages sur les performances  
 Pour obtenir une livraison chronologique des fichiers, BizTalk Server doit sérialiser le traitement des messages ordonnés à des points différents du parcours du message. Cela fonctionne avec des techniques de déploiement, telles que l’utilisation de plusieurs instances d’hôte pour le traitement en parallèle des messages. Lorsque vous utilisez la livraison chronologique des messages, même les ports configurés pour s'exécuter sur plusieurs instances d'hôte ne s'exécutent que sur une seule instance d'hôte pour garantir une livraison chronologique des messages. Toutefois, dans cette situation, la haute disponibilité est conservée. En effet, si une instance d'hôte échoue lors du traitement d’une livraison chronologique des messages, le message ayant échoué sera de nouveau traité sur une autre instance d'hôte disponible.  
  
 Lorsque la livraison chronologique des messages est activé, la valeur par défaut **intervalle avant nouvelle tentative** est de 5 minutes. Pour améliorer les performances, configurez l’intervalle avant nouvelle tentative sur la valeur minimale, à savoir 1 minute. Le **intervalle avant nouvelle tentative** propriété peut accepter une valeur de zéro (0) mais de zéro (0) n’est pas valide. Le **Retry Count** peuvent également être paramétrées pour le nombre de tentatives que nécessaire. Par exemple, si vous savez que la requête doit normalement être traitée en <1 minute et si l’emplacement de destination du port d’envoi est toujours accessible, configurez les deux valeurs sur 1.  
  
 Pour modifier les valeurs de nouvelle tentative, accédez à [comment configurer les Options avancées de Transport pour un Port d’envoi](http://go.microsoft.com/fwlink/p/?LinkID=267697).  
  
 Pour plus d’informations sur l’option Livraison chronologique des messages, consultez les rubriques suivantes :  
  
 [BizTalk : De bout en bout chronologique des Options de traitement des messages](http://social.technet.microsoft.com/wiki/contents/articles/12887.biztalk-end-to-end-ordered-message-processing-options.aspx)  
  
 [BizTalk : Livraison chronologique des messages](http://social.technet.microsoft.com/wiki/contents/articles/6681.biztalk-ordered-delivery.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Livraison chronologique des Messages avec l’adaptateur MSMQ](../core/ordered-delivery-of-messages-with-the-msmq-adapter.md)   
 [Livraison chronologique des Messages avec l’adaptateur MQSeries](../core/ordered-delivery-of-messages-with-the-mqseries-adapter.md)