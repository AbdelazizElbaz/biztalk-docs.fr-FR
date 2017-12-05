---
title: "Appeler des fonctions et procédures avec des Types d’enregistrements dans la base de données Oracle à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccdc150e-055a-47df-af3e-64931946455d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d8aa9b3202adaf57e7ec213a81384606eb1b8a4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-functions-and-procedures-with-record-types-in-oracle-database-using-biztalk-server"></a>Appeler des fonctions et procédures avec des Types d’enregistrements dans la base de données Oracle à l’aide de BizTalk Server
Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL. Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes. Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge des Types d’enregistrements, consultez [opérations sur les fonctions et procédures avec des Types d’enregistrements dans la base de données Oracle.](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-procedures-with-record-types-in-oracle-database.md). Pour plus d’informations sur la structure XML des Types d’enregistrements, consultez [des schémas de Message pour les Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md).  
  
## <a name="how-to-invoke-functions-in-an-oracle-database"></a>Explique comment appeler des fonctions dans une base de données Oracle ?  
 Une opération sur une base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour appeler une fonction dans une base de données Oracle qui retourne simple et imbriquée des types d’enregistrements, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour la fonction à appeler dans une base de données Oracle.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour appeler la fonction dans la base de données Oracle.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, Func_RecordTypes, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] nous appellerons des paramètres de type de prise en charge l’appel de fonction qui retournent l’enregistrement :  
  
-   La fonction GET_ACCOUNTADDRESS qui retourne un type d’enregistrement simple.  
  
-   La fonction GET_ACCOUNTINFO qui retourne un type d’enregistrement imbriqué.  
  
 Ces fonctions sont disponibles dans le cadre de la ACCOUNT_PKG créée en exécutant les scripts SQL fournis avec les exemples. Pour en savoir plus sur les exemples et les scripts SQL, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
 Par conséquent, nous devons génération du schéma pour les deux les fonctions GET_ACCOUNTADDRESS et GET_ACCOUNTINFO, disponibles sous le schéma SCOTT\Package\ACCOUNT_PKG. Consultez [de récupérer les métadonnées pour des opérations Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la fenêtre Vue Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux jeux de message de demande-réponse, une demande-réponse définie pour appeler la fonction GET_ACCOUNTADDRESS et recevoir une réponse ; l’autre message de demande-réponse définie pour appeler la fonction GET_ACCOUNTINFO et recevoir une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTINFO*, où *Func_RecordTypes* est le nom de votre Projet BizTalk. *OracleDBBindingSchema* est le schéma généré pour la fonction GET_ACCOUNTADDRESS.|  
  
5.  Répétez l’étape précédente pour créer plus de trois messages. Dans le **propriétés** volet pour les nouveaux messages, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Réponse|*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTINFOResponse*|  
    |MAX2|*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTADDRESS*|  
    |Réponse aux menaces2|*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTADDRESSResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler une fonction retourne des types simples et complexes d’enregistrements. Dans cette orchestration, vous supprimez deux messages de demande :  
  
-   Une pour la fonction GET_ACCOUNTADDRESS qui retourne un type d’enregistrement simple.  
  
-   Une pour la fonction GET_ACCOUNTINFO qui retourne un type d’enregistrement imbriqué.  
  
 Ces messages sont supprimés à un emplacement de réception. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme les messages et les transmet à la base de données Oracle via ODP. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Étant donné que l’orchestration récupère simultanément les deux requêtes, vous devez inclure une forme Actions parallèles dans l’orchestration. Pour chaque action parallèle, vous devez inclure les envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses, respectivement. Toutefois, vous pouvez utiliser les mêmes ports pour envoyer et recevoir des messages pour les deux opérations. Contiendrait une orchestration classique simultanément les deux opérations :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestration permettant d’utiliser des Types d’enregistrements dans Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/6ee5e57b-48d5-435a-a16b-83bac878d0b7.gif "6ee5e57b-48d5-435a-a16b-83bac878d0b7")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné. Le tableau suivant répertorie les formes, que vous devez inclure pour l’une des actions parallèles.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
 Le tableau suivant répertorie les formes que vous devez inclure pour l’autre action parallèle.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage2|Recevoir|-Définissez **nom** à *ReceiveMessage2*<br />-Définissez **activer** à *True*|  
|SendMessage2|Send|-Définissez **nom** à *SendMessage2*|  
|ReceiveResponse2|Recevoir|-Définissez **nom** à *ReceiveResponse2*<br />-Définissez **activer** à *False*|  
|SendResponse2|Send|-Définissez **nom** à *SendResponse2*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br />-Définissez **Type** à *SaveResponseType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
 Étant donné que vous allez traiter deux requêtes et les messages de réponse à l’aide de ces ports, vous devez créer deux opérations pour chaque port, où chaque opération correspond à un type de message. Pour créer une opération, avec le bouton droit de la forme port et sélectionnez **nouvelle opération**. Nom de la première opération pour chaque port en tant que **NestedRecType** et la seconde opération pour chaque port en tant que **SimpleRecType**.  
  
### <a name="using-correlations"></a>À l’aide de corrélations  
 La corrélation est le processus de mise en correspondance d'un message entrant et de l'instance appropriée d'une orchestration. Dans l’orchestration que vous sera envoyé par lots deux messages de demande, un pour chaque surcharge. Utilisation de la corrélation, vous associez un message de demande l’orchestration à droite. Pour plus d’informations sur la corrélation, consultez [à l’aide de corrélations dans les Orchestrations](../../core/using-correlations-in-orchestrations.md)  
  
##### <a name="to-use-correlations"></a>Pour utiliser des corrélations  
  
1.  Promouvoir une propriété à partir du schéma généré pour chaque fonction. Par exemple, de promouvoir la propriété CUSTNAME à partir du schéma de la fonction GET_ACCOUNTADDRESS ; promouvoir la propriété de l’aide à partir du schéma de la fonction GET_ACCOUNTINFO. Pour promouvoir une propriété, avec le bouton droit de la propriété dans la vue schéma, pointez sur **promouvoir**, puis sélectionnez **Promotion rapide**. Cela ajoute un fichier PropertySchema.xsd à votre projet BizTalk.  
  
     Pour plus d’informations sur la promotion d’une propriété, consultez [promotion des propriétés](../../core/promoting-properties.md).  
  
2.  À partir de la vue Orchestration, cliquez sur **Types de corrélations**, puis sélectionnez **nouveau Type de corrélation**.  
  
3.  Le **propriétés de corrélation** boîte de dialogue répertorie les propriétés que vous avez promu à l’étape 1. Sélectionnez une propriété, puis cliquez sur **ajouter**.  
  
4.  Cliquez sur **OK**.  
  
5.  Pour créer des types de corrélations pour la propriété promue, répétez ces étapes.  
  
6.  Renommez les types de corrélation basées sur la propriété à laquelle elles sont associées. Vous pouvez renommer les types de corrélations pour *CorrelationType_CUSTNAME* (pour la propriété CUSTNAME) et *CorrelationType_AID* (pour la propriété de l’aide).  
  
7.  À partir de la vue Orchestration, cliquez sur **des ensembles de corrélations**, puis sélectionnez **nouvel ensemble de corrélations**.  
  
8.  Avec le bouton droit de l’ensemble de corrélations nouvellement ajoutée, puis cliquez sur **propriétés**. Dans le **propriétés** volet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Type de corrélation|*Func_RecordTypes.CorrelationType_CUSTNAME*|  
    |Identificateur|*Correlation_CUSTNAME*|  
  
9. Ajouter un autre ensemble de corrélations et spécifiez les propriétés suivantes à partir de la **propriétés** volet.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Type de corrélation|*Func_RecordTypes.CorrelationType_AID*|  
    |Identificateur|*Correlation_AID*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **l’initialisation des ensembles de corrélations** à *Correlation_AID*<br />-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.NestedRecType.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.NestedRecType.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.NestedRecType.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.NestedRecType.Request*|  
|ReceiveMessage2|-Définissez **l’initialisation des ensembles de corrélations** à *Correlation_CUSTNAME*<br />-Définissez **Message** à *MAX2*<br />-Définissez **opération** à *FileIn.SimpleRecType.Request*|  
|SendMessage2|-Définissez **Message** à *MAX2*<br />-Définissez **opération** à *LOBPort.SimpleRecType.Request*|  
|ReceiveResponse2|-Définissez **Message** à *réponse aux menaces2*<br />-Définissez **opération** à *LOBPort.SimpleRecType.Response*|  
|SendResponse2|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.SimpleRecType.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
-   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer les messages de demande, une pour chaque procédure surchargée. L’orchestration BizTalk consommer les messages de demande et l’envoyer à la base de données Oracle.  
  
-   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprime les messages de réponse, une pour chaque fonction, contenant la réponse à la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleDB physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création des ports WCF-Custom ou WCF-OracleDB, consultez [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md). Car le WCF-Custom ou WCF-OracleDB port d’envoi envoie et recevoir des messages conformes à plusieurs schémas et effectue deux opérations, vous devez définir une action dynamique pour les opérations. Pour plus d’informations sur les actions, consultez [configurer l’action SOAP pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md). Pour cette orchestration, l’action doit être définie comme suit :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="NestedRecType" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO" />  
          <Operation Name="SimpleRecType" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS" />  
        </BtsActionMapping>  
        ```  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk permettant d’appeler une fonction dans une table de base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-OracleDB à envoyer des messages à la base de données Oracle est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer deux demande d’emplacement de réception de messages (une pour chaque fonction) dans le fichier. Le schéma pour les messages de demande doit être conforme au schéma pour les fonctions que vous avez généré précédemment. L’orchestration consomme les messages de requête et les envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée à un autre emplacement de fichier définie dans le cadre de l’orchestration.  
  
 Consultez [des schémas de Message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md) pour plus d’informations sur le schéma de message de demande pour l’appel de fonctions à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Par exemple, le message de demande pour appeler la fonction GET_ACCOUNINFO est la suivante :  
  
```  
<GET_ACCOUNTINFO xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <AID>100000</AID>  
</GET_ACCOUNTINFO>  
```  
  
 De même, le message de demande pour appeler la fonction GET_ACCOUNTADDRESS est :  
  
```  
<GET_ACCOUNTADDRESS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <CUSTNAME>Mindy Martin</CUSTNAME>  
</GET_ACCOUNTADDRESS>  
```  
  
 Le premier message de demande appelle la fonction GET_ACCOUNTINFO qui retourne un type d’enregistrement imbriqué. Le message de réponse pour l’appel de la fonction GET_ACCOUNTINFO est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<GET_ACCOUNTINFOResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <GET_ACCOUNTINFOResult>  
    <ACCT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO">  
      <ACCTID>100000</ACCTID>   
      <NAME>Kim Ralls</NAME>   
      <BALANCE>10000</BALANCE>   
    </ACCT>  
    <ADDRESS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO">  
      <STREET>1234 Main St.</STREET>   
      <CITY>Seattle</CITY>   
      <STATE>WA</STATE>   
    </ADDRESS>  
  </GET_ACCOUNTINFOResult>  
</GET_ACCOUNTINFOResponse>  
```  
  
 Le deuxième message de demande appelle la fonction GET_ACCOUNTADDRESS qui retourne un type d’enregistrement simple. Le message de réponse pour l’appel de la fonction GET_ACCOUNTADDRESS est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<GET_ACCOUNTADDRESSResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <GET_ACCOUNTADDRESSResult>  
    <ID xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">100004</ID>  
    <NAME xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">Mindy Martin</NAME>  
    <STREET xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">6789 Cherry St.</STREET>  
    <CITY xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">New York</CITY>  
    <STATE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">NY</STATE>  
  </GET_ACCOUNTADDRESSResult>  
</GET_ACCOUNTADDRESSResponse>  
```  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’appel des fonctions ou à l’aide de procédures [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour les applications BizTalk de développer avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)