---
title: "L’exemple DynamicReceive (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fa7c934-7ec3-45ad-b226-c8c53934ecb1
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e0dc620d2d12933d34df0dce9eb02b697871bdc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="dynamicreceive-sample-biztalk-server-sample"></a>Exemple DynamicReceive (exemple BizTalk Server)
L'exemple DynamicReceive illustre la réception de messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'une file d'attente MQSeries lorsque l'URI de la file d'attente MQSeries est spécifié de façon dynamique.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple crée dynamiquement une file d’attente MQSeries comme spécifié par le **queueManager**, **file d’attente**, et **server** variables. Il permet une dynamique scénario de réception et obtient [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messages à partir de la file d’attente MQSeries spécifié de façon dynamique en fonction de critères de filtre spécifiés dans la **MQMD_MsgId** et **MQMD_CorrelId** propriétés de message.  
  
## <a name="how-this-sample-was-designed-and-why"></a>Conception et finalité de cet exemple  
 L'adaptateur MQSeries peut recevoir de façon dynamique les messages d'une file d'attente MQSeries en spécifiant l'adresse URI de la file d'attente dans l'orchestration. Cette fonctionnalité est activée via l'utilisation d'un port d'envoi de sollicitation-réponse.  
  
 Pour recevoir des messages de manière dynamique, spécifiez les éléments suivants dans un **Expression** forme de l’orchestration :  
  
1.  Activez la réception dynamique en définissant la propriété suivante sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message : **MQSeries.DynamicReceive** = `'Yes'`  
  
2.  Spécifiez l'adresse à laquelle récupérer les messages en définissant l'URI du port. Vous pouvez également spécifier les éléments suivants :  
  
    -   Spécifiez le délai d’attente avant d’obtenir les messages à l’aide de la **MQSeries.WaitInterval** propriété du message.  
  
    -   Spécifier les critères de correspondance pour la réception des messages. Les options de critères de correspondance sont **ID de Message**, **CorrelationID**, **GroupID**, et **MessageSequenceNumber**. Consultez « Propriétés associées à BizTalk Server » à [http://go.microsoft.com/fwlink/?LinkId=89396](http://go.microsoft.com/fwlink/?LinkId=89396) pour plus d’informations.  
  
 Une fois le message créé avec ces propriétés, il est envoyé à la file d'attente MQSeries via le port d'envoi de sollicitation-réponse. Le port indique l'adaptateur à utiliser pour la réception des messages provenant de l'URI spécifié avec les options de correspondance définies. Il en résulte les actions suivantes :  
  
-   Si les critères de filtre permettant de récupérer un message sont atteints, le message est extrait de la file d'attente et renvoyé à l'orchestration.  
  
-   Si les critères de filtre permettant de récupérer un message ne sont pas atteints, une réponse factice est renvoyée. Cela indique que les options spécifiées n'ont renvoyé aucun message de la file d'attente.  
  
 L'utilisation de la fonctionnalité de réponse dynamique offre davantage de souplesse car aucun emplacement de réception fixe n'est requis. Il peut arriver que vous ne connaissiez l'URI qu'au moment de l'exécution. La fonctionnalité de réception dynamique permet de déterminer de façon dynamique l'emplacement à partir duquel récupérer des messages. Cela signifie également qu'il n'est pas nécessaire d'implémenter un accord de mise en file d'attente au sein de l'orchestration.  Vous pouvez attendre de recevoir les messages à l'aide d'un URI spécifié de façon dynamique depuis la file d'attente MQSeries sur la base des critères de correspondance définis.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Samples\AdaptersUsage\MQSeriesAdapter\DynamicReceive  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|||  
|-|-|  
|Fichier| Description|  
|DynamicReceive.btproj,<br /><br /> DynamicReceive.sln|Fichiers de projet et de solution de l'application.|  
|DynamicReceive e.odx|Fichier d'orchestration BizTalk de l'application.|  
|Setup.bat|Fichier de commandes permettant de créer le fichier de clé, puis de compiler et déployer le projet.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Spécifiez le **Microsoft.XLANGs.BaseTypes.Address** appropriée pour votre solution. Modifier la **MQSeries.WaitInterval** pour spécifier lorsque vous attendez à recevoir les messages de réponse. Mettre à jour (ou ajoutez) les options de correspondance ou supprimez-les si vous souhaitez obtenir tous les messages.  
  
## <a name="building-and-running-the-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-create-the-sample"></a>Pour créer l'exemple  
  
1.  Créez un nouveau projet d'orchestration dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Activer la dynamique opération de réception en définissant le **MQSeries.DynamicReceive** propriété sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] un message à `'Yes'`.  
  
3.  Spécifiez l’adresse à partir duquel obtenir les messages en définissant le **URI du Port**.  
  
4.  Les deux propriétés suivantes peuvent également être définies :  
  
    1.  Spécifiez un délai d’attente avant d’obtenir les messages à l’aide de la **MQSeries.WaitInterval** propriété du message.  
  
    2.  Spécifier les critères de correspondance pour la réception des messages. Pour plus d'informations, consultez la rubrique « Options de correspondance » de l'Aide.  
  
5.  Modifiez les variables suivantes dans l'orchestration pour spécifier l'emplacement de récupération des messages :  
  
    -   **File d’attente**, **queueManager**, et **server**. Celles-ci sont utilisées pour créer l’URI dans le **Expression** forme.  
  
6.  Modifier la **Expression** forme pour commenter les options de création et de correspondance de file d’attente dynamique selon les besoins.  
  
7.  Vous pouvez créer et déployer le projet de l'une des manières suivantes :  
  
    -   Ouvrez la solution, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions et cliquez sur **propriétés** pour afficher les propriétés du projet. Sous l’onglet signature, cliquez sur  **\<nouveau... \>**  dans les **choisir un fichier de clé de nom fort** zone déroulante. Renseignez le nom du fichier de clé, puis déployez le projet.  
  
    -   Vous pouvez également exécuter le fichier setup.bat pour créer le fichier de clé, puis créer et déployer le projet.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
1.  Liez l'orchestration à l'hôte BizTalk.  
  
2.  Activez le port de réception du fichier créé par l'orchestration. Modifier le fichier emplacement de réception du **c:\temp\in** vers le dossier approprié.  
  
3.  Inscrivez et démarrez les deux ports d'envoi créés. L'un est un port dynamique de sollicitation-réponse, l'autre est à la fois un port d'envoi FILE et la file d'attente à laquelle le message sera envoyé. Assurez-vous que cet emplacement est défini correctement.  
  
4.  Pour démarrer l'orchestration, placez un fichier dans le dossier d'entrée. Il appelle l’adaptateur MQSeries et appelle le **MQSAgent2** composant COM + sur le serveur spécifié pour obtenir le message. Le message reçu apparaît dans le dossier spécifié dans le port d'envoi FILE.  
  
5.  Si aucun message n’est trouvé, qui correspond aux critères spécifiés dans le **Expression** forme, un message factice est déposé dans le dossier de sortie. Pour désactiver des options de correspondance, commentez les deux dernières lignes dans le **Expression** forme.  
  
## <a name="comments"></a>Commentaires  
  
-   Si la file d'attente créée de façon dynamique n'est pas supprimée, des erreurs seront générées lors de l'activation de l'instance d'orchestration suivante.  
  
-   Il y a d'autres manières de définir l'URI de façon dynamique ; cet exemple ne couvre qu'une seule option. Par exemple, l'URI peut être défini via la lecture de propriétés dans le contexte du message.  
  
-   Si aucun message dans la file d'attente ne répond aux critères de correspondance, un message factice est renvoyé.  
  
-   Comme cet exemple utilise les ports d'envoi dynamiques, il peut être nécessaire de spécifier d'autres options, telles que Réessayer et Transactions. Utilisez les propriétés de contexte exposées par l'adaptateur pour définir ces options avant d'envoyer le message au port dynamique de sollicitation-réponse.  
  
-   Files d’attente MQSeries peuvent être créés et supprimés de manière dynamique à l’aide de la **MQSAdapterAdmin2** interface. Pour obtenir un exemple montrant comment créer dynamiquement des files d’attente MQSeries, consultez « Gestion de la prise en charge de file d’attente » à [http://go.microsoft.com/fwlink/?LinkId=89400](http://go.microsoft.com/fwlink/?LinkId=89400).