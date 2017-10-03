---
title: Adaptateurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- adapters
- send adapters
- adapters, about adapters
- send adapters, about send adapters
- receive adapters, about receive adapters
- adapters, adapter framework
- receive adapters
- adapters, send adapters
ms.assetid: 7803a806-3396-4662-877f-eae11cb5e3e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a7f58a9d67b9702cfbb7b21788f751717ac61e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapters"></a>Adaptateurs
Pour échanger des messages avec des systèmes externes, des applications et des entités, Microsoft BizTalk Server fait appel aux adaptateurs. *Adaptateurs* sont COM ou. Les composants NET qui transfèrent les messages vers et à partir de la terminaison de l’entreprise (par exemple, les systèmes de fichiers, les bases de données et les applications d’entreprise personnalisées) à l’aide de divers protocoles de communication.  
  
 BizTalk Server les utilisent pour échanger des messages avec des entités externes dans le cadre d'opérations d'envoi et de réception  
  
-   Les opérations d'envoi (ou côté envoi) ont lieu lorsque des informations sont envoyées par BizTalk Server à une entité externe à l'aide des divers protocoles pris en charge par l'adaptateur.  
  
-   Les opérations de réception (ou côté réception) ont lieu lorsque l'adaptateur reçoit des informations provenant d'une entité externe et les transmet au moteur de messagerie BizTalk Server.  
  
## <a name="the-adapter-framework"></a>Infrastructure de l'adaptateur  
 La figure suivante montre comment fonctionnent un adaptateur et l'infrastructure d'adaptateurs pour connecter votre application à BizTalk Server.  
  
1.  Les données sont reçues à un emplacement de réception qui écoute les messages d'un protocole donné à une adresse spécifiée. Cet emplacement de réception est associé à un adaptateur et à un pipeline de réception. Vous pouvez configurer à la fois l'adaptateur et les composants de pipeline pour appliquer une logique spécifique aux messages associés à un protocole prédéterminé.  
  
2.  Une fois que le message a été reçu à l'emplacement de réception, il est transmis à l'adaptateur, qui, à sont tour, crée un message BizTalk Server. L'adaptateur joint ensuite le flux de données au message (généralement dans le corps du message), ajoute les métadonnées appartenant au point de terminaison depuis lequel les données ont été reçues, puis soumet le message au moteur de messagerie BizTalk.  
  
3.  Le moteur de messagerie envoie le message au pipeline de réception au sein duquel plusieurs opérations ont lieu : conversion des données au format XML, authentification de l'expéditeur du message, décryptage du message et validation des données XML.  
  
4.  Le moteur de messagerie publie le message dans la MessageBox. Cette base de données est une table Microsoft SQL Server qui contient les messages à traiter. Les orchestrations et les ports d'envoi peuvent s'y abonner.  
  
5.  Le moteur de messagerie envoie le message soit à une orchestration, soit à un port d'envoi abonné en fonction des propriétés de contexte du message correspondant aux spécifications définies dans le filtre de l'abonné.  
  
6.  Si une orchestration est l’abonné, il traite le message et l’envoie à l’aide d’un port d’envoi. Une fois que le port d'envoi a envoyé le message ou s'il n'est que le seul abonné, le message passe par le pipeline d'envoi, puis par un adaptateur d'envoi avant d'être transmis sur le réseau.  
  
 Infrastructure de l'adaptateur  
  
 ![L’infrastructure d’adaptateurs](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")  
  
## <a name="receive-adapters"></a>Adaptateurs de réception  
 Un adaptateur de réception est chargé de créer un message BizTalk Server en joignant le flux de données réseau/sources au corps du message. Il ajoute également les métadonnées pertinentes au point de terminaison sur lequel les données a été reçues, puis soumet le message au moteur de messagerie.  
  
 L'adaptateur supprime les données du point de terminaison de réception ou envoie l'accusé de réception approprié au client en lui indiquant que les données ont été acceptées dans BizTalk Server.  
  
## <a name="send-adapters"></a>Adaptateur d'envoi  
 Un adaptateur d'envoi est chargé d'envoyer un message BizTalk à un point de terminaison spécifié à l'aide d'un protocole qui lui est spécifique.  
  
 Pour plus d’informations à propos des adaptateurs, la structure d’un adaptateur et l’écriture des adaptateurs personnalisés, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Artefacts](../core/artifacts.md)