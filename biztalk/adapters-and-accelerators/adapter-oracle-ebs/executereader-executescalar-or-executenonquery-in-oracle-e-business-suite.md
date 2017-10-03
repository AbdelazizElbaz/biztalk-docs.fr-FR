---
title: "Les opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e2d377d-60a2-45fe-8458-433e6f4f6619
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cff3d58712ca8e926ada18519fcebb5fddc7ea65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite"></a>Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les opérations génériques tels que **ExecuteNonQuery**, **ExecuteReader**, et **ExecuteScalar**. Vous pouvez utiliser ces opérations à exécuter n’importe quelle instruction SQL sur la base de données Oracle. Ces opérations varient en fonction du type de réponse pour l’instruction SQL. Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
 Cette rubrique montre comment effectuer une **ExecuteReader** à l’aide de l’opération la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez suivre le même ensemble de procédures décrites dans cette rubrique pour effectuer **ExecuteNonQuery** et **ExecuteScalar** operations.  
  
## <a name="how-to-invoke-executereader-operation-on-oracle-database"></a>Comment l’opération ExecuteReader de code non managé sur la base de données Oracle  
 Une opération sur une base de données Oracle à l’aide de [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour appeler le **ExecuteReader** opération sur la base de données Oracle, ces tâches sont :  
  
1.  Créez un projet BizTalk et la génération du schéma pour le **ExecuteReader** opération.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour appeler l’opération sur la base de données Oracle.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment appeler le **ExecuteReader** opération sur une base de données Oracle à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Le **ExecuteReader** opération accepte n’importe quelle instruction SQL en tant que paramètre et retourne le jeu de résultats de l’opération sous forme de tableau du jeu de données. Pour cette rubrique, nous exécuter une instruction SELECT sur la table ACCOUNTACTIVITY à l’aide du **ExecuteReader** opération. La table ACCOUNTACTIVITY est créée en exécutant les scripts fournis avec les exemples. Pour plus d’informations sur le script, consultez [exemples](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).  
  
 Pour illustrer comment appeler **ExecuteReader** opération, le schéma est généré pour le **ExecuteReader** opération. Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Pour plus d’informations sur la façon de générer des schémas, consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Execute_Reader.GenericOperation.ExecuteReader*, où Execute_Reader est le nom de votre projet BizTalk. *GenericOperation* est le schéma généré pour le **ExecuteReader** opération.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Execute_Reader.GenericOperation.ExecuteReaderResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer une opération sur la base de données Oracle. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consomme ce message et le transmet à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Une orchestration classique pour appeler des opérations génériques tel que **ExecuteReader** contient :  
  
-   Envoyer et recevoir des formes pour envoyer et recevoir des messages à partir d’une base de données Oracle.  
  
-   Un double port de réception pour envoyer et recevoir des messages à partir d’une base de données Oracle.  
  
-   Un port d’envoi unidirectionnel pour envoyer la réponse à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration permettant d’appeler un **ExecuteReader** opération ressemble à ceci :  
  
 ![Orchestration permettant d’appeler l’opération ExecuteReader](../../adapters-and-accelerators/adapter-oracle-ebs/media/37b63331-76b7-47a2-b9d3-0c60e165d993.gif "37b63331-76b7-47a2-b9d3-0c60e165d993")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Vous devez configurer les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de la forme correspondent aux noms des formes de message, tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Pour chacun des ports logiques, configurez les propriétés dans le tableau ci-dessous. Les noms répertoriés dans la colonne Port correspondent aux noms des ports, comme indiqué dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les valeurs de propriété pour spécifier des messages pour les formes d’action et lier les messages aux ports. Les noms répertoriés dans le **forme** colonne correspondent aux noms des formes de message, tel qu’affiché dans le diagramme d’orchestration précédemment.  
  
 Une fois que vous avez configurer ces propriétés, les formes de message et les ports sont connectés, et l’orchestration est terminée.  
  
 Ensuite, vous devez maintenant générer la solution BizTalk et déployez-le sur BizTalk Server. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.Exec_Reader.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.Exec_Reader.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.Exec_Reader.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.Exec_Reader.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés, et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le sur BizTalk Server. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données Oracle.  
  
    -   Définir un physique WCF-Custom ou WCF-OracleEBS port d’envoi pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports d’envoi, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business ](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).  
  
        > [!IMPORTANT]
        >  Comme partie des opérations génériques, si vous exécutez des opérations sur des objets, par exemple les procédures stockées, fonctions, tables d’interface ou vues de l’interface, qui appartiennent à une application Oracle E-Business Suite, vous devez définir le contexte d’application en spécifiant propriétés de liaison requis. Pour plus d’informations sur la définition du contexte d’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
        >   
        >  Vous pouvez définir le contexte de l’application soit en spécifiant les propriétés de liaison, ou en définissant des propriétés de contexte exposées par le message le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour obtenir des instructions sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk avant d’appeler **ExecuteReader** opération sur la base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour envoyer des messages à Oracle de base de données est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour le **ExecuteReader** opération que vous avez généré précédemment. Par exemple, le message de demande pour exécuter une instruction SELECT à l’aide un **ExecuteReader** l’opération est :  
  
```  
<ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/">  
  <Query>SELECT * FROM ACCOUNTACTIVITY</Query>  
</ExecuteReader>  
```  
  
 Consultez les schémas de Message pour ExecuteReader, ExecuteScalar et opérations ExecuteNonQuery pour plus d’informations sur le schéma de message de demande pour l’appel d’une **ExecuteReader** à l’aide de l’opération la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 L’orchestration consomme le message et l’envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. La réponse pour le **ExecuteReader** opération contient un jeu de résultats comme un jeu de données. Par exemple, la réponse à partir de la base de données Oracle pour le précédent message de demande est la suivante :  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/">  
  <ExecuteReaderResult>  
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
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-08-04T13:04:20</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        </NewTable>  
        <NewTable>  
          ......  
          ......  
        </NewTable>  
        ......  
        ......  
      </NewDataSet>  
    \</diffgr:diffgram>  
  </ExecuteReaderResult>  
</ExecuteReaderResponse>  
```  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Après avoir généré un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)