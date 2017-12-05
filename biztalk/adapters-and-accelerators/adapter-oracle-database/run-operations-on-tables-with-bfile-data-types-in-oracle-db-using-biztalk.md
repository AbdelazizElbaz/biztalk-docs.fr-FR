---
title: "Exécuter des opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations on tables with BFILE data types, performing by using BizTalk Server
- BFILE data types
ms.assetid: 2e4af5a9-acde-419b-a99c-3eaa0c72daa8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a716056bdeb16900c23bdf748028e9d60e4316ab
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-operations-on-tables-with-bfile-data-types-in-oracle-database-using-biztalk-server"></a>Exécuter des opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle à l’aide de BizTalk Server
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge le type de données BFILE dans les tables et procédures stockées. Cette section fournit des informations sur la façon d’effectuer des opérations sur les tables qui possèdent une colonne BFILE du type de données. Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge BFILE, consultez [opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-with-bfile-data-types-in-oracle-database.md).  
  
## <a name="setting-up-your-oracle-database-server-for-operations-on-bfile"></a>Configuration de votre serveur de base de données Oracle pour les opérations sur BFILE  
 Cette section montre comment appeler une procédure qui insère un enregistrement dans le SCOTT. Table CUSTOMERDOC. Cette table contient une colonne de type de données BFILE et est créée en exécutant les scripts SQL fournis avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples. Pour en savoir plus sur les exemples et les scripts SQL, consultez [exemples pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/samples-for-the-oracle-database-adapter.md).  
  
 Après avoir exécuté le script pour créer la table CUSTOMERDOC, vous devez effectuer certaines actions sur l’ordinateur qui exécute la base de données Oracle pour permettre les opérations sur les types de données BFILE. Les tâches que vous devez effectuer sur la base de données Oracle sont :  
  
1.  Créez un répertoire C:\MYDIR sur l’ordinateur exécutant la base de données Oracle.  
  
2.  Créer un répertoire logique dans la base de données Oracle. Cela nécessite généralement un utilisateur avec des privilèges SYSDBA. Exemple :  
  
    ```  
    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\MYDIR';  
    ```  
  
3.  Ajouter des privilèges à l’utilisateur d’accéder au répertoire logique dans Oracle. Exemple :  
  
    ```  
    GRANT READ, WRITE ON DIRECTORY MYDIR to SCOTT;  
    ```  
  
4.  Copiez les fichiers accessibles dans le répertoire physique sur l’ordinateur exécutant la base de données Oracle, associée au répertoire logique dans Oracle. Vous avez créé ce répertoire à l’étape 1.  
  
     En fonction de l’exemple ci-dessus, copiez un fichier, customer_profile.txt dans le répertoire C:\MYDIR. Ce fichier est maintenant disponible pour les opérations de BFILE. Pour plus d’informations sur l’exécution d’opérations, consultez [effectuant des opérations sur les Tables avec des données de Types d’objet volumineuses par à l’aide de BizTalk Server dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-object-data-types-in-oracle-database.md).  
  
    > [!IMPORTANT]
    >  L’opération ReadLOB est pris en charge sur les tables avec le type de données BFILE. L’opération UpdateLOB n’est pas pris en charge. Toutefois, les utilisateurs peuvent également utiliser l’opération de mise à jour.  
  
## <a name="how-to-perform-operations-using-bfile-data-types"></a>Comment effectuer des opérations à l’aide des Types de données BFILE  
 Une opération sur une base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour appeler une procédure qui insère un enregistrement dans le SCOTT. Table CUSTOMERDOC, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour la procédure stockée de CREATE_CUSTOMERDOC.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour appeler l’opération sur la table de base de données Oracle ou la vue.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, Operate_BFILE, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/samples-for-the-oracle-database-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour montrer comment effectuer des opérations sur une table avec des colonnes BFILE, nous appellerons la procédure CREATE_CUSTOMERDOC. Cette procédure est créée sous le schéma SCOTT\Package\ACCOUNT_PKG en exécutant les scripts SQL fournis avec les exemples. Cette procédure prend le type d’enregistrement BFILE et ajoute un enregistrement dans la table CUSTOMERDOC. Pour plus d’informations sur les scripts SQL, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
 Consultez [de récupérer les métadonnées pour des opérations Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *BFILE_Operations.OracleDBBindingSchema.CREATE_CUSTOMERDOC*, où *BFILE_Operations* est le nom de votre projet BizTalk. *OracleDBBindingSchema* est le schéma généré pour la procédure CREATE_CUSTOMERDOC.|  
  
5.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *BFILE_Operations.OracleDBBindingSchema.CREATE_CUSTOMERDOCResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour exécuter une procédure. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme ce message et le transmet à la base de données Oracle via ODP. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Contiendrait une orchestration classique pour effectuer des opérations sur les colonnes BFILE dans une table de base de données Oracle :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestration permettant d’effectuer des opérations avec BFILE](../../adapters-and-accelerators/adapter-oracle-database/media/5902cf48-0555-4d9a-b902-5208949b6c87.gif "5902cf48-0555-4d9a-b902-5208949b6c87")  
  
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
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.Create_BFILE. Demande*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.Create_BFILE. Demande*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.Create_BFILE. Réponse*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.Create_BFILE. Demande*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleDB physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création des ports WCF-Custom ou WCF-OracleDB, consultez [configurer manuellement la liaison du port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour l’appel de la procédure qui crée un enregistrement dans la table CUSTOMERDOC. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-OracleDB à envoyer des messages à la base de données Oracle est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour la procédure que vous avez généré précédemment. Consultez [des schémas de Message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md) pour plus d’informations sur le schéma de message de demande pour l’appel de procédure à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Par exemple, le message de demande pour appeler la procédure CREATE_CUSTOMERDOC est la suivante :  
  
```  
<CREATE_CUSTOMERDOC xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <CNAME>John Smith</CNAME>  
  <CDOC>MYDIR/John_Smith_profile.txt</CDOC>  
</CREATE_CUSTOMERDOC>  
```  
  
> [!NOTE]
>  Le fichier texte, John_Smith_profile.txt doit être présent dans l’emplacement du répertoire physique associé au répertoire logique dans Oracle. Pour cet exemple, le fichier texte doit être présent dans C:\MYDIR  
  
 L’orchestration consomme le message et l’envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données Oracle pour le message de demande ci-dessus est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CREATE_CUSTOMERDOCResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG"></CREATE_CUSTOMERDOCResponse>  
```  
  
> [!NOTE]
>  Vous pouvez créer une orchestration similaire pour lire les données des tables qui possèdent des champs de type BFILE. Le script SQL fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] crée un ACCOUNT_PKG qui contient une procédure GET_CUSTOMERDOC. Vous pouvez utiliser cette procédure pour récupérer les données BFILE de SCOTT. Table CUSTOMERDOC.  
>   
>  Un exemple, Operate_BFILE, est également inclus dans les exemples de [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Cet exemple montre comment insérer des enregistrements dans le SCOTT. Table CUSTOMERDOC à l’aide de la CREATE_CUSTOMERDOC une procédure stockée (comme décrit dans cette rubrique.) L’exemple montre également comment lire les données BFILE SCOTT. Table CUSTOMERDOC à l’aide de GET_CUSTOMERDOC de procédure stockée.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’exécution d’une opération DML à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)