---
title: "Exécuter des procédures stockées avec un seul paramètre XML dans SQL Server à l’aide de BizTalk Server | Documents Microsoft"
description: "Passer d’un seul paramètre dans une procédure stockée à l’aide de port personnalisé WCF et l’adaptateur SQL dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: deb9333a-5e28-4e8d-8e0b-07b5a97a111b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02c5f239300140022b1d26f35664add744b630c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="execute-stored-procedures-with-a-single-xml-parameter-in-sql-server-using-biztalk-server"></a>Exécuter des procédures stockées avec un seul paramètre XML dans SQL Server à l’aide de BizTalk Server
L’exécution d’une procédure stockée qui accepte un seul paramètre est similaire à l’exécution d’une autre procédure stockée comme décrit dans [exécuter les procédures stockées de SQL Server à l’aide de BizTalk Server](execute-stored-procedures-in-sql-server-using-biztalk-server.md). Toutefois, pour l’approche décrite dans le lien précédent, vous devez générer des métadonnées pour la procédure stockée au moment du design et créer une orchestration pour appeler la procédure en cours d’exécution.  
  
 Considérez un scénario dans lequel vous souhaitez simplement passer une valeur unique à une procédure stockée sans effectuer tout traitement de cette valeur. Dans ce cas, vous ne souhaitez pas la charge de la génération des métadonnées, création d’une orchestration, le déploiement de l’orchestration et l’exécution de l’opération. Au lieu de cela, vous pouvez configurer un port d’envoi WCF-SQL ou de WCF-Custom pour appeler directement la procédure stockée. Cette rubrique montre comment effectuer ces tâches à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!NOTE]
>  Cette rubrique fournit des instructions sur la configuration WCF-Custom d’envoi port pour l’exécution de procédure stockée qui accepte un seul paramètre. Vous pouvez effectuer les mêmes étapes en configurant un port WCF-SQL. Pour obtenir des instructions sur la configuration du port WCF-SQL, consultez [configurer un Port à l’aide de l’adaptateur WCF-SQL](configure-a-port-using-the-wcf-sql-adapter.md).  
  
## <a name="invoke-stored-procedures-without-orchestration"></a>Appeler des procédures stockées sans orchestration  
 Pour illustrer comment exécuter des procédures stockées avec paramètres uniques sans une orchestration, cette rubrique utilise la procédure stockée de ADD_LAST_EMP_XML_INFO. Cette procédure prend une valeur XML en tant que paramètre et l’insère dans le **adresse** colonne de la **employé** table. Vous devez disposer de la valeur XML que vous allez passer à la procédure stockée. Toutefois, pour exécuter la procédure stockée à l’aide de l’adaptateur, vous devez envoyer un message de demande conformes au schéma de la procédure, et que la valeur contenant le code XML pour le **adresse** au champ, le serveur SQL Server. Par conséquent, vous devez créer ce message de demande par :  
  
-   À l’aide de la **modèle** option dans la configuration de port d’envoi à l’aide de laquelle vous pouvez créer un message de demande à l’aide d’un modèle de message.  
  
-   Placer le code XML de valeur pour le **adresse** champ dans le message.  
  
 Toutes ces étapes sont décrites en détail dans cette rubrique. Vous devez effectuer l’ensemble suivant de tâches :  
  
1.  Créer un fichier de réception du port sur lequel vous allez déposer le fichier XML qui sera inséré dans le **adresse** champ XML de la **employé** table. Supposons que ce port est appelé **(messagein)** port.  
  
2.  Créer un port d’envoi unidirectionnel WCF-Custom que récupère le code XML du fichier à partir du fichier port de réception et construit le message en utilisant le modèle de message et il envoie à SQL Server pour exécuter la procédure stockée.  
  
 Cette partie de la rubrique fournit des instructions sur la configuration WCF-Custom port d’envoi avec le modèle de message.  
  
> [!NOTE]
>  Bien que les informations contenues dans cette rubrique montre comment exécuter une procédure stockée avec un paramètre XML unique, vous pouvez effectuer les tâches pour effectuer toute opération qui accepte un seul paramètre de n’importe quel type de données. La seule différence se trouve dans la procédure de que création d’un modèle de message pour une opération spécifique. Vous pouvez créer un modèle de message en prenant le message de demande que vous utilisez pour exécuter l’opération de corps du message à l’aide d’une orchestration et en remplaçant la valeur du paramètre par BizTalk.  
  
##  <a name="BKMK_OneWay"></a>Configurer un port d’envoi WCF-Custom  
 Avant de créer le WCF-Custom port d’envoi, vérifiez que vous avez créé le fichier de port de réception **(messagein)**.  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
4.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis pointez sur **Port d’envoi unidirectionnel statique**.  
  
5.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
6.  Configurer le port pour recevoir tout port de réception de messages déposés au niveau du fichier **(messagein)**.  
  
    1.  Dans le **propriétés de Port d’envoi** boîte de dialogue, dans le volet gauche, cliquez sur **filtres**.  
  
    2.  Dans le volet droit, sous la **propriété** colonne, cliquez sur la grille, puis sélectionnez **BTS. ReceivePortName** propriété.  
  
    3.  Pour le **opérateur** colonne, sélectionnez «**==**».  
  
    4.  Pour le **valeur** colonne, spécifiez le nom du fichier de port de réception, `MessageIn`.  
  
7.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** onglet, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **Configurer**.  
  
8.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour SQL Server. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) pour obtenir la liste des actions pour chaque opération. Par exemple, l’action à appeler le ADD_LAST_EMP_XML_INFO est :  
  
        ```  
        Procedure/dbo/ADD_LAST_EMP_XML_INFO  
        ```  
  
    3.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** liste, sélectionnez **sqlBinding**. Vous pouvez spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
    4.  Cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
            > [!NOTE]
            >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe.  
  
        -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
             Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).
  
    5.  Cliquez sur le **Messages** onglet et dans le **le corps du message WCF sortant** , choisissez le **modèle** option.  
  
    6.  Dans le **XML** texte, spécifiez le modèle qui servira à construire le message WCF. En procédant ainsi, vous créez un message qui est conforme à l’opération ADD_LAST_EMP_XML_INFO pour la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
         ![Spécifiez le modèle de message WCF sortant](../../adapters-and-accelerators/adapter-sql/media/012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55.gif "012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55")  
  
         Pour la procédure stockée de ADD_LAST_EMP_XML_INFO, vous devez spécifier le modèle suivant :  
  
        ```  
        <ADD_LAST_EMP_XML_INFO xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
        <xml_info>  
        <bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/>  
        </xml_info>  
        </ADD_LAST_EMP_XML_INFO>  
        ```  
  
        > [!IMPORTANT]
        >  L’encodage dans le modèle de message doit être toujours « string », quel que soit le type du paramètre pour l’opération qui sera appelé à l’aide du port d’envoi. Par exemple, le ADD_LAST_EMP_XML_INFO prend un paramètre de type XML, mais le codage dans le modèle de message est chaîne.  
  
        > [!NOTE]
        >  Vous pouvez créer ce modèle de message en copiant le message de demande pour la procédure stockée et en remplaçant la valeur dans les balises < xml_info > par le corps du message BizTalk. Vous pouvez obtenir le message de demande pour la procédure stockée en générant le schéma pour la procédure à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], puis de générer une instance du schéma pour obtenir la requête XML.  
  
    7.  Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
9. À partir de la **Gestionnaire d’envoi** liste, sélectionnez **BizTalkServerApplication**.  
  
10. À partir de la **pipeline d’envoi** , sélectionnez le pipeline qui correspond à **PassThruTransmit**.  
  
11. Cliquez sur **OK**.  
  
## <a name="start-the-application"></a>Démarrer l’Application  
 Pour démarrer l’application BizTalk, vous pouvez démarrer le fichier de l’emplacement de réception et le port d’envoi WCF-Custom individuellement. Vous devez maintenant l’emplacement de réception copie un fichier XML dans le dossier mappé au fichier. L’application BizTalk utilise le fichier, et la valeur XML est insérée dans la colonne adresse de la table Employee. Vous pouvez le vérifier à l’aide d’un client SQL Server et de sélectionner des enregistrements à partir de la table Employee.  
  
## <a name="using-a-two-way-wcf-custom-send-port"></a>À l’aide d’un Port d’envoi WCF-Custom bidirectionnel  
 Les instructions fournies dans cette rubrique, dans la section [comment configurer un Port d’envoi WCF-Custom](../../core/how-to-configure-a-wcf-custom-send-port.md), montrent comment configurer un port d’envoi unidirectionnel WCF-Custom pour exécuter une procédure stockée avec un seul paramètre sans l’aide de BizTalk orchestration. Toutefois, dans ce cas, pour vérifier si la procédure stockée est exécutée avec succès avoir à vérifier dans la base de données SQL Server, si la colonne adresse dans la table Employee est mis à jour.  
  
 Au lieu de cela, vous pouvez créer un port d’envoi WCF-Custom bidirectionnel qui obtient également la réponse à partir de SQL Server, si la procédure stockée est exécutée avec succès. Vous devez effectuer quelques étapes supplémentaires si vous créez un port personnalisé WCF bidirectionnel. Notez que vous devez toujours un fichier emplacement de réception, comme indiqué dans les instructions précédentes.  
  
1.  Créer un port d’envoi WCF-Custom bidirectionnels, par exemple, **ExecProcedure**. Les étapes pour configurer le port d’envoi sont semblables à celles du port d’envoi unidirectionnel. La seule différence est que pour le port bidirectionnel vous devez également spécifier un pipeline de réception. Veillez à sélectionner **PassThruReceive** pour le pipeline de réception.  
  
2.  Créer un port d’envoi FILE. Ce port supprimera le message de réponse à partir de la base de données SQL Server dans un dossier. À l’aide de la **filtres** onglet de la boîte de dialogue Propriétés du port, configurez le port d’envoi FILE pour recevoir tous les messages de réponse à partir du port d’envoi WCF-Custom.  
  
    1.  Dans le **propriétés de Port d’envoi** boîte de dialogue, dans le volet gauche, cliquez sur **filtres**.  
  
    2.  Dans le volet droit, sous la **propriété** colonne, cliquez sur la grille, puis sélectionnez **BTS. SPName** propriété.  
  
    3.  Pour le **opérateur** colonne, sélectionnez «**==**».  
  
    4.  Pour le **valeur** colonne, spécifiez le nom de WCF-Custom port d’envoi, `ExecProcedure`.  
  
 Démarrer tous les trois ports. Copie un fichier XML dans le dossier mappé au fichier emplacement de réception. Recherchez la réponse dans le dossier mappé au port d’envoi de fichier.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)