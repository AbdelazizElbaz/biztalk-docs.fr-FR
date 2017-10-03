---
title: "Recevoir des fortement typée d’interrogation de modification de données de messages à partir de SQL Server à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6e6ba7e-9e13-4e28-b57d-d24569277bbc
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 451987a9b6461064047041ee6afa348d32929b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-strongly-typed-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a>Recevoir des fortement typée d’interrogation de modification de données de messages à partir de SQL Server à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de l’interrogation fortement typée à partir de SQL Server. Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.  
  
 Vous devez utiliser interrogation fortement typée dans un scénario dans lequel vous souhaitez mapper les éléments dans le message d’interrogation à n’importe quel autre schéma. Le schéma que vous souhaitez mapper aux peut être pour une autre opération sur SQL Server. Par exemple, vous pouvez mapper certains éléments dans le message d’interrogation pour le schéma pour une opération d’insertion sur une autre table. Par conséquent, les valeurs dans le message d’interrogation de servent de paramètres pour l’opération d’insertion. Dans un scénario plus simple, vous pouvez mapper le schéma de message d’interrogation fortement typée à un fichier de schéma qui stocke des informations.  
  
> [!IMPORTANT]
>  Si vous souhaitez disposer d’interrogation plus d’une opération dans une même application BizTalk, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique. Avec un URI de connexion unique, vous pouvez créer plusieurs ports de réception qui interrogent la même base de données, ou même de la même table dans une base de données. Pour plus d’informations, consultez [de réception d’interrogation Messages entre plusieurs Ports réception à partir de SQL à l’aide de Biztalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge l’interrogation fortement typée, consultez [prise en charge pour l’interrogation](https://msdn.microsoft.com/library/dd788416.aspx). Pour plus d’informations sur le schéma de message pour une interrogation fortement typée, consultez [des schémas de Message pour l’interrogation et les opérations de TypedPolling](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md).  
  
## <a name="how-this-topic-demonstrates-strongly-typed-polling"></a>Comment cette rubrique illustre interrogation fortement typée  
 Cette rubrique montre comment utiliser l’interrogation fortement typée pour mapper le message d’interrogation à un autre schéma. Cette rubrique montre comment créer un projet BizTalk et générer le schéma de **TypedPolling** opération. Avant de générer le schéma pour **TypedPolling** opération, vous devez procédez comme suit :  
  
-   Vous devez spécifier un **InboundID** dans le cadre de l’URI de connexion.  
  
-   Vous devez spécifier une instruction d’interrogation pour le **PollingStatement** propriété de liaison.  
  
 Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :  
  
-   Sélectionnez toutes les lignes de la table Employee.  
  
-   Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.  
  
-   Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee. Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.  
  
 Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison :  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 Étant donné que vous générez le schéma pour le **TypedPolling** opération, le schéma est fortement typée et contient tous les éléments qui seront inclus dans le message d’interrogation.  
  
 Dans le cadre d’un projet BizTalk, vous ajoutez un autre fichier de schéma, par exemple EmployeeDetails.xsd. Le schéma pour EmployeeDetails.xsd ressemble à ceci :  
  
```  
\<?xml version="1.0" encoding="utf-16" ?>   
\<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://Typed_Polling.EmployeeDetails" elementFormDefault="qualified" targetNamespace="http://Typed_Polling.EmployeeDetails" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  \<xs:element name="EmployeeDetails">  
    \<xs:complexType>  
      \<xs:sequence>  
        \<xs:element name="Employee_Info" type="xs:string" />   
        \<xs:element name="Employee_Profile" type="xs:string" />   
        \<xs:element name="Employee_Performance" type="xs:string" />   
      \</xs:sequence>  
    \</xs:complexType>  
  \</xs:element>  
\</xs:schema>  
```  
  
 Vous montre également comment ajouter un Mappeur BizTalk pour le projet pour mapper les éléments de la table Employee (reçus en tant que message de sondage) pour les éléments dans le schéma EmployeeDetails.xsd. Dans le cadre de la carte, vous combinez un ou plusieurs éléments à partir du message d’interrogation et le mapper à un élément unique dans le schéma EmployeeDetails. Vous pouvez le faire à l’aide de la **concaténation de chaînes** fonctoid.  
  
 Enfin, dans le cadre du projet BizTalk, un fichier conforme au schéma de EmployeeDetails.xsd est supprimé pour un port d’envoi FILE.  
  
## <a name="configure-typed-polling-with-the-sql-adapter-binding-properties"></a>Configurer l’interrogation typée avec l’adaptateur SQL propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison. Autre que le **PollingStatement** propriété de liaison, toutes les autres propriétés de liaison répertoriées dans cette section sont requises lors de la configuration du port de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez spécifier le **PollingStatement** propriété de liaison avant de générer le schéma pour le **TypedPolling** opération.  
  
> [!NOTE]
>  Pour l’interrogation typée, vous devez spécifier le **PollingStatement** liaison de propriété lors de la génération du schéma. Vous pouvez choisir de spécifier les autres propriétés de liaison ainsi lors de la génération du schéma, même s’ils ne sont pas obligatoires. Si vous ne spécifiez pas les propriétés de liaison, la liaison du port de fichiers qui le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère comme partie de la génération de métadonnées contient également les valeurs spécifiées pour les propriétés de liaison. Vous pouvez importer ultérieurement ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] port de réception de la console Administration pour créer le WCF-custom ou WCF-SQL avec la liaison de propriétés déjà définies. Pour plus d’informations sur la création d’un port à l’aide du fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**. Pour recevoir des messages d’interrogation fortement typée, affectez la valeur **TypedPolling**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes. Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.|  
|**PollingIntervalInSeconds**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.|  
|**PollingStatement**|Spécifie l’instruction SQL pour interroger la table de base de données SQL Server. Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation. La valeur par défaut est null. Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison. Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule.<br /><br /> **Important :** pour **TypedPolling**, vous devez spécifier cette propriété de liaison avant de générer des métadonnées.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié. Valeur par défaut est **false**.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, poursuivre la lecture.  
  
## <a name="how-to-receive-strongly-typed-data-change-messages-from-the-sql-server-database"></a>La réception des Messages de modification de données fortement typé à partir de la base de données SQL Server  
 Une opération sur la base de données SQL Server à l’aide [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour configurer l’adaptateur pour recevoir des messages de modification de données fortement typées, ces tâches sont :  
  
1.  Créez un projet BizTalk, puis générer le schéma pour le **TypedPolling** opération. Vous devez spécifier le **InboundID** propriété de connexion et le **PollingStatement** lors de la génération de schéma de propriété de liaison. Par exemple, un URI avec l’ID d’entrée spécifié de connexion ressemble à ceci :  
  
    ```  
    mssql://mysqlserver//mysqldatabase?InboundID=mydatabaseId  
    ```  
  
2.  Créez un message dans le projet BizTalk pour recevoir des messages à partir de la base de données SQL Server.  
  
3.  Créez une orchestration pour recevoir des messages à partir de la base de données SQL Server et les enregistrer dans un dossier.  
  
4.  Ajouter un schéma, par exemple, EmployeeDetails.xsd, dans le projet BizTalk.  
  
5.  Ajoutez un Mappeur BizTalk pour mapper le schéma pour le message d’interrogation au schéma de EmployeeDetails.xsd.  
  
6.  Générez et déployez le projet BizTalk.  
  
7.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!IMPORTANT]
    >  Pour les scénarios de trafic entrant d’interrogation, vous devez toujours configurer un WCF-Custom unidirectionnel ou port de réception WCF-SQL. Ports de réception bidirectionnel WCF-Custom ou WCF-SQL ne sont pas pris en charge pour les opérations entrantes.  
  
8.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple TypedPolling, en fonction de cette rubrique est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
## <a name="generate-schema"></a>Générer un schéma  
 Vous devez générer le schéma pour le **TypedPolling** opération. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer le schéma. Effectuer les tâches suivantes lors de la génération du schéma.  
  
1.  Spécifiez le **InboundID** propriété de connexion lors de la spécification de l’URI de connexion. Pour cette rubrique, vous pouvez spécifier le **InboundID** en tant que **employé**. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
2.  Spécifiez une valeur pour le **PollingStatement** propriété de liaison. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
     Pour obtenir des instructions sur la façon de spécifier les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
3.  Sélectionnez le type de contrat **Service (opération entrante)**.  
  
4.  Génération du schéma pour le **TypedPolling** opération.  
  
## <a name="define-messages-and-message-types"></a>Définir les Messages et le Message Types  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Pour cette rubrique, vous devez créer un message à recevoir des messages à partir de la base de données SQL Server.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="create-messages-and-link-to-schema"></a>Créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis **ajouter**.  
  
2.  Ouvrez la fenêtre Vue orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **PollingMessage**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Typed_Polling.TypedPolling_Employee.TypedPolling*, où *Typed_Polling* est le nom de votre BizTalk projet. *TypedPolling_Employee* est le schéma généré pour le **TypedPolling** opération.|  
  
## <a name="set-up-the-orchestration"></a>Configurer l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir les messages de modification de données reposant sur l’interrogation de la base de données SQL Server. Dans cette orchestration, l’adaptateur reçoit le message de l’interrogation de l’instruction d’interrogation spécifié. Le Mappeur BizTalk mappe ensuite le schéma de message d’interrogation au schéma EmployeeDetails.xsd. Le message mappé est ensuite enregistré dans un emplacement de fichier. Contiendrait une orchestration par défaut pour la réception du message d’interrogation fortement typée à partir d’une base de données SQL Server :  
  
-   Recevoir et envoyer des formes pour recevoir des messages à partir de SQL Server et les envoyer vers un port FILE, respectivement.  
  
-   Unidirectionnel port de réception pour recevoir des messages à partir de SQL Server.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
-   Un port d’envoi unidirectionnel pour envoyer des réponses d’interrogation à partir d’une base de données SQL Server dans un dossier.  
  
-   Mappeur BizTalk pour mapper le schéma du message d’interrogation à n’importe quel autre schéma.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration pour fortement &#45; interrogation typée](../../adapters-and-accelerators/adapter-sql/media/1db03859-b7f8-470c-9158-2be4da0b45ae.gif "1db03859-b7f8-470c-9158-2be4da0b45ae")  
  
### <a name="add-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br /><br /> -Définissez **activer** à *True*|  
|SaveMessage|Send|-Définissez **nom** à *SaveMessage*|  
  
### <a name="add-ports"></a>Ajouter des Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|SQLReceivePort|-Définissez **identificateur** à *SQLReceivePort*<br /><br /> -Définissez **Type** à *SQLReceivePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|SaveMessagePort|-Définissez **identificateur** à *SaveMessagePort*<br /><br /> -Définissez **Type** à *SaveMessagePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="enter-messages-for-action-shapes-and-connect-to-ports"></a>Entrez les Messages de formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|Définissez **Message** à *PollingMessage*<br /><br /> Définissez **opération** à *SQLReceivePort.TypedPolling.Request*|  
|SaveMessage|Définissez **Message** à *PollingMessage*<br /><br /> Définissez **opération** à *SaveMessagePort.TypedPolling.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés.  
  
### <a name="add-a-biztalk-mapper"></a>Ajouter un Mappeur BizTalk  
 Vous devez ajouter un Mappeur BizTalk à l’orchestration pour mapper le schéma du message d’interrogation au schéma EmployeeDetails.xsd. Dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous utiliserez ce mappeur pour mapper le schéma pour le message d’interrogation au schéma EmployeeDetails.xsd.  
  

1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
     Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que `MapSchema.btm`. Cliquez sur **Ajouter**.  
  
2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message d’interrogation. Pour cette rubrique, sélectionnez Typed_Polling.TypedPolling_Employee. Cliquez sur **OK**.  
  
4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez TypedPolling, cliquez sur **OK**.  
  
5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma pour EmployeeDetails. Pour cette rubrique, sélectionnez Typed_Polling.EmployeeDetails. Cliquez sur **OK**.  
  
7.  Dans le schéma de la source du message de sondage, développez le nœud TypedPollingResultSet0 et les nœuds suivants pour afficher les éléments qui sont retournées dans le message d’interrogation. Dans le schéma de destination, développez le nœud de EmployeeDetails pour voir les différents éléments dans le schéma. Pour cette rubrique, vous devez mapper les schémas de sorte que :  
  
    -   **Employee_id** et **nom** dans la source de schéma doit mapper à **Employee_Info** dans le schéma de destination.  
  
    -   **Désignation** et **Job_Description** dans la source de schéma doit mapper à **Employee_Profile** dans le schéma de destination.  
  
    -   **Évaluation** et **salaire** dans la source de schéma doit mapper à **Employee_Performance** dans le schéma de destination.  
  
     Pour combiner plusieurs nœuds dans le schéma source et les mapper à un seul nœud dans le schéma de destination, vous devez utiliser le **fonctoid concaténation de chaînes**. Détails [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
8.  Pour utiliser le fonctoid concaténation de chaînes :  
  
    1.  À partir de la **boîte à outils**, faites glisser le **concaténation de chaînes** fonctoid et déposez-la sur la grille du mappeur.  
  
    2.  Connecter le **Employee_ID** et **nom** éléments dans le schéma source vers le fonctoid.  
  
    3.  Connectez le fonctoid à la **Employee_Info** élément dans le schéma de destination.  
  
    4.  Répétez ces étapes pour tous les éléments que vous voulez mapper. Un mappage terminé ressemble à ceci :  
  
         ![Mapper le schéma d’interrogation fortement typée](../../adapters-and-accelerators/adapter-sql/media/0a4a2608-3b84-4bac-9a16-512cf42c7525.gif "0a4a2608-3b84-4bac-9a16-512cf42c7525")  
  
    5.  Enregistrez le mappage.  
  
 L’orchestration est terminée après avoir créé le mappeur. Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configure-the-biztalk-application"></a>Configurer l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un WCF-Custom physique ou le port de réception unidirectionnel WCF-SQL. Ce port interroge la base de données SQL Server avec l’instruction d’interrogation que vous spécifiez pour le port. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        > [!IMPORTANT]
        >  Assurez-vous que vous spécifiez la **InboundID** dans le cadre de l’URI de connexion. L’ID de trafic entrant doit être celui que vous avez spécifié lors de la génération du schéma.  
  
        > [!IMPORTANT]
        >  Vous n’avez pas besoin d’effectuer cette étape si vous avez spécifié les propriétés de liaison au moment du design. Dans ce cas, vous pouvez créer un WCF-custom ou WCF-SQL port de réception, avec le jeu de propriétés de liaison requis, en important le fichier de liaison créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Assurez-vous que vous affectez la valeur **TypedPolling**.|  
        |**PolledDataAvailableStatement**|Assurez-vous que vous spécifiez la même instruction SQL que vous avez spécifié lors de la génération du schéma, qui est :<br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |**PollingStatement**|Vérifiez que vous fournissez la même instruction d’interrogation que vous avez spécifié lors de la génération du schéma, qui est :<br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez effectuer afin d’en ajoutant le service de port de réception comportement lors de la configuration WCF-Custom ou WCF-SQL. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer Transaction Isolation Level et délai de Transaction SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
    -   Définir un port d’envoi de fichier dans lequel l’adaptateur supprime le message. Ce port d’envoi utilise également le mappage que vous avez créé dans l’orchestration pour mapper le message de l’interrogation à un message conforme au schéma EmployeeDetails.xsd. Procédez comme suit pour configurer le port d’envoi de fichier pour utiliser le mappage.  
  
        1.  Créer un port d’envoi FILE.  
  
        2.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages sortants**. Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **MapSchema**. Cliquez sur **OK**.  
  
             ![Configurer le mappage sortant sur le port d’envoi FILE](../../adapters-and-accelerators/adapter-sql/media/831c9aee-fd97-466f-9270-3b04dbccd9fe.gif "831c9aee-fd97-466f-9270-3b04dbccd9fe")  
  
## <a name="start-the-application"></a>Démarrer l’Application  
 Vous devez démarrer l’application BizTalk pour recevoir des messages à partir de la base de données SQL Server. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-SQL unidirectionnel port de réception, qui interroge la base de données SQL Server à l’aide d’instructions spécifiées pour le **PollingStatement** propriété, de liaison est en cours d’exécution.  
  
-   Le port d’envoi FILE, qui mappe le message d’interrogation au schéma EmployeeDetails, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="execute-the-operation"></a>Exécuter l’opération  
 Après avoir exécuté l’application, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur exécute le **PolledDataAvailableStatement** sur l’employé de table et détermine que la table comporte des enregistrements pour l’interrogation.  
  
-   L’adaptateur exécute l’instruction d’interrogation. Étant donné que l’instruction d’interrogation se compose d’une instruction SELECT et les procédures stockées, l’adaptateur s’exécute toutes les instructions une après l’autre.  
  
    -   Tout d’abord, l’adaptateur exécute l’instruction SELECT qui retourne tous les enregistrements dans la table Employee.  
  
    -   L’adaptateur exécute ensuite la procédure MOVE_EMP_DATA stockées qui déplace toutes les données à partir de la table Employee à la table HistoriqueEmployé. Cette procédure stockée ne retourne pas de n’importe quelle valeur.  
  
    -   L’adaptateur exécute ensuite la procédure stockée de ADD_EMP_DETAILS qui ajoute un enregistrement à la table Employee. Cette procédure stockée renvoie l’ID d’employé de l’enregistrement inséré.  
  
     Après exécution de l’instruction d’interrogation et le message est reçu, le message d’interrogation obtient envoi au port d’envoi de fichier. Ici, le mappage sortant (**MapSchema**) configuré sur les mappages de port d’envoi, le message d’interrogation au schéma EmployeeDetails et dépose le message vers un emplacement de fichier. Le message ressemble à ceci :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <EmployeeDetails xmlns="http://Typed_Polling.EmployeeDetails">  
      <Employee_Info>10751John</Employee_Info>   
      <Employee_Profile>TesterManagesTesting</Employee_Profile>   
      <Employee_Performance>100000</EmployeePerformance>  
    </EmployeeDetails>  
    ```  
  
     Dans la réponse précédente, vous pouvez remarquer que l’élément Employee_Info contient une combinaison de l’ID d’employé (10751) et le nom de l’employé (John). Les autres éléments contiennent également des combinaisons mappé dans le Mappeur que vous avez créé dans le cadre de l’orchestration.  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] continue à interroger jusqu'à ce que vous désactiviez explicitement le port de réception à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)