---
title: "Résoudre les problèmes opérationnels avec l’adaptateur Oracle E-Business Suite | Documents Microsoft"
description: "Problèmes courants et des solutions pour l’adaptateur Oracle eBusiness Suite dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 667633e0-055a-418a-ab64-d4f6e6c7a898
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92f888c185a7c7bea800986615da04ce57c80db0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-oracle-e-business-suite-adapter"></a>Résoudre les problèmes opérationnels avec l’adaptateur Oracle E-Business Suite
Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## <a name="enabling-tracing"></a>L’activation du traçage  
 Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], [le suivi de Diagnostic et de journalisation des messages dans l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md).  
  
## <a name="known-issues"></a>Problèmes connus  
 Voici les erreurs les plus courantes que vous pouvez rencontrer en utilisant le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], ainsi que leur cause probable et de la résolution.  
  
  
  
###  <a name="BKMK_LoadBindings"></a>Erreur lors du chargement des liaisons de l’adaptateur  
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
  
-   Assurez-vous que les versions de client LOB requis sont installées sur l’ordinateur où vous avez installé le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations sur les versions de client pris en charge, consultez le guide d’installation disponible à l’adresse \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
-   Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.  
  
###  <a name="BKMK_Display"></a>L’adaptateur Oracle E-Business Suite n’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server  
 **Problème**  
  
 Contrairement à la version antérieure des adaptateurs fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des cartes dans les [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 **Cause**  
  
 La dernière version [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est une liaison WCF personnalisée. Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ajouter explicitement le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [ajouter l’adaptateur Oracle E-Business Suite à la console d’Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_MissingAction"></a>Erreur lors de l’exécution d’opérations sur Oracle E-Business Suite  
 **Problème**  
  
 L’adaptateur renvoie l’erreur suivante lors de l’exécution de toute opération sur le Oracle E-Business Suite à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Pour[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **Cause**  
  
 L’action WCF pour le message n’est pas spécifiée. WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.  
  
 **Résolution**  
  
 Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk. Pour obtenir des instructions, consultez [configurer l’action SOAP pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md). Consultez [Messages et des schémas de Message pour l’adaptateur Oracle eBusiness Suite](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md) pour afficher la liste des actions pour chaque opération.  
  
###  <a name="BKMK_WrongClient"></a>Processus BizTalk peut se bloquer en raison d’une version incorrecte du client Oracle lorsqu’un message de demande est supprimé à l’emplacement de réception  
 **Problème**  
  
 Après la suppression d’un message de demande à un emplacement de réception défini dans une orchestration BizTalk, l’orchestration consomme le message et que l’hôte BizTalk (BTSNTSvc.exe) s’arrête et redémarre.  
  
 **Cause**  
  
 L’installation du client Oracle d’ajoute la référence aux assemblys client plus récente dans la variable de chemin d’accès. En outre, les références à l’installation la plus récente de l’assembly de client Oracle précèdent la référence aux assemblys de client existant. Par conséquent, si l’installation du client Oracle plus récente n’est pas d’une version prise en charge client, l’hôte BizTalk se bloque, puis redémarre.  
  
 Par exemple, supposons que le client Oracle prises en charge 11.1.0.7 est déjà installé sur l’ordinateur et que la variable de chemin d’accès a la référence suivante :  
  
```  
C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 Si un client Oracle non pris en charge, par exemple 10.2.0.3, est installé sur le même ordinateur, la variable de chemin d’accès aura la référence suivante :  
  
```  
C:\oracle\product\10.2.0\db_2\bin;C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 Notez que la version du client non pris en charge est référencée avant la version prise en charge et par conséquent, l’hôte BizTalk tombe en panne. S’il existe plusieurs hôtes BizTalk en cours d’exécution, puis de celui hébergeant l’adaptateur se bloque.  
  
 **Résolution**  
  
 Si plusieurs clients Oracle est installé sur le même ordinateur, assurez-vous que la version du client Oracle prises en charge est référencée avant les autres versions de client Oracle dans la variable de chemin d’accès. Par exemple, si la version du client Oracle prises en charge est 11.1.0.7, la référence dans la variable de chemin d’accès doit ressembler à :  
  
```  
  
C:\oracle\product\11.1.0\client_1\bin;C:\oracle\product\10.2.0\db_2\bin;  
```  
  
###  <a name="BKMK_Overflow"></a>L’adaptateur peut lever une exception de dépassement de capacité sur l’exécution d’une opération  
 **Problème**  
  
 À l’aide de la carte, si vous essayez d’effectuer une opération qui contiennent des types de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR, l’adaptateur peut lever une exception de dépassement de capacité.  
  
 **Cause**  
  
 Cela se produit si vous fournissez une valeur élevée pour le type de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR qui ne tiennent pas dans le type .NET respectif.  
  
 **Résolution**  
  
 Si vous souhaitez passer des valeurs élevées pour le type de données numériques à l’intérieur des jeux de données ou faiblement typée REF CURSOR Oracle, vous devez activer la saisie sécurisée en définissant la valeur de la **EnableSafeTyping** liaison de propriété **true**. L’activation de la saisie sécurisée expose les type de données numériques à l’intérieur des jeux de données ou faiblement typée REF CURSOR Oracle en tant que chaînes.  
  
###  <a name="BKMK_Arithmetic"></a>L’adaptateur peut lever une exception de dépassement de capacité arithmétique sur l’exécution d’une opération ExecuteScalar  
 **Problème**  
  
 À l’aide de la carte, si vous essayez d’exécuter une instruction SELECT dans une opération ExecuteScalar qui Récupère un grand nombre, l’adaptateur lève l’exception suivante : « System.OverflowException : opération arithmétique a entraîné un dépassement de capacité. »  
  
 **Cause**  
  
 Cela se produit en raison de la limitation connue de l’opération ExecuteScalar dans ODP.NET. ODP.NET essaie d’ajuster les données dans le type de données .NET Decimal, et si le résultat est trop grand pour tenir dans le type Decimal .NET, l’exception est levée.  
  
 **Résolution**  
  
 Utilisez TO_CHAR() dans l’instruction SELECT dans l’opération ExecuteScalar pour convertir les données retournées sous forme de chaîne.  
  
###  <a name="BKMK_AppContext"></a>Client de l’adaptateur peut lever l’exception suivante sur l’exécution d’une opération : « Impossible d’extraire les id utilisateur, id de responsabilité, id de l’application.  Vérifiez si les valeurs correctes ont été passés. »  
 **Problème**  
  
 Les clients de l’adaptateur peuvent lever cette exception si vous effectuez des opérations sur les artefacts d’Oracle E-Business Suite (tables d’interface, vues de l’interface, des programmes simultanés et ensembles de requêtes).  
  
 **Cause**  
  
 Cela se produit si vous fournissez une combinaison incorrecte de nom d’utilisateur, mot de passe et nom de la responsabilité Oracle lors de l’exécution d’opérations sur les tables d’interface, vues de l’interface, des programmes simultanés et ensembles de requêtes. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] requiert ces valeurs afin de définir le contexte d’application de ces artefacts. Pour plus d’informations sur le contexte d’application de paramètre, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 **Résolution**  
  
 Vous devez spécifier une combinaison correcte du nom d’utilisateur Oracle, le mot de passe et la responsabilité définition appropriée de contexte d’application pour un artefact d’Oracle E-Business Suite. Pour spécifier les valeurs de nom d’utilisateur Oracle et le mot de passe, vous devez utiliser le **OracleUserName** et **OraclePassword** propriétés de liaison. Pour spécifier la valeur de la responsabilité d’Oracle, vous pouvez utiliser la **OracleEBSResponsibilityName** propriété de contexte de message ou de la propriété de liaison.  
  
###  <a name="BKMK_RootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk  
 **Problème**  
  
 Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Résolution**  
  
1.  Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.  
  
2.  Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).  
  
###  <a name="BKMK_InvalidBinding"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio  
 **Problème**  
  
 Lorsque vous utilisez l’adaptateur pour créer une application dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :  
  
```  
The element 'bindings' has invalid child element 'oracleEBSBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 Cet avertissement s’affiche, car le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] de liaison, `oracleEBSBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ignorer cet avertissement sans problème.  
  
###  <a name="BKMK_Notify"></a>BizTalk Server lève une exception si vous utilisez plusieurs schémas de Notification dans la même application ou le schéma de Notification entre plusieurs applications sur le même hôte  
 **Problème**  
  
 BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.  
  
 **Cause**  
  
 Cela se produit en raison de le des manières suivantes :  
  
-   Vous avez généré plus d’un schéma de Notification dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour recevoir des notifications à partir de la base de données Oracle. Étant donné que les schémas de Notification sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.  
  
-   En cas de plusieurs projets, vous avez généré un schéma de Notification pour chacun des projets, déployés dans chaque projet à une application BizTalk Server distincte sur le même hôte BizTalk Server, puis exécutez une application ou les applications de recevoir des notifications à partir de la base de données Oracle. Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.  
  
 **Résolution**  
  
 Utiliser un seul fichier de schéma de Notification pour une application BizTalk Server. Si vous avez besoin d’utiliser le schéma de Notification dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un seul schéma de Notification, puis utiliser le schéma de notification à partir de toutes les autres applications dans BizTalk Server.  
  
###  <a name="BKMK_Timeout"></a>Exception de délai d’attente lors de l’exploration d’Oracle E-Business Suite artefacts dans Visual Studio  
 **Problème**  
  
 Lors de l’exploration des artefacts d’Oracle E-Business Suite dans un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] de projet à l’aide de la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] vous pouvez rencontrer une exception de délai d’attente.  
  
 **Cause**  
  
 Cela peut se produire si le serveur qui héberge le Oracle E-Business Suite est lent, serveur se trouve à un emplacement distant, ou le schéma que vous cherchez sous possède un grand nombre d’artefacts.  
  
 **Résolution**  
  
 Vous pouvez choisir d’augmenter la valeur de la **SendTimeout** propriété de liaison ou de fournir une expression de recherche dans le **recherche dans la catégorie** zone de texte afin de réduire le nombre d’artefacts que l’adaptateur récupère.  
  
 Pour plus d’informations sur la spécification des propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour plus d’informations sur la recherche d’artefacts dans Oracle E-Business Suite, consultez [Parcourir, rechercher et obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
###  <a name="BKMK_MemUsage"></a>Utilisation de la mémoire et de thread nombre augmente lors de l’utilisation de la carte dans une opération entrante  
 **Problème**  
  
 Dans une opération entrante, telles que l’interrogation, **si aucune donnée n’est disponible dans la table interrogée** et l’adaptateur continue à interroger, sur une période de temps, vous rencontrez une augmentation de l’utilisation de la mémoire et le nombre de threads.  
  
 **Cause**  
  
 **Si aucune donnée n’est disponible dans la table interrogée**, après chaque cycle de délai d’attente de réception [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] génère un nouveau thread pour poursuivre l’opération d’interrogation. Par conséquent, l’utilisation de count et de la mémoire du thread augmente sur une période de temps. Toutefois, si la table interrogée possède des données, le même thread continue à effectuer toutes les interrogations suivantes.  
  
 **Résolution**  
  
 Nous vous recommandons d’affecter le **ReceiveTimeout** à la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours) afin qu’un nouveau thread est généré uniquement 24 jours. Cela garantit que le nombre de threads et de l’utilisation de mémoire n’augmente pas trop trop tôt.  
  
 Pour plus d’informations sur la **ReceiveTimeout** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir des instructions sur la spécification des propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).  
  
> [!NOTE]
>  Lors de l’utilisation de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], définir le délai d’attente pour une valeur élevée n’affecte pas les fonctionnalités de la carte.  
  
## <a name="see-also"></a>Voir aussi  
[Dépannage de l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)