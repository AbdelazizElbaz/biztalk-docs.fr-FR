---
title: "Livraison chronologique des Messages avec l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MQSeries adapters, ordered delivery
ms.assetid: 517ff2a4-7315-43b5-8d4b-7494adf141e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8b602adf93152f6af1e5dbbc576180d570a4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages-with-the-mqseries-adapter"></a>Livraison chronologique des messages à l'aide de l'adaptateur MQSeries Adapter
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit un **livraison chronologique des messages** option statique pour les ports d’envoi. Définition de la **livraison chronologique des messages** option sur un port d’envoi à **True** permet de s’assurer que BizTalk Server remet les messages au port d’envoi dans le même ordre qu’ils sont publiés dans la base de données MessageBox de BizTalk. Pour garantir une livraison chronologique des messages de bout en bout, les conditions ci-dessous doivent être remplies :  
  
-   Les messages doivent être reçus avec un adaptateur qui conserve leur ordre d'arrivée lors de leur envoi à BizTalk Server. Par exemple, lors de la réception des messages avec l’adaptateur de réception MQSeries, l’emplacement de réception doit être configuré avec l’option **classer avec arrêt** ou **classer avec suspension**.  
  
-   Vous devez vous abonner à ces messages avec un port d’envoi de la **livraison chronologique des messages** option **True**.  
  
-   Si une orchestration permet de traiter les messages, une seule instance de l’orchestration doivent être utilisés, l’orchestration doit être configurée pour utiliser un convoi séquentiel et la **livraison chronologique des messages** propriété de la port de réception de l’orchestration doit être défini sur **True**.  
  
## <a name="using-the-mqseries-adapter-for-ordered-delivery-of-messages"></a>Utilisation de l'adaptateur MQSeries pour la livraison chronologique des messages  
 L'adaptateur de réception MQSeries offre une prise en charge de la conservation de l'ordre des messages lors de leur envoi à BizTalk Server. Bout en bout chronologique de remise des messages via BizTalk Server peut être obtenue lors de leur réception avec l’adaptateur MQSeries si les messages sont traités par un port d’envoi configuré avec le **livraison chronologique des messages** option définie sur **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md)   
 [Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)