---
title: "Meilleures pratiques pour les paramètres de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e62024e1-f502-45a8-932f-edd8460bcf5f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf1f89ced33be6f10ceaae37ccb2c899c4e01eac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-biztalk-server-settings"></a>Meilleures pratiques pour les paramètres de BizTalk Server
Cette rubrique répertorie les meilleures pratiques à suivre quand vous effectuez les procédures de préparation opérationnel pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Configurer le traitement par lots du message pour augmenter les performances de l’adaptateur**  
  
-   Réduisez le nombre de transactions effectuées par un adaptateur en combinant plusieurs opérations dans un lot unique.  
  
-   Limiter la taille de lot en fonction du nombre total d’octets dans le lot, en plus du nombre de messages. Pour plus d’informations sur la limitation de la taille de lot, consultez [configurer le traitement par lot pour améliorer les performances de l’adaptateur](../technical-guides/configuring-batching-to-improve-adapter-performance.md).  
  
 **Ajustez le seuil de messages volumineux**  
  
-   Pour améliorer le débit, augmentez le seuil de messages volumineux, ce qui réduit le nombre de messages volumineux qui sont en mémoire tampon sur le disque lors du mappage.  
  
 **Déterminer les informations que vous devez suivre lors de la planification**  
  
-   Pendant les phases de planification, vous devez déterminer les informations que vous avez besoin pour effectuer le suivi. Ainsi, après avoir déployé le projet, vous pouvez définir les options de suivi et limiter la quantité de données suivies afin de vous donner uniquement les informations que vous avez besoin.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur les meilleures pratiques relatives au suivi, consultez [planification pour le suivi](../technical-guides/planning-for-tracking.md) dans ce guide et [suivi des activités et](http://go.microsoft.com/fwlink/p/?LinkId=154187) (http://go.microsoft.com/fwlink/p/?LinkId=154187).  
  
 **Ne suivez pas tous les messages**  
  
-   Nous vous recommandons de pas suivre tous les messages. Il s’agit, car chaque fois qu’un message est couvertes, BizTalk Server effectue une autre copie du message. Vous pouvez limiter à la place de la portée en effectuant le suivi d’un port spécifique uniquement. Cela permet d’optimiser les performances de votre système et de conserver les bases de données ne soit pas encombré.  
  
 **Définition du suivi sur les ports d’envoi et ports au lieu d’un pipeline de réception**  
  
-   Si vous définissez des options de suivi sur les pipelines, vous allez également définir les options de suivi global pour tous les ports qui utilise le pipeline. Cela peut à son tour entraîner beaucoup plus de données en cours de suivi que vous avez l’intention, qui ralentit les performances du système. Au lieu de cela, vous pouvez définir les options de suivi de l’envoi de ports et les ports de réception.  
  
 **Ajuster la limitation basée sur l’utilisation des ressources**  
  
-   La limitation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est configuré par défaut pour fournir une protection intégrée satisfaisante du système. Surveillez les compteurs de performances pour la limitation des États pour voir si la limitation est en cours. Évaluer par vous-même si la ressource sur laquelle la limitation est basée (par exemple, la base de données d’utilisation de taille ou de la mémoire) est sous ou surutilisée. Ensuite, ajustez la limitation les seuils au-dessus ou au-dessous. Pour plus d’informations, consultez [ajuster les seuils de limitation : quand et pourquoi](http://go.microsoft.com/fwlink/p/?LinkId=154188) (http://go.microsoft.com/fwlink/p/?LinkId=154188).  
  
 **Utilisez le pipeline PassThruTransmit si possible**  
  
-   Si aucun traitement de document n’est requis avant d’envoyer un message vers sa destination, utilisez le pipeline PassThruTransmit au lieu du pipeline d’envoi XML.  
  
 **Réduire l’utilisation de l’orchestration « de début de la forme et de fin » suivi d’événements**  
  
-   Lors de la forme de suivi de l’orchestration présente des avantages évidents pour le débogage de l’orchestration, il a des implications en matière d’évolutivité et de performances. Le **forme début et fin** le suivi des événements peuvent provoquer un surcroît de traitement. Il est préférable réduire son utilisation dans des environnements de production où un débit élevé est nécessaire.  
  
    > [!NOTE]  
    >  **La forme début et fin** événements de suivi sont activées par défaut sur toutes les orchestrations.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)