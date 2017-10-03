---
title: "Interrogation Oracle E-Business Suite à l’aide de procédures stockées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9e89dfe-f33a-436b-94c6-be78e84d5efd
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fbe58571866949dbd373440604e0cb02e32ed92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-stored-procedures"></a>Interrogation Oracle E-Business Suite à l’aide de procédures stockées
Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques à l’aide de procédures stockées pour l’interrogation de façon permanente la base de données Oracle. Vous pouvez spécifier une procédure stockée en tant qu’une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour interroger la base de données Oracle.  
  
 Pour activer l’interrogation, vous devez spécifier le que port de réception de certaines propriétés de liaison sur le WCF-Custom ou WCF-OracleEBS.  Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md). Pour plus d’informations sur la structure du message SOAP pour les opérations d’interrogation, consultez [des schémas de Message pour les opérations d’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md).  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-adapter-binding-properties"></a>Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business  
 Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison. Vous devez spécifier le port de réception de ces propriétés de liaison lors de la configuration WCF-Custom ou WCF-OracleEBS le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer un **d’interrogation** ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. Uniquement si un enregistrement n’est disponible, la procédure stockée que vous avez spécifié pour le **PollingInput** liaison de la propriété sera exécutée.|  
|**PollingInterval**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.|  
|**PollingInput**|Spécifie l’instruction d’interrogation. Pour interroger à l’aide d’une procédure stockée, vous devez spécifier le message de requête entière pour cette propriété de liaison. Le message de demande doit être le même que vous envoyez à l’adaptateur pour l’appel de la procédure stockée sous forme d’opération sortante. La valeur par défaut est null.<br /><br /> Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.|  
|**PollingAction**|Spécifie l’action pour l’opération d’interrogation. Vous pouvez déterminer l’action de l’interrogation d’une opération spécifique à partir des métadonnées que vous générez pour l’opération en utilisant la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].|  
|**PostPollStatement**|Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié. La valeur par défaut est False.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle, lisez les sections suivantes.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de données modifier des messages à l’aide de procédures stockées, créez un projet BizTalk et générer le schéma de la procédure stockée que vous souhaitez utiliser pour interroger la base de données Oracle. Dans cette rubrique, nous utilisons la procédure stockée de GET_ACTIVITYS pour interroger la table ACCOUNTACTIVITY. Cette procédure stockée est disponible avec le package ACCOUNT_PKG. Vous pouvez exécuter les scripts SQL fournis avec les exemples pour créer ces objets dans la base de données.  
  
> [!NOTE]
>  L’orchestration sous cette forme de sondages rubrique le ACCOUNTACTIVITY de table, qui est une table de base de données créée en exécutant les scripts fournis avec les exemples. Vous devez effectuer les procédures similaires comme décrit dans cette rubrique pour interroger toute autre table, y compris les tables de l’interface.  
  
 Pour illustrer une opération d’interrogation, nous les opérations suivantes :  
  
-   Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où la table interrogés (ACCOUNTACTIVITY) comporte des données. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  
  
     Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table ACCOUNTACTIVITY a des enregistrements.  
  
-   Exécuter une procédure stockée, GET_ACTIVITYS, en fournissant le message de demande dans le cadre de la **PollingInput** propriété de liaison. Cette procédure stockée récupère toutes les lignes dans la table ACCOUNTACTIVITY et vous obtiendrez un message de réponse de l’adaptateur.  
  
-   EXÉCUTION d’un bloc de PL/SQL dans le cadre de la **PostPollStatement** propriété de liaison. Cette instruction déplacera toutes les données à partir de la table ACCOUNTACTIVITY à une autre table dans la base de données. Une fois que cela se produit, la prochaine fois **PollingInput** sera exécutée, elle ne permet pas d’extraire des données et par conséquent, la procédure stockée de GET_ACTIVITYS retournera un message de réponse vide.  
  
-   Jusqu'à ce que davantage de données est ajouté à la table ACCOUNTACTIVITY, vous continuerez de recevoir des messages de réponse vide. Par conséquent, vous devez remplir de nouveau la table ACCOUNTACTIVITY avec les nouveaux enregistrements. Vous pouvez le faire en exécutant le script more_activity_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.  
  
## <a name="how-to-receive-data-change-messages-from-oracle"></a>La réception des Messages de modification de données à partir d’Oracle  
 Une opération sur l’utilisation de base de données Oracle [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches procédurales suivantes décrites dans [blocs de construction pour créer la liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour configurer l’adaptateur pour interroger la base de données Oracle à l’aide d’une procédure stockée, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma de la procédure stockée que vous souhaitez utiliser pour l’interrogation.  
  
2.  Créez un message dans le projet BizTalk pour recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour recevoir des messages à partir de la base de données Oracle et les enregistrer dans un dossier.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, PollingUsingStoredProc, en fonction de cette rubrique est également fourni avec BizTalk Adapter Pack. Pour plus d’informations, consultez [exemples](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour l’opération GET_ACTIVITYS. Effectuer les tâches suivantes lors de la génération de schéma à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
-   Sélectionnez le type de contrat **Service (opération entrante)**.  
  
-   Génération du schéma pour le **GET_ACTIVITYS** procédure.  
  
 Pour plus d’informations sur la génération de schéma, consultez [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Pour cette rubrique, vous devez créer un message à recevoir des messages à partir d’Oracle.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis **ajouter**.  
  
2.  Ouvrez la fenêtre Vue orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réception**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Polling.OracleEBSBindingSchema*, où *d’interrogation* est le nom de votre projet BizTalk. *OracleEBSBindingSchema* est le schéma de réponse généré pour le **GET_ACTIVITYS** procédure stockée.<br /><br /> **Important :** , car l’interrogation est une opération unidirectionnelle, le schéma généré par l’adaptateur ne contient pas un nœud de la réponse, et il n'est qu’un seul nœud racine dans le schéma. Si vous utilisez ce type de schéma pour un type de message, vous devez identifier le schéma par le nom de fichier du schéma généré.<br /><br /> Par exemple, si vous créez le schéma pour une opération bidirectionnelle, les nœuds dans le schéma de fichier avec un nom `OracleEBSBindingSchema` peut ressembler à « Requête » et « Réponse ». Si vous souhaitez créer un message dans l’orchestration qui mappe au schéma de requête, vous pouvez identifier le schéma dans la liste en recherchant `OracleEBSBindingSchema.Request`. Toutefois, dans le cas d’opération d’interrogation, car le seul nœud est « Interrogation », il n’est pas facile d’identifier le schéma que vous voulez mapper à, car les schémas avec des nœuds individuels ne sont pas répertoriées en tant que \<schemafilename >.\< rootnodename >. Au lieu de cela, ces schémas sont répertoriées par uniquement le nom de fichier. Dans ce cas, la seule façon d’identifier le schéma est par le nom de fichier de schéma, par exemple, OracleEBSBindingSchema.|  
  
     Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère le schéma pour les opérations entrantes et sortantes pour le GET_ACTIVITYS de procédure stockée. Vous devez utiliser le schéma d’opération entrante :  
  
    -   Mapper le message créé dans le cadre de l’orchestration.  
  
    -   Pour récupérer l’action que vous devez spécifier pour le **PollingAction** propriété de liaison au moment de l’exécution.  
  
     Vous devez utiliser le schéma pour l’opération sortante pour obtenir le message de demande que vous devez spécifier dans le cadre de la **PollingInput** propriété de liaison.  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir les messages de modification de données reposant sur l’interrogation à partir d’Oracle. Dans cette orchestration, l’adaptateur reçoit la réponse en exécutant la procédure stockée pour lequel vous avez spécifié le message de demande dans le cadre de la **PollingInput** propriété de liaison. Le message de réponse pour la procédure stockée est enregistré dans un emplacement de fichier. Contiendrait une orchestration classique de l’interrogation de la base de données Oracle :  
  
-   Formes réception et envoi pour recevoir des messages à partir d’Oracle et l’envoyer vers un port FILE, respectivement.  
  
-   Port pour recevoir des messages à partir de la base de données Oracle de réception unidirectionnel.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
-   Un port d’envoi unidirectionnel pour envoyer des réponses d’interrogation à partir de la base de données Oracle.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration pour une requête d’interrogation pour Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3.gif "6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br /><br /> -Définissez **activer** à *True*|  
|SaveMessage|Send|-Définissez **nom** à *SaveMessage*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|OracleReceivePort|-Définissez **identificateur** à *OracleReceivePort*<br /><br /> -Définissez **Type** à *OracleReceivePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|SaveMessagePort|-Définissez **identificateur** à *SaveMessagePort*<br /><br /> -Définissez **Type** à *SaveMessagePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *de réception*<br /><br /> -Définissez **opération** à *OracleReceivePort.Polling.Request*|  
|SaveMessage|-Définissez **Message** à *de réception*<br /><br /> -Définissez **opération** à *SaveMessagePort.Polling.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera les messages à partir d’Oracle. Ces messages seront en réponse à l’instruction d’interrogation que vous spécifiez pour le port de réception.  
  
    -   Définir un WCF-Custom physique ou port de réception WCF-OracleEBS à sens unique. Ce port interroge la base de données Oracle. Pour plus d’informations sur la création des ports de réception, consultez [configurer manuellement un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Affectez la valeur **d’interrogation**.|  
        |**PolledDataAvailableStatement**|Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `SELECT COUNT (*) FROM ACCOUNTACTIVITY`<br /><br /> Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table ACCOUNTACTIVITY a des enregistrements.|  
        |**PollingAction**|L’action d’interrogation de récupérer à partir du schéma généré pour le message entrant pour la procédure GET_ACTIVITYS. Pour cet exemple, affectez à cette propriété de liaison **PollingPackageApis/applications/ACCOUNT_PKG/GET_ACTIVITYS**.|  
        |**PollingInput**|Pour cette propriété de liaison, spécifiez le message de demande pour appeler le GET_ACTIVITYS de procédure stockée. Vous pouvez obtenir le message de demande à partir du schéma pour l’opération sortante générée par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Vous devez fournir l’intégralité du message XML comme entrée pour cette propriété de liaison. Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `<GET_ACTIVITYS xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG">   <INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS> </GET_ACTIVITYS>`<br /><br /> Le GET_ACTIVITYS stockées procédure prend un REF CURSOR d’entrée en tant que paramètre.|  
        |**PostPollStatement**|Spécifiez l’instruction après interrogation pour déplacer toutes les données à partir de la table ACCOUNTACTIVITY à une autre table. Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;`|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
        > [!IMPORTANT]
        >  Si vous sont l’interrogation d’une table d’interface, vous devez définir le contexte d’application en spécifiant les propriétés de liaison requis. Pour plus d’informations sur la définition du contexte d’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Vous pouvez le faire en ajoutant le comportement de service lors de la configuration WCF-Custom ou WCF-OracleEBS port de réception. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer au niveau d’Isolation de Transaction et le délai d’attente de Transaction avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk afin d’interroger la base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-OracleEBS à sens unique port de réception, qui interroge Oracle à l’aide de la procédure stockée spécifiée pour le **PollingInput** propriété, de liaison est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir de la base de données Oracle, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur exécute le **PolledDataAvailableStatement** qui retourne une valeur positive indiquant l’adaptateur pour exécuter l’instruction spécifiée pour **PollingInput** propriété de liaison.  
  
-   L’adaptateur exécute la procédure stockée de GET_ACTIVITYS spécifiée pour le **PollingInput** liaison de propriété et retourne toutes les lignes dans la table ACCOUNTACTIVITY. La réponse à partir de la base de données Oracle ressemble à ceci :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <GET_ACTIVITYS xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG">  
      <OUTRECS>  
        <OUTRECSRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ReferencedRecordTypes/APPS/ACCOUNT_PKG/GET_ACTIVITYS/APPS/GET_ACTIVITYS">  
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-06-21T15:52:19</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        </OUTRECSRecord>  
        <OUTRECSRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ReferencedRecordTypes/APPS/ACCOUNT_PKG/GET_ACTIVITYS/APPS/GET_ACTIVITYS">  
          ......  
          ......   
        </OUTRECSRecord>  
        ......  
        ......  
      </OUTRECS>  
    </GET_ACTIVITYS>  
    ```  
  
-   L’adaptateur exécute l’instruction après interrogation, ce qui déplace toutes les données à partir de la table ACCOUNTACTIVITY à une autre table.  
  
-   Après l’intervalle d’interrogation, l’adaptateur s’exécute à nouveau **PolledDataAvailableStatement**. Car ACCOUNTACTIVITY table aucun enregistrement maintenant, **PolledDataAvailableStatement** ne retourne pas une valeur positive et par conséquent, l’adaptateur ne s’exécute pas l’instruction spécifiée pour le **PollingInput** propriété de liaison. Par conséquent, client de carte n’obtient pas de tout message d’interrogation.  
  
-   Le client de carte n’obtiendra pas plus de messages d’interrogation jusqu'à ce que des enregistrements sont insérés explicitement dans la table ACCOUNTACTIVITY. Pour insérer des enregistrements de plus, vous pouvez exécuter le script more_activity_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, lors du prochain **PolledDataAvailableStatement** est exécutée, elle retourne une valeur positive. Par conséquent, l’adaptateur exécute l’instruction d’interrogation et les clients de carte à nouveau un message d’interrogation.  
  
> [!NOTE]
>  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] continue à interroger jusqu'à ce que vous désactiviez explicitement le port de réception à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de réutiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)