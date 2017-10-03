---
title: "Effectuer des opérations composites sur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 886d066d-2ec8-41b4-bdd5-d8afcb5e3e58
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2dd906105f4bd028867e4588d7c075b56253ab9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complete-composite-operations-on-oracle-e-business-suite"></a>Effectuer des opérations composites sur Oracle E-Business Suite
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients d’adaptateur effectuer des opérations composites sur la base de données Oracle. Une opération composite peut inclure :  
  
-   Insérer, mettre à jour, supprimer et sélectionnez les opérations sur les tables de base de données. Opération SELECT sur les vues de base de données.  
  
-   Insérer, mettre à jour, supprimer et sélectionnez les opérations sur les tables d’interface. Sélectionner une opération sur les vues de l’interface.  
  
-   Procédures stockées et des fonctions, à l’intérieur ou à l’extérieur d’un package.  
  
 Une seule opération composite peut avoir un nombre quelconque de ces opérations, dans n’importe quel ordre. Par exemple, vous pouvez avoir deux insertions suivies d’une suppression et enfin une exécution de la procédure stockée. En outre, vous pouvez avoir différentes opérations ciblant des tables de base de données différente ou des vues. Pour plus d’informations sur la façon dont l’adaptateur prend en charge des opérations composites, consultez [prise en charge des opérations composites](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md). Pour plus d’informations sur la structure du message SOAP pour des opérations composites, consultez [des schémas de Message pour l’opération Composite](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md).  
  
## <a name="how-to-perform-composite-operations-on-oracle-database"></a>Comment effectuer des opérations composites sur la base de données Oracle ?  
 Une opération sur l’utilisation de base de données Oracle [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour effectuer des opérations composites sur la base de données Oracle, ces tâches sont :  
  
1.  Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et générer le schéma pour toutes les opérations que vous souhaitez appeler.  
  
2.  Créer manuellement un fichier de schéma qui inclut des références à tous les schémas que vous avez créé à l’étape précédente.  
  
3.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle. Ces messages doivent respecter le schéma de demande et de réponse que vous avez créé à l’étape précédente.  
  
4.  Créez une orchestration pour appeler l’opération composite sur la base de données Oracle.  
  
5.  Générez et déployez le projet BizTalk.  
  
6.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
7.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour montrer comment effectuer des opérations composites, nous allons effectuer les tâches suivantes dans le même ordre :  
  
-   Insérer l’enregistrement dans la table ACCOUNTACTIVITY.  
  
-   Récupérer tous les enregistrements dans la table ACCOUNTACTIVITY en appelant la procédure GET_ALL_ACTIVITY dans le package ACCOUNT_PKG.  
  
-   Supprimer l’enregistrement de la table ACCOUNTACTIVITY.  
  
 Exécutez les scripts fournis avec les exemples pour créer la table ACCOUNTACTIVITY. Pour plus d’informations sur les exemples, consultez [exemples](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).  
  
 Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour plus d’informations sur la façon de générer des schémas.  
  
## <a name="creating-a-composite-schema-definition"></a>Création d’une définition de schéma Composite  
 Vous devez maintenant créer un schéma composite dans la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet BizTalk qui fait référence à des schémas créés pour les opérations individuelles. Procédez comme suit pour créer une définition de schéma composite.  
  
#### <a name="to-add-a-composite-schema-definition"></a>Pour ajouter une définition de schéma composite  
  
1.  Ajouter un fichier de schéma au projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Cliquez sur le nom de la solution, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **catégories** , cliquez sur **les fichiers de schéma**. À partir de la **modèles** , cliquez sur **schéma**. Spécifiez un nom pour le fichier de schéma et cliquez sur **OK**.  
  
     Pour cet exemple, spécifiez le nom de fichier de schéma en tant que `CompositeSchema.xsd`.  
  
2.  Ajouter des références au schéma généré pour les différentes opérations que vous souhaitez effectuer. Dans cet exemple, les différents schémas générés pour les opérations sont :  
  
    -   OracleEBSBinding.xsd, pour les opérations Insert et Delete sur la table ACCOUNTACTIVITY.  
  
    -   OracleEBSBinding2.xsd, pour la procédure GET_ALL_ACTIVITY.  
  
     Pour ajouter des références :  
  
    1.  Avec le bouton droit de la racine  **\<schéma >** nœud dans le CompositeSchema.xsd, puis cliquez sur **propriétés**.  
  
    2.  Dans le **propriété** , cliquez sur le bouton de sélection **(...)**  contre le **importations** propriété.  
  
         ![Importer les définitions de schéma](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")  
  
    3.  Dans le **importations** boîte de dialogue, à partir de la **importer le nouveau schéma en tant que** liste, sélectionnez **XSD : importer**, puis cliquez sur **ajouter**.  
  
    4.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nœud de nom de projet BizTalk, développez **schémas**, puis sélectionnez le schéma que vous souhaitez importer. Dans cet exemple, sélectionnez < BizTalk_project_name >. OracleEBSBinding.xsd. Cliquez sur **OK**.  
  
         Répétez cette étape pour importer < BizTalk_project_name >. OracleEBSBinding2.xsd trop.  
  
    5.  Dans le **importations** boîte de dialogue, cliquez sur **OK**.  
  
3.  Ajoutez deux nœuds enfants au nœud de schéma racine. Un nœud enfant correspond au schéma de requête de l’opération composite. L’autre nœud enfant correspond au schéma de réponse. Le nœud qui correspond au schéma de requête peut avoir n’importe quel nom. Le nœud qui correspond au schéma de réponse doit être appelé < request_schema_node > réponse. Pour cet exemple, nous appelons le nœud de schéma de demande en tant que **demande**. Par conséquent, le nœud de schéma de réponse est appelé **requête-réponse**.  
  
    > [!NOTE]
    >  Par défaut, un **racine** nœud est également ajouté à un fichier de schéma. Vous pouvez renommer la **racine** nœud **demande**. Pour renommer un nœud, cliquez sur le nom de nœud et cliquez sur **renommer**.  
  
     Pour ajouter un nœud sous la  **\<schéma >** nœud :  
  
    1.  Avec le bouton droit le  **\<schéma >** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
    2.  Renommez le nouveau nœud **requête-réponse**.  
  
4.  Ajouter des nœuds enfants sous le **demande** nœud qui correspondent au schéma de requête pour chaque opération que vous effectuerez dans le cadre de l’opération composite. Pour cet exemple, vous devez ajouter des nœuds enfants correspondant à ce qui suit :  
  
    -   Insérer et supprimer des opérations sur la table ACCOUNTACTIVITY.  
  
    -   Procédure GET_ALL_ACTIVITY.  
  
    > [!IMPORTANT]
    >  Vous devez ajouter les nœuds dans le même ordre que celui dans lequel vous souhaitez effectuer les opérations. Par exemple, si vous souhaitez insérer un enregistrement, puis exécuter une procédure stockée et supprimez un enregistrement, vous devez d’abord ajouter un nœud pour l’opération d’insertion, suivi par un nœud de la procédure stockée et enfin sur un nœud pour l’opération de suppression.  
  
     Pour ajouter des nœuds enfants à la **demande** nœud :  
  
    1.  Avec le bouton droit le **demande** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
         ![Insérer des nœuds enfants pour un schéma](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")  
  
    2.  Renommer l’enregistrement pour correspondre à un schéma de demande pour une opération que vous effectuez dans le cadre de l’opération composite. Par exemple, renommer le nœud « INSERT ».  
  
    3.  Mappage de la **insérer** nœud pour le schéma de demande pour l’opération d’insertion sur la table ACCOUNTACTIVITY. Pour ce faire, cliquez sur le **insérer** nœud, puis cliquez sur **propriétés**. Dans le **propriétés** zone, à partir de la **Data Structure Type** liste, sélectionnez **Insert (référence)**.  
  
         ![Mapper des nœuds enfants au schéma de demande](../../adapters-and-accelerators/adapter-oracle-database/media/b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e.gif "b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e")  
  
    4.  Répétez ces étapes pour ajouter des nœuds pour les schémas de requête pour la procédure GET_ALL_ACTIVITY stockées et de l’opération de suppression. Spécifiez les noms des nœuds et les mapper vers le schéma correspondant, comme indiqué dans le tableau suivant.  
  
        |Nom de nœud|Mappé au schéma|  
        |---------------|----------------------|  
        |GET_ALL_ACTIVITY|GET_ALL_ACTIVITY (référence)|  
        |DELETE|Delete (référence)|  
  
5.  Ajouter des nœuds enfants sous le **requête-réponse** nœud qui correspondent au schéma de réponse pour chaque opération que vous effectuerez dans le cadre de l’opération composite. Pour cet exemple, vous devez ajouter des nœuds enfants correspondant à ce qui suit :  
  
    -   Insérer et supprimer des opérations sur la table ACCOUNTACTIVITY.  
  
    -   GET_ALL_ACTIVITY de procédure stockée.  
  
    > [!IMPORTANT]
    >  Vous devez ajouter les nœuds enfants dans le même ordre que les nœuds enfants sous le **demande** nœud.  
  
     Pour ajouter des nœuds enfants à la **requête-réponse** nœud :  
  
    1.  Avec le bouton droit le **requête-réponse** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
    2.  Renommer l’enregistrement pour correspondre à un schéma de réponse pour une opération que vous effectuez dans le cadre de l’opération composite. Par exemple, renommer le nœud à « InsertResponse ».  
  
    3.  Mappage de la **InsertResponse** nœud pour le schéma de réponse pour l’opération d’insertion sur la table ACCOUNTACTIVITY. Pour ce faire, cliquez sur le **InsertResponse** nœud, puis cliquez sur **propriétés**. Dans le **propriétés** zone, à partir de la **Data Structure Type** liste, sélectionnez **InsertResponse (référence)**.  
  
    4.  Répétez ces étapes pour ajouter des nœuds pour les schémas de réponse pour la procédure stockée de GET_ALL_ACTIVITY et l’opération de suppression. Spécifiez les noms des nœuds et les mapper vers le schéma correspondant, comme indiqué dans le tableau suivant.  
  
        |Nom de nœud|Mappé au schéma|  
        |---------------|----------------------|  
        |GET_ALL_ACTIVITYResponse|GET_ALL_ACTIVITYResponse (référence)|  
        |DeleteResponse|DeleteResponse (référence)|  
  
6.  Enregistrer le **CompositeSchema.xsd** fichier.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma composite que vous avez créé dans la dernière étape décrit les « types » requis pour les messages dans une orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier au schéma que vous avez créé à l’étape précédente.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Composite_Op.CompositeSchema.Request*, où Composite_Op est le nom de votre projet BizTalk. CompositeSchema est le schéma que vous avez créé manuellement pour les opérations composites.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Composite_Op.CompositeSchema.RequestResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer des opérations composites sur la base de données Oracle. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le message de demande doit être conforme au schéma composite que vous avez créé précédemment. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consomme ce message et le transmet à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses, respectivement. Une orchestration de base pour effectuer des opérations composites ressemble à ceci :  
  
 ![Orchestration permettant d’effectuer des opérations composites](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")  
  
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
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.CompositeOp.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.CompositeOp.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.CompositeOp.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.CompositeOp.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir de la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleEBS physique pour envoyer des messages à la base de données Oracle. Étant donné que les opérations étant comme partie de l’opération composite sont exécutées dans une transaction unique, assurez-vous que le **UseAmbientTransaction** liaison de la propriété est définie sur **True**.  
  
         Vous devez également spécifier l’action dans le port d’envoi. L’action pour une opération composite est « CompositeOperation ». Pour plus d’informations sur la création de ports, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). Pour plus d’informations sur la façon de spécifier des actions pour les ports, consultez [configurer l’Action SOAP pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md).  
  
        > [!IMPORTANT]
        >  Comme partie des opérations composites, si vous exécutez des opérations sur des objets, par exemple les procédures stockées, fonctions, tables d’interface ou vues de l’interface, qui appartiennent à une application Oracle E-Business Suite, vous devez définir le contexte d’application à spécifier les propriétés de liaison requis. Pour plus d’informations sur la définition du contexte d’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
        >   
        >  Vous pouvez définir le contexte de l’application soit en spécifiant les propriétés de liaison, ou en définissant des propriétés de contexte exposées par le message le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour obtenir des instructions sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md). Si vous importez ce fichier de liaison, l’action sur le port d’envoi est définie à une action dynamique impliquant toutes les opérations que vous avez sélectionné dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] lors de la génération du schéma. Pour une opération composite, vous devez remplacer l’action dynamique avec « CompositeOperation ».  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour effectuer des opérations composites sur la base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour envoyer des messages à Oracle de base de données est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour les opérations composites que vous avez créé précédemment. Par exemple, un message de demande qui insère un enregistrement dans la table ACCOUNTACTIVITY, appelle la procédure stockée de GET_ALL_ACTIVITY et supprime un enregistrement de la table ACCOUNTACTIVITY est la suivante :  
  
```  
<Request xmlns="http://Composite_Op.CompositeSchema">  
  <Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/ACCOUNTACTIVITY">  
    <RECORDSET>  
      <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/SCOTT/ACCOUNTACTIVITY">  
        <TID InlineValue="tid_seq.nextval"></TID>  
        <ACCOUNT>100001</ACCOUNT>  
        <AMOUNT>1500</AMOUNT>  
        <DESCRIPTION></DESCRIPTION>  
        <TRANSDATE InlineValue="sysdate">1999-05-31T13:20:00</TRANSDATE>  
        <PROCESSED>n</PROCESSED>  
      </InsertRecord>  
    </RECORDSET>  
  </Insert>  
  <GET_ALL_ACTIVITY xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG" />  
  <Delete xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/ACCOUNTACTIVITY">  
    <FILTER>WHERE AMOUNT = 1500</FILTER>  
  </Delete>  
</Request>  
```  
  
 Le précédent message de demande tout d’abord insère un enregistrement et appelle ensuite la procédure GET_ALL_ACTIVITY pour obtenir tous les enregistrements dans la table ACCOUNTACTIVITY. Ensuite, l’enregistrement inséré est supprimé en spécifiant une clause de filtre. Consultez les schémas de Message pour les opérations composites pour plus d’informations sur le schéma de message de demande pour effectuer des opérations composites sur l’utilisation de base de données Oracle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
> [!NOTE]
>  Dans le message précédent, l’extrait de l’opération d’insertion utilise l’attribut « InlineValue ». Pour plus d’informations sur l’attribut « InlineValue », consultez la description du schéma de l’opération d’insertion dans [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).  
  
 L’orchestration consomme le message et l’envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données Oracle pour le précédent message de demande ressemble à ceci :  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<RequestResponse xmlns="http://Composite_Op.CompositeSchema">  
  <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/ACCOUNTACTIVITY">  
    <InsertResult>1</InsertResult>   
  </InsertResponse>  
  <GET_ALL_ACTIVITYResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG">  
    <ALLRECS>  
      \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
        \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
          \<xs:complexType>  
            \<xs:sequence>  
              \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                \<xs:complexType>  
                  \<xs:sequence>  
                    \<xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                    \<xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                    \<xs:element minOccurs="0" name="AMOUNT" type="xs:decimal" />   
                    \<xs:element minOccurs="0" name="DESCRIPTION" type="xs:string" />   
                    \<xs:element minOccurs="0" name="TRANSDATE" type="xs:dateTime" />   
                    \<xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
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
            ......   
            ......   
          </NewTable>  
          ......  
          ......  
          <NewTable>  
            <TID>10</TID>   
            <ACCOUNT>100001</ACCOUNT>   
            <AMOUNT>1000</AMOUNT>   
            <TRANSDATE>2008-07-28T21:39:57</TRANSDATE>   
            <PROCESSED>n</PROCESSED>   
          </NewTable>  
        </NewDataSet>  
      \</diffgr:diffgram>  
    </ALLRECS>  
  </GET_ALL_ACTIVITYResponse>  
  <DeleteResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/ACCOUNTACTIVITY">  
    <DeleteResult>1</DeleteResult>   
  </DeleteResponse>  
</RequestResponse>  
```  
  
 La réponse précédente contient plusieurs jeux de résultats correspondant différentes opérations effectuées dans le cadre de l’opération composite. Par exemple, le `InsertResult` élément contient '1', qui indique le nombre de lignes insérées par l’opération d’insertion. De même, le `DeleteResult` élément contient '1', qui indique le nombre de lignes supprimées par l’opération de suppression.  
  
> [!IMPORTANT]
>  Si vous rencontrez des problèmes de délai d’attente lors de l’exécution d’une opération composite ce peut être, car le nombre de connexions est inférieur au nombre d’opérations dans une opération composite impliquant :  
>   
>  -   Les procédures stockées contenant des BFILE, BLOB, CLOB, NCLOB et REF CURSOR comme OUT ou IN OUT.  
> -   Sélectionnez l’opération.  
>   
>  Pour résoudre ce problème, vous devez vous assurer que s’il existe le nombre de « n » de ces opérations dans une opération composite, la valeur spécifiée pour le **MinPoolSize** propriété de liaison est « n + 1 » ou supérieur. Pour plus d’informations sur la **MinPoolSize** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)