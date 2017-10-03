---
title: "Comment configurer un Port d’envoi MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, send ports
- send ports, MSMQ adapters
- configuring [MSMQ adapters], send ports
ms.assetid: 37313d45-8148-4aaf-a3f2-ea05b3b8b448
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1281426116d3b83730fd98a355d1d1b78ac24c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-send-port"></a>Comment configurer un Port d’envoi MSMQ
La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de définir des variables d'adaptateur de port d'envoi MSMQ. Si aucune propriété n'est définie pour le port d'envoi, les valeurs par défaut du gestionnaire d'envoi définies dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont utilisées.  
  
> [!IMPORTANT]
>  Si une instance de l'hôte est associée à un port d'envoi ou à un emplacement de réception MSMQ, vérifiez que le service MSMQ est en cours d'exécution sur cet ordinateur. Si le service ne fonctionne pas, les ports de réception MSMQ sont fermés peu de temps après leur démarrage, et l'envoi de messages aux ports d'envoi MSMQ est suspendu.  
>   
>  Dans un scénario de mise en cluster, non seulement l'instance MSMQ en cluster doit être en cours d'exécution, mais le service MSMQ sur chaque ordinateur du cluster doit l'être également.  
  
## <a name="to-configure-variables-for-an-msmq-send-port"></a>Pour configurer des variables pour un port d'envoi MSMQ  
 Pour configurer des variables pour un port d'envoi MSMQ, procédez comme suit :  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md) pour plus d’informations. Configurer toutes les options de port d'envoi. Sur le **général** sous l’onglet du **Transport** section, spécifiez **MSMQ** pour le **Type** option.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans le **propriétés du Transport MSMQ** boîte de dialogue zone, procédez comme suit :  
  
    |Utilisez cette propriété.|Pour effectuer cette opération|Type de données|Valeur par défaut|  
    |-----------------------|----------------|---------------|-------------------|  
    |**Mot de passe**|Définir le mot de passe à utiliser pour une file d'attente distante. Utiliser avec **nom d’utilisateur**.|Chaîne|Vide|  
    |**Nom d'utilisateur**|Définir le nom d'utilisateur à utiliser pour une file d'attente distante. Utiliser avec **mot de passe**. Vous ne pouvez pas indiquer ici le nom de l'utilisateur local de l'ordinateur distant.|Chaîne|Vide|  
    |**Type d’accusé de réception**|Indiquer le type d'accusé de réception que Message Queuing doit retourner à l'application émettrice. Vous pouvez choisir plusieurs types d'accusés de réception. Les types d’accusé de réception dans le **System.Messaging.AcknowledgeTypes** énumération sont disponibles.|Chaîne|Aucune|  
    |**File d’attente d’administration**|Indiquer le nom de la file d'attente qui reçoit l'accusé de réception.|Chaîne|Vide|  
    |**Type de corps**|Spécifier le type du corps de message dans MSMQ. Les valeurs valides sont membres du .NET **VarEnum** énumération.|int|8209|  
    |**Empreinte numérique du certificat**|Indiquer l'empreinte de certificat à utiliser pour l'authentification des messages. Utilisez cette propriété conjointement avec la **utiliser l’authentification** propriété pour vérifier les messages. Utilisez le **nom d’utilisateur** et **mot de passe** propriétés pour accéder aux files d’attente.|Chaîne|Vide|  
    |**File d’attente de destination**|Spécifier la file d'attente de destination. Pour plus d’informations sur les files d’attente, consultez [les files d’attente Message Queuing](../core/message-queuing-queues.md). **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|Chaîne|Vide|  
    |**Algorithme de chiffrement**|Sélectionnez **RC2**, **RC4**, ou **aucun** pour l’algorithme de chiffrement.|Enum|Aucune|  
    |**Taille maximale des messages (en kilo-octets)**|Indiquer la taille maximale des messages que vous envoyez à la file d'attente spécifiée.|UnsignedInt|1024|  
    |**Priorité du message**|Définir la priorité du message.|Enum|Normale|  
    |**Récupérables**|Spécifiez s’il faut garantir la récupération d’un message.|Booléen|False|  
    |**Segmentation de prise en charge**|Définissez cette valeur de propriété booléenne sur **True** pour segmenter les messages supérieurs à 4 Mo.|Booléen|False|  
    |**Délai d'expiration**|Indiquer le délai maximal pendant lequel attendre que les messages atteignent la file d'attente de destination. Cette option n'est valable que si vous utilisez des transactions.|int|0|  
    |**Unité de délai d’attente**|Définir l’unité à utiliser pour le **délai d’attente** propriété.<br /><br /> Sélectionnez **jours**, **heures**, **Minutes**, ou **secondes**.|Enum|Jours|  
    |**Transactionnelle**|Définissez cette valeur sur **True** pour envoyer des messages si vous utilisez des transactions.|Booléen|False|  
    |**Utiliser l’authentification**|Définissez cette valeur de propriété booléenne sur **True** pour contrôler l’authentification. Utilisez cette propriété conjointement avec la **empreinte numérique du certificat** propriété pour vérifier les messages. Utilisez le **nom d’utilisateur** et **mot de passe** propriétés pour accéder aux files d’attente.|Booléen|False|  
    |**Utiliser la file d’attente de lettres mortes**|Définissez cette valeur sur **True** pour envoyer des messages à la file d’attente de lettres mortes si une défaillance se produit.|Booléen|True|  
    |**Utiliser la file d’attente du Journal**|Définissez cette valeur sur **True** pour enregistrer une copie du message chaque fois que le message est traité.|Booléen|False|  
  
4.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer un MSMQ emplacement de réception](../core/how-to-configure-an-msmq-receive-location.md)   
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)