---
title: Extension de messages volumineux Message Queuing BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Message Queuing Large Message Extension
- utilities, BizTalk Message Queuing Large Message Extension
ms.assetid: 5d6892d3-fda8-41a3-8111-d28c11bd71fb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 399c8e02d59a931dbf30bfa31ca28980dfa312be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-message-queuing-large-message-extension"></a>extension de messages volumineux Message Queuing BizTalk
Natif message queuing ne peut pas traiter un message avec un corps supérieur à 4megabytes (Mo). Cependant, Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un composant additionnel pour Message Queuing en mode natif qui autorise le traitement des messages de plus de 4 Mo. Ce module complémentaire est fournie en tant que le fichier Mqrtlarge.dll et expose le **MQSendLargeMessage** et **MQReceiveLargeMessage** application programming interfaces (API) et le modèle COM analogue. Ces fonctions sont implémentées en tant qu’API, message queuing standard **MQSendMessage** et **MQReceiveMessage** respectivement.  
  
 Pour que l'ordinateur Message Queuing puisse participer aux échanges de messages volumineux, il faut que le fichier Mqrtlarge.dll y soit installé et que l'application Message Queuing utilise les interfaces API du composant additionnel. À défaut, ces messages sont fragmentés.  
  
 **Emplacement dans le Kit de développement logiciel**  
  
 \<*Chemin d’installation*\>\SDK\ Mqrtlarge.dll  
  
 **Inventaire des fichiers**  
  
 Le tableau suivant présente le fichier utilisé par cet utilitaire et décrit sa finalité.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Mqrtlarge.dll|Une bibliothèque de liens dynamiques Win32 qui expose **MQSendLargeMessage** et **MQReceiveLargeMessage**.<br /><br /> Les fichiers d’en-tête se trouvent dans le  *\<chemin d’Installation\>*répertoire \SDK\Include. **Remarque :** vous devez installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur une version 64 bits de Windows pour accéder à la version 64 bits de Mqrtlarge.dll.|  
  
 **À l’aide de cet utilitaire**  
  
 Suivez la procédure suivante pour exécuter le fichier Mqrtlarge.dll.  
  
### <a name="to-use-the-mqrtlargedll-file"></a>Pour utiliser le fichier Mqrtlarge.dll  
  
1.  > [!NOTE]
    >  Une solution MSMQ sans BizTalk Server, MQRTLarge.dll peut toujours fonctionner correctement. Toutefois, cette configuration n’est pas recommandée qui prend en charge de Microsoft et des résultats inattendus peuvent se produire si utilisé en dehors de l’environnement BizTalk Server.  
  
     Ajoutez le fichier Mqrtlarge.dll à l'ordinateur qui ne contient pas d'installation de BizTalk Server. Message Queuing se sert du fichier Mqrtlarge.dll pour envoyer des messages à BizTalk Server ou en recevoir.  
  
2.  Pour accéder aux API du fichier Mqrtlarge.dll, ajoutez une référence au fichier Mqrtlarge.dll dans les applications qui envoient ou reçoivent les messages vers ou depuis d'autres ordinateurs au niveau du point de terminaison Message Queuing BizTalk.  
  
 **Section Notes**  
  
 Les messages volumineux sont envoyés vers les files d'attente Message Queuing (ou MSMQ) standard. Il est conseillé de n'utiliser que les API de messages volumineux sur ces files d'attente, bien que cela ne soit pas obligatoire.  
  
 Vous pouvez toujours utiliser **MQSendMessage** pour envoyer des messages à une file d’attente à laquelle vous avez envoyé des messages volumineux. De même, vous pouvez utiliser **MQReceiveMessage** pour recevoir des messages à partir de ces files d’attente, bien qu’il n’est pas recommandé, car il peut affecter les performances de la **MQReceiveLargeMessage** API.  
  
 À des fins de récupération, il est recommandé d’utiliser **DEAD_LETTER** la journalisation.  
  
 **Fragmentation**  
  
 En règle générale, un message volumineux est fragmenté en plusieurs messages, chacun de taille inférieure à 4 Mo. Il est important de comprendre que seul le corps fait l'objet d'une fragmentation. Le reste des propriétés est envoyé avec chaque fragment.  
  
 Le nombre de fragments est fonction de la taille du message et de celle des fragments. La taille des fragments peut être automatiquement définie par le fichier Mqrtlarge.dll ou par la partie appropriée de Message Queuing BizTalk. Les applications peuvent également indiquer cette taille de manière explicite.  
  
 Notez que l'extension de messages volumineux implique d'étendre le message en lui ajoutant des données internes supplémentaires de taille constante.  
  
 **PROPID_M_EXTENSION**  
  
 Vous pouvez utiliser la **PROPID_M_EXTENSION/PROPID_M_EXTENSION_LEN** propriétés pour signer le message. La signature compose de 40 octets (B). Le tableau suivant montre les fragments de signature.  
  
| Description|Taille|  
|-----------------|----------|  
|Identificateur global unique (GUID) indiquant que ce message a été envoyé à l’aide de **MQSendLargeMessage**|16 B|  
|GUID pour le message : ID unique pour chaque message volumineux qui est commune à toutes les parties du message|16 B|  
|Taille totale du message volumineux|4 B|  
|Numéro de la partie|2 B|  
|Nombre de parties du message|2 B|  
  
 La décision d’utiliser **PROPID_M_EXTENSION** présente d’autres. Le pont MSMQ-MQSeries Microsoft Host Integration Server utilise cette propriété pour transmettre une structure contenant les propriétés qui ne font pas l'objet d'un mappage direct entre les messages MQSeries et Message Queuing. Toutes les applications qui envoient des messages vers et depuis MQSeries utilisent, de manière explicite ou implicite, cette structure. Message Queuing peut générer un accusé de réception lorsqu'un message est reçu depuis une file d'attente par une application réceptrice. Les accusés de réception sont envoyés vers la file d'attente spécifiée par l'application émettrice. Dans le cas de messages volumineux, cet accusé est uniquement envoyé pour la dernière partie du message.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires du SDK](../core/utilities-in-the-sdk.md)