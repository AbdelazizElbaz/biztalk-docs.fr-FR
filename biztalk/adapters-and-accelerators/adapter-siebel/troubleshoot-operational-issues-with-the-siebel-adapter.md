---
title: "Résoudre les problèmes opérationnels avec l’adaptateur Siebel dans BizTalk | Documents Microsoft"
description: "Problèmes courants et des solutions pour l’adaptateur Siebel dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d152d9-9893-4f93-894a-350bae8be7bd
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a7fd507b301d20d84680cb626953d21b8a6e201
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="troubleshoot-operational-issues-with-the-siebel-adapter"></a>Résoudre les problèmes opérationnels avec l’adaptateur Siebel
Cette section fournit un emplacement centralisé pour plus d’informations sur les problèmes opérationnels, vous pouvez rencontrer en utilisant le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## <a name="enabling-tracing"></a>L’activation du traçage  
 Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md).  
  
## <a name="known-issues"></a>Problèmes connus  
 Voici certains problèmes et les solutions recommandées que vous pouvez rencontrer lors de l’utilisation du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
  
###  <a name="BKMK_SiebelBindingError"></a>Erreur lors du chargement des liaisons de l’adaptateur  
 **Problème**  
  
 Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], l’interface graphique utilisateur attribue l’erreur suivante :  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 Lorsque vous démarrez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF charge les liaisons de l’adaptateur pour tous les adaptateurs installés. À son tour, les liaisons de l’adaptateur sont dépendants sur le logiciel client d’application spécifiques de l’entreprise. Par conséquent, vous pourriez être confronté ce problème pour les raisons suivantes :  
  
-   Le logiciel client LOB requis n’est pas installé sur l’ordinateur où vous avez installé l’adaptateur.  
  
-   Vous avez effectué une installation « Standard » ou « Terminé » de l’adaptateur, qui installe tous les adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Toutefois, les bibliothèques clientes peuvent être installés pour seulement une application d’entreprise. Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.  
  
 **Résolution**  
  
-   Assurez-vous que les versions de client requises sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
-   Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.  
  
###  <a name="BKMK_SiebelDispAdap"></a>L’adaptateur Siebel n’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server  
 **Problème**  
  
 Contrairement à la version antérieure des adaptateurs livrés avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournie avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des adaptateurs dans la console Administration de BizTalk Server.  
  
 **Cause**  
  
 La dernière version [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est une liaison WCF personnalisée. Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ajouter explicitement le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_SiebelConnecting"></a>Erreur lors de la connexion au système Siebel  
 **Problème**  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] attribue l’erreur suivante lorsque vous essayez de vous connecter au système Siebel :  
  
```  
Connecting to the system LOB has failed. Retrieving the COM class factory for component with CLSID {ID} failed due to the following error: 80040154  
```  
  
 **Cause**  
  
 Le client Siebel Web ne peut pas être installé sur l’ordinateur.  
  
 **Résolution**  
  
 Assurez-vous que la version prise en charge du client Siebel Web est installée sur l’ordinateur. Consultez le guide d’installation de clients pris en charge et les versions de serveur pour Siebel. Le guide d’installation est disponible à l’adresse \<lecteur système > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
  
###  <a name="BKMK_SiebelXMLRetrieve"></a>Erreur lors de la récupération XMLs avec plus de 65 536 nœuds  
 **Problème**  
  
 L’adaptateur attribue l’erreur suivante lors de la récupération de sortie XML qui a plus de 65 536 nœuds.  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **Cause**  
  
 L’adaptateur ne peut pas sérialiser et désérialiser un objet avec des éléments de plus de 65 536.  
  
 **Résolution**  
  
 Vous pouvez résoudre ce problème en définissant le `maxItemsInObjectGraph` paramètre. Vous pouvez le définir dans un des deux manières suivantes :  
  
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
  
 Un exemple app.config doit ressembler à :  
  
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
      <endpoint   behaviorConfiguration="NewBehavior" binding="siebelBinding"  
       contract="IOutboundContract" name="siebel_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_SiebelConnURI"></a>Erreur lors de la spécification d’un URI de connexion pour un port personnalisé WCF dans BizTalk Server  
 **Problème**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]attribue l’erreur suivante lorsque vous spécifiez un URI de connexion pour se connecter au système Siebel.  
  
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
  
###  <a name="BKMK_SiebelPerfOps"></a>Erreur lors de l’opération sur le système Siebel  
 **Problème**  
  
 L’adaptateur attribue l’erreur suivante lors de l’exécution de toute opération sur le système Siebel en utilisant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Pour[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **Cause**  
  
 L’action WCF pour le message n’est pas spécifiée. WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.  
  
 **Résolution**  
  
 Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk. Pour obtenir des instructions, consultez [configurer l’action SOAP pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md). Consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) pour obtenir la liste des actions pour chaque opération.  
  
###  <a name="BKMK_SiebelXmlParsing"></a>XmlReaderParsingException en raison d’un nom d’opération incorrecte dans l’action spécifiée  
 **Problème**  
  
 La console Administration de BizTalk Server attribue l’erreur suivante lors de l’envoi de messages à un système Siebel :  
  
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
  
 Dans le format précédent, le nom de l’opération est régi par l’opération que vous avez choisi lors de la génération du schéma. Par exemple, si vous avez généré le schéma pour une opération de requête sur un composant d’entreprise Siebel, le nom de l’opération dans l’action sera « Requête ». Toutefois, le nom de l’opération dans le port logique créé dans l’orchestration BizTalk de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] peut être différent.  
  
 **Résolution**  
  
 Vérifiez que les noms des opérations dans les deux le port logique (dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) et le port physique (dans la console Administration de BizTalk Server) sont les mêmes.  
  
###  <a name="BKMK_SiebelTerminate"></a>Application à l’aide de l’adaptateur Siebel n’arrête pas  
 **Problème**  
  
 Une application qui utilise le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Siebel 7.5 version du client n’arrête pas.  
  
 **Cause**  
  
 Cela est dû à un problème de client Siebel où le processus ne se termine pas lorsque la déconnexion d’un serveur Siebel.  
  
 **Résolution**  
  
 Assurez-vous que vous disposez du correctif 7.5.3.17 installé pour le serveur Siebel, ainsi que la correction rapide QF0H05.  
  
###  <a name="BKMK_SiebelHang"></a>L’adaptateur Siebel peut se bloquer si le redémarrage du serveur Siebel  
 **Problème**  
  
 Si le serveur Siebel est redémarré pendant la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] envoie un message à l’utilisation de serveur Siebel, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut se bloquer.  
  
 **Résolution**  
  
 Redémarrez l’instance d’hôte BizTalk application. Pour le faire à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, dans l’arborescence de la console, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**. Dans le volet droit, cliquez sur le nom d’hôte, puis sélectionnez **redémarrer**.  
  
###  <a name="BKMK_SiebelAction"></a>L’adaptateur ne reconnaît pas l’action sur le port physique, même si le fichier de liaison généré par le complément Consume Adapter Service vous permet de créer les ports  
 **Problème**  
  
 Après avoir utilisé le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour une opération spécifique sur le système Siebel, le complément crée également un fichier de liaison de port. Vous pouvez importer ce fichier à l’aide de la liaison la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports physiques dans BizTalk Server. Toutefois, lorsque vous envoyez des messages au système Siebel à l’aide de ces ports, l’adaptateur ne parvient pas à comprendre l’action spécifiée sur le port et génère une erreur semblable au suivant :  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **Cause**  
  
 Lorsque vous créez des ports logiques dans une orchestration BizTalk, vous spécifiez certains noms pour les opérations sur ces ports ou vous utilisez simplement les noms par défaut comme Operation_1, Operation_2, etc. Toutefois, dans le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le nom de l’opération est identique au nom de l’opération pour laquelle générer des métadonnées. Par exemple, si vous générez des métadonnées pour l’opération d’insertion sur le composant de gestion de compte, l’action est fixée à ce qui suit :  
  
```  
<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
```  
  
 Lorsque vous importez le fichier de liaison, la même action est définie sur le port physique. Par conséquent, les noms de l’opération sur le port logique (Operation_1, Operation_2, etc.) ne correspondent pas les noms de l’opération spécifiées dans l’action sur le port physique, ce qui entraîne une erreur.  
  
 **Résolution**  
  
 Assurez-vous que le nom de l’opération dans le port logique est la même que le nom d’opération spécifié dans le cadre de l’action dans le port physique. Procédez de l'une des manières suivantes :  
  
-   Modifier le nom de l’opération dans le port logique dans le Concepteur d’orchestration BizTalk à partir de Operation_1, etc. à l’opération pour laquelle générer des métadonnées, par exemple, Insert.  
  
-   Modifier le nom de l’opération dans l’action sur le port physique pour le nom de l’opération dans le port logique. Par exemple, vous pouvez modifier l’action dans le port physique pour ressembler à ceci :  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
    ```  
  
###  <a name="BKMK_SiebelXMLEncode"></a>L’adaptateur Siebel ne gère pas les objets Siebel avec des chaînes XML encodé dans le nom  
 **Problème**  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne peut pas effectuer des opérations impliquant des objets Siebel (des objets métier, des composants d’entreprise, services d’entreprise, liste de choix, méthodes, champs, arguments, etc.) qui ont des chaînes XML encodé dans leur nom. Par exemple, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne sera pas en mesure d’appeler une méthode de service d’entreprise avec le nom Time_x0020_Stamp.  
  
 **Résolution**  
  
 Assurez-vous que les objets Siebel ne contiennent pas de chaînes XML encodé dans leur nom.  
  
###  <a name="BKMK_SiebelRootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk  
 **Problème**  
  
 Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Résolution**  
  
1.  Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.  
  
2.  Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).  
  
###  <a name="BKMK_SiebelVS2008"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio  
 **Problème**  
  
 Lorsque vous utilisez l’adaptateur pour créer une application dans Visual Studio et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :  
  
```  
The element 'bindings' has invalid child element 'siebelBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 Cet avertissement s’affiche, car le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] de liaison, `siebelBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ignorer cet avertissement sans problème.  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)