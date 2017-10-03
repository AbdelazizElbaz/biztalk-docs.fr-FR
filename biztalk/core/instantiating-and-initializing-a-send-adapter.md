---
title: "Instanciation et initialisation d’un adaptateur d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f10e6507-3351-4173-95f5-48546ca5f5c4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ed590b73d31a03a4b3316a4d84edfc1e39eb0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-and-initializing-a-send-adapter"></a>Instanciation et initialisation d'un adaptateur d'envoi
Par défaut, les adaptateurs d'envoi ne sont pas instanciés tant qu'un premier message ne leur a pas été remis. Ce processus est appelé « création différée ». L'approche de création différée par défaut permet de préserver les ressources système. Une fois l'adaptateur d'envoi créé, il est mis en cache et est actif jusqu'à ce que le service BizTalk Server soit arrêté.  
  
 Le **InitTransmitterOnServiceStart** membre de la **fonctionnalités** énumération dirige le moteur de messagerie pour créer l’adaptateur d’envoi sur le démarrage du service, au lieu d’utiliser la création différée par défaut, Si cela est nécessaire.  
  
 L'envoi d'un message diffère de la réception en ce qui concerne le traitement par lots des messages. Lors de la réception, l'adaptateur dispose de messages entrants à insérer dans un lot transmis par le moteur de messagerie. Dans le cas de l'envoi, le moteur de messagerie reçoit un lot de la part de l'adaptateur et envoie les messages à l'adaptateur pour transmission. Les deux processus utilisent le proxy de transport pour obtenir les objets du lot de messages.  
  
## <a name="how-a-send-adapter-is-initialized"></a>Initialisation d'un adaptateur d'envoi  
 Pour permettre la configuration et la liaison vers le proxy de transport, les adaptateurs doivent implémenter les interfaces de configuration suivantes :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
 Les étapes suivantes décrivent la séquence d'événements impliqués dans l'initialisation d'un adaptateur d'envoi :  
  
1.  Lorsque le moteur de messagerie Initialise un adaptateur d’envoi, elle effectue d’abord un **QueryInterface** pour **IPersistPropertyBag**, qui est une interface facultative. Si l’adaptateur implémente l’interface, la configuration du gestionnaire est transmise à l’adaptateur dans le **charge** appel de méthode. L'adaptateur utilise ces informations pour vérifier sa bonne configuration.  
  
2.  Le moteur de messagerie effectue une **QueryInterface** pour **IBTTransportControl**, qui est une interface obligatoire.  
  
3.  Le moteur appelle **IBTTransportControl.Initialize**, en passant le proxy de transport pour la carte.  
  
4.  Le moteur de messagerie effectue une **QueryInterface** pour **IBTTransmitter**.  
  
     Si le moteur de messagerie découvre cette interface, l'adaptateur est traité comme un émetteur ne dépendant pas des lots.  
  
     Si le moteur de messagerie ne découvre pas cette interface, le moteur de messagerie effectue une **QueryInterface** pour **IBTBatchTransmitter**, dont la découverte indique que l’adaptateur est un lot prenant en charge émetteur.  
  
     Si le moteur de messagerie ne découvre aucune de ces interfaces, une erreur survient, qui entraîne l'échec de l'initialisation. L'initialisation échoue si les interfaces obligatoires ne sont pas découvertes.  
  
 Le schéma ci-dessous illustre cette séquence d'appels d'API. Les interfaces en bleu sont implémentées par l'adaptateur.  
  
 ![](../core/media/transmit-adapter-init.gif "Transmit_adapter_init")  
  
 L'adaptateur peut envoyer des messages dès qu'il est initialisé et configuré.  
  
 Le schéma ci-dessous indique les interactions d'objets impliquées dans l'initialisation d'un adaptateur d'envoi.  
  
 ![](../core/media/ebiz-sdk-devadapter10.gif "ebiz_sdk_devadapter10")  
Workflow d'initialisation d'un adaptateur d'envoi  
  
> [!NOTE]
>  Adaptateurs ne doivent pas empêcher le moteur de messagerie telles que **IBTTransportControl.Initialize** et **IPersistPropertyBag.Load**. Un traitement excessif dans ces appels peut avoir un impact négatif sur le délai de démarrage du service.