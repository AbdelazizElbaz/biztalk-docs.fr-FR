---
title: Comment configurer la forme envoi | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Send shape [Orchestration Designer], delivery notification
- send ports, delivery notifications
- configuring [Orchestration Designer], Send shapes
- Send shape [Orchestration Designer], configuring
- delivery notification
- messages, delivery notification
ms.assetid: 2cf4755b-1cfc-484e-bd9c-c9f3855af556
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c32711b841b915d793e5c8a22ffe9513e2ec28d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-send-shape"></a>Configuration de la forme Envoi
![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")  
Forme Envoi  
  
 Si vous vous attendez à recevoir une réponse indirecte ou asynchrone au message envoyé (sans passer par un port de requête-réponse), vous devez mettre le message en corrélation avec l'instance d'orchestration en cours d'exécution, afin que la réponse puisse être dirigée vers l'instance appropriée. Vous pouvez appliquer un suivant ensemble de corrélations pour le **envoyer** forme pour une corrélation précédemment initialisée, ou vous pouvez appliquer un ensemble de corrélations initial. Pour plus d’informations, consultez [à l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md).  
  
### <a name="to-configure-a-send-shape"></a>Pour configurer une forme Envoi  
  
1.  Définissez un message et une opération de port.  
  
    1.  Dans la fenêtre Vue Orchestration, vérifiez que votre orchestration comporte à la fois un message et une opération de port définis pour le type de message à parties multiples envoyé.  
  
    2.  Dans la fenêtre Propriétés, sélectionnez le message à envoyer à partir de la **Message** liste de propriétés de liste déroulante.  
  
    3.  Dans la fenêtre Propriétés, sélectionnez l’opération de port qui envoie le message à partir de la **opération de Port** liste déroulante.  
  
         — Ou :  
  
         Faites glisser le connecteur d’envoi à partir de la **envoyer** forme pour le socket de port qui envoie le message.  
  
2.  Spécifier les ensembles de corrélations pour limiter les messages le **envoyer** forme enverra ou pour initialiser les valeurs dans un ensemble de corrélations.  
  
    1.  Pour chaque ensemble de corrélations que vous souhaitez utiliser, vérifiez une corrélation défini dans la liste déroulante sur le **ensembles de corrélations suivants** propriété.  
  
    2.  Pour chaque correspondance de jeu que vous souhaitez initialiser, vérifiez une corrélation défini dans la liste déroulante sur le **l’initialisation des ensembles de corrélations** propriété.  
  
## <a name="delivery-notification"></a>Accusé de réception  
 Pour vérifier qu'un message a été envoyé correctement sur un port d'envoi, procédez selon les étapes suivantes :  
  
1.  Placez votre forme Envoi dans une étendue non transactionnelle, à long terme ou atomique.  
  
2.  Sur votre port d’envoi, définissez la propriété accusé de réception **transmis**.  
  
3.  Ajoutez un gestionnaire catch à votre étendue pour gérer une exception DeliveryFailureException.  
  
    > [!NOTE]
    >  Si la forme envoi est contenue dans une étendue atomique, l’exception DeliveryFailureException peut toujours être interceptée, mais nécessite une forme étendue externe être ajoutés à un Type de Transaction que la valeur **Long terme** ou **aucun** . Les étendues atomiques ne sont pas en mesure d’intercepter les exceptions directement.  
  
 L’orchestration attend l’accusé de réception à la fin de l'étendue non atomique associée, ou à la fin de l'orchestration, pour recevoir l’accusé de réception.  
  
> [!NOTE]
>  Cela s'applique uniquement aux opérations unidirectionnelles ; un échec dans une opération bidirectionnelle (requête-réponse) donne lieu à une exception SoapException (accusé de réception négatif) même sans qu'un attribut de port ne soit défini.  
  
> [!NOTE]
>  L'accusé de réception n'est pas pris en charge pour la liaison directe.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs](../core/error-handling.md)