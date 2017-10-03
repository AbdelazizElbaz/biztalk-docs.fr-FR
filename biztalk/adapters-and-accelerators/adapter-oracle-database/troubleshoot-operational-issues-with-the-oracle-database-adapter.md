---
title: "Résoudre les problèmes opérationnels avec l’adaptateur de base de données Oracle | Documents Microsoft"
description: "Problèmes courants et des résolutions de carte de base de données Oracle dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fb83245-2b6a-48cc-8601-b923bb009a58
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1de0198d26f804ee8d1974d5dd542387408ea53a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-oracle-database-adapter"></a>Résoudre les problèmes opérationnels avec l’adaptateur de base de données Oracle
Résolution des problèmes techniques pour résoudre les erreurs opérationnels que vous pouvez rencontrer à l’aide de [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
## <a name="enable-tracing"></a>Activer le suivi  
 Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md).  
  
## <a name="known-issues"></a>Problèmes connus  
 Voici les erreurs les plus courantes que vous pouvez rencontrer en utilisant le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ainsi que leur cause probable et de la résolution.   
  
### <a name="BKMK_OraDBLoading"></a>Erreur lors du chargement des liaisons de l’adaptateur  
 **Problème**  
  
 Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], vous obtenez l’erreur suivante :  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF charge les liaisons de l’adaptateur pour tous les adaptateurs installés. À son tour, les liaisons de l’adaptateur sont dépendantes du logiciel client spécifique pour l’application d’entreprise. Vous risquez de rencontrer ce problème pour les raisons suivantes :  
  
-   Le logiciel client LOB requis n’est pas installé sur l’ordinateur où vous avez installé l’adaptateur.  
  
-   Vous avez effectué une installation standard ou complète de la carte, qui installe tous les adaptateurs contenus dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Toutefois, les bibliothèques clientes LOB peuvent être installés pour seulement une application d’entreprise. Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.  
  
 **Résolution**  
  
-   Assurez-vous que les versions de client LOB requis sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. [Prise en charge des systèmes d’entreprise et de métier (LOB)](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions de client pris en charge.  
  
-   Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.  
  
    > [!NOTE]
    >  Pour vous assurer que votre application fonctionne avec la version la plus récente de ODP.NET, vous devez avoir « Stratégie dll » installé sur l’ordinateur et enregistré dans le GAC. Pour plus d’informations, consultez [le fournisseur de données Oracle pour .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) sur le site Web d’Oracle.  
  
###  <a name="BKMK_OraDBAdapDisplay"></a>L’adaptateur de base de données Oracle n’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server  
 **Problème**  
  
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] inclus avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] ne figure pas dans la liste des adaptateurs dans la console Administration de BizTalk Server.  
  
 **Cause**  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée. Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ajouter explicitement le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_OraDBXMLRetrieve"></a>Erreur lors de la récupération de sortie XML avec les nœuds de plus de 65 536  
 **Problème**  
  
 L’adaptateur renvoie l’erreur suivante lors de la récupération du XML de sortie qui a plus de 65 536 nœuds.  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **Cause**  
  
 L’adaptateur ne peut pas sérialiser et désérialiser un objet avec des éléments de plus de 65 536.  
  
 **Résolution**  
  
 Vous pouvez résoudre ce problème en définissant le `maxItemsInObjectGraph` paramètre. Vous pouvez le définir dans une des deux manières suivantes :  
  
-   Définissez ce paramètre en modifiant le `maxItemsInObjectGraph` paramètre dans le `ServiceBehavior` attribut sur votre classe de service.  
  
-   Ajoutez le code suivant au fichier app.config de votre application.  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 Un fichier app.config exemple ressemble à ceci.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  \<system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="oracleDBBinding"  
       contract="IOutboundContract" name="oracle_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_OraDBPerfOps"></a>Erreur lors de l’exécution d’opérations sur la base de données Oracle  
 **Problème**  
  
 L’adaptateur renvoie l’erreur suivante lors de l’exécution de toute opération sur la base de données Oracle à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Pour[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **Cause**  
  
 L’action WCF pour le message n’est pas spécifiée. WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.  
  
 **Résolution**  
  
 Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk. Pour obtenir des instructions, consultez [configurer l’action SOAP pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md). Consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) pour afficher la liste des actions pour chaque opération.  
  
###  <a name="BKMK_OraDBXmlParsing"></a>XmlReaderParsingException en raison d’un nom d’opération incorrecte dans l’action spécifiée  
 **Problème**  
  
 La Console Administration de BizTalk Server attribue l’erreur suivante lors de l’envoi de messages à une base de données Oracle :  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 **Cause**  
  
 Si vous configurez un port personnalisé WCF en important le fichier de liaison de port créé par le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’action dans le port est spécifiée dans le format suivant :  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 Dans le format ci-dessus, le nom de l’opération est régi par l’opération que vous avez choisi lors de la génération du schéma. Par exemple, si vous avez généré le schéma pour l’opération d’insertion sur une table, le nom de l’opération dans l’action sera « Insert ». Toutefois, le nom de l’opération dans le port logique créé dans l’orchestration BizTalk de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] peut être différent.  
  
 **Résolution**  
  
 Vérifiez que les noms des opérations dans les deux le port logique (dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) et le port physique (dans la Console Administration de BizTalk Server) sont les mêmes.  
  
###  <a name="BKMK_OraDBConnURI"></a>Erreur lors de la spécification d’un URI de connexion pour un port personnalisé WCF dans BizTalk Server  
 **Problème**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]attribue l’erreur suivante lorsque vous spécifiez un URI de connexion pour se connecter à la base de données Oracle.  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 **Cause**  
  
 L’URI de connexion n’est pas conforme au format de codage standard. Par exemple, la valeur d’un paramètre peut contenir un espace.  
  
 **Résolution**  
  
 Vérifiez que la connexion URI que vous spécifiez respecte le format d’encodage standard. Par exemple, un espace vide doit être remplacé par « %20 ».  
  
###  <a name="BKMK_OraDBInvalCursor"></a>Exception de curseur non valide lors de l’appel de procédures stockées qui acceptent des paramètres REF CURSOR  
 **Problème**  
  
 Lorsque vous appelez les procédures dans la base de données Oracle qui acceptent des entrées de REF CURSOR, vous pouvez obtenir l’exception suivante :  
  
```  
Microsoft.ServiceModel.Channels.Common.TargetSystemException: ORA-01001: invalid cursor ---> Oracle.DataAccess.Client.OracleException  
```  
  
 **Cause**  
  
 Le bloc de PL/SQL pour la procédure que vous appelez pourrait être transférant les REF CURSOR, autrement dit, le IN REF CURSOR peut être mise en route attribué à des REF CURSOR.  
  
 **Résolution**  
  
 Le bloc de PL/SQL doit diriger pas IN à la sortie REF CURSOR sans traitement approprié.  
  
###  <a name="BKMK_OraDBValidateResp"></a>Erreur lors de la validation de la réponse pour l’opération ReadLOB à l’aide de BizTalk Server  
 **Problème**  
  
 Lors de l’exécution d’une opération de ReadLOB à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], la réponse à partir de la base de données Oracle échoue à la validation par rapport à la Description langage WSDL (Web Services).  
  
 **Cause**  
  
 Le fichier WSDL contient un nom de nœud StreamBody qui est défini pour l’exécution de demandes basées sur le service, mais n’est pas nécessaire pour les scénarios de BizTalk. Par conséquent, lorsque le fichier de sortie XML, qui ne contient pas le nœud StreamBody, est comparée avec le WSDL, la validation échoue.  
  
 **Résolution**  
  
 Supprimez le nœud StreamBody à partir de WSDL lors de la validation par rapport à la sortie qui a été générée à l’aide de BizTalk Server. Effectuez les étapes suivantes pour ce faire :  
  
1.  Le fichier WSDL qui contient le nœud StreamBody ressemble à ceci.  
  
    ```  
    \<xs:element name="ReadLOBResponse">  
        \<xs:annotation>  
          \<xs:documentation>  
            \<doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>  
          \</xs:documentation>  
        \</xs:annotation>  
        \<xs:complexType>  
          \<xs:sequence>  
            \<xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" nillable="true" type="ns3:StreamBody" />  
          \</xs:sequence>  
        \</xs:complexType>  
      \</xs:element>  
    ```  
  
     Remplacez l’exemple précédent avec les éléments suivants.  
  
    ```  
    \<xs:element name="ReadLOBResponse">  
     \<xs:annotation>  
     \<xs:documentation>  
      \<doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>   
      \</xs:documentation>  
      \</xs:annotation>  
     \<xs:complexType>  
     \<xs:sequence>  
      \<xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" type="xs:base64Binary" />   
      \</xs:sequence>  
      \</xs:complexType>  
      \</xs:element>  
    ```  
  
     Dans cette étape, vous avez supprimé la référence au type = « ns3:StreamBody » dans le schéma XSD d’origine et l’a remplacé avec type = « xs : base64Binary ». En outre, vous avez supprimé la valeur « true » = « nillable » à partir du XSD d’origine.  
  
2.  Supprimer les éléments suivants à partir de WSDL.  
  
    ```  
    \<xs:complexType name="StreamBody">  
        \<xs:sequence>  
          \<xs:element minOccurs="1" maxOccurs="1" name="Stream">  
            \<xs:simpleType>  
              \<xs:restriction base="xs:base64Binary">  
                \<xs:minLength value="0" />  
              \</xs:restriction>  
            \</xs:simpleType>  
          \</xs:element>  
        \</xs:sequence>  
      \</xs:complexType>  
      \<xs:element name="StreamBody" nillable="true" type="ns3:StreamBody" />  
    ```  
  
    > [!NOTE]
    >  Opération de ReadLOB n’est pas pris en charge avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Vous devez utiliser une opération de sélection de table pour lire des données LOB à partir d’un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
###  <a name="BKMK_OraDBSchemaValidateFail"></a>Validation de schéma risque d’échouer dans les scénarios d’interrogation  
 **Problème**  
  
 Échec de la validation de schéma dans les scénarios où le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interroge les tables qui contiennent des champs de type ROWID ou UNROWID de base de données.  
  
 **Cause**  
  
 Au moment du design, lorsque l’adaptateur génère des métadonnées pour la table contenant les champs de type ROWID ou UNROWID, le schéma inclut « nillable = false », ce qui signifie que les champs de type ROWID ou UNROWID ne peut pas être null. Toutefois, au moment de l’exécution lorsque l’adaptateur récupère les métadonnées, les champs de type ROWID ou UNROWID contiennent des valeurs null. Par conséquent, la validation de schéma échoue.  
  
 **Résolution**  
  
 Si vous utilisez la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez choisir de désactiver la validation de schéma. Ou bien, vous pouvez modifier manuellement le schéma pour modifier « nillbale = true » pour les types de données ROWID et UNROWID.  
  
###  <a name="BKMK_OraDBUnreasonConv"></a>Erreur 'Conversion déraisonnable demandée' lors de l’exécution de procédures stockées avec des Types d’enregistrements en tant que paramètres  
 **Cause**  
  
 Envisagez un scénario où Oracle stockées procédure prend un Type d’enregistrement en tant que paramètre. Supposons que le Type d’enregistrement est déclaré comme \<nom de table > % ROWTYPE, où la table contient une colonne de type de données de type LONG. Lorsque le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] rencontre le LONG type de données, il définit la taille du type de données égal à la valeur spécifiée pour le **LongDatatypeColumnSize** propriété de liaison. Toutefois, la base de données Oracle ne définit pas une taille pour le type de données de type LONG. Par conséquent, lorsque l’adaptateur appelle la procédure stockée, il génère une erreur « Conversion déraisonnable demandée ».  
  
 **Résolution**  
  
 Si un Type d’enregistrement a un type de données de type LONG, vous devez le définir explicitement en tant que partie d’un package.  
  
###  <a name="BKMK_OraDBAdapRecognize"></a>L’adaptateur ne reconnaît pas l’action sur le port physique, même si le fichier de liaison généré par le complément Consume Adapter Service vous permet de créer les ports  
 **Problème**  
  
 Après avoir utilisé le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour une opération spécifique sur la base de données Oracle, le complément crée également un fichier de liaison de port. Vous pouvez importer ce fichier à l’aide de la liaison la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports physiques dans BizTalk Server. Toutefois, lorsque vous envoyez des messages à la base de données Oracle à l’aide de ces ports, l’adaptateur ne parvient pas à comprendre l’action spécifiée sur le port et génère une erreur semblable au suivant :  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **Cause**  
  
 Lorsque vous créez des ports logiques dans une orchestration BizTalk, vous spécifiez certains noms pour les opérations sur ces ports ou vous utilisez simplement les noms par défaut comme Operation_1, Operation_2, etc.. Toutefois, dans le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le nom de l’opération est identique au nom de l’opération de base de données Oracle pour lequel générer des métadonnées. Par exemple, si vous générez des métadonnées pour une opération Select sur la table ACCOUNTACTIVITY dans la base de données Oracle, l’action est fixée à ce qui suit :  
  
```  
<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
```  
  
 Lorsque vous importez le fichier de liaison, la même action est définie sur le port physique. Par conséquent, les noms de l’opération sur le port logique (Operation_1, Operation_2, etc.) ne correspondent pas les noms de l’opération spécifiées dans l’action sur le port physique, ce qui entraîne une erreur.  
  
 **Résolution**  
  
 Assurez-vous que le nom de l’opération dans le port logique est la même que le nom d’opération spécifié dans le cadre de l’action dans le port physique. Procédez de l'une des manières suivantes :  
  
-   Modifier le nom de l’opération dans le port logique dans le Concepteur d’orchestration BizTalk à partir de Operation_1, etc. à l’opération pour laquelle générer des métadonnées, par exemple Select.  
  
-   Modifier le nom de l’opération dans l’action sur le port physique pour le nom de l’opération dans le port logique. Par exemple, vous pouvez modifier l’action dans le port physique pour ressembler à ceci :  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
    ```  
  
###  <a name="BKMK_OraDBOverflowExcep"></a>Adaptateur lève une exception de dépassement de capacité (« System.OverflowException ») sur l’exécution d’une opération  
 **Problème**  
  
 À l’aide de la carte, si vous essayez d’effectuer une opération qui contiennent des types de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR, l’adaptateur peut lever une exception de dépassement de capacité.  
  
 **Cause**  
  
 Cela se produit si vous fournissez une valeur élevée pour le type de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR qui ne tiennent pas dans le type .NET respectif.  
  
 **Résolution**  
  
 Si vous souhaitez passer des valeurs élevées pour le type de données numériques à l’intérieur des jeux de données ou faiblement typée REF CURSOR Oracle, vous devez activer la saisie sécurisée en définissant la valeur de la **EnableSafeTyping** liaison de propriété **true**. L’activation de la saisie sécurisée expose les type de données numériques à l’intérieur des jeux de données ou faiblement typée REF CURSOR Oracle en tant que chaînes.  
  
###  <a name="BKMK_OraDBRootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk  
 **Problème**  
  
 Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Résolution**  
  
1.  Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.  
  
2.  Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).  
  
###  <a name="BKMK_OraDBInvalBinding"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio  
 **Problème**  
  
 Lorsque vous utilisez l’adaptateur pour créer une application dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :  
  
```  
The element 'bindings' has invalid child element 'oracleDBBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 Cet avertissement s’affiche, car le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] de liaison, `oracleDBBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ignorer cet avertissement sans problème.  
  
###  <a name="BKMK_OraDBNotification"></a>BizTalk Server lève une exception si vous utilisez plusieurs schémas de Notification dans la même application ou le schéma de Notification entre plusieurs applications sur le même hôte  
 **Problème**  
  
 BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.  
  
 **Cause**  
  
 Cela se produit en raison de le des manières suivantes :  
  
-   Vous avez généré plus d’un schéma de Notification dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour recevoir des notifications à partir de la base de données Oracle. Étant donné que les schémas de Notification sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.  
  
-   En cas de plusieurs projets, vous avez généré un schéma de Notification pour chacun des projets, déployés dans chaque projet à une application BizTalk Server distincte sur le même hôte BizTalk Server, puis exécutez une application ou les applications de recevoir des notifications à partir de la base de données Oracle. Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.  
  
 **Résolution**  
  
 Utiliser un seul fichier de schéma de Notification pour une application BizTalk Server. Si vous avez besoin d’utiliser le schéma de Notification dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un seul schéma de Notification, puis utiliser le schéma de notification à partir de toutes les autres applications dans BizTalk Server.  
  
###  <a name="BKMK_MemUsage"></a>Utilisation de la mémoire et de thread nombre augmente lors de l’utilisation de la carte dans une opération entrante  
 **Problème**  
  
 Dans une opération entrante, telles que l’interrogation, **si aucune donnée n’est disponible dans la table interrogée** et l’adaptateur continue à interroger, sur une période de temps, vous rencontrez une augmentation de l’utilisation de la mémoire et le nombre de threads.  
  
 **Cause**  
  
 **Si aucune donnée n’est disponible dans la table interrogée**, après chaque cycle de délai d’attente de réception [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] génère un nouveau thread pour poursuivre l’opération d’interrogation. Par conséquent, l’utilisation de count et de la mémoire du thread augmente sur une période de temps. Toutefois, si la table interrogée possède des données, le même thread continue à effectuer toutes les interrogations suivantes.  
  
 **Résolution**  
  
 Nous vous recommandons d’affecter le **ReceiveTimeout** à la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours) afin qu’un nouveau thread est généré uniquement 24 jours. Cela garantit que le nombre de threads et de l’utilisation de mémoire n’augmente pas trop trop tôt.  
  
> [!NOTE]
>  Si SqlAdapterInboundTransactionBehavior a été défini, assurez-vous que le TransactionTimeout est également configuré pour la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours). Lorsque vous utilisez cette solution de contournement, nous pouvons ajouter la SqlAdapterInboundTransactionBehavior uniquement si le niveau d’isolation de transaction doit être configurée. Sinon, il est recommandé de supprimer ce comportement.  
  
 Pour plus d’informations sur la **ReceiveTimeout** liaison de propriété, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). Pour obtenir des instructions sur la spécification des propriétés de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
> [!NOTE]
>  Lors de l’utilisation de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], définir le délai d’attente pour une valeur élevée n’affecte pas les fonctionnalités de la carte.  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[Résoudre les problèmes d’installation de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)