---
title: Commande flux via le Gestionnaire de processus | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: e2b51eff-44b5-440f-a7d1-0872543e5f27
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8556bce43ba4a951d0045d22f76d4bd222fcd8f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="order-flow-through-the-process-manager"></a>Flux de commandes par le biais du Gestionnaire de processus
Cette section décrit comment le Southridge Video commande Gestionnaire de processus, le **OrderManager** d’orchestration, les commandes de processus. Cette section suit une nouvelle commande dans l'orchestration. La section explique également comment l'orchestration gère les mises à jour des commandes.  
  
> [!NOTE]
>  La solution de gestionnaire de processus d'entreprise inclut un seul gestionnaire de processus, bien qu'il soit écrit qu'il peut utiliser plusieurs types de gestionnaires.  
  
 Le **OrderManager** orchestration coordonne les orchestrations subordonnées qui implémentent le processus d’entreprise pour gérer la commande. Le **OrderManager** envoie la commande en deux étapes qui, combinés, valider la commande, envoyer les informations au groupe d’installations, l’ordre d’envoi au système de commande via les composants de la communication à distance et mettre à jour l’historique des commandes. Vous pouvez ajouter, supprimer ou modifier ces étapes sans devoir modifier le **OrderManager**.  
  
> [!NOTE]
>  En raison de la taille et la portée de la **OrderManager** orchestration, vous voudrez lire cette section avec l’orchestration ouverte dans Microsoft Visual Studio.  
  
## <a name="order-manager-structure"></a>Structure du gestionnaire de commandes  
 Le **OrderManager** orchestration commence par une forme réception qui active l’orchestration. Le diagramme suivant illustre la structure générale de la **OrderManager** orchestration.  
  
 ![Schéma du Gestionnaire de commandes](../core/media/ordermanagerblockdiagram.gif "OrderManagerBlockDiagram")  
  
 La première forme Réception donne deux branches principales. Une branche, à droite, traite les nouvelles commandes. La branche de gauche gère les annulations de commande. Il accepte l’entrée d’utilisateur, il est possible pour le **OrderManager** pour recevoir une annulation de commande après une commande est déjà terminée. C'est le cas géré par la branche principale à gauche. La branche gère l'annulation isolée en définissant des indicateurs pour terminer le traitement et en ajoutant un avertissement au journal des événements. L'orchestration gère les annulations de commande qui arrivent tandis qu'une commande est en cours de traitement dans la branche de droite.  
  
 La branche de traitement de commande effectue une initialisation, puis entre dans deux boucles imbriquées. La boucle externe s'exécute une seule fois pour chaque étape du traitement de commande. La boucle interne s'exécute lors du traitement de l'étape. Le gestionnaire de commandes recherche également de possibles mises à jour de la commande à l'intérieur de la boucle interne. Une fois que les boucles s'arrêtent, le gestionnaire de commandes envoie un message d'achèvement.  
  
 Les étapes de traitement de commande utilisent des ports dynamiques, d’autocorrélation pour communiquer avec le **OrderManager** orchestration. Cela simplifie la corrélation de le **OrderManager** avec les instances des étapes car elle élimine la nécessité d’utiliser un ensemble de corrélations. Pour plus d’informations sur les ports d’autocorrélation, consultez [liaisons de Port](../core/port-bindings.md).  
  
## <a name="receiving-orders"></a>Réception de commandes  
 Le **OrderManager** reçoit des messages de commande à partir de la **OrderBroker** orchestration via le **FromBrokerPort** port. Ce port est lié directement à la base de données MessageBox. L’orchestration a deux **réception** formes connectées au port : un pour les nouvelles commandes et un pour mettre à jour les commandes.  
  
 Le **OrderManger** détermine les messages à traiter en fonction d’une expression de filtre. L’expression de filtre teste la valeur dans le champ d’état de message et le champ de type de gestionnaire de commande, **OrderMgrType**. Si le champ d’état est égal à ACCEPTED et **OrderMgrType** est CABLEORDER, la commande est nouvelle et destinée à ce gestionnaire de processus.  
  
 La nouvelle commande active une nouvelle instance de l'orchestration. Le **OrderManager** vérifie ensuite le type de la demande dans un **décision** forme. Si le type est Terminer, l'orchestration exécute la branche de gauche et met fin à la commande. Dans le cas contraire, l'orchestration procède au traitement de la commande. Notez que cela inclut la recherche de messages suivants liés à cette commande particulière.  
  
## <a name="initialization-for-new-orders"></a>Initialisation de nouvelles commandes  
 Après le **OrderManager** orchestration reçoit un message initial et commence la branche principale de droite, il obtient ses informations de configuration à partir de la **SSOConfigStore**. Pour cela, via un objet singleton défini dans le **utilitaires** assembly. Les valeurs de configuration sont les propriétés de l'objet. L'objet gère un cache local des valeurs de configuration, similaire à la solution d'architecture orientée services. Pour plus d’informations sur l’objet singleton, consultez [à l’aide de l’authentification unique efficacement dans la Solution de gestion des processus métier](../core/using-sso-efficiently-in-the-business-process-management-solution.md).  
  
 Comme la solution orientée services, la solution de gestion des processus d'entreprise utilise le magasin des secrets car il est présent lorsque BizTalk est installé, SSO met en cache les informations de configuration afin que les valeurs soient immédiatement disponibles et il peut protéger des informations, telles que des chaînes de connexion à la base de données et des mots de passe. Pour toutes ces raisons, le magasin des secrets est un bon endroit pour les informations de configuration, même si les authentifications uniques ne sont pas utilisées pour gérer les connexions aux applications principales.  
  
> [!NOTE]
>  L'orchestration extrait les informations de configuration avant de commencer le traitement. Cela garantit que l'orchestration utilise la même configuration si elle est en attente et, ultérieurement, réalimentée. Pour plus d’informations sur la mise en attente, consultez [mise en attente de l’Orchestration et la réactivation](../core/orchestration-dehydration-and-rehydration.md).  
  
 Le Gestionnaire de commandes utilise une valeur des données de configuration : **TotalStages**, le nombre total d’étapes dans l’ordre de la gestion des processus. Le gestionnaire affecte cette valeur à une variable locale, **numStages**. Il définit également les deux autres variables connectées à la boucle externe, **étape** et **arrêter**. Le **étape** indique l’étape actuelle et est le compteur de la boucle externe ; **arrêter** la valeur d’arrêt.  
  
 Enfin, le gestionnaire définit les **orderStatus** variable Started et entre dans la boucle de traitement externe.  
  
## <a name="new-order-processing-loops"></a>Boucles de traitement de nouvelles commandes  
 La boucle externe s’exécute en tant que la valeur de la **étape** variable est inférieure à la valeur de la **numStages** variable. La boucle externe dirige le traitement pour chaque étape. La boucle interne s'exécute tant qu'une étape est toujours en cours de traitement. Elle recherche également les modifications éventuellement apportées à la commande.  
  
### <a name="outer-loop"></a>Boucle externe  
 L’orchestration commence la boucle externe en attribuant le message reçu (**NewOrderMgrMsg**) à une variable, **OrderMgrMsg**. Elle copie ensuite l'étape et l'état dans la partie de routage du message. L’orchestration définit également l’adresse de retour dans le message à l’adresse de la **StageCompletionPort**:  
  
```  
OrderMgrMsg.RoutingPart.OrderMgrReturnAddress =   
       StageCompletionPort(Microsoft.XLANGs.BaseTypes.Address);  
```  
  
 L’orchestration envoie la commande à la **StagePort**, un port de sollicitation-réponse. Puis, l'orchestration attend un accusé de réception de l'étape, indiquant que le traitement de commande a démarré. L’étape envoie un **OrderAck** message lorsqu’il démarre le traitement de la commande.  
  
> [!NOTE]
>  Le **OrderAck** message est un des nombreux dans la solution définie par les classes .NET plutôt qu’un schéma. Pour plus d’informations sur l’utilisation de classes .NET pour définir des messages, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
 Lorsque l’orchestration reçoit l’accusé de réception, il attribue l’étape à la **currentStage** variable et entre dans la boucle interne.  
  
### <a name="inner-loop"></a>Boucle interne  
 La boucle interne s’exécute tant que la **currentStage** variable est égale à la **étape** variable ; c'est-à-dire, à condition que l’étape actuelle est en cours de traitement. Le corps de la boucle est un **écouter** forme avec trois **réception** formes. La forme la plus à gauche dans l’orchestration, **demande d’ordre**, fait partie du mécanisme de mise à jour de commande, décrit dans la section suivante.  
  
 Lorsqu’une commande de fin de l’étape de traitement, il envoie un message à la **StageCompletion** port de la **OrderManager** orchestration. Si l’étape s’arrête brusquement en raison d’une erreur, il envoie un **TerminatedMessage**. Dans ce cas, le **OrderManager** lève une exception. Le Gestionnaire d’exceptions le plus externe intercepte l’exception et envoie un message d’erreur pour le **OperatorPort**.  
  
 Si l’étape envoie un **OrderMgrMsg**, le **OrderManager** incrémente le **étape** variable. S’il existe plusieurs étapes (stage inférieur ou égal à numStages), les orchestrations définit l’état de la commande **OrderMgrMsg** sur STAGE_n_COMPLETED, où n est le numéro de l’étape actuelle. S'il n'y a pas d'étape supplémentaire, elle définit l'état de la commande sur COMPLETED et quitte les boucles.  
  
## <a name="order-updates"></a>Mises à jour des commandes  
 Le **OrderManager** orchestration écoute les mises à jour à l’intérieur de la boucle de traitement interne. Notez que la **réception** mettre en forme utilise pour ce faire, **OrderRequest**, utilise également le **FromBrokerPort**. L'utilisation d'une seconde forme Réception sur le même port dans une boucle, combinée à des ensembles de corrélations, crée un modèle BizTalk Server courant, le modèle de convoi. Vous utilisez le modèle de convoi pour garantir que la même instance d'une orchestration traite le premier message et les messages suivants connectés à une opération particulière.  
  
 Lorsque le gestionnaire de commandes reçoit le premier message connecté à une commande, il initialise deux ensembles de corrélations. La première, **OrderCorrelation**, utilise l’ID de client (**CustID**) et l’ID de commande (**OrderID**). Le gestionnaire de commandes partage cette corrélation avec les étapes de traitement de la commande. La seconde corrélation est la corrélation de convoi, **OrderConvoyCorrelation**, qui utilise l’état de la commande (**état**) en plus de l’ID du client et l’ID de commande. Le **OrderRequestReceive** utilise la forme **OrderConvoyCorrelation** comme un ensemble de corrélations suivant. Cette définition de la configuration de la corrélation garantit que l'instance du gestionnaire de commandes travaillant sur une commande particulière reçoit les modifications éventuelles.  
  
> [!NOTE]
>  Rappelez-vous qu'un ensemble de corrélations est un regroupement de propriétés de message utilisées pour déterminer si un message appartient ou non à une instance donnée d'une orchestration. Pour plus d’informations, consultez [à l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md).  
  
 Lorsque le **OrderManager** reçoit un message d’une commande, il vérifie tout d’abord le type de demande. Si le type de demande est TERMINATE, la forme Décision exécute la branche Terminer. Dans le cas contraire, l'orchestration teste le nouveau message pour voir s'il s'agit d'une mise à jour. Un message de mise à jour a un numéro de séquence supérieur (**SeqNum**) à la demande d’origine. Si le numéro de séquence du nouveau message est supérieur, l'orchestration commence le traitement de la commande par ce nouveau message. Si le message d'origine et de mise à jour ont le même numéro de séquence ou un numéro inférieur, il s'agit d'une erreur de séquence. Si les numéros de séquence sont égaux, la commande est en double et indiquée comme une erreur de doublon.  
  
 Pour plus d’informations sur **SeqNum**, consultez [les champs et les Messages de clé](../core/key-messages-and-fields.md).  
  
## <a name="final-steps"></a>Dernières étapes  
 Après avoir quitté les boucles, le Gestionnaire de commandes affecte l’adresse de réponse au port dynamique **CSRCompletionPort**. Le gestionnaire crée alors le message d'état d'achèvement, l'envoie et teste pour détecter une erreur. Si une erreur s'est produite, l'orchestration exécute une forme Terminer, sinon elle prend simplement fin.  
  
## <a name="coordinating-with-the-stages"></a>Coordination avec les étapes  
 Les deux le **OrderBroker** d’orchestration et la seconde orchestration d’étape de traitement (**CableOrder2**) créent des entrées dans la base de données de l’historique. L’orchestration CableOrder2 met à jour les informations de l’historique des entrées par le **OrderBroker** orchestration. Vérifiez qu’il existe une entrée dans la base de données pour mettre à jour, afin du **OrderBroker** utilise l’accusé de réception sur le port utilisé pour la base de données.  
  
 Mappages de configuration de la **OrderBroker** port pour la base de données de l’historique d’envoi à un groupe de ports d’envoi contenant deux ports : un port pour la configuration de test (**HistoryInsert-Test-SP**), un pour la mise à jour configuration (**HistoryInsert-SP**). Si vous laissez les deux ports actifs dans le groupe, la solution envoie des messages aux deux ports. Ainsi, elle demande deux accusés de réception mais n'en traite qu'un.  
  
 Pour éviter cette situation, désinscrivez le port de test (**HistoryInsert-Test-SP**), ou arrêtez la version de test de l’application. Pour plus d’informations sur l’accusé de réception, consultez [accusés de réception à l’aide de](../core/using-acknowledgments.md).  
  
## <a name="errors-and-routing-repaired-messagesdesign-choices"></a>Erreurs et routage de messages réparés : choix de conception  
 L’orchestration de gestionnaire d’exception et les orchestrations utilisées par les étapes de traitement de la commande utilisent une erreur de gestion d’orchestration (**ErrorHandlerOrch**) pour router les commandes incorrectes pour la réparation. La conception suppose qu'il existe un service ou un groupe qui répare la commande dans la forme souhaitée. La commande réparée n’est pas renvoyée par l’orchestration orderbroker (**OrderBroker**). Au lieu de cela, la commande normalisée est réparée dans sa forme normalisée. Dans la conception actuelle de la solution, l'orchestration du gestionnaire route le message d'erreur vers la source de la commande d'origine. Les commandes réparées, cependant, doivent être routées vers un port MSMQ sur l'orchestration du gestionnaire des erreurs. (La version de test de la solution utilise un dossier de fichiers.) Le gestionnaire d'erreurs renvoie ensuite le message réparé à l'orchestration d'appel.  
  
 Cette solution utilise cette conception car le courtier de commandes effectue une validation et une normalisation importantes du message de commande. À son tour, le message de commande nécessitant une réparation est également dans la forme normalisée. La maintenance de la forme normalisée du message évite de devoir contourner la différence entre les formes envoyée et normalisée des messages.  
  
## <a name="see-also"></a>Voir aussi  
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)   
 [Champs et les Messages de clé](../core/key-messages-and-fields.md)