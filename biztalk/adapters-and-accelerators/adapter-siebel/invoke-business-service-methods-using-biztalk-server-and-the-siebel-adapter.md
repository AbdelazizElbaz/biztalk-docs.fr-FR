---
title: "Appeler des méthodes de Service Business à l’aide de BizTalk Server et l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke business service methods
- business service methods, invoking
ms.assetid: cf437c4f-fa65-4f89-a197-c83869930b2c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79a11d3be19ca27bd27146ef728ce168c3285884
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter"></a>Appeler des méthodes de Service Business à l’aide de BizTalk Server et l’adaptateur Siebel
Un service d’entreprise Siebel est une collection de méthodes d’entreprise qui peuvent être appelées directement dans Siebel. Pour plus d’informations sur la façon dont [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge l’appel de services d’entreprise dans un système Siebel, consultez [opérations sur les Services métier Siebel](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md). Pour plus d’informations sur la structure de SOAP des messages pour effectuer des opérations de service d’entreprise, consultez [des schémas de Message pour des opérations de Service Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md).  
  
## <a name="how-to-invoke-business-services"></a>Comment faire pour appeler des Services d’entreprise ?  
 Une opération sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md). Pour appeler un service d’entreprise, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour la méthode de service métier que vous souhaitez appeler.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système Siebel.  
  
3.  Créer l’orchestration pour appeler une méthode de service d’entreprise dans le système Siebel.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, BusinessService, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment appeler une méthode de service d’entreprise, nous allons générer de schéma pour le **Execute** méthode exposée par le **TimeStamp** service métier. Consultez [récupérer des métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour envoyer une demande au système Siebel et l’autre pour recevoir une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma :  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *BusinessService.SiebelBindingSchema.Execute*, où *BusinessService* est le nom de votre projet BizTalk. *SiebelBindingSchema* est le schéma généré pour appeler le *Execute* méthode de service d’entreprise.|  
  
5.  Répétez l’étape précédente pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *BusinessService.SiebelBindingSchema.ExecuteResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler un service d’entreprise. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] consomme ce message et le transmet au système Siebel. La réponse à partir du système Siebel est enregistrée dans un autre emplacement. Contiendrait une orchestration classique permettant d’appeler les méthodes de Service de l’entreprise :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à Siebel et recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à Siebel de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Siebel et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de Siebel vers un dossier.  
  
 Un exemple d’orchestration pour appeler le *Execute* méthode pour le *TimeStamp* service métier ressemble à ceci :  
  
 ![Orchestration permettant d’appeler un service d’entreprise](../../adapters-and-accelerators/adapter-siebel/media/5a776e5d-855f-4d1b-8d26-7de747b1865d.gif "5a776e5d-855f-4d1b-8d26-7de747b1865d")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveXML|Recevoir|-Définissez **nom** à *ReceiveXML*<br />-Définissez **activer** à *True*|  
|SendToLOB|Send|-Définissez **nom** à *SendToLOB*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br />-Définissez **Type** à *SaveResponseType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveXML|-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.ServiceInvoke.Request*|  
|SendToLOB|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.ServiceInvoke.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.ServiceInvoke.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.ServiceInvoke.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [comment générer des Orchestrations](../../core/how-to-build-orchestrations.md) et [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md). 
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [la création d’une Application](../../core/how-to-create-an-application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système Siebel.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir du système Siebel.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-Siebel physique pour envoyer des messages au système Siebel. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la Console Administration de BizTalk pour créer des ports d’envoi (pour les appels sortants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour l’exécution de la *Execute* méthode sur le *TimeStamp* service d’entreprise dans Siebel. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [démarrer une Application BizTalk](../../core/how-to-start-and-stop-a-biztalk-application.md) ou [démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-Siebel à envoyer des messages au système Siebel est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Vous devez supprimer le message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit respecter le schéma que vous avez généré précédemment dans cette rubrique. Consultez [des schémas de Message pour des opérations de Service Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md) pour plus d’informations sur le schéma pour l’appel d’un service d’entreprise. Par exemple, le message de demande pour appeler le *Execute* méthode sur le *TimeStamp* service d’entreprise est :  
  
```  
<Execute xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/TimeStamp/Operation" />  
```  
  
 L’orchestration consomme le message de demande et les transmet au système Siebel. La réponse à partir du système Siebel est enregistrée à l’emplacement d’envoi de fichier. La réponse pour le message de demande ci-dessus est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ExecuteResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/TimeStamp/Operation">  
  <ExecuteResult>  
    <Time xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/TimeStamp">2007-11-25T20:42:11.0000000</Time>  
  </ExecuteResult>  
</ExecuteResponse>  
```  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors d’une opération sur l’utilisation de service business [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur dans l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des Applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)