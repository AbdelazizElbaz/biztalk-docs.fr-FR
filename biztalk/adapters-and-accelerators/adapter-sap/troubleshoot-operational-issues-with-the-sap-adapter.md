---
title: "Résoudre les problèmes opérationnels avec l’adaptateur SAP dans BizTalk | Documents Microsoft"
description: "Erreurs courantes, des problèmes et résolutions avec mySAP adaptateur dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb0f005b-7548-478b-8243-69e07c29d02c
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5298782f23cb8c7c32a2bcbd512f3a1b78f8a69d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-sap-adapter"></a>Résoudre les problèmes opérationnels avec l’adaptateur SAP
Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
### <a name="enable-tracing"></a>Activer le suivi  
 Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md).  
  
##  <a name="client_dll"></a>Erreur lors du chargement de la liaison  
 **Problème**  
  
 Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’interface graphique utilisateur attribue l’erreur suivante :  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 Lorsque vous démarrez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] charge les liaisons de l’adaptateur pour tous les adaptateurs installés. À son tour, les liaisons de l’adaptateur sont dépendantes du logiciel client spécifique pour l’application d’entreprise. Vous risquez de rencontrer ce problème pour les raisons suivantes :  
  
-   Le logiciel client LOB requis n’est pas installé sur l’ordinateur où vous avez installé l’adaptateur.  
  
-   Vous avez effectué une installation standard ou complète de la carte, qui installe tous les adaptateurs contenus dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Toutefois, les bibliothèques clientes LOB peuvent être installés pour seulement une application d’entreprise. Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.  
  
 **Résolution**  
  
-   Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.  
  
-   Assurez-vous que les versions de client LOB requises sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. [Prise en charge des systèmes métier](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions prises en charge. Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] requiert également certaines DLL interagir avec le système SAP. Pour plus d’informations sur les DLL requises par l’adaptateur, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).
  
##  <a name="BKMK_SAPDisplay"></a>L’adaptateur SAP est manquant dans la console Administration de BizTalk  
 **Problème**  
  
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] inclus avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des adaptateurs dans la console Administration de BizTalk Server.  
  
 **Cause**  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée. Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ajouter explicitement le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
##  <a name="BKMK_SAPConnOpen"></a>DLL sont manquantes erreur d’ouverture d’une connexion à SAP  
 **Problème**  
  
 Lorsque vous essayez d’ouvrir une connexion au système SAP en utilisant le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], une boîte de dialogue s’affiche dans le système SAP, informant que certaines DLL est manquantes.  
  
 **Cause**  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise librfc32u.dll pour établir une connexion avec le système SAP. Le librfc32u.dll, exige à son tour, un ensemble de DLL pour fonctionner. Vous obtenez cette erreur si ces DLL de prise en charge ne sont pas ajoutés à la variable de chemin d’accès sur l’ordinateur où le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est installé.  
  
 **Résolution**  
  
 Reportez-vous à la table spécifiée comme une solution à la [erreur lors du chargement des liaisons de l’adaptateur](#client_dll) problème. Le tableau répertorie les DLL de prise en charge nécessaires pour interagir avec le système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
##  <a name="BKMK_SAPXmlRetrieve"></a>Erreur durant la récupération de XML avec les nœuds de plus de 65 536  
 **Problème**  
  
 L’adaptateur attribue l’erreur suivante lors de la récupération de sortie XML qui a plus de 65 536 nœuds.  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **Cause**  
  
 L’adaptateur ne peut pas sérialiser et désérialiser un objet avec des éléments de plus de 65 536.  
  
 **Résolution**  
  
 Vous pouvez résoudre ce problème en définissant le `maxItemsInObjectGraph` paramètre dans une des deux manières suivantes :  
  
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
  
 Un app.config exemple ressemble à ce qui suit.  
  
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
      <endpoint   behaviorConfiguration="NewBehavior" binding="sapBinding"  
       contract="IOutboundContract" name="sap_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
##  <a name="BKMK_SAPConnURI"></a>Erreur de saisie d’un URI de connexion pour un port personnalisé WCF dans BizTalk Server  
 **Problème**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]attribue l’erreur suivante lorsque vous spécifiez un URI de connexion pour se connecter au système SAP.  
  
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
  
##  <a name="BKMK_SAPOperate"></a>Erreur System.ArgumentNullException lors de l’exécution d’une opération sur SAP  
 **Problème**  
  
 L’adaptateur renvoie l’erreur suivante lors de l’exécution de toute opération sur le système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
```  
System.ArgumentNullException: Value cannot be null.  
```  
  
 **Cause**  
  
 L’action WCF pour le message n’est pas spécifiée. WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.  
  
 **Résolution**  
  
 Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk. Pour obtenir des instructions, consultez [configurer l’action SOAP pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md). Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) pour afficher la liste des actions pour chaque opération.  
  
##  <a name="BKMK_SAPXmlParsing"></a>XmlReaderParsingException en raison d’un fonctionnement incorrect dans l’action spécifiée  
 **Problème**  
  
 La Console Administration de BizTalk Server attribue l’erreur suivante lors de l’envoi de messages à un système SAP :  
  
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
  
 Dans le format ci-dessus, le nom de l’opération est régi par l’opération que vous avez choisi lors de la génération du schéma. Par exemple, si vous avez généré le schéma pour RFC_CUSTOMER_GET, le nom de l’opération dans l’action sera « RFC_CUSTOMER_GET ». Toutefois, le nom de l’opération dans le port logique créé dans l’orchestration BizTalk de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] peut être différent.  
  
 **Résolution**  
  
 Vérifiez que les noms des opérations dans les deux le port logique (dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) et le port physique (dans la Console Administration de BizTalk Server) sont les mêmes.  
  
##  <a name="BKMK_SAPHundredCons"></a>Erreur d’ouverture de plus de 100 connexions à SAP  
 **Problème**  
  
 L’adaptateur lève l’exception suivante lors de l’ouverture de plus de 100 connexions au système SAP.  
  
```  
Microsoft.ServiceModel.Channels.Common.ConnectionException: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  GWHOST=<gw_host>, GWSERV=<gw_serv>, SYSNR=<sys_number>  
LOCATION    CPIC (TCP/IP) on local host with Unicode  
ERROR       max no of 100 conversations exceeded  
```  
  
 **Cause**  
  
 Par défaut, SAP n’active pas plus de 100 connexions dans le système.  
  
 **Résolution**  
  
 Pour augmenter le nombre maximal de connexions, vous devez créer une variable d’environnement sur l’ordinateur qui a des bibliothèques clientes SAP installé et lui affecte une valeur numérique. La valeur que vous spécifiez pour cette variable d’environnement est le nombre maximal de connexions qui peuvent être effectuées dans le système SAP. Créer la variable d’environnement avec les détails suivants :  
  
-   **Nom de la variable**: CPIC_MAX_CONV  
  
-   **Valeur de la variable**: une valeur numérique positive. Par exemple, pour activer les 200 connexions dans le système SAP, spécifiez la valeur 200.  
  
 Pour obtenir des instructions sur la création d’une variable d’environnement, consultez « Comment faire pour créer les Variables système dans Windows 2000 » à [http://go.microsoft.com/fwlink/?LinkId=95020](http://go.microsoft.com/fwlink/?LinkId=95020).  
  
##  <a name="BKMK_SAPIDOCMetadata"></a>Erreur de la génération ou de la récupération des métadonnées des IDOC  
 **Problème**  
  
 Lors de la génération de métadonnées pour le **réception** opération pour un IDOC dans un système SAP, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] attribue l’erreur suivante.  
  
```  
Error while retrieving or generating the WSDL.  
Adapter message: Details: ErrorCode=RFC_EXCEPTION.  
ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage= OBJECT_UNKNOWN.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: IDOCTYPE_READ_COMPLETE.  
```  
  
 **Cause**  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise la RFC IDOCTYPE_READ_COMPLETE pour récupérer les métadonnées pour le **réception** opération pour un IDOC. Appel de ce document RFC requiert des autorisations d’utilisateur spécifique dans le système SAP. Pour générer des métadonnées, si vous êtes connecté au système SAP à l’aide des informations d’identification qui ne sont pas autorisé à appeler la RFC IDOCTYPE_READ_COMPLETE, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère une erreur.  
  
 **Résolution**  
  
 Connectez-vous à l’interface utilisateur graphique SAP à l’aide de ces mêmes informations que vous aviez utilisé pour la carte. Accédez à la transaction SE37 et entrez le nom de la RFC à exécuter en tant que IDOCTYPE_READ_COMPLETE.  
  
 Pour les paramètres d’entrée PI_IDOCTYP et PI_CIMTYP, entrez les valeurs correspondant à l’IDoc personnalisé. Pour les paramètres PI_VERSION et PI_RELEASE, entrez les mêmes valeurs comme étant choisi dans l’interface de métadonnées d’adaptateur. Puis, appuyez sur F8 à exécuter.  
  
 Vous devez obtenir la même exception que ce que l’adaptateur reçoit, avec plus d’informations sur le problème.  
  
 Si vous êtes toujours pas en mesure de résoudre le problème, générer un schéma pour le **ReceiveIdoc** opération au lieu du **réception** opération. Dans ce cas, l’adaptateur SAP n’utilise pas IDOCTYPE_READ_COMPLETE et ne lève pas d’erreur.  
  
##  <a name="BKMK_SAPIDOCReceive"></a>Erreur envoyer ou recevoir des IDOC qui ont non commerciales des segments  
 **Problème**  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] donne une XmlReaderParsingException lors de l’envoi des IDOC (à l’aide de **envoyer** opération) ou de recevoir des IDOC (à l’aide de **réception** opération) qui ont non commerciales des segments.  
  
 **Cause**  
  
 IDOC sont constitués de segments. Lors de la génération de métadonnées, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère tous les segments publiées qui sont présents dans le système SAP. Toutefois, lorsque l’adaptateur utilise les métadonnées pour effectuer une opération telle que la réception d’un IDOC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] donne une XmlReaderParsingException. Cela se produit, car lorsque l’IDOC est reçu, le système SAP peut envoyé certains segments non commercialisés, les métadonnées pour ce qui n’a pas été générée par l’adaptateur.  
  
 **Résolution**  
  
 Effectuez l’une des opérations suivantes :  
  
-   Mettre à niveau votre système SAP en appliquant les correctifs appropriés pour les segments non commercialisés.  
  
-   Utilisez **SendIdoc** ou **ReceiveIdoc** operations pour envoyer et recevoir des IDOC respectivement. Pour plus d’informations sur ces opérations, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
##  <a name="BKMK_SAPIDOCSend"></a>Erreur d’envoi de fichier plat IDOC à SAP qui ont été reçus à l’aide de la FilePort SAP  
 **Problème**  
  
 Si vous essayez d’envoyer (à l’aide de **envoyer** opération) un IDOC de fichier plat à un système SAP qui a été généré à l’aide d’un FilePort SAP, l’Analyseur de fichier plat dans l’orchestration BizTalk ne peut pas convertir le fichier flatf dans un format XML, ce qui échouent le IDOD **envoyer** opération.  
  
 **Cause**  
  
 Lorsque le système SAP génère un IDOC à l’aide d’un FilePort, il supprime les désactiver tous les espaces à la fin d’un segment vides. Toutefois, l’Analyseur de fichier plat attend que les données du dernier champ du segment doivent être présents pour convertir le format de fichier plat au format XML. Étant donné que les espaces vides ne sont pas présents dans le segment, l’Analyseur de fichier plat ne parvient pas à analyser le fichier plat au format XML.  
  
 **Résolution**  
  
 Pour ce type IDOC de fichier plat générés à l’aide de le FilePort de SAP, utilisez le **SendIdoc** opération à la place. Pour plus d’informations sur cette opération, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
##  <a name="BKMK_SAPRecIDOCCompat"></a>Erreur de réception IDOC de SAP si EnableBizTalkCompatibilityMode est définie sur true  
 **Problème**  
  
 L’exception suivante est rencontrée lors de la réception d’un IDOC avec la **EnableBizTalkCompatibilityMode** jeu de propriétés de liaison à la valeur true :  
  
```  
System.Exception: Loading property information list by namespace failed or property not found in the list. Verify that the schema is deployed properly.  
```  
  
 **Cause**  
  
 Si la propriété de liaison **EnableBizTalkCompatibilityMode** a la valeur **true**, vous devez ajouter le fichier DLL du schéma de propriété BizTalk pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en tant que ressource dans votre application BizTalk, autrement dit, le application dans laquelle votre projet est déployé.  
  
 **Résolution**  
  
 Le nom du schéma de propriété BizTalk pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*. Il est installé par le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation sous \<lecteur d’installation > : \ Programme Files\Microsoft BizTalk adaptateur Pack\bin. Procédez comme suit pour ajouter cet assembly en tant que ressource dans votre application BizTalk.  
  
#### <a name="add-an-assembly-as-a-resource-in-biztalk-application"></a>Ajouter un assembly en tant que ressource dans l’application BizTalk  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, développez **Applications**et puis l’application à laquelle vous souhaitez ajouter un assembly BizTalk.  
  
3.  Développez **Applications** et l’application à laquelle vous souhaitez ajouter un assembly BizTalk.  
  
4.  Avec le bouton droit **ressources**, pointez sur **ajouter**, puis cliquez sur **assemblys BizTalk**.  
  
5.  Cliquez sur **ajouter**, accédez au dossier contenant le fichier d’assembly BizTalk, sélectionnez le fichier d’assembly BizTalk, puis cliquez sur **ouvrir**.  
  
6.  Dans **Options**, spécifiez les options d’installation de l’assembly BizTalk dans le GAC, puis cliquez sur **OK**.  
  
##  <a name="BKMK_SAPIDOCValidate"></a>Erreur de validation lors de la réception des IDOC à partir d’un système SAP  
 **Problème**  
  
 Un IDOC reçu à partir d’un système SAP échoue à la validation avec une erreur semblable au suivant :  
  
```  
There was a failure executing the receive pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=<token>"  
Source: "Pipeline " Receive Port: "ReceiveIdoc" URI: "<connection uri>"  
Reason: The document failed to validate because of the following error:  
"The 'http://Microsoft.LobServices.Sap/2007/03/Types/Idoc/3/CREMAS03//620:TAXBS' element has an invalid value according to its data type."  
```  
  
 **Cause**  
  
 Les métadonnées générées pour la réception d’un IDOC contient les valeurs possibles qui peuvent être reçus d’une colonne particulière dans le cadre de l’opération de réception. Ces valeurs sont exposées en tant qu’énumération dans les métadonnées générées. Toutefois, lorsque l’IDOC est reçu, la valeur reçue peut être différente de valeurs énumérées. Par conséquent, l’opération de réception échoue lors de la validation des valeurs. Par exemple, l’erreur ci-dessus, validation de message échoue pour la colonne TAXBS.  
  
 **Résolution**  
  
 Vous devez modifier manuellement l’énumération dans le schéma (pour les projets BizTalk) ou le proxy client (pour les projets .NET à l’aide de WCF de modèle de service) pour inclure la valeur reçue à partir du système SAP.  
  
##  <a name="BKMK_SAPFFIDOC"></a>Format de fichier plat IDOC, avant et après la conversion en XML, ne sont pas identiques  
 **Problème**  
  
 Si vous utilisez un analyseur de fichier plat pour convertir un IDOC de fichier plat en utilisant le schéma XML, puis convertir le code XML vers un fichier plat IDOC via un pipeline à l’aide du schéma, les deux IDOC de fichier plat ne sont pas identiques.  
  
 **Cause**  
  
 Lorsque vous générez le code XML à partir d’un fichier plat IDOC, l’Analyseur de fichier plat ne génère pas les nœuds XML avec des valeurs vides. Lorsque ce code XML est converti en un format de fichier plat, les nœuds manquants à partir du XML ne sont pas répercutées dans le format de fichier plat IDOC. Par conséquent, les format de fichier plat IDOC ne sont pas identiques.  
  
 **Résolution**  
  
 Dans le schéma utilisé pour convertir le format de fichier plat en XML et vice versa, dans la définition du nœud « Envoi » ou « Réception », procédez comme suit :  
  
1.  Définir le **suppress_empty_nodes** propriété **false** et définir le **generate_empty_nodes** propriété **true**. Par défaut, le **suppress_empty_nodes** est définie sur **true** et **generate_empty_nodes** est définie sur **false**, et Par conséquent, tous les nœuds vides ne sont pas répercutées dans le document XML.  
  
2.  Le format de fichier plat peut contenir un retour chariot supplémentaire à la fin. Vous pouvez définir le **suppress_trailing_delimiters** propriété **Oui** afin d’éviter ce retour de chariot supplémentaire. Cette propriété est également exposée en tant que le **supprimer les délimiteurs** si vous ouvrez le schéma de propriété [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
##  <a name="BKMK_SAPAction"></a>Erreur d’Action incorrecte à l’aide d’un port physique création d’un fichier de liaison  
 **Problème**  
  
 Après avoir utilisé le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour une opération spécifique sur le système SAP, le complément crée également un fichier de liaison de port. Vous pouvez importer ce fichier à l’aide de la liaison la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports physiques dans BizTalk Server. Toutefois, lorsque vous envoyez des messages au système SAP à l’aide de ces ports, l’adaptateur ne parvient pas à comprendre l’action spécifiée sur le port et génère une erreur semblable au suivant :  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **Cause**  
  
 Lorsque vous créez des ports logiques dans une orchestration BizTalk, vous spécifiez certains noms pour les opérations sur ces ports ou vous utilisez simplement les noms par défaut comme Operation_1, Operation_2, etc.. Toutefois, dans le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le nom de l’opération est identique au nom de l’opération pour laquelle générer des métadonnées. Par exemple, si vous générez des métadonnées pour RFC_CUSTOMER_GET, l’action est fixée à ce qui suit :  
  
```  
<Operation Name="RFC_CUSTOMER_GET" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
```  
  
 Lorsque vous importez le fichier de liaison, la même action est définie sur le port physique. Par conséquent, les noms de l’opération sur le port logique (Operation_1, Operation_2, etc.) ne correspondent pas les noms de l’opération spécifiées dans l’action sur le port physique, ce qui entraîne une erreur.  
  
 **Résolution**  
  
 Assurez-vous que le nom de l’opération dans le port logique est la même que le nom d’opération spécifié dans le cadre de l’action dans le port physique. Procédez de l'une des manières suivantes :  
  
-   Modifier le nom de l’opération dans le port logique dans le Concepteur d’orchestration BizTalk à partir de Operation_1, etc. à l’opération pour laquelle générer des métadonnées, par exemple RFC_CUSTOMER_GET.  
  
-   Modifier le nom de l’opération dans l’action sur le port physique pour le nom de l’opération dans le port logique. Par exemple, vous pouvez modifier l’action dans le port physique pour ressembler à ceci :  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
    ```  
  
##  <a name="BKMK_SAPTableParams"></a>Le message de réponse pour une opération s’exécutait sur SAP ne contient pas tous les paramètres table  
 **Cause**  
  
 Si vous utilisez le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour exécuter une opération sur le système SAP, qui retourne un grand nombre de tables, et chaque table possède un grand nombre d’enregistrements, qui s’élève à un dataset volumineux en tant que partie du message de réponse retourné à partir du système SAP. C’est le cas, par défaut, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne retourne pas les paramètres de la table en tant que partie du message de réponse.  
  
 **Résolution**  
  
 Vous pouvez demander les tables que vous souhaitez [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à retourner dans le cadre de la réponse. Vous pouvez le faire en fournissant un paramètre table vide en tant que partie du message de demande que vous envoyez au système SAP. Par exemple, `<table_parameter_name />`.  
  
##  <a name="BKMK_SAPIncorrectCreds"></a>Les Clients de l’adaptateur ne reçoivent pas de la réponse à partir de SAP
 **Problème**  
  
 Lorsque vous utilisez les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], si les informations d’identification sur WCF-custom envoie de port sont incorrectes, les messages de demande ne sont pas traités. Après avoir spécifié les informations d’identification correctes, le message est envoyé au système SAP et une réponse est reçue. Toutefois, le message de réponse n’est pas disponible pour le port de sortie.  
  
 **Résolution**  
  
 Redémarrez l’instance d’hôte BizTalk.  
  
##  <a name="BKMK_SAPInboundConn"></a>Problèmes de connectivité de la réception d’un message entrant à partir du serveur SAP  
 **Problème**  
  
 Vous obtenez l’erreur suivante uniquement lors de la réception d’un message entrant à partir du serveur SAP à l’aide de WCF-Custom port de réception pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
```  
The Messaging Engine failed to add a receive location "<location_name>" with URL "<connection URI>" to the adapter "WCF-Custom".  
Reason: "Microsoft.Adapters.SAP.RFCException: Details: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  TPNAME=<name>, GWHOST=<host>, GWSERV=<server>  
```  
  
 Toutefois, vous êtes correctement capable d’envoyer des messages au système SAP à l’aide de WCF-Custom port d’envoi.  
  
 **Résolution**  
  
 Installez l’interface utilisateur graphique SAP sur le même ordinateur où vous exécutez le client de carte et essayez de recevoir le message entrant à nouveau. Pour plus d’informations sur l’installation de l’interface GUI SAP, reportez-vous à la documentation de SAP.  
  
##  <a name="BKMK_SAPRootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk  
 **Problème**  
  
 Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Résolution**  
  
1.  Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.  
  
2.  Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).  
  
##  <a name="BKMK_SAPVS2008"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio  
 **Problème**  
  
 Lorsque vous utilisez l’adaptateur pour créer une application dans Visual Studio et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :  
  
```  
The element 'bindings' has invalid child element 'sapBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 Cet avertissement s’affiche, car le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] de liaison, `sapBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ignorer cet avertissement sans problème.  
  
##  <a name="BKMK_SAPSimilarSchema"></a>Exception XLANG dans BizTalk Server
 **Problème**  
  
 BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.  
  
 **Cause**  
  
 Cela se produit en raison de le des manières suivantes :  
  
-   Vous avez généré plus d’un schéma d’une opération générique (par exemple, SendIdoc et ReceiveIdoc) dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour effectuer des opérations respectives sur un système SAP. Étant donné que les schémas sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.  
  
-   En cas de plusieurs projets, vous avez généré un schéma générique opération pour chacun des projets BizTalk Server, déployé chaque projet séparément de l’application BizTalk Server sur le même hôte et puis exécuté une application ou applications d’exécuter respectifs opérations sur un système SAP. Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.  
  
 **Résolution**  
  
 Utiliser un fichier de schéma d’opération générique unique pour une application BizTalk Server. Si vous avez besoin d’utiliser un schéma d’opération générique dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un schéma de la seule opération générique et ensuite utiliser le schéma d’opération générique à partir de toutes les autres applications dans BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)