---
title: "Livraison chronologique des Messages avec l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MSMQ adapters, ordered delivery
ms.assetid: e8dafc76-e894-4120-9cea-d014d635850e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac842fcd1e9b386fa885844f3a797504ed7c4c3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages-with-the-msmq-adapter"></a>Livraison chronologique des Messages avec l’adaptateur MSMQ
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit un **livraison chronologique des messages** option statique pour les ports d’envoi. Définition de la **livraison chronologique des messages** option sur un port d’envoi à **True** permet de s’assurer que BizTalk Server remet les messages au port d’envoi dans le même ordre qu’ils sont publiés dans la base de données MessageBox. Pour garantir une livraison chronologique des messages de bout en bout, les conditions ci-dessous doivent être remplies :  
  
-   Les messages doivent être reçus avec un adaptateur qui conserve leur ordre d'arrivée lors de leur envoi à BizTalk Server.  
  
-   Vous devez vous abonner à ces messages avec un port d’envoi de la **livraison chronologique des messages** option **True**.  
  
-   Si une orchestration permet de traiter les messages, une seule instance de l’orchestration doivent être utilisés, l’orchestration doit être configurée pour utiliser un convoi séquentiel et la **livraison chronologique des messages** propriété de la port de réception de l’orchestration doit être défini sur **True**.  
  
## <a name="using-the-msmq-adapter-for-ordered-delivery-of-messages"></a>Utilisation de l'adaptateur MSMQ pour la livraison chronologique des messages  
 L'adaptateur de réception MSMQ offre une prise en charge de la conservation de l'ordre des messages lors de leur envoi à BizTalk Server. Bout en bout chronologique de remise des messages via BizTalk Server peut être obtenue lors de leur réception avec l’adaptateur MSMQ si les messages sont traités par un port d’envoi configuré avec le **livraison chronologique des messages** lavaleurd’option **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md)   
 [Pour configurer un MSMQ emplacement de réception](../core/how-to-configure-an-msmq-receive-location.md)