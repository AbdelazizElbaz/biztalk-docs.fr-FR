---
title: "Comment activer le routage pour les Messages ayant échoué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d33beed4-1ae2-4282-95ac-5d68aab7fb5d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bfa76ba9378bc2177b31fac085b603971232840
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-routing-for-failed-messages"></a>Activation du routage pour les messages ayant échoué
Le routage des messages ayant échoué est une propriété des ports d'envoi et de réception. Il est activé par l'intermédiaire de l'option « Activer le routage pour les messages ayant échoué » de la page de propriétés de ces ports.  
  
> [!NOTE]
>  La configuration d'un port de réception s'applique à tous les emplacements de réception qui lui sont associés.  
  
> [!NOTE]
>  La configuration d'un port d'envoi s'applique à la fois aux transports principaux et secondaires.  
  
### <a name="to-configure-failed-message-routing-for-a-receive-port-this-applies-to-both-one-way-and-request-response-receive-ports"></a>Pour configurer le routage des messages ayant échoué pour un port de réception (unidirectionnel ou de requête-réponse)  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application à laquelle appartient le port d’envoi.  
  
3.  Cliquez sur le **Ports de réception** dossier.  
  
4.  Dans le volet de droite, double-cliquez sur le nom du port de réception à configurer.  
  
5.  Sur la page de propriétés du port de réception, dans le volet gauche, sélectionnez le **général** catégorie.  
  
6.  Dans le volet droit, sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, puis cliquez sur **appliquer**.  
  
### <a name="to-configure-failed-message-routing-for-a-send-port-this-applies-only-to-static-one-way-and-static-solicit-response-send-ports"></a>Pour configurer le routage des messages ayant échoué pour un port d'envoi (unidirectionnel statique ou de sollicitation-réponse statique uniquement)  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application à laquelle appartient le port d’envoi.  
  
3.  Cliquez sur le **Ports d’envoi** dossier.  
  
4.  Dans le volet de droite, double-cliquez sur le nom du port d'envoi à configurer.  
  
5.  Page des propriétés du port d’envoi dans le volet gauche, sélectionnez le **Options avancées de Transport** catégorie.  
  
6.  Dans le volet droit, dans le **Options de Transport** zone de groupe, sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, puis cliquez sur **appliquer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs](../core/error-handling.md)