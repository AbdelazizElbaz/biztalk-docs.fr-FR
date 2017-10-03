---
title: "Comment gérer les défaillances d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdceb364-38d6-4aab-a176-bf751da1be25
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ce45dbf8fcc46c952ddd5ccf7ed45e633641a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-handle-adapter-failures"></a>Gestion des échecs de l'adaptateur
Les adaptateurs doivent en principe suspendre les messages qu'ils ne peuvent pas traiter. Par exemple, un adaptateur de réception qui rencontre un échec d'envoi doit en principe suspendre les messages, bien que cette décision dépende de l'objectif de l'adaptateur. Il faut également prendre en considération la sécurité en ce qui concerne la gestion des échecs. Par exemple, si un adaptateur suspend automatiquement tous les messages ayant échoué, il est peut être ouvert sur une attaque par déni de service, ce qui entraîne le remplissage de la file d'attente des messages suspendus BizTalk Server.  Certains adaptateurs, comme HTTP, peuvent renvoyer un code d'erreur au client, lui indiquant que la requête a été rejetée. Ce type d'adaptateur renvoie souvent un code d'erreur plutôt que de suspendre le message. En principe, les adaptateurs d'envoi ne suspendent les messages qu'une fois toutes les tentatives effectuées pour les transports principal et secondaire.  
  
## <a name="associate-error-processing-with-an-individual-operation-and-not-with-the-batch-that-contains-the-operation"></a>Association du traitement de l'erreur à une opération individuelle, et non au lot contenant l'opération  
 Le traitement par lot des messages dans l'adaptateur doit être invisible pour l'utilisateur. Cela signifie que l'échec d'une opération dans un lot ne doit en aucun cas affecter d'autres opérations. Toutefois, les lots sont atomiques, l'échec d'un message se traduit donc par une erreur pour le lot, et aucune opération n'est traitée.  
  
 Vous écrivez le code chargé de la gestion de l'erreur, qui renvoie les messages sans erreur et suspend les messages ayant échoué. Heureusement, BizTalk Server propose une structure des erreurs détaillée qui permet à l'adaptateur de déterminer l'opération qui a échoué. Il permet de créer d'autres lots dans lesquels les opérations ayant réussi sont envoyées à nouveau et les opérations ayant échoué sont suspendues.  
  
 L'étape finale de l'opération ne doit pas être affectée par le traitement par lot au sein de l'adaptateur.  
  
## <a name="use-seterrorinfo-to-report-failure-to-biztalk-server"></a>Utilisation de SetErrorInfo pour le rapport de l'échec à BizTalk Server  
 Si vous suspendez un message, vous devez fournir à BizTalk Server des informations sur l'échec à partir du contexte de message précédent. BizTalk Server fournit des fonctionnalités à l’aide de rapports d’erreurs le **SetErrorInfo** méthode sur les deux le **IBaseMessage** et **ITransportProxy** interfaces. Vous pouvez signaler les erreurs comme suit :  
  
-   Lorsqu’une défaillance se produit lors du traitement d’un message, définissez l’exception à l’aide de **SetErrorInfo (Exception e)** sur le message (**IBaseMessage**) doit être suspendu. Le moteur conserve ainsi l'erreur et le message pour un diagnostic ultérieur, et la consigne dans le journal des événements pour notification à l'administrateur.  
  
-   Si vous rencontrez une erreur pendant l’initialisation ou de comptabilité interne (et non pendant le traitement des messages), vous devez appeler **SetErrorInfo (Exception e)** sur la **ITransportProxy** pointeur qui a été passé à Pour vous lors de l’initialisation. Si l'adaptateur est basé sur une implémentation BaseAdapter, vous devez toujours avoir accès à ce pointeur. Sinon, vous devez être certain de le mettre en cache.  
  
 L'utilisation de l'une de ces méthodes entraîne l'écriture du message d'erreur dans le journal des événements. Il est important d'associer l'erreur au message correspondant si possible.  
  
## <a name="handle-a-database-offline-condition"></a>Gestion d'une condition de base de données hors connexion  
 Si l'une des bases de données BizTalk Server est déconnectée, le service BizTalk se recycle. Le moteur de messagerie tente de fermer tous les emplacements de réception avant de recycler le service. Si cela prend plus de 60 secondes, le service est arrêté. Étant donné que le moteur est traité par la transaction, il n'entraîne aucune perte de données.  
  
 Ce délai peut être réglé dans le Registre à l'aide de la clé suivante :  
  
```  
DWORD   
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{Host Guid}\MessagingDBFailoverShutdownTimeLimit  
```  
  
 Pour les adaptateurs isolés, étant donné que BizTalk Server ne possède pas le processus, les emplacements de réception sont désactivés lorsque l'une des bases de données BizTalk Server est hors connexion. Une fois la base de données à nouveau connectée, les emplacements de réception sont de nouveau activés.  
  
## <a name="write-to-the-event-log"></a>Écriture dans le journal des événements  
 L’adaptateur peut écrire des entrées de journal des événements à l’aide de la **IBTTransportProxy** interface en passant une exception. Adaptateurs développés en code natif doivent passer dans un **IErrorInfo** interface, **IBTTransportProxy.SetErrorInfo (Exception** `e` **)**.  
  
 Le moteur de messagerie écrit dans le journal des événements sur demande de l'adaptateur, pour des événements, comme une nouvelle tentative de l'adaptateur après un échec de transmission d'un message, l'envoi d'un message au transport secondaire ou la suspension du message. Pour de telles opérations, l'adaptateur doit simplement définir l'exception sur le message avant d'appeler l'API. Le fragment de code suivant illustre ceci :  
  
```  
IBaseMessage msg;  
...  
// Set exception on msg to indicate why transmission failed...  
msg.SetErrorInfo(  
 new ApplicationException(  
 "The TCP connection was closed by the destination"));  
```  
  
## <a name="handle-receive-specific-batch-errors"></a>Gestion des échecs de réception spécifiques au lot  
  
### <a name="handle-receive-failures"></a>Gestion des échecs de réception  
 Lorsque l'adaptateur envoie une opération (ou un lot d'opérations) au serveur BizTalk Server, les motifs d'échecs peuvent être divers. Les deux échecs les plus significatifs sont les suivants :  
  
-   Le pipeline de réception a échoué.  
  
-   Un échec de routage s'est produit au cours de la publication d'un message.  
  
 Le moteur de message tente automatiquement de suspendre le message lorsqu'il reçoit un échec du pipeline de réception, mais cette opération ne réussit pas systématiquement. Par exemple, si le moteur de message rencontre un échec de routage lors de la publication du message, il ne suspend pas le message.  
  
 Il est toujours possible qu'un message échoue. Dans ce cas, l’adaptateur doit appeler explicitement la **MoveToSuspendQ** API et tenter de suspendre le message. Lorsqu'il tente cette suspension, l'un des cas suivants doit être confirmé :  
  
-   L'objet de message identique à celui envoyé par l'adaptateur (recommandé) doit être suspendu.  
  
-   Si l'adaptateur doit créer un message, il doit définir le contexte du nouveau message avec le pointeur orienté sur le contexte du message initial, car le contexte du message comporte de nombreuses informations précieuses concernant le message et l'échec. Ces informations sont nécessaires au débogage du message ayant échoué.  
  
> [!NOTE]
>  Si l'adaptateur crée un objet de message et le suspend, il doit copier les informations concernant l'erreur à partir de l'objet de message initial dans le nouvel objet.  
  
 Certains adaptateurs, comme l'adaptateur HTTP fourni avec BizTalk Server, n'exigent pas la suspension du message. Ils renvoient une erreur à leur client.  
  
#### <a name="causes-of-failure"></a>Causes de l'échec  
 Causes simples d’échec sont les erreurs qui peuvent se produire lorsque le lot est construit ou **IBTTransportBatch::Done** est appelée.  
  
-   **Échec de l’envoi.** Le **Submit** appel peut échouer pour un nombre limité de raisons, et tous sont irrécupérables. Les raisons sont les suivantes :  
  
-   Des erreurs de mémoire insuffisante se produisent dans l'espace de processus BizTalk Server.  
  
-   L'assembly du schéma a été supprimé du déploiement. Dans ce cas, le **Submit** échoue avec une erreur peu claire. Dans l'adaptateur MQSeries, l'exception générique d'échec provenant de BizTalk Server est interceptée et un message d'erreur étendue est inscrit dans le journal des événements du système. Le message indique que l'une des causes possible de l'erreur est la suppression d'une manière ou d'une autre de l'assembly du schéma du déploiement.  
  
     En général, si **Submit** échoue, il est conseillé de suspendre le message à l’aide de la même transaction.  
  
-   **Échec de IBTTransportBatch::Done** Le **IBTTransportBatch::Done** appel peut échouer pour plusieurs raisons. En général, vous devez toujours tenter une suspension et terminer la transaction uniquement si celle-ci échoue. Un des codes d’erreur peut s’afficher à partir de l’échec de **IBTTransportBatch::Done** est que BizTalk Server tente d’arrêter. Dans ce cas, vous devez simplement terminer la transaction et laisser car le **Terminate** appel est probablement lieu en même temps. Autres scénarios se produisent lorsque vous avez construit correctement le lot et s’est exécutée correctement **IBTTransportBatch::Done**. Dans ces cas, les erreurs sont retournées dans **BatchComplete** et l’adaptateur doit déterminer comment procéder avec eux. Le reste de cette rubrique traite de ce cas.  
  
#### <a name="processing-batchcomplete-errors"></a>Traitements des erreurs BatchComplete  
 **BatchComplete** est un rappel fourni par l’adaptateur est appelé par BizTalk Server pour indiquer l’état d’achèvement d’une opération de traitement par lots.  
  
 Le paramètre le plus important passé à **BatchComplete** est l’état du lot `hResult`. Il indique la réussite ou l'échec du lot. En cas d'échec du lot, cela signifie que toutes les opérations du lot ont échoué. L’adaptateur passe par la structure d’état du lot et détermine les messages ayant échoué (il s’agit en tant que *filtrage du lot*).  
  
#### <a name="nontransactional-batchcomplete-errors"></a>Erreurs BatchComplete non transactionnelles  
 Pour les adaptateurs non transactionnels, vous devez choisir la réponse si une défaillance se produit pour un **SubmitMessage**/**SubmitRequestMessage** ou **SubmitResponseMessage** opération. En général, les adaptateurs suspendent le message en appelant **MoveToSuspendQ**.  
  
 Les opérations suivantes sont supposées toujours passer : **DeleteMessage**, **MoveToSuspendQ**, **ResubmitMessage**. Si elles échouent, cela indique généralement un bogue au niveau de l'adaptateur. Vous n'avez pas besoin d'écrire de code pour gérer l'échec dans ce cas. En revanche, si le lot échoue en raison de l'échec d'une autre opération, ces opérations doivent être réexécutées dans un nouveau lot.  
  
 Si l’adaptateur appelle **MovetoBackupTransport** qui échoue (car il n’a aucun transport secondaire), puis l’adaptateur doit appeler **MoveToSuspendQ** de suspendre le message.  
  
#### <a name="transactional-batchcomplete-errors"></a>Erreurs BatchComplete transactionnelles  
 Lorsque vous envoyez les lots à BizTalk Server à l'aide d'une transaction créée par l'adaptateur, vous devez suivre l'un des deux scénarios suivants :  
  
-   **Utilisez des lots de message unique.** : envoyez un lot composé d'un seul message au serveur BizTalk Server. Si cette opération échoue, vous devez envoyer un second lot à BizTalk Server sous la même transaction, mais vous devez déplacer le message problématique dans la file d'attente des messages interrompus au lieu de le renvoyer. Une fois le message ayant échoué supprimé, l'envoi du nouveau lot doit être effectué correctement. Si tel est le cas, BizTalk Server confirme la réussite de l'envoi et vous pouvez alors valider la transaction. Si le second lot échoue, l'adaptateur doit abandonner la transaction ou trouver un autre emplacement pour le message. Dans ce cas, les performances baissent immédiatement en raison du traitement de l'annulation de la transaction.  
  
     Des techniques d'optimisation s'offrent à vous pour vous permettre d'améliorer les performances de l'adaptateur. Par exemple, l'adaptateur MQSeries ajuste son approche de manière dynamique au moment de l'exécution. Il s'exécute avec des lots contenant 100 messages. S'il rencontre une erreur, il doit terminer le lot, mais passe à des lots composés d'un seul message le temps de dépasser le message générant l'erreur. Il reprend ensuite les lots de 100 messages. Si l'erreur se reproduit, il ralentit à nouveau.  
  
-   **Utilisez la suspension préemptive.** : créez un lot composé de plusieurs messages, dans lequel les messages contenant des erreurs sont suspendus de manière préemptive. Le lot contienne un mélange de **Submit** et **MoveToSuspendQ** opérations, et est le premier et unique lot sous la transaction. Ce lot doit réussir car les données contenant des erreurs ont été suspendues de manière préemptive et la transaction peut être validée (une fois la confirmation de BizTalk Server reçue).  
  
     Cela peut demander un examen ultérieur, mais cette technique a été utilisée dans l'adaptateur MSMQ. Elle dépend de l'existence d'ID fiables de messages uniques. L'adaptateur crée un lot de messages. Si un échec se produit, il annule la transaction (et donc le lot), mais conserve l'ID du message dans une structure de données temporaire. (Pour éviter que cette structure n'augmente indéfiniment, les éléments qu'elle contient sont supprimés à l'expiration d'un délai donné.) Avant l'envoi de chaque lot, l'adaptateur vérifie la liste des ID de messages incorrects. S'il en rencontre un, il détecte que le message échouera (car il a déjà échoué auparavant) et le suspend de manière préemptive au lieu de le renvoyer.  
  
     Les adaptateurs n'ont pas tous d'ID fiables de messages uniques, et un magasin de transactions est encore moins susceptible d'en avoir un. Ainsi, de nombreux adaptateurs transactionnels sont limités à l'envoi de lots composés d'un seul message.  
  
#### <a name="processing-other-errors"></a>Traitement des autres erreurs  
 Dans tous les autres cas, (comme un échec de suspension de message), l'adaptateur doit terminer la transaction. Tout autre résultat se traduira par la présence de messages dupliqués ou une suppression des messages.  
  
 Lorsque l'adaptateur en a la possibilité, il doit abandonner la transaction si un lot échoue. Cependant, dans certains cas, il ne peut pas procéder à cet abandon. Il doit alors suspendre le message à l'aide de la même transaction.  
  
#### <a name="processing-errors-on-transactional-receive"></a>Traitement des erreurs de réception transactionnelle  
 L'arrêt de la transaction en cas d'erreur constitue le modèle de traitement transactionnel commun. Dans ce cas, chaque élément retourne à son état précédent et aucune donnée n'est perdue. Toutefois, si vous utilisez des données à partir d'une source transactionnelle (par exemple, retirer une par une les lignes d'une table intermédiaire dans une base de données, ou retirer un par un les messages d'un produit de mise en file d'attente comme MQSeries ou MSMQ), cela peut s'avérer insuffisant. Si vous terminez simplement la transaction et que vous reprenez les mêmes données, la même erreur risque de se reproduire et le système risque de se bloquer dans une boucle répétée.  
  
 L'adaptateur SQL d'une version antérieure de BizTalk Server se comportait ainsi. Peu après la sortie du produit, le comportement de cet adaptateur a été modifié de sorte qu'il tente de suspendre un message ayant échoué et de valider la transaction. Le déplacement d'un message vers la file d'attente des messages interrompus sous la même transaction et la validation de la transaction empêche de perdre des données et permet à l'adaptateur de passer les données erronées.  
  
 Lorsque la partie réception d’un adaptateur reçoit un message d’erreur en réponse à une **Submit** message d’opération, l’adaptateur doit traiter l’erreur et déplacer le message vers la file d’attente de messages interrompus.  
  
 Dans le cas de lots transactionnels pour lesquels l'adaptateur a créé un objet de transaction et envoie les messages sous la transaction, l'adaptateur doit logiquement déplacer le message dans la file d'attente des messages interrompus sous la même transaction si un échec se produit. La transaction garantit que les données ne sont pas supprimées. Même les données qui génèrent l'erreur ne doivent jamais être supprimées.  
  
### <a name="handle-messages-without-subscriptions"></a>Gestion des messages sans abonnement  
 BizTalk Server rejette la publication d'un message dans la base de données MessageBox si aucun abonnement n'est défini pour l'accepter. Les abonnements sont enregistrés soit par les orchestrations, soit par les ports d'envoi. Il est possible de définir plusieurs abonnements, auquel cas le message est envoyé à plusieurs destinations. En cas d'absence d'abonnement, BizTalk Server rejette le message et ne tente pas de le suspendre. Si l'adaptateur ne gère pas cette erreur et ne suspend pas de manière explicite le message, ce dernier est supprimé et ses données peuvent être perdues. Un adaptateur transactionnel peut évidemment terminer la transaction et renvoyer le message à sa destination.  
  
### <a name="support-seek-with-your-receive-stream"></a>Prise en charge de la méthode Seek avec le flux de réception  
 Le flux de réception doit prendre en charge la **recherche** procédé de BizTalk Server être en mesure de suspendre le message sur une erreur de pipeline. Si le flux de message n’est pas identifiable, BizTalk Server génère une erreur lorsqu’il tente d’exécuter **recherche**.  
  
 Dans de nombreux cas de prise en charge **recherche** n’est pas facile. Lors d'un flux de données à partir d'un réseau, par exemple, il peut s'avérer difficile de revenir à la ressource réseau et de redemander les données.  
  
 Plusieurs adaptateurs fournis avec BizTalk Server mettent en file d'attente les données du message dans un fichier ou sur le disque pendant que BizTalk Server les lit. Cela permet à la carte à utiliser **recherche** sur le fichier s’il rencontre une erreur (dans le traitement du pipeline des données du message, par exemple). En interne, l’adaptateur utilise le **ReadOnlySeekableStream** classe qui encapsule un flux non identifiable entrant et déborde sur le disque lorsqu’un seuil de taille configurable est atteint. Pour les messages de taille inférieure au seuil, le disque n'est jamais atteint.  
  
### <a name="consider-user-configurable-error-handling-options"></a>Prise en compte des options de gestion d'erreur configurables par l'utilisateur  
 Il peut arriver parfois qu'il n'existe aucune réponse pour corriger une erreur. Dans ce cas, vous devez tenir compte de l'option configurable par l'utilisateur à choisir entre divers comportements, ce que fait l'adaptateur MQSeries.  
  
 Le problème avec un adaptateur suspend les messages lorsqu’il rencontre une erreur est que la file d’attente de messages interrompus dans BizTalk Server est un élément d’un « trou noir ». Il est relativement facile d’obtenir les messages dans la file d’attente, mais très difficile de les retirer à nouveau.  
  
 Certains utilisateurs de l'adaptateur préfèrent que la file d'attente des messages interrompus soit vide. Dans le cas de l'adaptateur MQSeries par exemple, l'utilisateur dispose d'une option de configuration afin d'effectuer l'une des opérations suivantes :  
  
-   définir l'adaptateur pour qu'il termine la transaction en cours et se désactive lorsqu'il rencontre une erreur ;  
  
-   suspendre le message ayant échoué et valider la transaction. L'adaptateur procède ainsi même lorsque BizTalk Server a correctement suspendu le message. Cette action répond aux besoins du client même si le journal des événements n'est alors pas strictement correct.  
  
### <a name="implement-receive-ordering-by-using-a-single-thread-and-waiting-on-batchcomplete"></a>Implémentation du classement de réception à l'aide d'un seul thread et attente de BatchComplete  
 L'interface de BizTalk Server est conçue pour des performances optimales et pour pouvoir évoluer grâce à la prise en charge de l'accès concurrentiel. Toutefois, si vous souhaitez classer de manière stricte la réception des messages (comme cela est parfois requis lors de la réception de messages provenant d'un produit de mise en file d'attente de messages tel que MQSeries ou MSMQ), vous devez effectuer des opérations supplémentaires dans l'adaptateur pour désactiver en partie l'accès concurrentiel. Cette opération peut être effectuée en deux étapes :  
  
1.  Vous devez utiliser un seul thread pour tout traitement de données dans l'adaptateur.  
  
2.  Vous devez attendre que BizTalk Server ait complètement traité chaque lot. Ce point est important et vous pouvez l'effectuer à l'aide des primitives de synchronisation de threads .NET. Par exemple, en utilisant un **AutoResetEvent**, vous devez :  
  
    -   Déclarez l’objet d’événement où il est accessible par les deux le thread de travail principal et le **BatchComplete** objet de rappel.  
  
    -   Sur le thread de travail principal, envoyer des messages au lot comme d’habitude, puis appeler **AutoResetEvent.Reset** sur l’objet d’événement juste avant l’appel au lot **IBTTransportBatch::Done**.  
  
    -   Appelez **AutoResetEvent.WaitOne** sur l’objet d’événement à partir de ce même thread. Le thread de travail principal est ainsi bloqué. Dans le **BatchComplete** rappel à partir de BizTalk Server vous appelez ensuite **AutoResetEvent.Set** sur le même objet d’événement pour débloquer le thread de travail, il est prêt à traiter un autre message.  
  
 Il est fortement recommandé que *classement de réception* comme cela sera rendu configurable, car elle force dégradation significative des performances. De nombreux scénarios (et même la plupart) ne requièrent pas le classement des messages. La suspension des messages peut également interrompre le classement. La marche à suivre dans ce cas dépend de l'application. Il est donc préférable que l'adaptateur propose à l'utilisateur une possibilité de configuration.  
  
 Dans certains cas de classement, des clients ont indiqué préférer arrêter le traitement, c'est-à-dire désactiver l'adaptateur, plutôt qu'interrompre le classement. L'adaptateur MQSeries, qui prend en charge le classement de réception, propose cette option.  
  
## <a name="handle-send-specific-batch-errors"></a>Gestion des échecs d'envoi spécifiques au lot  
  
### <a name="handle-send-retry-and-batching"></a>Gestion des tentatives d'envoi et du traitement par lot  
 Voici un exemple type de traitement par lot d'envoi :  
  
-   BizTalk Server transmet un lot de messages à l'adaptateur.  
  
-   Lorsque l'adaptateur détermine qu'il a remis le message à la destination, il exécute la suppression sur BizTalk Server, ce qui indique que la tâche est effectuée. (Comme toujours, plusieurs messages peuvent être mis en lot de manière arbitraire pour améliorer les performances.)  
  
 Si l'adaptateur au niveau de l'envoi ne parvient pas à traiter un message, il a plusieurs possibilités :  
  
-   Il doit indiquer à BizTalk Server que le message doit à nouveau être envoyé. BizTalk Server ne renvoie pas automatiquement le message. BizTalk Server conserve le nombre de tentatives et l'affiche dans le contexte du message.  
  
-   Il peut déterminer qu'il lui est impossible de traiter un message. Dans ce cas, il peut déplacer le message dans le transport suivant. L’adaptateur procède à la **MoveToNextTransport** appeler sur le **lot** objet.  
  
-   Il peut placer le message dans la file d'attente des messages interrompus.  
  
 Il détermine les événements suivants pour le message. Il est cependant préférable que les adaptateurs se comportent de manière cohérente de sorte à faciliter la prise en charge de l'installation BizTalk Server.  
  
 Il est vivement conseillé que les adaptateurs se comportent comme décrit ci-après. Les adaptateurs fournis avec BizTalk Server se comportent ainsi.  
  
### <a name="recommended-behavior-for-handling-send-errors-in-a-batch"></a>Comportement recommandé pour la gestion des erreurs d'envoi dans un lot  
 L'adaptateur d'envoi reçoit des messages et les envoie à BizTalk Server.  
  
 L'adaptateur supprime un message sur BizTalk Server chaque fois qu'il est traité correctement. Toute communication de retour vers BizTalk Server et effectuée par lot, et les suppressions peuvent aussi être effectuées par lot. Le lot peut être différent de celui créé par BizTalk Server sur l'adaptateur. En cas de messages de réponse (comme pour un scénario SolicitResponse), ils doivent être renvoyés à BizTalk Server (avec SubmitResponse) avec la suppression associée.  
  
-   Si le traitement du message a échoué dans l'adaptateur, vérifiez le nombre de tentatives.  
  
    -   Si le nombre de tentatives n'a pas été dépassé, renvoyez le message à BizTalk Server, et pensez à définir le délai de tentatives sur le message. Le contexte du message fournit le nombre de tentatives et l'intervalle avant nouvelle tentative que doit utiliser l'adaptateur.  
  
    -   Si le nombre de tentatives a été dépassé, l’adaptateur doit tenter de déplacer le message à l’aide de **MoveToNextTransport**. Le nouvel envoi et **MoveToNextTransport** messages peuvent être mélangés aux suppressions dans le même lot à BizTalk Server. Cette étape n'est pas obligatoire mais peut s'avérer utile.  
  
-   Le nouvel envoi et la **MoveToNextTransport** sont des méthodes de la carte pour traiter les échecs. Lors du traitement d'un échec, un autre échec peut se produire. Dans ce cas, lors du traitement de la réponse à partir de BizTalk Server (dans le **BatchComplete** méthode) l’adaptateur doit créer un autre lot sur BizTalk Server pour indiquer comment traiter cet échec.  
  
     Procédez comme suit pour traiter un échec qui se produit pendant le traitement d'un autre échec :  
  
    -   Si le nouvel envoi échoue, utilisez **MoveToNextTransport**.  
  
    -   Si le **MoveToNextTransport** échoue, utilisez **MoveToSuspendQ**.  
  
 Vous devez poursuivre la création de lots sur BizTalk Server jusqu'à ce que ce dernier reçoive une action correctement effectuée.  
  
### <a name="serialization-of-message-context-property"></a>Sérialisation d'une propriété de contexte de message  
 Tous les objets affectés à une propriété de contexte de message doivent être sérialisables, Dans le cas contraire, le moteur de messagerie lève une exception de type **E_NOINTERFACE**. Cette valeur renvoyée représente de manière ambiguë un objet non sérialisable tentant d'être affecté au contexte de message.