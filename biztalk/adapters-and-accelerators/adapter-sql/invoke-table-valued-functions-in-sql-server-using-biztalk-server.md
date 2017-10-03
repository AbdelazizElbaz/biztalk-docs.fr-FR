---
title: "Appeler des fonctions table dans SQL Server à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d360c15-699e-4859-8143-798c1de821db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24713b4df4064c788651b0b34397a58c110b0d65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-table-valued-functions-in-sql-server-using-biztalk-server"></a>Appeler des fonctions table dans SQL Server à l’aide de BizTalk Server
Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler des fonctions table dans SQL Server. L’adaptateur expose les fonctions table en tant qu’opérations qui peuvent être appelées directement sur le serveur SQL Server. Pour plus d’informations sur la façon dont l’adaptateur prend en charge les fonctions table, consultez [Executing Table-Valued des fonctions dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md). Pour plus d’informations sur la structure du message SOAP pour appeler des fonctions table, consultez [des schémas de Message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Créer un [clé de nom fort du fichier et découvrez les outils](prerequisites-to-create-sql-applications-using-the-sql-adapter.md)
  
-   [Configurer MSDTC](configure-msdtc-on-sql-server-and-adapter-client.md) sur les ordinateurs exécutant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et SQL Server.
  
## <a name="invoke-table-valued-functions-on-a-sql-server-database"></a>Appeler des fonctions table dans une base de données SQL Server  
 Une opération sur une base de données SQL Server à l’aide de [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour appeler des fonctions table dans SQL Server, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour la fonction table que vous souhaitez appeler dans SQL Server.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de SQL Server.  
  
3.  Créez une orchestration pour appeler l’opération sur SQL Server.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generate-schema"></a>Générer un schéma  
 Cette rubrique montre comment appeler des fonctions table dans SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour illustrer cette opération, dans cette rubrique, vous exécutez la fonction TVF_EMPLOYEE. Cette fonction prend la désignation d’un employé en tant que paramètre et retourne tous les enregistrements d’employés avec cette désignation, un type de table. La table Employee et la fonction sont créées en exécutant les scripts fournis avec les exemples. Pour plus d’informations sur le script, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
 Pour illustrer comment appeler des fonctions table, le schéma est généré pour la fonction table TVF_EMPLOYEE. Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer des schémas.  
  
## <a name="define-messages-and-message-types"></a>Définir les Messages et le Message Types  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, du type défini par le schéma correspondant. Maintenant, créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *TableFunctions.TableValuedFunction_dbo. TVF_EMPLOYEE*, où TableFunctions est le nom de votre projet BizTalk. TableValuedFunction_dbo est le schéma généré pour la fonction TVF_EMPLOYEE.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *TableFunctions.TableValuedFunction_dbo. TVF_EMPLOYEEResponse*.|  
  
## <a name="set-up-the-orchestration"></a>Configurer l’Orchestration  
 Créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer une opération sur SQL Server. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consomme ce message et le transmet à SQL Server. La réponse à partir de SQL Server est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des messages à SQL Server et de recevoir des réponses, respectivement. Un exemple d’orchestration permettant d’appeler une fonction table ressemble à ceci :  
  
 ![Orchestration permettant d’appeler une table &#45; la fonction table](../../adapters-and-accelerators/adapter-sql/media/28ca3930-7ce8-423a-9edd-cb2888eebaac.gif "28ca3930-7ce8-423a-9edd-cb2888eebaac")  
  
### <a name="add-message-shapes"></a>Ajouter des formes de Message  
 Entrez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="add-ports"></a>Ajouter des Ports  
 Entrez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="enter-messages-for-action-shapes-and-connect-them-to-ports"></a>Entrez les Messages de formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.TVF.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.TVF.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.TVF.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.TVF.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés, et l’orchestration est terminée.  
  
 Maintenant, générez la solution BizTalk et déployez-le sur BizTalk Server. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configure-the-biztalk-application"></a>Configurer l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md). 
 
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données SQL Server.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SQL physique pour envoyer des messages à la base de données SQL Server. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
## <a name="start-the-application"></a>Démarrer l’Application  
 Démarrez l’application BizTalk pour appeler des fonctions table dans la base de données SQL Server. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SQL pour envoyer des messages à la base de données SQL Server est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="execute-the-operation"></a>Exécuter l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour la fonction de table TVF_EMPLOYEE que vous avez généré précédemment. Par exemple, le message de demande pour appeler la fonction TVF_EMPLOYEE est la suivante :  
  
```  
<TVF_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/dbo">  
  <emp_desig>Tester</emp_desig>  
</TVF_EMPLOYEE>  
```  
  
 Ce message de demande appelle la fonction TVF_EMPLOYEE pour récupérer les enregistrements d’employés à la désignation en tant que « Testeur ». Consultez [des schémas de Message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md) pour plus d’informations sur le schéma de message de demande pour l’appel de fonctions table dans SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
> [!NOTE]
>  Si vous ne spécifiez pas une valeur pour le paramètre de l’adaptateur s’exécute en interne la fonction en utilisant le mot clé par défaut, ce qui signifie que l’adaptateur s’exécute la fonction en passant la valeur par défaut pour le paramètre, si elle est disponible dans le cadre de la définition de fonction.  
  
 L’orchestration consomme le message et l’envoie à la base de données SQL Server. La réponse à partir de la base de données SQL Server est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données SQL Server pour le précédent message de demande est la suivante :  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<TVF_EMPLOYEEResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/dbo">  
  <TVF_EMPLOYEEResult>  
    <TVF_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/TableFunctionReturnTables/dbo">  
      <Employee_ID>10499</Employee_ID>   
      <Name>John</Name>   
      <Designation>Tester</Designation>   
      <Salary>999999.00</Salary>   
      <Last_Modified>AAAAAAAAJBM=</Last_Modified>   
    </TVF_EMPLOYEE>  
    <TVF_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/TableFunctionReturnTables/dbo">  
      ......  
      ......  
    </TVF_EMPLOYEE>  
    ......  
    ......  
  </TVF_EMPLOYEEResult>  
</TVF_EMPLOYEEResponse>  
```  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)