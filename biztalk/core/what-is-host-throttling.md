---
title: "Qu'est-ce que la limitation des hôtes ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host throttling, outbound
- host throttling, inbound
- host throttling, about host throttling
ms.assetid: 36d1818b-c8a2-4f23-bfb3-c034ee242f69
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4730a93b6491f53fc06004ca8bb0dcb0d970cc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-host-throttling"></a>Qu'est-ce que la limitation des hôtes ?
La plupart du traitement qui se déroule sur un serveur BizTalk se produit dans une entité logique appelée instance de l'hôte BizTalk Server, qui est un processus exécuté en tant que service Windows ou que processus hôte isolé sur le serveur BizTalk. Pour gérer l'utilisation des ressources par un processus de l'instance de l'hôte, BizTalk Server utilise un mécanisme de limitation réglable qui régit le flux et le traitement de messages sur une instance de l'hôte.  
  
 Le mécanisme de limitation modère la charge de travail de l'instance de l'hôte pour vérifier qu'elle ne dépasse pas la capacité de cette instance ou des instances de l'hôte en aval. Le mécanisme de limitation empêche également une condition dite de conflit de ressources, qui peut réduire les performances globales du processus de l'instance de l'hôte ou d'autres processus système. Un conflit de ressources se produit lorsqu' un ou plusieurs processus utilisent une ressource limitée à leur détriment et/ou à celui d'un autre processus. Par exemple, la consommation d'une quantité excessive de mémoire ou de threads peut provoquer des échecs d'allocation de mémoire ou de nombreux changements de contexte de thread susceptibles d'affecter les performances du processus. De tels conflits peuvent nuire aux performances globales de BizTalk Server.  
  
 Le mécanisme de limitation de l'hôte détecte également à quel moment les ressources disponibles sont sous-utilisées. Lorsque les ressources disponibles sont sous-utilisées, le mécanisme de limitation autorise le traitement de messages supplémentaires par une instance de l'hôte. Il vérifie en permanence si les ressources disponibles sont sur- ou sous-utilisées et règle en conséquence le flux de messages sur l'instance de l'hôte.  
  
 Le mécanisme de limitation de l'hôte BizTalk Server permet de vérifier que le système fonctionne à un niveau optimal et acceptable.  
  
 Les paramètres de configuration de limitation de l'hôte sont définis par hôte sur la console Administration de BizTalk Server. Notez que les paramètres de configuration de limitation définis pour l'hôte s'appliquent à un ou à tous les gestionnaires de réception et d'envoi et aux orchestrations qui sont hébergées dans les instances de l'hôte correspondantes. Si vous souhaitez définir des paramètres de limitation qui ne seront appliqués qu'à un gestionnaire de réception ou d'envoi ou à une orchestration, procédez comme indiqué ci-dessous :  
  
-   Créez un hôte et définissez les paramètres de limitation appropriés.  
  
-   Configurez le gestionnaire de réception, le gestionnaire d'envoi ou l'orchestration de sorte qu'il soit exécuté sur cet hôte.  
  
-   Créez une ou plusieurs instances de l'hôte qui seront exécutées sur vos serveurs BizTalk.  
  
## <a name="inbound-host-throttling"></a>Limitation de l'hôte au niveau des entrées  
 Limitation, également connu sous le nom de l’hôte *limitation de la publication de messages* dans BizTalk Server, est appliquée aux instances d’hôte qui contiennent des adaptateurs de réception ou les orchestrations qui publient des messages à la base de données MessageBox. Une condition de limitation de l'hôte au niveau des entrées peut être déclenchée dans les conditions suivantes :  
  
-   La quantité de mémoire, le nombre de threads ou le nombre de connexions de base de données utilisées par l’instance de l’hôte dépasse les seuils de limitation définis dans **Panneau de configuration** disponibles dans le groupe BizTalk, puis en sélectionnant **Paramètres**. Ces valeurs peuvent être mesurées avec les compteurs de performance disponibles sous les **BizTalk : Agent** catégorie d’objet de performance.  
  
-   Les hôtes en aval sont incapables de traiter les messages publiés. Cela augmente la valeur de la **nombre dans la base de données de messages** paramètre. Le seuil auquel la **nombre dans la base de données de messages** déclenche une condition de limitation peut être définie sur la valeur la **hôtes** option **Panneau de configuration**. Le nombre de messages dans la base de données peut être mesuré avec le **taille de la base de données** compteur sous le **BizTalk : Agent** catégorie d’objet de performance.  
  
-   Le **vitesse d’entrée de publication de messages** de l’hôte instance dépasse le **vitesse de sortie de publication de messages\***  spécifié **facteur de dépassement de vitesse** valeur. Le **facteur de dépassement de vitesse** valeur est définie dans **Panneau de configuration de**, **hôtes** , puis **basé sur le taux de limitation**. Taux entrants et sortants de publication de messages peuvent être mesurées avec les compteurs d’analyseur de performances correspondants sous la **BizTalk : Agent** catégorie d’objet de performance.  
  
-   Le comportement de limitation par défaut a été modifiée. [À l’aide du Panneau de configuration pour l’optimisation des performances de BizTalk Server](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) décrit les différentes valeurs qui affectent le comportement de limitation.  
  
 Selon la gravité de la condition de limitation, les mesures suivantes sont prises :  
  
-   Un délai progressif est implémenté dans la logique de traitement de l'instance de l'hôte. Ce délai peut être implémenté lorsqu'un thread du Gestionnaire de points de terminaison reçoit un lot de messages de l'adaptateur de transport et/ou lorsque ce gestionnaire soumet un lot de messages pour publication dans la base de données MessageBox. La durée du délai de traitement et la vitesse à laquelle cette durée est incrémentée déterminent la gravité de la condition de limitation.  
  
-   Le nombre de threads disponibles pour le Gestionnaire de points de terminaison est restreint. Ce gestionnaire reçoit des lots de messages des adaptateurs et publie ces messages dans la base de données MessageBox. Par défaut, le Gestionnaire de points de terminaison est configuré pour utiliser 20 threads par UC. Si le mécanisme de limitation de l’hôte détecte une condition de stress pour le traitement entrant, il peut réduire provisoirement le nombre de threads mis à la disposition du gestionnaire jusqu’à ce que la condition de stress soit éliminée. Le Gestionnaire de points de terminaison ne peut traiter des messages des adaptateurs de transport ou remettre des lots de messages dans la base de données MessageBox que si un thread du Gestionnaire de points de terminaison est disponible pour traiter ce lot de messages entrants.  
  
-   L'utilisation de la mémoire et d'autres ressources est réduite en fonction des besoins. BizTalk Server peut envoyer des instructions à d’autres classes de service pour limiter l’utilisation de la mémoire en mettant les planifications, de réduction de taille du cache mémoire, en cours d’exécution et en limitant l’utilisation de threads de nécessitant beaucoup de mémoire.  
  
 **Flux de messages entrants à partir de l’adaptateur de base de données MessageBox**  
  
 ![Flux des messages à partir de l’adaptateur de base de données MessageBox entrants](../core/media/inboundmsgflow.gif "InboundMsgFlow")  
  
## <a name="outbound-host-throttling"></a>Limitation de l'hôte au niveau des sorties  
 Limitation, également connu sous le nom de l’hôte *la limitation du traitement des messages* dans BizTalk Server, est appliquée aux instances d’hôte qui contiennent les orchestrations ou adaptateurs d’envoi et de réception et remettent ou traitent des messages qui ont été publié dans MessageBox. Une condition de limitation de l'hôte au niveau des sorties peut être déclenchée dans les conditions suivantes :  
  
-   La quantité de mémoire, le nombre de threads ou le nombre de connexions de base de données utilisées par l’instance de l’hôte dépasse les seuils de limitation définis dans **limitation basée sur une ressource** dans **Panneau de configuration de**. Ces valeurs peuvent être mesurées avec les compteurs de performance disponibles sous les **BizTalk : Agent** catégorie d’objet de performance.  
  
-   Le **vitesse de remise de messages entrant** de l’hôte instance dépasse le **vitesse de sortie de remise de messages** \* spécifié **facteur de dépassement de vitesse** valeur . Le **facteur de dépassement de vitesse** est défini dans le **limitation basée sur un taux de** onglet **Panneau de configuration**. Compteurs de la remise de messages entrants et sortants taux peuvent être mesurées avec l’Analyseur de performances correspondants sous la **BizTalk : Agent** catégorie d’objet de performance.  
  
-   Le nombre de messages traités simultanément par l’instance d’hôte dépasse la **messages par UC In-process** \* le nombre d’UC disponibles dans la zone. Le **messages In-process** seuil est défini sur le **limitation basée sur une ressource** onglet **Panneau de configuration**. Le nombre de messages traités simultanément par l’instance d’hôte peut être mesuré avec le **nombre de messages In-process** compteur de performances sous le **BizTalk : Agent** objet de performance catégorie.  
  
-   Le comportement de limitation par défaut a été modifiée. [À l’aide du Panneau de configuration pour l’optimisation des performances de BizTalk Server](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) décrit les différentes valeurs qui affectent le comportement de limitation.  
  
 Selon la gravité de la condition de limitation, les actions suivantes sont exécutées :  
  
-   Un délai progressif dans la logique de traitement de l'instance d'hôte est implémenté avant la remise des messages à l'adaptateur de transport sortant ou au moteur d'orchestration pour traitement. La durée du délai de traitement logique et la vitesse à laquelle cette durée est incrémentée déterminent la gravité de la condition de limitation.  
  
-   Le nombre de messages qui peuvent être contenus dans la file d'attente en mémoire est limité. La file d'attente en mémoire sert d'espace réservé temporaire pour la remise des messages de la base de données MessageBox à l'agent des messages qui, à son tour, remet des messages à XLANG ou aux adaptateurs d'envoi. Par défaut, la file d'attente en mémoire est définie pour contenir 100 messages par UC. Lorsque la file d'attente est pleine, aucun message n'est supprimé de la base de données MessageBox tant que de l'espace n'est pas libéré de cette file d'attente.  
  
-   La taille du pool de threads de l'agent des messages est limitée et, de ce fait, le mécanisme de limitation de l'hôte réduit considérablement le nombre de messages qui sont remis à XLANG et aux adaptateurs.  
  
     La taille de pool de threads de l’Agent des messages par défaut peut être modifiée en changeant le **nombre maximal de threads de moteur** valeur sur le **général** onglet **Panneau de configuration**. Pour plus d’informations sur la modification de cette valeur, consultez [comment modifier les paramètres généraux](../core/how-to-modify-general-settings.md).  
  
-   L'utilisation de la mémoire et d'autres ressources est réduite en fonction des besoins. BizTalk Server peut envoyer des instructions à d'autres classes de service afin de limiter l'utilisation de la mémoire en mettant en attente les planifications en cours d'exécution, en réduisant la taille du cache et en limitant l'utilisation de threads qui nécessitent un volume important de mémoire.  
  
 **Flux de message sortant à partir de la MessageBox aux adaptateurs et XLANG**  
  
 ![Flux de messages sortant vers adaptateurs et XLANG](../core/media/outboundmsgflow.gif "OutboundMsgFlow")  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server implémente la limitation de l’hôte](../core/how-biztalk-server-implements-host-throttling.md)   
 [À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)