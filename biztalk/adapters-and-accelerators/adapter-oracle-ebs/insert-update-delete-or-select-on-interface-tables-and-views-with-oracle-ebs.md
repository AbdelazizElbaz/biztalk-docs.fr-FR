---
title: "Insérer, mettre à jour, supprimer ou sélectionnez des tables d’interface et les vues de l’interface avec Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85f42431-80fb-49be-86d1-bb21eee5e4f5
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adc837fb72c0e18370d28450bf40f162f9849230
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="insert-update-delete-or-select-on-interface-tables-and-interface-views-with-oracle-e-business-suite"></a>Insérer, mettre à jour, supprimer ou sélectionnez des tables d’interface et les vues de l’interface avec Oracle E-Business Suite
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]surfaces un ensemble d’opérations standard, telles que Insert, Update, Delete, Select interface tables et vues. Cette rubrique fournit des instructions sur la façon d’effectuer ces opérations à l’aide de l’adaptateur. Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md). Pour plus d’informations sur la structure du message SOAP pour ces opérations, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).  
  
> [!NOTE]
>  L’adaptateur expose également des opérations spécifiques pour les tables et vues qui contiennent des types de données de grande taille telles que les objets BLOB, CLOB, NCLOB et BFILE. Pour plus d’informations sur ces opérations, consultez [opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues que contiennent LOB des données](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md). Pour obtenir des instructions sur la façon d’effectuer des opérations sur les tables et colonnes avec les types de données de grande taille à l’aide de BizTalk Server, consultez [terminer les opérations sur les tables avec des types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md).  
  
## <a name="how-to-perform-basic-operations-on-oracle-e-business-suite"></a>Comment effectuer des opérations de base sur Oracle E-Business Suite  
 Une opération sur Oracle E-Business Suite à l’aide de [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour exécuter Insert, Update, Delete ou des opérations Select sur les tables et vues dans Oracle E-Business Suite, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour l’opération que vous souhaitez appeler sur une table d’interface ou une vue.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir d’Oracle E-Business Suite.  
  
3.  Créez une orchestration pour appeler l’opération sur la table d’interface ou la vue.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment effectuer base Insert, Update, Delete ou opérations Select en insérant des enregistrements dans la table d’interface AR_ARCHIVE_PURGE_INTERIM dans Oracle E-Business Suite. Cette table d’interface n’est disponible dans le **des comptes clients** application dans Oracle E-Business Suite.  
  
 Pour illustrer comment insérer des enregistrements, le schéma est généré pour l’opération d’insertion pour la table AR_ARCHIVE_PURGE_INTERIM. Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour plus d’informations sur la façon de générer des schémas.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, du type défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *InsertInterfaceTable.OracleEBSBinding.Insert*, où InsertInterfaceTable est le nom de votre projet BizTalk. OracleEBSBinding est le schéma généré pour l’opération d’insertion sur la table AR_ARCHIVE_PURGE_INTERIM.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *InsertInterfaceTable.OracleEBSBinding.InsertResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer une opération sur Oracle E-Business Suite. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consomme ce message et le transmet à Oracle E-Business Suite. La réponse à partir d’Oracle E-Business Suite est enregistrée dans un autre emplacement. Contiendrait une orchestration classique pour effectuer des opérations de table de base sur la base de données Oracle :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration pour l’opération Select ressemble à ceci :  
  
 ![Orchestration permettant d’insérer des données dans les tables d’interface](../../adapters-and-accelerators/adapter-oracle-ebs/media/8a4508c5-9949-4043-9de5-d1226db8117b.gif "8a4508c5-9949-4043-9de5-d1226db8117b")  
  
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
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.Insert.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.Insert.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.Insert.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.Insert.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés, et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le sur BizTalk Server. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer pour Oracle E-Business Suite.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir d’Oracle E-Business Suite.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleEBS physique pour envoyer des messages pour Oracle E-Business Suite. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)  
  
         Pour effectuer des opérations sur les tables d’interface ou interface vues à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez définir le contexte de l’application appropriée dans lequel l’opération est appelée. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] fournit certaines propriétés de liaison pour spécifier le contexte d’application pour toute opération. Vous devez définir ces propriétés de liaison sur le port WCF-Custom ou WCF-OracleEBS utilisé pour effectuer des opérations sur les tables d’interface.  
  
        -   Si le **ClientCredentialType** liaison de la propriété est définie sur **base de données**, vous devez spécifier les propriétés de liaison suivantes pour définir le contexte des applications.  
  
            |Propriété de liaison|Valeur|  
            |----------------------|-----------|  
            |**OracleUserName**|Spécifiez le nom d’un utilisateur Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez pour le **OracleUserName** liaison de la propriété lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que la casse du nom d’utilisateur doivent être conservés ou si vous souhaitez entrer un nom d’utilisateur contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
            |**OraclePassword**|Le mot de passe pour l’utilisateur Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez pour le **OraclePassword** liaison de la propriété lorsqu’il se connecte à Oracle E-Business Suite. Le mot de passe est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que le cas du mot de passe doivent être conservés ou si vous souhaitez entrer un mot de passe contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
            |**OracleEBSResponsibilityName**|La responsabilité est associée à l’utilisateur Oracle E-Business Suite.|  
  
        -   Si le **ClientCredentialType** liaison de la propriété est définie sur **EBusiness**, vous devez déjà avoir spécifié les informations d’identification de Oracle E-Business lors de l’établissement de la connexion. Dans ce cas, vous devez uniquement spécifier la valeur pour le **OracleEBSResponsibilityName** propriété de liaison.  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour plus d’informations sur la façon dont l’adaptateur prend en charge la définition du contexte de l’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
        > [!NOTE]
        >  Vous pouvez définir le contexte de l’application soit en spécifiant les propriétés de liaison, ou en définissant des propriétés de contexte exposées par le message le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour obtenir des instructions sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour insérer des enregistrements dans la table d’interface AR_ARCHIVE_PURGE_INTERIM. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour envoyer des messages pour Oracle E-Business Suite est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour l’opération d’insertion que vous avez créé précédemment. Par exemple, le message de demande pour sélectionner tous les enregistrements de la table d’interface AR_ARCHIVE_PURGE_INTERIM est la suivante :  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">  
      <TRX_ID>001</TRX_ID>  
      <RELATED_ID>002</RELATED_ID>  
    </InsertRecord>  
  </RECORDSET>    
</Insert>  
```  
  
 Ce message de demande insère les enregistrements dans la table d’interface AR_ARCHIVE_PURGE_INTERIM. Consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md) pour plus d’informations sur le schéma de message de demande pour effectuer des opérations DML base sur Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 Pour les colonnes de données simples, comme dans le précédent message de demande, vous pouvez également utiliser le **InlineValue** attribut. Pour plus d’informations sur l’attribut InlineValue, consultez la description de l’opération d’insertion dans [opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).  
  
 Par exemple, le précédent message de demande avec les valeurs inline ressemble à ceci :  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">  
      <TRX_ID InlineValue="(Select TRX_ID FROM table_name)">001</TRX_ID>  
      <RELATED_ID>002</RELATED_ID>  
    </InsertRecord>  
  </RECORDSET>    
</Insert>  
```  
  
 Dans ce message de demande, la valeur de colonne TRX_ID est récupérée à partir d’une autre table. Par conséquent, bien que « 001 » est spécifié en tant que valeur pour TRX_ID, la valeur de l’instruction SELECT spécifiée pour l’attribut de InlineValue sera insérée dans la table.  
  
 L’orchestration consomme le message et l’envoie à Oracle E-Business Suite. La réponse à partir d’Oracle E-Business Suite est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir d’Oracle E-Business Suite pour le précédent message de demande est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <InsertResult>1</InsertResult>   
</InsertResponse>  
```  
  
 La réponse contient le nombre de lignes insérées dans la table.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Après avoir généré un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)