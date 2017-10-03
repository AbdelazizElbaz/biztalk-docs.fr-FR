---
title: Optimisation de la Configuration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Concurrent Calls parameter
- optimizing, configuration
- configuring, optimizing
- messages, overload protection
ms.assetid: df0ae17b-fcfa-4e00-893c-63f4972d3822
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72b185d7738ac48d9a1dc3631c7c9faec9ac4b60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-configuration"></a>Optimisation de la Configuration
Cette section contient des informations sur l'optimisation de la configuration de l'adaptateur BizTalk pour PeopleSoft Enterprise ainsi que des descriptions de paramètres permettant de configurer celui-ci.  
  
## <a name="message-overload-protection"></a>Protection contre la surcharge du message  
 Le paramètre `Max Concurrent Calls` est une fonctionnalité permettant d'optimiser votre configuration. Vous pouvez utiliser ce paramètre dans les instances où le débit dépasse les capacités du traitement principal. Vous pouvez ajouter le paramètre aux adaptateurs dans le **propriétés de Port d’envoi** boîte de dialogue pour activer la protection contre les surcharges de message. La valeur par défaut est -1 : les messages sont illimités.  
  
 Lorsque BizTalk Server envoie des messages à l'adaptateur de transmission, il reçoit tout d'abord un lot de l'adaptateur, puis appelle `TransmitMessage()` sur le lot pour transmettre chaque message. Ensuite, BizTalk Server appelle `Done()` sur le lot et l'adaptateur commence à transmettre les messages au système principal. Si BizTalk Server obtient plusieurs lots avant l'appel de `Done`, la commande `Done` ne peut jamais se produire. En définissant le nombre maximal de messages dans un lot, vous pouvez contrôler les messages transmis au système principal. La modification de ce paramètre entre en vigueur dans une minute. BizTalk Server doit récupérer les modifications de la configuration de l'adaptateur enregistrée dans la base de données SQL.  
  
#### <a name="to-change-the-max-concurrent-calls-parameter"></a>Pour modifier le paramètre Nombre maximal d'appels simultanés  
  
1.  Dans le **propriétés de Port d’envoi** boîte de dialogue, entrez un **connexion** valeur.  
  
     La valeur par défaut est 40 sessions. Si vous indiquez une valeur inférieure, une dégradation des performances d'exécution peut se produire. L'inverse est également vrai : une valeur supérieure risque de provoquer le dépassement des capacités du serveur et de générer des erreurs d'exécution.  
  
2.  Sélectionnez **Oui** pour **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.  
  
     Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.  
  
     Le **actualiser l’Agent** paramètre actualise les agents de navigation et les moment de l’exécution. Le processus runtimeagent.exe effectue la mise à jour après un délai d'une minute ou à l'appel Envoyer suivant.  
  
3.  Renseignez les informations d'identification pour accéder au système PeopleSoft.  
  
     Deux méthodes permettent d'accéder au système :  
  
    -   les informations d'identification de connexion (paramètres de connexion des propriétés du transport) ;  
  
    -   authentification unique (SSO, Single Sign-On)  
  
4.  Sélectionnez **Oui** pour **utiliser SSO** à utiliser l’authentification unique.  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [à l’aide de l’authentification unique sur](../core/using-single-sign-on2.md).  
  
5.  Sélectionnez une application associée sur la liste.  
  
     Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que PeopleSoft. L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise utilise les informations d'identification d'un utilisateur d'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée. Les informations d'identification sont celles de l'utilisateur (utilisateur de l'application) qui a lancé le projet BizTalk.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création d’applications associées, consultez [création d’Applications associées](../core/creating-affiliate-applications2.md), ou l’aide en ligne de Microsoft BizTalk Server.  
  
6.  Après avoir entré toutes les informations requises pour accepter les informations de connexion, cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
     Vous devez définir des paramètres de connexion de l'adaptateur BizTalk pour PeopleSoft Enterprise afin d'accéder à PeopleSoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi PeopleSoft](../core/creating-peoplesoft-send-handlers.md)