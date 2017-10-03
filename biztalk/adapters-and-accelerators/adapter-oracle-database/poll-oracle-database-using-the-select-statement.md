---
title: "Base de données Oracle interrogation à l’aide de l’instruction SELECT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- polling-based notifications, receiving from Oracle
- polling query, configuring a
ms.assetid: d2689eb9-6f17-498f-8a32-07f43a368833
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26e840148b4a5cfb8b390d5e89ee0e8edc677aad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-database-using-the-select-statement"></a>Base de données Oracle interrogation à l’aide de l’instruction SELECT
Vous pouvez configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour recevoir des messages de modification de données périodiques à l’aide d’une instruction SELECT pour interroger en permanence des tables et des vues dans la base de données Oracle d’Oracle. Vous pouvez spécifier une instruction SELECT comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour interroger la base de données Oracle. Si vous le souhaitez, vous pouvez également spécifier un bloc de code après interrogation PL/SQL qui s’exécute de l’adaptateur s’il existe une modification de données. Ce bloc est souvent utilisé pour mettre à jour un champ sur les enregistrements interrogées dans la cible ou pour déplacer les enregistrements de requête vers une autre table ou vue.  
  
 Pour ce faire, vous devez spécifier certaines propriétés de liaison sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Vous pouvez également modifier l’espace de noms cible pour l’opération POLLINGSTMT en définissant le **PollingId** propriété dans l’URI de connexion. Pour plus d’informations, consultez [prise en charge de Messages basés sur la réception d’interrogation de données modifiées dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md) et [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md). Pour plus d’informations sur la structure du message SOAP pour les opérations d’interrogation, consultez [des schémas de Message pour l’interrogation Operations2](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).  
  
## <a name="configuring-a-polling-operation-with-oracle-database-adapter-binding-properties"></a>Configuration d’une opération d’interrogation avec l’adaptateur de base de données Oracle propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] messages de modification des propriétés de liaison que vous utilisez pour configurer l’adaptateur pour recevoir des données. Vous devez spécifier ces propriétés de liaison lors de la configuration du port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer d’interrogation ou de Notification opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. Uniquement si un enregistrement n’est disponible, l’instruction SELECT que vous spécifiez pour le **PollingStatement** liaison de la propriété sera exécutée. La valeur par défaut est `SELECT 1 FROM DUAL`, ce qui implique que l’adaptateur doit continuer d’interrogation même si la table interrogée a des données ou non.|  
|**PollingInterval**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 500 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.|  
|**PollingStatement**|Spécifie l’instruction d’interrogation. Pour interroger à l’aide d’une instruction SELECT, vous devez spécifier une instruction SELECT pour cette propriété de liaison. La valeur par défaut est null.<br /><br /> Vous devez spécifier une valeur pour **PollingStatement** propriété pour activer l’interrogation de liaison. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.|  
|**PollingAction**|Spécifie l’action pour l’opération d’interrogation. Vous pouvez déterminer l’action de l’interrogation d’une opération spécifique à partir des métadonnées que vous générez pour l’opération en utilisant la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].|  
|**PostPollStatement**|Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingStatement** propriété de liaison est exécutée.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié. La valeur par défaut est False.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger la base de données Oracle, poursuivre la lecture.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la réception de données modifier des messages à l’aide des instructions SELECT, créez un projet BizTalk et générer le schéma pour le **POLLINGSTMT** opération en définissant le  **PollingStatement** propriété de liaison à ce qui suit :  
  
```  
SELECT * FROM ACCOUNTACTIVITY FOR UPDATE  
```  
  
 La table ACCOUNTACTIVITY est créée lorsque vous exécutez les scripts SQL fournis avec les exemples pour créer ces objets dans la base de données.  
  
> [!NOTE]
>  L’orchestration sous cette forme de sondages rubrique le ACCOUNTACTIVITY de table, qui est une table de base de données créée en exécutant les scripts fournis avec les exemples. Vous devez effectuer les procédures similaires comme décrit dans cette rubrique pour interroger toute autre table.  
  
 Pour illustrer une opération d’interrogation, nous les opérations suivantes :  
  
-   Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où la table interrogés (ACCOUNTACTIVITY) comporte des données. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  
  
     Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table ACCOUNTACTIVITY a des enregistrements.  
  
-   Spécifiez l’instruction SELECT comme indiqué précédemment pour le **PollingStatement** propriété de liaison. Cette instruction récupère toutes les lignes dans la table ACCOUNTACTIVITY.  
  
-   EXÉCUTION d’un bloc de PL/SQL dans le cadre de la **PostPollStatement** propriété de liaison. Cette instruction déplacera toutes les données à partir de la table ACCOUNTACTIVITY à une autre table dans la base de données. Une fois que cela se produit, la prochaine fois que l’instruction spécifiée pour **PollingStatement** sera exécutée, elle ne permet pas d’extraire des données.  
  
-   Jusqu'à ce que davantage de données est ajouté à la table ACCOUNTACTIVITY, vous n’obtiendrez pas les messages d’interrogation. Par conséquent, vous devez remplir de nouveau la table ACCOUNTACTIVITY avec les nouveaux enregistrements. Vous pouvez le faire en exécutant le script more_activity_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.  
  
## <a name="how-to-receive-data-change-messages-from-oracle"></a>La réception des Messages de modification de données à partir d’Oracle  
 Une opération sur l’utilisation de base de données Oracle [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches procédurales suivantes décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour configurer l’adaptateur pour interroger la base de données Oracle à l’aide d’une instruction SELECT, ces tâches sont :  
  
1.  Créez un projet BizTalk et la génération du schéma pour le **POLLINGSTMT** opération pour la table que vous voulez interroger.  
  
2.  Créez un message dans le projet BizTalk pour recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour recevoir des messages à partir d’Oracle et les enregistrer dans un dossier.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le **POLLINGSTMT** opération. Effectuer les tâches suivantes lors de la génération de schéma à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
-   Spécifiez une valeur pour **PollingStatement** lors de la génération du schéma de propriété de liaison. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). Par exemple, spécifiez les éléments suivants en tant qu’une instruction d’interrogation :  
  
    ```  
    SELECT * FROM ACCOUNTACTIVITY FOR UPDATE  
    ```  
  
-   Sélectionnez le type de contrat **Service (opération entrante)**.  
  
-   Génération du schéma pour le **POLLINGSTMT** opération.  
  
 Pour plus d’informations sur la génération de schéma, consultez [Parcourir, rechercher et obtenir des métadonnées pour les opérations de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md).  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *TablePolling.OracleDBBinding*, où *TablePolling* est le nom de votre projet BizTalk. *OracleDBBindingSchema* est le schéma de réponse généré pour le **POLLINGSTMT** opération sur la table ACCOUNTACTIVITY.<br /><br /> **Important** , car l’interrogation est une opération unidirectionnelle, le schéma généré par l’adaptateur ne contient pas un nœud de la réponse, et il n'est qu’un seul nœud racine dans le schéma. Si vous utilisez ce type de schéma pour un type de message, vous devez identifier le schéma par le nom de fichier du schéma généré.<br /><br /> Par exemple, si vous créez le schéma pour une opération bidirectionnelle, les nœuds dans le schéma de fichier avec un nom `OracleDBBindingSchema` peut ressembler à « Requête » et « Réponse ». Si vous souhaitez créer un message dans l’orchestration qui mappe au schéma de requête, vous pouvez identifier le schéma dans la liste en recherchant `OracleDBBindingSchema.Request`. Toutefois, dans le cas d’opération d’interrogation, car le seul nœud est « POLLINGSTMT », il n’est pas facile d’identifier le schéma que vous voulez mapper à, car les schémas avec des nœuds individuels ne sont pas répertoriées en tant que \<schemafilename >.\< rootnodename >. Au lieu de cela, ces schémas sont répertoriées par uniquement le nom de fichier. Dans ce cas, la seule façon d’identifier le schéma est par le nom de fichier de schéma, par exemple, OracleDBBindingSchema.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir les messages de modification de données reposant sur l’interrogation à partir d’Oracle. Dans cette orchestration, l’adaptateur reçoit la réponse en exécutant l’instruction SELECT spécifiée pour le **PollingStatement** propriété de liaison. Le message de réponse pour l’instruction SELECT est enregistré dans un emplacement de fichier. Contiendrait une orchestration classique de l’interrogation de la base de données Oracle :  
  
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
  
    -   Définir un WCF-Custom physique ou port de réception WCF-OracleDB à sens unique. Ce port interroge la base de données Oracle. Pour plus d’informations sur la création des ports de réception, consultez [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Affectez la valeur **d’interrogation**.|  
        |**PolledDataAvailableStatement**|Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `SELECT COUNT (*) FROM ACCOUNTACTIVITY`<br /><br /> Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table ACCOUNTACTIVITY a des enregistrements.|  
        |**PollingStatement**|Pour cette propriété de liaison, spécifiez une instruction SELECT pour récupérer tous les enregistrements à partir de la table ACCOUNTACTIVITY. Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `SELECT * FROM ACCOUNTACTIVITY FOR UPDATE`|  
        |**PostPollStatement**|Spécifiez l’instruction après interrogation pour déplacer toutes les données à partir de la table ACCOUNTACTIVITY à une autre table. Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;`|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Vous pouvez le faire en ajoutant le comportement de service lors de la configuration du port de réception. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer le niveau d’isolation de transaction et le délai d’attente de transaction](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk afin d’interroger la base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-OracleDB unidirectionnel port de réception, qui interroge Oracle à l’aide de l’instruction SELECT spécifiée pour le **PollingStatement** propriété, de liaison est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir de la base de données Oracle, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur exécute le **PolledDataAvailableStatement** qui retourne une valeur positive indiquant l’adaptateur pour exécuter l’instruction spécifiée pour **PollingStatement** propriété de liaison.  
  
-   L’adaptateur exécute l’instruction SELECT pour le **PollingStatement** liaison de propriété et retourne toutes les lignes dans la table ACCOUNTACTIVITY. La réponse à partir de la base de données Oracle ressemble à ceci :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <POLLINGSTMT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT">  
      <POLLINGSTMTRECORD>  
        <POLLINGSTMTRECORD>  
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-08-03T20:10:28</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        <POLLINGSTMTRECORD>  
      <POLLINGSTMTRECORD>  
          ......  
          ......  
      </POLLINGSTMTRECORD>  
        ......  
        ......  
      </POLLINGSTMTRECORD>  
    </POLLINGSTMT>  
    ```  
  
-   L’adaptateur exécute l’instruction après interrogation, ce qui déplace toutes les données à partir de la table ACCOUNTACTIVITY à une autre table.  
  
-   Après l’intervalle d’interrogation, l’adaptateur s’exécute à nouveau **PolledDataAvailableStatement**. Car ACCOUNTACTIVITY table aucun enregistrement maintenant, **PolledDataAvailableStatement** ne retourne pas une valeur positive et par conséquent, l’adaptateur ne s’exécute pas l’instruction spécifiée pour le **PollingStatement**propriété de liaison. Par conséquent, client de carte n’obtient pas de tout message d’interrogation.  
  
-   Le client de carte n’obtiendra pas plus de messages d’interrogation jusqu'à ce que des enregistrements sont insérés explicitement dans la table ACCOUNTACTIVITY. Pour insérer des enregistrements de plus, vous pouvez exécuter le script more_activity_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, lors du prochain **PolledDataAvailableStatement** est exécutée, elle retourne une valeur positive. Par conséquent, l’adaptateur exécute l’instruction d’interrogation et les clients de carte à nouveau un message d’interrogation.  
  
> [!NOTE]
>  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] continue à interroger jusqu'à ce que vous désactiviez explicitement le port de réception à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de l’exécution d’une requête d’interrogation sur Oracle de base de données à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données Oracle interrogation à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)