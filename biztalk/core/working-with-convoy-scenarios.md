---
title: Utilisation des convois | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1028ab37-7ead-41a6-a186-53e5344d1a28
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f1c9931fe91b284c53a05c7868554c622306fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-convoy-scenarios"></a>Utilisation des convois
A *convoi* chaque fois que plusieurs messages doivent être liées pour obtenir le résultat requis. Il existe deux types principaux de convois : séquentielles et parallèles.  
  
 Dans certaines conditions, une instance d'orchestration instance peut recevoir un groupe de messages corrélés en même temps. Dans ce cas, une condition d'engorgement risque de se produire : l'un des messages du groupe doit initialiser un ensemble de corrélations dans l'instance d'orchestration avant que les autres messages ne puissent être corrélés à cette instance d'orchestration.   
  
 Pour vérifier que tous les messages corrélés sont reçus par la même instance d'orchestration, BizTalk Server détecte le risque d'engorgement et traite ces messages sous la forme d'un convoi. À l'inscription, l'exécution crée un abonnement général et l'identifie comme une partie d'un convoi. Une fois cet abonnement complété, le moteur de messagerie crée un abonnement temporaire basé sur les valeurs des propriétés de corrélation prédéfinies. Cet abonnement temporaire est appelé un *convoi ensemble*. Un ensemble de convois est un groupe d'ensemble de corrélations utilisées dans un convoi. Tous les messages supplémentaires correspondant à l'abonnement général sont évalués en fonction de l'ensemble de convois, et ceux qui lui correspondent sont acheminés vers un port existant.  
  
## <a name="using-convoys-with-business-processes"></a>Utilisation des convois dans les processus d'entreprise  
 Prenez en compte les éléments suivants lorsque vous utilisez le traitement en convoi dans un processus d'entreprise :  
  
-   A *ensemble de corrélations* est une liste de propriétés avec des valeurs spécifiques que vous utilisez pour acheminer les messages vers un processus d’entreprise spécifiques. L’ensemble de corrélations une **réception** forme ne peut pas contenir plus de trois propriétés utilisées pour la corrélation. Cela est dû au fait que ces valeurs sont identifiées et stockées au niveau de la base de données, qui ne prend en charge que trois paramètres au maximum.  
  
-   Des convois séquentiels et parallèles peuvent coexister dans le même processus d'entreprise, mais ils ne peuvent partager les mêmes ensembles de corrélations. En effet, un ensemble de corrélations ne peut appartenir qu'à un convoi.  
  
-   BizTalk Server ne prend pas en charge le traitement en convoi lorsque vous utilisez la **démarrer Orchestration** forme pour transmettre une ensemble dans une nouvelle orchestration de corrélations déjà initialisé. Cela est dû au fait que les ensembles de convois sont gérés au niveau de la base de données, indépendamment des instances d'orchestration en cours d'exécution.  
  
-   Vous ne pouvez pas utiliser un seul **réception** forme pour initialiser deux ou plusieurs ensembles de corrélations qui seront utilisées dans des convois séparés. Prenons l'exemple suivant : la réception r1 initialise les ensembles de corrélations c1 et c2 pour le premier convoi, la réception r2 suit c1 pour le deuxième convoi, et la réception r3 suit c2 pour le troisième convoi. Les ensembles de convois prévus pour le deuxième convoi sont c1, r2 et les ensembles de convois prévus pour le troisième convoi sont c2, r3, lesquels sont tous initialisés par r1. Dans ce cas, le moteur d’orchestration ne les traitera pas comme des convois. Cet exemple constitue un scénario de convoi valide si r2 et r3 suivent tous deux c1 et c2 (c1, r2, r3 et c2, r2, r3), si tous deux ne suivent que c1 (c1, r2, r3), ou si tous deux ne suivent que c2 (c2, r2, r3).  
  
## <a name="zombies"></a>Zombies  
 L'utilisation de convois peut déboucher sur des messages "perdus" appelés zombies. Lorsqu'un abonnement de réception de désactivation dans une orchestration en cours d'exécution correspond à un message dans la base de données MessageBox, celle-ci livre le message à l'orchestration. Vu que la MessageBox ne connaît pas la logique d'entreprise de l'orchestration, elle ne fait que livrer à l'orchestration tous les messages qui correspondent à l'abonnement. Si l'un de ces messages est livré alors que le flux d'exécution de l'orchestration a déjà traité les abonnements de réception susceptibles d'utiliser ce message, alors ce dernier devient un zombie.  
  
 Des zombies sont par exemple créés par une boucle de réception qui effectue 17 itérations et qui livre 18 messages correspondant à l'abonnement de réception de la boucle  (La MessageBox ne sait pas que la logique d’orchestration gère uniquement les 17 messages.) Le 18e message livré n’est pas utilisé par l’orchestration, car le flux d’exécution a déjà quitté la boucle. L'orchestration se termine avec des messages ignorés (zombies), qui ne peuvent être repris parce que l'instance d'orchestration a déjà pris fin.  
  
 Vous pouvez gérer les zombies à l'aide d'un script Windows Management Instrumentation (WMI) qui recherchera les instances dont l'état est "Suspendu - Ne peut être repris". Le moteur de messagerie écrit le message d'erreur "Terminé avec des messages ignorés" dans le journal des événements.  
  
 De plus, si vous avez un convoi séquentiel avec une étendue transactionnelle à long terme et si cette étendue a un délai d'expiration, certaines instances d'orchestration peuvent se terminer dans l'état "Suspendu - Ne peut être repris". Vous pouvez également remarquer que la somme du nombre de messages sortants et du nombre d'instances dans l'état "Suspendu - Ne peur être repris" est inférieure au nombre de messages entrants. Ce comportement est par défaut. Lorsqu'une exception d'expiration se produit, le code est envoyé dans le gestionnaire d'exception. BizTalk Server appelle le gestionnaire d'exception pour qu'il traite l'exception, ainsi que les zombies. Vous pouvez utiliser un port d'envoi du gestionnaire d'exception pour envoyer les zombies vers une autre destination spécifique à des fins d'étude et de traitement.  
  
 Les zombies peuvent être générés par d'autres scénarios. Prenons par exemple une instance d'orchestration qui attend un message de réponse de la part d'un processus d'entreprise et qui, pour une raison quelconque, reçoit deux messages de réponses correspondant à l'abonnement. Dans ce cas, le deuxième message de réponse devient un zombie. Un autre exemple est lorsque vous avez un **écouter** mettre en forme avec un **réception** forme sur une autre branche et un **délai** forme à l’autre branche. Si un message arrive au moment de l'expiration, il devient un zombie.  
  
 Pour plus d’informations sur la gestion des zombies, voir **suppression des Instances de Service suspendues** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes
 [Convois séquentiels](../core/sequential-convoys.md)  
  
 [Convois parallèles](../core/parallel-convoys.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md)