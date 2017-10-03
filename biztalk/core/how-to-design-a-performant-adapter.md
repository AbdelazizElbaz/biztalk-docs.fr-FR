---
title: Comment concevoir un adaptateur Performant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5a1f338-fd7c-41c8-a181-8da8b293c4cc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7958968809dc224a3446ac81f3f89d08f6128a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-design-a-performant-adapter"></a>Conception d'un adaptateur performant
Pour obtenir des performances optimales, l'ensemble des adaptateurs doivent reconnaître les lots en ce qui concerne l'envoi des lots de messages, leur transmission, et généralement l'exécution d'opérations sur les messages des lots. Les adaptateurs doivent essayer d'exposer des attributs de performance configurables (par exemple, la taille des lots ou le nombre d'octets d'un lot) à partir de l'interface utilisateur de conception de l'adaptateur.  
  
 Comme indiqué précédemment, les adaptateurs d'envoi doivent toujours effectuer des envois non bloquants afin d'éviter de dégrader les performances de l'hôte d'envoi. Le blocage des API du moteur de messagerie est déconseillé.  
  
 L'écriture et la lecture à partir du contexte de message affecte les performances d'exécution. En général, les adaptateurs doivent éviter de lire, écrire et promouvoir un nombre excessif de propriétés de contexte de message. La promotion des propriétés affecte également les performances en raison de l'évaluation de l'abonnement qui se produit sur chaque propriété promue au moment de l'exécution. Toutefois, il faut que le nombre de propriétés concernées soit très élevé pour que cela affecte les performances de manière significative. Il est donc conseillé de promouvoir uniquement les propriétés qui doivent impérativement l'être.  
  
## <a name="throttle-send-and-receive"></a>Limiter l'envoi et la réception  
 Lorsque la charge sur le moteur BizTalk dépasse le seuil configuré, le moteur limite les adaptateurs et les orchestrations afin de garantir des performances optimales. Du côté réception, lorsque la charge de travail sur le moteur dépasse un seuil donné, l’appel de l’adaptateur à **IBTTransportBatch.Done** est bloquée jusqu'à ce que la charge a pas suffisamment diminué. Cela oblige l'adaptateur à n'envoyer de nouvelles tâches dans le moteur que lorsque celui-ci est disponible. Au niveau de l'envoi, lorsque le moteur limite l'envoi de messages sortants par les adaptateurs, il ne remet pas de nouveau message à transmettre tant que la charge n'a pas diminué.  
  
 Pour ces raisons, l'adaptateur ne doit pas être concerné par la limitation sauf si cela s'avère nécessaire, par exemple, pour limiter le nombre de connexions au système principal. Ces types de scénario ne sont pas pris en charge par le moteur ou l'infrastructure d'adaptateurs.  
  
 Vous pouvez gérer la limitation du nombre de messages envoyés à partir d'un adaptateur d'envoi personnalisé de plusieurs manières, selon que vous contrôlez ou non le code source de celui-ci.  
  
### <a name="send-side-throttling-improves-performance"></a>La limitation au niveau envoi améliore les performances  
 Si vous contrôlez le code source de l'adaptateur, vous pouvez, à partir des heuristiques, déterminer le nombre maximal de messages dans la file d'attente à envoyer à tout moment. Lorsque le moteur de messagerie appelle la `TransmitMessage` méthode et passe l’adaptateur d’envoi un nouveau message, que vous pouvez choisir de bloquer le thread ou une vérification pour voir si le nombre de messages dans la file d’attente est supérieur à la valeur maximale que vous avez précédemment. Si le nombre maximal de messages a été dépassé, vous pouvez utiliser la `Resubmit` méthode pour renvoyer le message au moteur de messagerie. Notez que si l'adaptateur est synchrone, le message est déjà bloqué.  
  
 Si vous ne contrôlez pas le code source pour l’adaptateur, vous pouvez modifier le nombre de messages en file d’attente en modifiant le **Highwatermark** valeur dans la table Adm_serviceclass de la base de données de gestion BizTalk. La valeur maximale pour le **Highwatermark** propriété est 200. Vous pouvez également modifier la valeur de la **limite inférieure** propriété à une valeur inférieure.  
  
 N’oubliez pas que la valeur de la **Highwatermark** propriété pour les comptes d’adaptateurs asynchrones pour le nombre de messages que le moteur de messagerie a donné à l’adaptateur. Le moteur de messagerie les transmet à l’adaptateur via la `TransmitMessage` (méthode), ces messages peuvent être en attente de leur transmission, par exemple, si l’adaptateur n’a pas effectué un appel correspondant à la `DeleteMessage`, `Resubmit`, `MoveToNextTransport` , ou [Microsoft.BizTalk.TransportProxy.Interop.BatchOperationType.MoveToSuspendQ](http://msdn.microsoft.com/library/microsoft.biztalk.transportproxy.interop.batchoperationtype.aspx) méthodes. Pour les adaptateurs synchrones, le **Highwatermark** propriété uniquement des comptes pour le nombre de messages, le moteur de messagerie a passé à l’adaptateur à l’aide du **TransmitMessage** (méthode), car cet appel traite de façon synchrone, bloquer le thread appelant de moteur de messagerie.  
  
 Si vous écrivez un adaptateur d'envoi pour un protocole lent par nature (tels que HTTP, FTP ou SOAP bidirectionnel), prenez en compte les éléments suivants :  
  
-   Un adaptateur de ce type peut recevoir des messages pour transmission provenant du moteur de messagerie BizTalk plus rapidement qu'il ne peut les transmettre. Cet écart génère des problèmes à plusieurs niveaux. Les messages en cours de transmission restent en mémoire et utilisent de la mémoire virtuelle, ce qui ralentit l'ensemble du système.  
  
-   L'adaptateur peut utiliser des ressources spécifiques au protocole. Par exemple, il peut ouvrir un trop grand nombre de connexions simultanées au serveur, ce qui peut perturber le serveur distant.  
  
-   L'adaptateur peut affecter d'autres adaptateurs. Par exemple, si un nombre trop élevé de messages se trouvent dans la file d'attente d'un adaptateur spécifique, le moteur de messagerie arrête l'émission des requêtes vers d'autres adaptateurs d'envoi de ce processus.  
  
 L'une des solutions consiste à placer les adaptateurs lents et rapides dans des hôtes BizTalk distincts et à contrôler le nombre de messages à l'aide des paramètres « High Watermark » et « Low Watermark ».  
  
### <a name="receive-side-throttling-improves-performance"></a>La limitation au niveau réception améliore les performances  
 Il existe de nombreux cas dans lesquels un adaptateur de réception reçoit des messages plus rapidement que le débit auquel le reste du système peut les traiter. Dans ce cas, les messages sont mis en file d'attente dans la base de données MessageBox. Lorsque cela se produit, les performances de l'ensemble du système se dégradent de manière significative.  
  
 Si cela se produit avec votre adaptateur, vous pouvez utiliser l'une des techniques suivantes pour réduire la vitesse de l'adaptateur de réception :  
  
-   Réduire la taille de la réserve de threads du moteur de messagerie. Vous pouvez contrôler le nombre de threads que le moteur de messagerie utilise pour publier les messages dans la base de données MessageBox. En réduisant le nombre de threads, vous réduisez la vitesse à la quelle l'adaptateur de réception reçoit les messages dans la base de données MessageBox. Vous devez effectuer ce paramétrage uniquement pour l'hôte correspondant au gestionnaire de réception de l'adaptateur. Vous ne devez pas le faire pour celui correspondant au gestionnaire d'envoi de l'adaptateur, excepté si vous souhaitez ralentir également l'adaptateur d'envoi.  
  
-   Réduire la taille de lot de l'adaptateur. La plupart des adaptateurs de réception rapides publient les messages dans la base de données MessageBox par lots. La taille de ces lots est généralement configurable dans la page de propriétés de l'emplacement de réception. La réduction de la taille de lot vous permet de diminuer le débit global des messages entrant dans le système.  
  
-   Modifier d'autres paramètres spécifiques à l'adaptateur. Une fois les deux premières étapes terminées, vous pouvez essayer d'ajuster d'autres paramètres afin de réduire encore davantage le débit. Certains adaptateurs exposent des paramètres internes permettant de réduire le débit. Par exemple, l'adaptateur MQSeries est doté du paramètre « Livraison chronologique des messages ». La livraison chronologique indique que l'adaptateur publiera un lot de messages, attendra qu'il se termine, puis publiera le lot suivant. En activant ce paramètre, vous supprimez essentiellement tout parallélisme provenant de l'adaptateur de réception. Inversement, la désactivation de ces paramètres permet d'augmenter la vitesse de réception d'un adaptateur de réception.  
  
 Un adaptateur peut envoyer autant de lots que nécessaire au proxy de transport. Lorsque le système est trop fortement sollicitée, un appel à la **fait** méthode de la **IBTTransportBatch** interface bloque le message jusqu'à ce que les ressources nécessaires sont publiées dans le système.  
  
## <a name="plan-for-asynchronous-receive-and-send"></a>Planifier l'envoi et la réception asynchrones  
 Les API de messagerie de BizTalk Server prennent en charge la programmation asynchrone. Si vous souhaitez écrire un adaptateur évolutif, prévoyez d'utiliser dès le début un modèle asynchrone car celui-ci fournit un meilleur accès concurrentiel.  
  
 Du côté réception, lorsqu’un adaptateur envoie un lot de messages au moteur de messagerie BizTalk (en appelant **IBTTransportBatch::Done**), le moteur de messagerie des files d’attente en utilisant sa réserve de threads et retourne immédiatement. Le moteur traite les messages sur un autre thread, ce qui permet à l'adaptateur de lire davantage de messages à partir de sa source et de les envoyer sans avoir à attendre que le traitement des messages précédents soit terminé.  
  
 Au niveau envoi, votre adaptateur peut être asynchrone ou synchrone. Toutefois, si votre protocole prend en charge des opérations asynchrones, vous devez utiliser cette prise en charge pour écrire un adaptateur évolutif. Par exemple, les adaptateurs d'envoi File et HTTP sont totalement asynchrones et effectuent très peu d'opérations de blocage/asynchrones.  
  
 Les opération asynchrones garantissent que le moteur de messagerie et votre adaptateur continueront à traiter leurs opérations respectives en parallèle et ne s'attendront pas l'un l'autre pour le traitement normal des messages.  
  
## <a name="use-batching-to-improve-performance"></a>Utiliser le traitement par lot pour améliorer les performances  
 Le traitement par lot est le meilleur point de départ pour l'écriture d'un adaptateur évolutif. Cela se vérifie à la fois pour les adaptateurs au niveau réception et au niveau envoi. Chaque lot est soumis à une transaction de base de données dans BizTalk Server, même si votre adaptateur n'est pas transactionnel. Un délai fixe étant associé à chaque transaction, vous devez faire en sorte de limiter le nombre de transactions en les combinant dans un lot unique.  
  
## <a name="do-not-starve-the-net-thread-pool"></a>Ne pas épuiser la réserve de threads .NET  
 L'écriture d'adaptateurs BizTalk est une procédure d'écriture du code d'exécution .NET ; l'écriture du code d'exécution .NET est invariablement une procédure de programmation asynchrone.  
  
 L'épuisement de la réserve de threads .NET est risqué pour l'ensemble de la programmation asynchrone dans .NET, et il est particulièrement important pour le programmeur d'adaptateur BizTalk de l'éviter.  
  
 La réserve de threads .NET est une ressource limitée mais largement partagée. Il est très facile d'écrire du code qui utilise l'un des threads de la réserve et le conserve pendant une longue période, bloquant ainsi l'exécution des autres opérations.  
  
 Chaque fois que vous utilisez **BeginInvoke** ou utiliser un minuteur, vous utilisez un thread de pool de threads .NET. Si vous avez plusieurs éléments de travail à faire (par exemple copier des messages de MQSeries dans BizTalk Server), vous devez exécuter un élément de travail (un lot de messages dans BizTalk Server), puis les remettre dans le pool de threads s’il existe plus de travail à effectuer. Ne placez jamais un `while` boucle sur le thread.  
  
 Concrètement, cela signifie en remplaçant `while` boucles avec des appels répétés à **BeginInvoke**. Cette simple modification permet d'améliorer considérablement la réactivité et l'évolutivité de l'ensemble de l'implémentation.  
  
## <a name="choose-the-right-measurement-when-limiting-batch-size"></a>Choisir la mesure appropriée lors de la limitation de la taille de lot  
 Si vous envoyez des messages à BizTalk Server par lots, ne limitez pas la taille de lot en fonction du nombre de messages uniquement. Considérez ce qui arrive lorsqu’un adaptateur a été configuré pour traiter par lot basé uniquement sur le nombre de messages : si la taille de lot est deux et que l’adaptateur obtient quatre messages de taille de 4 Ko, 8 Ko, 1 Mo et 5 Mo respectivement, le premier lot sera de 12 Ko de taille , et le deuxième lot sera de 6 Mo.  
  
 Le moteur de messagerie BizTalk traitant tous les messages d'un lot unique de manière séquentielle, le deuxième lot dans cet exemple sera traité beaucoup plus lentement que le premier. Cela réduit considérablement le débit. L'une des méthodes préconisées pour résoudre ce problème consiste à limiter la taille de lot à la fois en fonction du nombre de messages et du nombre total d'octets dans le lot (c'est-à-dire, la taille de lot en octets). Il n'existe pas de nombre magique pour le nombre total d'octets. Cependant, dans un scénario de traitement normal, si la taille de lot dépasse 1 Mo, l'accès concurrentiel et le débit seront faibles.  
  
 Généralement, les adaptateurs sont indépendants des messages et ne connaissent pas la taille des message de l'environnement de production. La taille des messages entrants est susceptible de varier de manière significative. Par conséquent, limitez toujours la taille de lot en fonction du nombre de messages et du nombre total d'octets.