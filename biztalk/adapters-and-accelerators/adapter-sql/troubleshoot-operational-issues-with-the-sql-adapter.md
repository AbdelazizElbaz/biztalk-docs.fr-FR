---
title: "Résoudre les problèmes opérationnels avec l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Problèmes courants et des résolutions de l’adaptateur SQL dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c75f85f4-cd03-4c6a-aac9-a6d02d3c3449
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d3febbda1799c1f002ed352caecc5d9d838db00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-sql-adapter"></a>Résoudre les problèmes opérationnels avec l’adaptateur SQL
Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].  
  
## <a name="enabling-tracing"></a>L’activation du traçage  
 Vous devez activer le traçage entre l’adaptateur, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], et SQL Server pour collecter plus d’informations sur les problèmes que vous rencontrez lors de l’utilisation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages dans l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md).  
  
## <a name="known-issues"></a>Problèmes connus  
 Voici les erreurs les plus courantes que vous pouvez rencontrer en utilisant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ainsi que leur cause probable et de la résolution.  
  
  
  
###  <a name="BKMK_SQLLoadBinding"></a>Erreur lors du chargement des liaisons de l’adaptateur  
 **Problème**  
  
 Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], vous obtenez l’erreur suivante :  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF charge les liaisons de l’adaptateur pour tous les adaptateurs installés. À son tour, les liaisons de l’adaptateur sont dépendantes du logiciel client spécifique pour l’application d’entreprise. Vous risquez de rencontrer ce problème si vous avez effectué une installation standard ou complète de la carte, qui installe tous les adaptateurs contenus dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Toutefois, les bibliothèques clientes LOB peuvent être installés pour seulement une application d’entreprise. Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.  
  
 **Résolution**  
  
 Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.  
  
###  <a name="BKMK_SQLDisplay"></a>L’adaptateur SQL ne s’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server  
 **Problème**  
  
 Contrairement à la version antérieure des adaptateurs fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des cartes dans les [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 **Cause**  
  
 La dernière version [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est une liaison WCF personnalisée. Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ajouter explicitement le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_MissingAction"></a>Erreur lors de l’exécution d’opérations sur une base de données SQL Server  
 **Problème**  
  
 L’adaptateur renvoie l’erreur suivante lorsque vous effectuez une opération sur une base de données SQL Server à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Pour[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **Cause**  
  
 L’action WCF pour le message n’est pas spécifiée. WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.  
  
 **Résolution**  
  
 Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk. Pour obtenir des instructions, consultez [configurer l’action SOAP pour l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md). Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) pour afficher la liste des actions pour chaque opération.  
  
###  <a name="BKMK_SQLInvalidOp"></a>Exception InvalidOperationException avec le code d’erreur = 5 lors de l’exécution des opérations FILESTREAM  
 **Problème**  
  
 Vous obtenez l’erreur suivante lors de l’utilisation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer des opérations FILESTREAM.  
  
```  
System.InvalidOperationException: OpenSqlFileStream returned error.  
ErrorCode:5  
  
```  
  
 **Cause**  
  
 Vous avez peut-être spécifié des informations d’identification de la base de données pour se connecter à la base de données SQL Server. Pour effectuer des opérations FILESTREAM, vous devez toujours utiliser l’authentification Windows. Le code d’erreur « 5 » indique que l’accès est refusé en raison d’informations d’identification incorrectes. Pour plus d’informations sur les différents codes d’erreur, consultez [Codes d’erreurs système (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx).
  
 **Résolution**  
  
 Utiliser l’authentification Windows pour se connecter à la base de données SQL Server. Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez le faire en laissant l’utilisateur les champs nom et mot de passe vide dans la boîte de dialogue de configuration port WCF-Custom ou WCF-SQL.  
  
###  <a name="BKMK_SQLPolling"></a>Interrogation d’opération ne retourne pas les messages même si les instructions valides sont spécifiées pour PollingStatement et PolledDataAvailableStatement  
 **Problème**  
  
 Même si les valeurs valides sont spécifiées pour les propriétés de liaison PollingStatement et PolledDataAvailableStatement, l’adaptateur ne reçoit pas un message d’interrogation de SQL Server.  
  
 **Cause**  
  
 Vérifiez si une autre transaction a pris un verrou sur la table de l’interrogation de l’adaptateur.  
  
 **Résolution**  
  
 Si vous souhaitez interroger une table qui est mis à jour dans le cadre d’une autre transaction, vous pouvez envisager d’utiliser le paramètre « avec (nolock) » dans le cadre de la requête spécifiée pour la propriété de liaison PolledDataAvailableStatement pour vous assurer que les données sont retournées même si un verrou est imposé par l’autre transaction. Pour plus d’informations, consultez [verrouillage SQL dans le moteur de base de données](https://msdn.microsoft.com/library/ms190615.aspx).
  
###  <a name="BKMK_SQLSingleOp"></a>L’adaptateur ne parvient pas à insérer, mettre à jour ou supprimer des volumes importants de données en une seule opération à l’aide de BizTalk Server  
 **Problème**  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne parvient pas à insérer, mettre à jour ou supprimer des volumes importants de données dans une seule opération à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 **Cause**  
  
 Insertion, mise à jour ou suppression des volumes importants de données peut prendre un temps et le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ou la transaction dans laquelle l’opération est effectuée, peut expirer.  
  
 **Résolution**  
  
-   **Pour[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    1.  Spécifiez le délai d’attente pour l’adaptateur WCF dans le fichier machine.config. Accédez au fichier machine.config sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG et ajouter l’extrait de code qui ressemble à ceci.  
  
        ```  
        <configuration>  
         \<system.transactions>  
          <machineSettings maxTimeout="02:00:00" />  
         \</system.transactions>  
        </configuration>  
        ```  
  
         Avec ce paramètre, le délai d’attente de l’adaptateur WCF est définie à 2 heures.  
  
    2.  Spécifiez les paramètres de délai d’attente pour les transactions MSDTC dans le fichier machine.config. Accédez au fichier machine.config sous \<lecteur système > : \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG et ajouter l’extrait de code qui ressemble à ceci.  
  
        ```  
        \<system.transactions>   
                <defaultSettings distributedTransactionManagerName="<computer_name>" timeout="02:00:00"/>   
            \</system.transactions>  
  
        ```  
  
         Avec ce paramètre, le délai d’attente MSDTC est définie à 2 heures. La valeur par défaut pour le délai d’attente MSDTC est 10 minutes.  
  
        > [!IMPORTANT]
        >  Vous devez effectuer cette modification sur les ordinateurs exécutant le client de l’adaptateur et le SQL Server. Dans l’extrait de code, remplacez < nom_ordinateur > par le nom de l’ordinateur exécutant le client de l’adaptateur et le SQL Server.  
  
    3.  Définir le **SendTimeout** liaison de propriété pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à une valeur relativement élevée. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
###  <a name="BKMK_SQLFullSchemaValidate"></a>Échec de la validation de schéma complet dans BizTalk Server pour les messages de réponse qui contient le jeu de données  
 **Problème**  
  
 Pour les opérations qui retournent un message de réponse contenant un jeu de données, par exemple ExecuteReader, la validation de schéma complet échoue dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 **Résolution**  
  
 Nous vous recommandons de ne pas une validation de schéma complet pour les messages de réponse qui contient un jeu de données. Au lieu de cela, vous pouvez procédez comme suit :  
  
1.  Exécuter l’opération une fois qui retourne le message de réponse avec le schéma.  
  
2.  Copiez le schéma à partir du message de réponse dans un fichier .xsd et de l’ajouter à votre projet BizTalk.  
  
3.  Utiliser une requête xpath dans votre orchestration pour extraire les données à partir du message de réponse.  
  
###  <a name="BKMK_SQLRootNode"></a>Erreur avec RootNode TypeName dans les projets BizTalk  
 **Problème**  
  
 Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Résolution**  
  
1.  Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.  
  
2.  Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).  
  
###  <a name="BKMK_SQLMetadataStronglyTyped"></a>Adaptateur ne peut pas générer des métadonnées de fortement typée de procédure stockée avec des tables temporaires  
 **Problème**  
  
 L’adaptateur ne parvient pas à générer des métadonnées pour les procédures stockées fortement typée qui incluent des tables temporaires dans leur définition. L’adaptateur permet à l’exception suivante.  
  
```  
Microsoft.ServiceModel.Channels.Common.MetadataException:  
Retrieval of Operation Metadata has failed while building WSDL at 'TypedProcedure/<schema>/<stored_procedure_name>' --->  
System.Data.SqlClient.SqlException: Invalid object name '<temp_table_name>'.  
  
```  
  
 **Résolution**  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge générer des métadonnées pour les procédures stockées fortement typées qui contiennent des tables temporaires dans leur définition. Au lieu de cela, vous devez générer les métadonnées de la même procédure sous la **procédures** nœud lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
###  <a name="BKMK_SQLVS2008"></a>Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio  
 **Problème**  
  
 Lorsque vous utilisez l’adaptateur pour créer une application dans [!INCLUDE[vs2010](../../includes/vs2010-md.md)] et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :  
  
```  
The element 'bindings' has invalid child element 'sqlBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 Cet avertissement s’affiche, car le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] de liaison, `sqlBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Résolution**  
  
 Vous pouvez ignorer cet avertissement sans problème.  
  
###  <a name="BKMK_SQLNotification"></a>BizTalk Server lève une exception si vous utilisez plusieurs schémas de Notification dans la même application ou le schéma de Notification entre plusieurs applications sur le même hôte  
 **Problème**  
  
 BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.  
  
 **Cause**  
  
 Cela se produit en raison de le des manières suivantes :  
  
-   Vous avez généré plus d’un schéma de Notification dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour recevoir des notifications à partir de la base de données SQL Server. Étant donné que les schémas de Notification sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.  
  
-   En cas de plusieurs projets, vous avez généré un schéma de Notification pour chacun des projets, déployés dans chaque projet à une application BizTalk Server distincte sur le même hôte BizTalk Server, puis exécutez une application ou les applications de recevoir des notifications à partir de la base de données SQL Server. Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.  
  
 **Résolution**  
  
 Utiliser un seul fichier de schéma de Notification pour une application BizTalk Server. Si vous avez besoin d’utiliser le schéma de Notification dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un seul schéma de Notification, puis utiliser le schéma de notification à partir de toutes les autres applications dans BizTalk Server.  
  
###  <a name="BKMK_SQLRestoreConn"></a>Client de l’adaptateur lève une exception sur l’exécution d’une opération après la restauration de la connectivité entre le client de carte et de la base de données SQL Server  
 **Problème**  
  
 Client de l’adaptateur lève l’exception suivante sur l’exécution d’une opération sur la base de données SQL Server :  
  
```  
{System.Data.Common.DbException} = {"A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.)"}  
```  
  
 **Cause**  
  
 Pendant l’exécution d’une opération, l’adaptateur utilise la connexion à partir du pool de connexions SQL ADO.NET pour se connecter à la base de données SQL Server et d’effectuer l’opération. S’il existe une brève interruption de réseau entre le client de carte et de la base de données SQL Server, ou si la base de données SQL Server est momentanément indisponible, toutes les connexions dans le pool de connexions SQL ADO.NET deviennent non valides. Une fois la connectivité est rétablie et que vous essayez d’effectuer une opération sur la base de données SQL Server, l’adaptateur utilise les mêmes connexions non valides à partir du pool de connexions ADO.NET de SQL, et par conséquent, le client de l’adaptateur lève l’exception.  
  
 **Résolution**  
  
 Le client de l’adaptateur doit implémenter la logique de nouvelle tentative dans leur exécution de l’opération, où qu’ils doivent intercepter l’exception et spécifier le nombre de tentatives d’opération « n + 1 », où « n » est la valeur spécifiée pour la propriété de liaison MaxConnectionPoolSize. Cela signifie que s’il existe le nombre de « n » de connexions dans le pool de connexions qui ont été rendue non valide, en théorie l’adaptateur client doit réessayer pour un maximum de « n + 1 » reprises pour obtenir une connexion valide et donc d’effectuer l’opération.  
  
 Par exemple, pour spécifier le nombre de tentatives [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], ouvrez le **propriétés** boîte de dialogue d’un port d’envoi dans une application, cliquez sur **Options avancées de Transport** dans le volet gauche de la boîte de dialogue, puis dans le **Options de transport** zone, spécifiez une valeur dans la **nombre de tentatives** liste.  
  
###  <a name="BKMK_MemUsage"></a>Utilisation de la mémoire et de thread nombre augmente lors de l’utilisation de la carte dans une opération entrante  
 **Problème**  
  
 Dans une opération entrante, telles que l’interrogation, **si aucune donnée n’est disponible dans la table interrogée** et l’adaptateur continue à interroger, sur une période de temps, vous rencontrez une augmentation de l’utilisation de la mémoire et le nombre de threads.  
  
 **Cause**  
  
 **Si aucune donnée n’est disponible dans la table interrogée**, après chaque cycle de délai d’attente de réception [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] génère un nouveau thread pour poursuivre l’opération d’interrogation. Par conséquent, l’utilisation de count et de la mémoire du thread augmente sur une période de temps. Toutefois, si la table interrogée possède des données, le même thread continue à effectuer toutes les interrogations suivantes.  
  
 **Résolution**  
  
 Nous vous recommandons d’affecter le **ReceiveTimeout** à la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours) afin qu’un nouveau thread est généré uniquement 24 jours. Cela garantit que le nombre de threads et de l’utilisation de mémoire n’augmente pas trop trop tôt.  
  
> [!NOTE]
>  Si SqlAdapterInboundTransactionBehavior a été défini, assurez-vous que le TransactionTimeout est également configuré pour la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours). Lorsque vous utilisez cette solution de contournement, nous pouvons ajouter la SqlAdapterInboundTransactionBehavior uniquement si le niveau d’isolation de transaction doit être configurée. Sinon, il est recommandé de supprimer ce comportement.  
  
 Pour plus d’informations sur la **ReceiveTimeout** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir des instructions sur la spécification des propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
> [!NOTE]
>  Lors de l’utilisation de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], définir le délai d’attente pour une valeur élevée n’affecte pas les fonctionnalités de la carte.  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)