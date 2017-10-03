---
title: "Principales fonctionnalités de l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- features, operations-related
- adapters, new and deprecated features
- features, technology-related
- features, new and deprecated
- features, performance-related
- features, metadata-related
ms.assetid: 7e79714c-1472-4721-a693-5be2a9a0cd1f
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4277c5d0691d44bdae26b6b395a91d2ecb8f093
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="key-features-in-biztalk-adapter-for-oracle-database"></a>Principales fonctionnalités de l’adaptateur BizTalk pour base de données Oracle
Cette section répertorie les fonctionnalités nouvelles et déconseillées dans [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  

  
## <a name="technology-related-features"></a>Fonctionnalités liées à la technologie  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Nouvelle façon de se connecter à la base de données Oracle|En dehors de la connexion à la base de données Oracle à l’aide du nom de service réseau dans le fichier tnsnames.ora (comme dans la version précédente de l’adaptateur), l’adaptateur de clients peuvent désormais également se connecter à la base de données Oracle directement en spécifiant les paramètres de la connexion et par conséquent en éliminant la nécessité d’utiliser un nom de service réseau ou le fichier tnsnames.ora. Le fichier tnsnames.ora pour se connecter à la base de données Oracle ne nécessitant ne pas permet d’éviter de vous soucier de mettre à jour manuellement les paramètres de connexion (nom de service réseau) dans le fichier tnsnames.ora sur chaque ordinateur client lorsque vous ajoutez ou mettez à jour les serveurs Oracle dans votre environnement. Pour plus d’informations, consultez [créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md).|  
|Prise en charge pour l’authentification Windows|Les clients de l’adaptateur peuvent utiliser l’authentification Windows pour se connecter à la base de données Oracle. L’authentification Windows vous permet de déterminer l’identité de l’utilisateur basée sur les informations d’identification d’ouverture de session de Windows et ainsi vous aide à tirer parti de la sécurité intégrée de l’environnement Windows. Pour plus d’informations sur l’authentification Windows dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [se connecter à la base de données Oracle à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).|  
  
## <a name="operations-related-features"></a>Liées aux opérations de fonctionnalités 
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Prise en charge de la spécification de valeurs de ligne dans l’opération d’insertion|Vous pouvez utiliser la **InlineValue** attribut dans l’opération d’insertion pour insérer des valeurs calculées dans les tables ou vues dans la base de données Oracle. Ceci est un attribut facultatif et n’est disponible pour tous les enregistrements de données simple dans une opération d’insertion plusieurs enregistrement. Si vous spécifiez une valeur pour cet attribut, elle remplace la valeur spécifiée d’un enregistrement. Pour plus d’informations sur l’attribut InlineValue, consultez [Insert, Update, Delete et sélectionnez les opérations sur les Tables Oracle et des vues](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-and-select-operations-on-oracle-tables-and-views.md).|  
|Interrogation améliorée|Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend désormais en charge le message « reposant sur l’interrogation » modification de données à l’aide de procédures stockées, fonctions, ou les procédures ou fonctions interrogent régulièrement la base de données Oracle. Maintenant en plus de l’instruction SELECT, vous pouvez spécifier une procédure stockée, fonction ou procédure empaquetée ou fonctionner comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour interroger la base de données Oracle. Pour plus d’informations sur l’interrogation, consultez [prise en charge des Messages de modification de données basés sur la réception d’interrogation](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md).|  
|Prise en charge pour Oracle les Types définis par l’utilisateur (UDT)|Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge l’exécution d’opérations sur les artefacts dans la base de données Oracle qui contiennent les types UDT Oracle. Pour plus d’informations sur la prise en charge des UDT, consultez [prend en charge pour les Types de Oracle User-Defined dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/support-for-oracle-user-defined-types-in-oracle-database.md).|  
|Prise en charge des opérations composites|Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux clients d’adaptateur effectuer des opérations composites sur la base de données Oracle. Une opération composite peut inclure plusieurs des opérations suivantes et dans n’importe quel ordre :<br /><br /> -Les opérations sur les tables et les vues.<br />-Procédures, fonctions et des procédures stockées ou fonctions dans des packages qui sont signalées en tant qu’opérations dans l’adaptateur.<br /><br /> Pour plus d’informations sur des opérations composites, consultez [schéma de Message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).|  
|Prise en charge pour l’exécution des procédures stockées dans les schémas n’appartenant ne pas à l’utilisateur|Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet de vous permettent d’exécuter des procédures stockées dans un schéma, même si l’utilisateur actuel n’est pas le propriétaire du schéma, à condition que l’utilisateur dispose des autorisations sur le schéma dans Oracle. Toutefois, si la procédure stockée utilise des types d’enregistrements, elles doivent être définies dans le même schéma que la procédure stockée. Pour plus d’informations sur l’exécution de procédures stockées à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [opérations sur les fonctions et procédures stockées](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md).|  
|Prise en charge des notifications de modification de base de données|Les clients de carte peuvent recevoir des notifications de modification de base de données à partir de la base de données Oracle basé sur une instruction SELECT de déclenchement. La notification est envoyée par la base de données Oracle pour les clients de la carte en tant qu’et lorsque le jeu de résultats pour que les modifications de l’instruction SELECT. Pour plus d’informations sur les notifications de modification de base de données, consultez [considérations relatives à la réception des Notifications de modification de base de données](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).|  
|Prise en charge des synonymes|Les clients de carte peuvent effectuer des opérations sur les synonymes créés pour les tables, vues, procédures stockées, fonctions et des packages. Pour plus d’informations sur les synonymes, et comment vous pouvez utiliser la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour effectuer des opérations sur les synonymes, consultez [opérations sur les synonymes dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-synonyms-in-oracle-database.md).|  
|Prise en charge des paramètres booléens et les types de tables PL/SQL|Les clients de l’adaptateur peuvent effectuer des opérations dans les procédures stockées et les fonctions qui contiennent des paramètres booléens et type de table PL/SQL.|  
  
### <a name="other-features"></a>Autres fonctionnalités  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Nouvelle façon d’utiliser l’adaptateur dans BizTalk Server|Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-OracleDB dans BizTalk. Si vous souhaitez utiliser le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la console Administration de BizTalk Server, car le port WCF-Custom est ajouté à la console Administration de BizTalk Server par défaut. Toutefois, si vous souhaitez utiliser le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] via un port WCF-OracleDB, vous devez d’abord ajouter l’adaptateur WCF-OracleDB à la console Administration de BizTalk Server. Pour plus d’informations, consultez [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).|  
  
## <a name="deprecated-features-in-the-oracle-adapter"></a>Fonctionnalités déconseillées dans l’adaptateur Oracle  
 Le tableau suivant répertorie la fonctionnalité sont déconseillées dans la version actuelle de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Propriétés de liaison|Le **PollingRetryCount**, **TransactionIsolationLevel**, et **LongDataTypeColumnSize** propriétés de liaison sont déconseillées. <br/><br/>**Remarque** pour définir le niveau d’isolation de transaction pour les opérations entrantes, vous devez définir la valeur appropriée en ajoutant le comportement de service lors de la configuration du port de réception. Pour obtenir des instructions sur la façon de définir le niveau d’isolation de transaction, consultez [configurer au niveau d’Isolation de Transaction et le délai d’attente de Transaction](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).|  
  
## <a name="changes-to-note"></a>Modifications de noter

### <a name="general"></a>Général  
* Pour les paramètres de type dans les REF CURSOR

    -   Si aucune modification de la valeur de REF CURSOR à l’intérieur de la procédure stockée s’est produite, la valeur de la sortie est identique à la valeur de l’entrée REF CURSOR.  
  
    -   Les données d’entrée et de sortie dans le REF CURSOR sont du même type.  
  
-   Un comportement incorrect de l’attribut « nil » : pour tous les types de données simple, si vous définissez la valeur de l’attribut nil sur « true », et une valeur pour le champ ou le paramètre est présente puis l’adaptateur de base de données Oracle passe de manière incorrecte la valeur spécifiée au lieu de NULL. Pour résoudre ce problème, si vous souhaitez passer la valeur NULL pour un champ ou un paramètre, vous devez vous assurer qu’aucune valeur pour le champ ou le paramètre n’est spécifié. Par exemple, pour passer la valeur NULL pour un champ nommé « name » :  
  
    ```  
    <name xsi:nil="true"/>  
    ```  
-   Réel, Float, durée pendant laquelle les types de données et des zéros supplémentaires (0) à la fin de la valeur du jeu de résultats de l’opération Select ne sont pas tronqués. En outre, le jeu de résultats de l’opération Select toujours retourne une valeur avec précision 8 pour réel, Float et Long les types de données.  
  
-   Gestion des données pour les types d’enregistrements : la valeur passée pour ces nœuds dépendant de la valeur de la **SkipNilNodes** propriété de liaison. Pour plus d’informations sur cette propriété de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md). 
  
-   Opérations sortantes : aucune valeur n’est envoyée pour les paramètres qui n’ont pas une valeur spécifiée dans le fichier XML d’entrée. Si une valeur par défaut est spécifiée dans la procédure stockée, la base de données Oracle utilise cette valeur, car aucune valeur n’a été envoyée par l’adaptateur. Si une valeur NULL doit être envoyé, l’utilisateur doit spécifier un nœud de valeur NULL dans le fichier XML d’entrée en définissant la valeur d’attribut « nil » sur « true ».  
  
-   Délai de commande est prise en charge.  
  
-   L’opération de UpdateLOB doit être effectuée dans le cadre d’une transaction. Pour garantir cela, la valeur de la **UseAmbientTransaction** liaison de la propriété doit être définie sur **True**.  
  
### <a name="biztalk-scenario"></a>Scénario de BizTalk  
  
-   Opérations sortantes : si le **UseAmbientTransaction** liaison de la propriété est « True », les opérations sur la base de données Oracle et sur la BizTalk MessageBox, base de données sont effectuées dans la même transaction distribuée. Pour plus d’informations sur les transactions dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [gèrent les Transactions avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md).  
  
-   Opérations entrantes : vous ne pouvez pas utiliser une requête-réponse port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour les opérations entrantes à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Unidirectionnel uniquement recevoir des ports peuvent être utilisés.  
  
### <a name="other-scenarios"></a>Autres scénarios  
  
-   Opérations sortantes : l’adaptateur ne lance pas une transaction. Si l’utilisateur veut plusieurs lignes à insérer dans la même transaction, il est responsable de l’utilisateur pour exécuter l’opération dans une étendue de Transaction System.Transactions. L’utilisateur doit également définir la valeur de la **UseAmbientTransaction** propriété **True**. Pour plus d’informations sur les transactions dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [gèrent les Transactions avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md).  
  
-   Opérations sortantes : SSL pour les opérations sur le même objet IRequestChannel/proxy ne peuvent pas être effectuées sur la même connexion physique à la base de données Oracle.  
  
-   Modèle de canal WCF : Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge IReplyChannel lors de l’utilisation du modèle de canal WCF. Toutefois, vous pouvez utiliser IInputChannel pour effectuer les opérations entrantes. En outre, en ce qui concerne les transactions, l’adaptateur s’appuie sur la transaction de répartiteur WCF initiée pour exécuter l’instruction d’interrogation et de valider l’instruction de sondage sur la base de données Oracle. Le niveau d’isolation de transaction et le délai d’expiration de la transaction de répartiteur WCF initié peuvent être contrôlés en définissant les valeurs appropriées dans le ServiceBehavior.  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur Biztalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)