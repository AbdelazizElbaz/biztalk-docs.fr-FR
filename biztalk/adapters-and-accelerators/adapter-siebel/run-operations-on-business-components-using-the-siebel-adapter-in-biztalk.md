---
title: "Exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business components, performing operations by using BizTalk Server
- how to, perform operations on a business component by using BizTalk Server
ms.assetid: 5bd0f4d7-60ec-42ea-84c0-618aeef9688f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3fc90d0798e3fca420e567d1a50c58607db4ae3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-operations-on-business-components-using-biztalk-server-and-the-siebel-adapter"></a>Exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel
Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] couvre les opérations qui peuvent être appelées sur un composant d’entreprise. Les opérations sur les composants d’entreprise peuvent être classées comme :  
  
-   Opérations standard sur les composants d’entreprise. Cela comprend les mises à jour de l’insertion, la requête et suppriment. Cette rubrique explique comment effectuer ces opérations à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
-   Opérations sur les composants d’entreprise contenant des champs de groupe à valeurs multiples. Notamment les opérations standard ainsi associer, dissocier, Query_ [MVG_Child_Bussiness_Comp]. Pour plus d’informations sur ces opérations, consultez [exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)  
  
-   Opérations sur les composants d’entreprise contenant des champs de la liste de choix. Pour plus d’informations sur ces opérations, consultez [exécuter des opérations sur les composants d’entreprise avec les champs de liste de choix à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md).  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge les opérations sur les composants d’entreprise, consultez [opérations sur les composants d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md). Pour plus d’informations sur la structure de SOAP des messages pour effectuer ces opérations, consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
## <a name="how-to-perform-operations-on-a-business-component"></a>Comment effectuer des opérations sur un composant d’entreprise  
 Une opération sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md). 
 
 Pour effectuer une opération sur un composant d’entreprise, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma d’opération à appeler sur le composant de gestion.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système Siebel.  
  
3.  Créez une orchestration pour appeler une opération dans le système Siebel.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, SiebelAccount, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment appeler des opérations sur un composant d’entreprise, schéma sont générés pour l’opération d’insertion dans le composant de gestion de compte. Consultez [récupérer des métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SiebelAccount.SiebelBindingSchema.Insert*, où *SiebelAccount* est le nom de votre projet BizTalk. *SiebelBindingSchema* est le schéma généré pour appeler le *insérer* opération sur *compte* composant d’entreprise.|  
  
5.  Répétez l’étape précédente pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SiebelAccount.SiebelBindingSchema.InsertResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer une opération sur un composant d’entreprise Siebel. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] consomme ce message et le transmet au système Siebel. La réponse à partir du système Siebel est enregistrée dans un autre emplacement. Une orchestration classique pour effectuer des opérations sur les composants d’entreprise Siebel contient :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à Siebel et recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à Siebel de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Siebel et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de Siebel vers un dossier.  
  
 Un exemple d’orchestration pour les *insérer* opération sur un *compte* composant d’entreprise ressemble à ceci :  
  
 ![Orchestration permettant d’insérer des données dans Siebel BC](../../adapters-and-accelerators/adapter-siebel/media/f005df04-dfbf-4c75-8f9b-2bc3a357d52b.gif "f005df04-dfbf-4c75-8f9b-2bc3a357d52b")  
  
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
|ReceiveXML|-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.Insert.Request*|  
|SendToLOB|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.Insert.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.Insert.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.Insert.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [comment générer des Orchestrations](../../core/how-to-build-orchestrations.md) et [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. [Comment créer une Application](../../core/how-to-create-an-application.md) répertorie les étapes.
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système Siebel.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir du système Siebel.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-Siebel physique pour envoyer des messages au système Siebel. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la Console Administration de BizTalk pour créer des ports d’envoi (pour les appels sortants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour effectuer une *insérer* opération sur le *compte* composant d’entreprise dans Siebel. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [démarrer une Application BizTalk](../../core/how-to-start-and-stop-a-biztalk-application.md) ou [démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-Siebel à envoyer des messages au système Siebel est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer le message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma de l’opération d’insertion (sur le composant de compte d’entreprise) que vous avez généré précédemment. Par exemple, le message de demande d’insérer un enregistrement dans le composant de gestion de compte est :  
  
```  
<Insert xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
  <ArrayOfAccountInsertRecord>  
    <AccountInsertRecord xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">  
      <Currency_x0020_Code>usd</Currency_x0020_Code>  
      <Current_x0020_Volume>9</Current_x0020_Volume>  
      <Customer_x0020_Account_x0020_Group>Sold-To Party</Customer_x0020_Account_x0020_Group>  
      <Location>Location_1</Location>  
      <Main_x0020_Phone_x0020_Number>4256543212</Main_x0020_Phone_x0020_Number>  
      <Name>Name_Surname</Name>  
      <Party_x0020_Name>test_party</Party_x0020_Name>  
      <Primary_x0020_Address_x0020_Id>1212 street</Primary_x0020_Address_x0020_Id>  
    </AccountInsertRecord>  
  </ArrayOfAccountInsertRecord>  
</Insert>  
```  
  
 Consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md) pour plus d’informations sur le schéma du message de demande.  
  
 L’orchestration consomme le message de demande et les transmet au système Siebel. La réponse à partir du système Siebel est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse du système Siebel pour le message de demande ci-dessus est :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<InsertResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
  <InsertResult>  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">1-8ANYV</string>  
  </InsertResult>  
</InsertResponse>  
```  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’exécution d’une opération sur l’entreprise à l’aide de composant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur dans l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des Applications BizTalk à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)