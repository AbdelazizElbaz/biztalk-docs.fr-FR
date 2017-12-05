---
title: "Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLEXECUTE operation, performing by using BizTalk Server
- SQLEXECUTE operation
ms.assetid: 7fdd1ead-0bf0-46cf-86fc-db513f76f6b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02a5da0a5c6ff3560d265759d3c5320e55d7d621
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-sqlexecute-operation-in-oracle-database-using-biztalk-server"></a>Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide de BizTalk Server
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux clients d’exécuter l’instruction SQL paramétrée sur une base de données Oracle. Pour prendre en charge ces opérations, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence une opération SQLEXECUTE. Opération SQLEXECUTE prend en charge un bloc de paramètre d’entrée composé des jeux de paramètres qui vous permettent d’exécuter la même instruction SQL une fois pour chaque jeu. L’opération SQLEXECUTE renvoie les résultats de l’instruction SQL dans un jeu d’enregistrements générique. Pour plus d’informations sur l’opération, consultez [opération SQLEXECUTE dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md). Pour plus d’informations sur la structure du message SOAP pour l’opération SQLEXECUTE, consultez [des schémas de Message pour l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).  
  
## <a name="how-to-perform-a-sqlexecute-operation-on-an-oracle-database"></a>Comment effectuer une opération SQLEXECUTE sur une base de données Oracle ?  
 Une opération sur une base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour effectuer une opération SQLEXECUTE, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour l’opération SQLEXECUTE. L’opération SQLEXECUTE apparaît sous le nœud racine (/) dans le **sélectionner une catégorie** volet dans le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour appeler l’opération sur la table de base de données Oracle ou la vue.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, SqlExec, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment exécuter une requête SQL paramétrable, nous allons générer de schéma pour l’opération SQLEXECUTE disponible au niveau du nœud racine (/) dans le **sélectionner une catégorie** volet dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Consultez [de récupérer les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la fenêtre Vue Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour envoyer une demande à la base de données Oracle et l’autre pour recevoir une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SqlExec.OracleDBBindingSchema.SQLEXECUTE*, où *SqlExec* est le nom de votre projet BizTalk. *OracleDBBindingSchema* est le schéma généré pour l’opération SQLEXECUTE.|  
  
5.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SqlExec.OracleDBBindingSchema.SQLEXECUTEResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour SQL paramétrable en cours d’exécution de requête à l’aide de l’opération SQLEXECUTE. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme ce message et le transmet à la base de données Oracle via ODP. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Contiendrait une orchestration classique pour effectuer l’opération SQLEXECUTE sur la base de données Oracle :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration pour l’opération SQLEXECUTE ressemble à ceci :  
  
 ![Orchestration permettant d’appeler l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/media/bdb47660-6013-46f7-aa4b-fe5eb83f3a1e.gif "bdb47660-6013-46f7-aa4b-fe5eb83f3a1e")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br />-Définissez **Type** à *SaveResponseType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.SQLEXECUTE.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.SQLEXECUTE.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.SQLEXECUTE.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.SQLEXECUTE.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleDB physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création des ports WCF-Custom ou WCF-OracleDB, consultez [configurer manuellement une liaison de port physique pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour effectuer l’opération SQLEXECUTE. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-OracleDB à envoyer des messages à la base de données Oracle est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour l’opération SQLEXECUTE que vous avez généré précédemment. L’orchestration consomme le message et l’envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Consultez [des schémas de Message pour l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md) pour plus d’informations sur le schéma de message de demande pour l’appel d’une opération SQLEXECUTE.  
  
 Étant donné que l’opération SQLEXECUTE n’est pas exposée en surface sous n’importe quel objet de base de données Oracle, vous pouvez utiliser le même schéma pour effectuer une requête SQL paramétrable sur une vue ou d’exécuter une procédure qui fonctionne sur une autre table.  
  
 Par exemple, le message de demande suivant exécute une instruction SELECT paramétrable sur la table de compte à l’aide de l’opération SQLEXECUTE. Le tableau de compte est créé sous le schéma SCOTT en exécutant les scripts SQL fournis avec les exemples. Pour en savoir plus sur les exemples, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
```  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
  <SQLSTATEMENT>select * from ACCOUNT where ACCTID=:num</SQLSTATEMENT>  
  <PARAMETERSCHEMA>num number</PARAMETERSCHEMA>  
  <PARAMETERSET>  
    <PARAMETERDATA xmlns="http://Microsoft.LobServices.OracleDB/2007/03">  
      <PARAMETER>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">100000</string>  
      </PARAMETER>  
    </PARAMETERDATA>  
  </PARAMETERSET>  
</SQLEXECUTE>  
```  
  
 La réponse à partir de la base de données Oracle pour le message de demande ci-dessus est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<SQLEXECUTEResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
  <SQLEXECUTEResult>  
    <GenRecordRow xmlns="http://Microsoft.LobServices.OracleDB/2007/03">  
      <GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>ACCTID</ColumnName>   
          <ColumnValue>100000</ColumnValue>   
          <ColumnType>System.Decimal</ColumnType>   
        </GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>NAME</ColumnName>   
          <ColumnValue>Kim Ralls</ColumnValue>   
          <ColumnType>System.String</ColumnType>   
        </GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>BALANCE</ColumnName>   
          <ColumnValue>10000</ColumnValue>   
          <ColumnType>System.Decimal</ColumnType>   
        </GenRecordColumn>  
      </GenRecordColumn>  
    </GenRecordRow>  
  </SQLEXECUTEResult>  
</SQLEXECUTEResponse>  
```  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’exécution d’une opération DML à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur réutiliser la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)