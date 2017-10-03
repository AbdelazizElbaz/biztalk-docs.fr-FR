---
title: "Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ecaf6f7-974b-4487-8c65-d1ab628cbfeb
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b86a58a092f5f38c4a09c014feb0b4fe85d1fc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a>Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de modification de données périodiques de tables SQL Server ou des vues. Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.  

  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge pour l’interrogation](https://msdn.microsoft.com/library/dd788416.aspx). Pour plus d’informations sur la structure du message SOAP pour les opérations d’interrogation, consultez [des schémas de Message pour l’interrogation et les opérations de TypedPolling](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md).  
  
> [!NOTE]
>  Cette rubrique montre comment utiliser le **d’interrogation** entrant d’opération à utiliser les messages d’interrogation. Le message de l’opération d’interrogation n’est pas fortement typée et schéma de l’objet interrogé est récupérée en même temps que le message au moment de l’exécution. Si vous souhaitez obtenir le message d’interrogation fortement typée, vous devez utiliser le **TypedPolling** opération. Vous devez également utiliser le **TypedPolling** opération plusieurs opérations d’interrogation dans une même application BizTalk. Pour obtenir des instructions sur la façon d’effectuer **TypedPolling** opération, consultez [réception fortement typé reposant sur l’interrogation Messages de modification de données à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md).  
  
> [!IMPORTANT]
>  Si vous souhaitez disposer d’interrogation plus d’une opération dans une même application BizTalk, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique. Avec un URI de connexion unique, vous pouvez créer plusieurs ports de réception qui interrogent la même base de données, ou même de la même table dans une base de données. Pour plus d’informations, consultez [de réception d’interrogation Messages entre plusieurs Ports réception à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception de données les messages de modification, créez un projet BizTalk et générer le schéma pour le **d’interrogation** opération. Si vous souhaitez spécifier l’interrogation liées au moment du design des propriétés de liaison, spécifiez la **PolledDataAvailableStatement** en tant que :  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 Le **PolledDataAvailableStatement** doit retourner un jeu de résultats avec la première cellule contenant une valeur positive. Si la première cellule ne contient pas une valeur positive, l’adaptateur n’exécute pas l’instruction d’interrogation.  
  
 Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :  
  
-   Sélectionnez toutes les lignes de la table Employee.  
  
-   Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.  
  
-   Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee. Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.  
  
 Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison :  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 Après l’exécution de l’instruction d’interrogation, tous les enregistrements de la table Employee sont sélectionnés et le message à partir de SQL Server est supprimé à un emplacement de réception. Une fois la procédure stockée de MOVE_EMP_DATA est exécutée par l’adaptateur, tous les enregistrements sont déplacés vers la table HistoriqueEmployé. Ensuite, la procédure stockée de ADD_EMP_DETAILS est exécutée pour ajouter un nouvel enregistrement dans la table Employee. L’exécution de l’interrogation suivante retourne uniquement un seul enregistrement. Ce cycle se poursuit jusqu'à ce que vous désactiviez la réception port qui interroge SQL Server.  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a>Configuration d’une requête d’interrogation avec l’adaptateur SQL propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison. Vous devez spécifier ces propriétés de liaison lors de la configuration du port de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!NOTE]
>  Vous pouvez choisir de spécifier ces propriétés de liaison lors de la génération du schéma pour le **d’interrogation** opération, même si elle n’est pas obligatoire. Si vous procédez ainsi, la liaison du port de fichiers qui le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère comme partie de la génération de métadonnées contient également les valeurs spécifiées pour les propriétés de liaison. Vous pouvez importer ultérieurement ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] port de réception de la console Administration pour créer le WCF-custom ou WCF-SQL avec la liaison de propriétés déjà définies. Pour plus d’informations sur la création d’un port à l’aide du fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
|Propriété de liaison| Description|  
|---|---|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes. Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.|  
|**PollingIntervalInSeconds**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.|  
|**PollingStatement**|Spécifie l’instruction SQL pour interroger la table de base de données SQL Server. Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation. La valeur par défaut est null. Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison. Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié. Valeur par défaut est **false**.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, poursuivre la lecture.  
  
## <a name="how-to-receive-data-change-messages-from-the-sql-server-database"></a>La réception des Messages de modification de données à partir de la base de données SQL Server  
 Une opération sur la base de données SQL Server à l’aide [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour configurer l’adaptateur pour recevoir des messages de modification de données, ces tâches sont :  
  
1.  Créez un projet BizTalk, puis générer le schéma pour le **d’interrogation** opération. Si vous le souhaitez, vous pouvez spécifier des valeurs pour le **PolledDataAvailableStatement** et **PollingStatement** propriétés de liaison.  
  
2.  Créez un message dans le projet BizTalk pour recevoir des messages à partir de la base de données SQL Server.  
  
3.  Créez une orchestration pour recevoir des messages à partir de la base de données SQL Server et les enregistrer dans un dossier.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!IMPORTANT]
    >  Pour les scénarios de trafic entrant d’interrogation, vous devez toujours configurer un WCF-Custom unidirectionnel ou port de réception WCF-SQL. Ports de réception bidirectionnel WCF-Custom ou WCF-SQL ne sont pas pris en charge pour les opérations entrantes.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le **d’interrogation** opération. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer le schéma. Effectuer les tâches suivantes lors de la génération du schéma. Ignorer la première étape si vous ne souhaitez pas spécifier les propriétés de liaison au moment du design.  
  
1.  Spécifiez une valeur pour **PolledDataAvailableStatement** et **PollingStatement** propriétés de liaison lors de la génération du schéma. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
     Pour obtenir des instructions sur la façon de spécifier les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
2.  Sélectionnez le type de contrat **Service (opération entrante)**.  
  
3.  Génération du schéma pour le **d’interrogation** opération.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Pour cette rubrique, vous devez créer un message à recevoir des messages à partir de la base de données SQL Server.  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *PollingQuery.Polling*, où *PollingQuery* est le nom de votre projet BizTalk. *L’interrogation* est le schéma généré pour le **d’interrogation** opération.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir les messages de modification de données reposant sur l’interrogation de la base de données SQL Server. Dans cette orchestration, l’adaptateur reçoit la réponse de l’instruction select spécifiée pour le **PollingStatement** propriété de liaison. La réponse pour l’instruction SELECT est enregistrée dans un emplacement de fichier. Contiendrait une orchestration classique permettant l’interrogation d’une base de données SQL Server :  
  
-   Recevoir et envoyer des formes pour recevoir des messages à partir de SQL Server et les envoyer vers un port FILE, respectivement.  
  
-   Unidirectionnel port de réception pour recevoir des messages à partir de SQL Server.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
-   Un port d’envoi unidirectionnel pour envoyer des réponses d’interrogation à partir d’une base de données SQL Server dans un dossier.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration permettant l’interrogation d’une base de données SQL Server](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")  
  
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
|SQLReceivePort|-Définissez **identificateur** à *SQLReceivePort*<br /><br /> -Définissez **Type** à *SQLReceivePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|SaveMessagePort|-Définissez **identificateur** à *SaveMessagePort*<br /><br /> -Définissez **Type** à *SaveMessagePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *de réception*<br /><br /> -Définissez **opération** à *SQLReceivePort.Polling.Request*|  
|SaveMessage|-Définissez **Message** à *de réception*<br /><br /> -Définissez **opération** à *SaveMessagePort.Polling.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md). 
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera les messages à partir de la base de données SQL Server. Ces messages seront en réponse à l’instruction d’interrogation que vous spécifiez pour le port de réception.  
  
    -   Définir un WCF-Custom physique ou le port de réception unidirectionnel WCF-SQL. Ce port interroge la base de données SQL Server avec l’instruction d’interrogation que vous spécifiez pour le port. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        > [!IMPORTANT]
        >  Vous n’avez pas besoin d’effectuer cette étape si vous avez spécifié les propriétés de liaison au moment du design. Dans ce cas, vous pouvez créer un WCF-custom ou WCF-SQL port de réception, avec le jeu de propriétés de liaison requis, en important le fichier de liaison créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Assurez-vous que vous affectez la valeur **d’interrogation**.|  
        |**PolledDataAvailableStatement**|Assurez-vous que vous spécifiez une instruction SQL. Pour cette rubrique, spécifiez :<br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |**PollingStatement**|Assurez-vous que vous spécifiez l’instruction d’interrogation. Pour cette rubrique, spécifiez :<br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez effectuer afin d’en ajoutant le service de port de réception comportement lors de la configuration WCF-Custom ou WCF-SQL. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer Transaction Isolation Level et délai de Transaction SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour recevoir des messages à partir de la base de données SQL Server. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-SQL unidirectionnel port de réception, qui interroge la base de données SQL Server à l’aide d’instructions spécifiées pour le **PollingStatement** propriété, de liaison est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir de SQL Server, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur exécute le **PolledDataAvailableStatement** sur l’employé de table et détermine que la table comporte des enregistrements pour l’interrogation.  
  
-   L’adaptateur exécute l’instruction d’interrogation. Étant donné que l’instruction d’interrogation se compose d’une instruction SELECT et les procédures stockées, l’adaptateur s’exécute toutes les instructions une après l’autre.  
  
    -   Tout d’abord, l’adaptateur exécute l’instruction SELECT qui retourne tous les enregistrements dans la table Employee.  
  
    -   L’adaptateur exécute ensuite la procédure MOVE_EMP_DATA stockées qui déplace toutes les données à partir de la table Employee à la table HistoriqueEmployé. Cette procédure stockée ne retourne pas de n’importe quelle valeur.  
  
    -   L’adaptateur exécute ensuite la procédure stockée de ADD_EMP_DETAILS qui ajoute un enregistrement à la table Employee. Cette procédure stockée renvoie l’ID d’employé de l’enregistrement inséré.  
  
     Par conséquent, le message reçu à partir de SQL Server contient plusieurs jeux de résultats (pour l’instruction SELECT et pour la procédure ADD_EMP_DETAILS stockées) et ressemble à ceci :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling/">  
      <PolledData>  
        <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
          \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
            \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                    \<xs:complexType>  
                      \<xs:sequence>  
                        \<xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                        \<xs:element minOccurs="0" name="Name" type="xs:string" />   
                        \<xs:element minOccurs="0" name="DOJ" type="xs:dateTime" />   
                        \<xs:element minOccurs="0" name="Designation" type="xs:string" />   
                        \<xs:element minOccurs="0" name="Job_Description" type="xs:string" />   
                        \<xs:element minOccurs="0" name="Photo" type="xs:base64Binary" />   
                        \<xs:element minOccurs="0" name="Rating" type="xs:string" />   
                        \<xs:element minOccurs="0" name="Salary" type="xs:decimal" />   
                        \<xs:element minOccurs="0" name="Last_Modified" type="xs:base64Binary" />   
                      \</xs:sequence>  
                    \</xs:complexType>  
                  \</xs:element>  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
          \</xs:schema>  
          \<diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
            <NewDataSet xmlns="">  
              <NewTable>  
                <Employee_ID>10001</Employee_ID>   
                <Name>John</Name>   
                <Designation>Tester</Designation>   
                <Salary>100000.00</Salary>   
                <Last_Modified>AAAAAAAAF34=</Last_Modified>   
              </NewTable>  
              ........  
              ........  
              <NewTable>  
                <Employee_ID>10005</Employee_ID>   
                <Name>Wilson</Name>   
                <Designation>Tester3</Designation>   
                <Salary>100000.00</Salary>   
                <Last_Modified>AAAAAAAAF4E=</Last_Modified>   
              </NewTable>  
            </NewDataSet>  
          \</diffgr:diffgram>  
        </DataSet>  
        <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
          \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
            \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                    \<xs:complexType>  
                      \<xs:sequence>  
                        \<xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                      \</xs:sequence>  
                    \</xs:complexType>  
                  \</xs:element>  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
          \</xs:schema>  
          \<diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
            <NewDataSet xmlns="">  
              <NewTable>  
                <Employee_ID>10006</Employee_ID>  
              </NewTable>  
            </NewDataSet>  
          \</diffgr:diffgram>  
        </DataSet>  
      </PolledData>  
    </Polling>  
    ```  
  
     La réponse précédente contient deux jeux de données. Le premier jeu de données contient la réponse de l’instruction SELECT. L’instruction SELECT sélectionne tous les enregistrements dans la table Employee. Le deuxième jeu de données est pour la procédure stockée de ADD_EMP_DETAILS. Cette procédure stockée ajoute un enregistrement à la table Employee et retourne l’ID d’employé pour le nouvel enregistrement.  
  
    > [!NOTE]
    >  La procédure stockée de MOVE_EMP_DATA ne retourne pas d’un jeu de résultats. Par conséquent, il n’existe aucun jeu de données correspondant dans le message de réponse.  
  
-   Lorsque l’adaptateur s’exécute le **PollDataAvailableStatement** , il trouve un enregistrement a été inséré par le ADD_EMP_DETAILS de procédure stockée. L’adaptateur exécute ensuite toutes les trois instructions qui sont spécifiées pour le **PollingStatement** propriété de liaison. Cette fois-ci, la réponse à partir de SQL Server contient seulement un enregistrement pour l’instruction SELECT et un enregistrement pour le ADD_EMP_DETAILS de procédure stockée. Toutes les interrogations suivantes retournent des réponses similaire.  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] continue à interroger jusqu'à ce que vous désactiviez explicitement le port de réception à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)