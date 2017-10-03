---
title: "Configurer l’URI de connexion de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6460b22-48e4-4b7e-b82e-151e7dab1e09
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9959a88f9799730cb60d2b05358f226b31d0f84c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-connection-uri-for-the-sql-adapter"></a>Configurer l’URI de connexion de l’adaptateur SQL
URI de connexion est une chaîne de connexion qui contient les paramètres requis pour se connecter à SQL Server. Lors de l’utilisation du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier l’URI pour se connecter à SQL Server pour générer des métadonnées. Lors de la configuration d’un envoi ou réception à l’aide du port la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier l’URI pour se connecter à SQL Server pour effectuer des opérations.  
  
## <a name="enter-the-connection-uri-from-visual-studio"></a>Entrez l’URI de connexion à partir de Visual Studio  
 À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous pouvez spécifier l’URI de connexion à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
### <a name="use-the-consume-adapter-service-add-in"></a>Utilisez le Consume Adapter Service Add-in  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **sqlBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet. À partir de la **type d’informations d’identification du Client** liste, effectuez l’une des opérations suivantes :  
  
    > [!NOTE]
    >  Si vous vous connectez à SQL Server à l’aide de l’authentification Windows, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    |Cliquez sur ce bouton|Pour effectuer cette opération|  
    |----------------|----------------|  
    |**Aucun**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Windows**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Nom d’utilisateur**|Spécifier le nom d’utilisateur et le mot de passe pour vous connecter à SQL Server en spécifiant des informations d’identification pour un utilisateur défini dans une base de données SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse. **Remarque :** si vous laissez le **nom d’utilisateur** et **mot de passe** champs, l’adaptateur se connecte à SQL Server à l’aide de l’authentification Windows.|  
  
6.  Cliquez sur le **propriétés URI** onglet et spécifier les valeurs des paramètres différents. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
7.  Cliquez sur le **propriétés de liaison** onglet et spécifier des valeurs pour les propriétés de liaison, si elle existe, qui sont nécessaires avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
8.  Cliquez sur **OK**.  
  
### <a name="use-the-add-adapter-metadata-wizard"></a>Utilisez l’Assistant Ajouter des métadonnées de l’adaptateur  
  
1.  Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
4.  Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF-SQL**. Sélectionnez l’ordinateur sur lequel BizTalk Server est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF-SQL configuré dans BizTalk Server, sélectionnez le port à partir de la **Port** liste.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **sqlBinding**, puis cliquez sur **configurer**.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, effectuez l’une des opérations suivantes :  
  
    > [!NOTE]
    >  Si vous vous connectez à SQL Server à l’aide de l’authentification Windows, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    |Cliquez sur ce bouton|Pour effectuer cette opération|  
    |----------------|----------------|  
    |**Aucun**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Windows**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Nom d’utilisateur**|Spécifier le nom d’utilisateur et le mot de passe pour vous connecter à SQL Server en spécifiant des informations d’identification pour un utilisateur défini dans une base de données SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse. **Remarque :** si vous laissez le **nom d’utilisateur** et **mot de passe** champs, l’adaptateur se connecte à SQL Server à l’aide de l’authentification Windows.|  
  
8.  Cliquez sur le **propriétés URI** onglet et spécifiez des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
9. Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un port d’envoi WCF-SQL existant, vous ne devez pas spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
10. Cliquez sur **OK**.  
  
## <a name="enter-the-connection-uri-from-the-biztalk-server-administration-console"></a>Entrez l’URI de connexion à partir de la Console Administration de BizTalk Server  
 À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez spécifier l’URI de connexion en tant que partie de WCF-Custom ou une configuration de port WCF-SQL.  
  
### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a>Entrez l’URI de connexion pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **adresse (URI)** zone de texte, spécifiez l’URI de connexion pour se connecter à SQL Server. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
6.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet. À partir de la **Type de liaison** la liste déroulante, sélectionnez **sqlBinding**.  
  
7.  Si vous créez un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
8.  Si vous créez un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
9. Cliquez sur **OK**.  
  
### <a name="enter-the-connection-uri-for-the-wcf-sql-port"></a>Entrez l’URI de connexion pour le port WCF-SQL  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SQL que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.  
  
6.  Cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
7.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.  
  
    > [!NOTE]
    >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.  
  
8.  Si vous créez un port d’envoi dans la boîte de dialogue des propriétés de transport, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
9. Si vous créez un port de réception dans la boîte de dialogue des propriétés de transport, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)