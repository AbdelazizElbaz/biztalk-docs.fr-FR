---
title: "Configurer l’authentification dans les informations d’identification de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c20e177-0e64-4df3-a3dd-dca3fcf314db
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f07a3840524988e5f643ca89799b7c7f23ff0fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-sql-adapter"></a>Configurer l’authentification dans les informations d’identification de l’adaptateur SQL
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] demande que les clients de l’adaptateur fournir des informations d’identification du client. L’adaptateur utilise ces informations d’identification pour authentifier l’utilisateur avec SQL Server et pour établir une connexion.  
  
 Les clients de l’adaptateur peuvent fournir au client les informations d’identification lors de l’utilisation [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et lorsque vous utilisez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Lorsque vous utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], informations d’identification sont requises pour générer des métadonnées. Lorsque vous utilisez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, les informations d’identification sont requises pour effectuer des opérations sur SQL Server.  
  
 Cette section fournit des informations sur la spécification des informations d’identification du client dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="enter-credentials-from-visual-studio"></a>Entrez les informations d’identification à partir de Visual Studio  
 À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous pouvez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
### <a name="using-consume-adapter-service-add-in"></a>À l’aide de Consume Adapter Service Add-in  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **sqlBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste, effectuez l’une des opérations suivantes :  
  
    > [!NOTE]
    >  Si vous vous connectez à SQL Server à l’aide de l’authentification Windows, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    |Cliquez sur ce bouton|Pour effectuer cette opération|  
    |----------------|----------------|  
    |**Aucun**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Windows**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Nom d’utilisateur**|Spécifier le nom d’utilisateur et le mot de passe pour vous connecter à SQL Server en spécifiant des informations d’identification pour un utilisateur défini dans une base de données SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse. **Remarque :** si vous laissez le **nom d’utilisateur** et **mot de passe** champs, l’adaptateur se connecte à SQL Server à l’aide de l’authentification Windows.|  
  
6.  Cliquez sur **OK**.  
  
### <a name="using-add-adapter-metadata-wizard"></a>À l’aide d’Assistant Ajout d’adaptateur métadonnées  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
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
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **sqlBinding**, puis cliquez sur **configurer**.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste, effectuez l’une des opérations suivantes :  
  
    > [!NOTE]
    >  Si vous vous connectez à SQL Server à l’aide de l’authentification Windows, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    |Cliquez sur ce bouton|Pour effectuer cette opération|  
    |----------------|----------------|  
    |**Aucun**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Windows**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Nom d’utilisateur**|Spécifier le nom d’utilisateur et le mot de passe pour vous connecter à SQL Server en spécifiant des informations d’identification pour un utilisateur défini dans une base de données SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse. **Remarque :** si vous laissez le **nom d’utilisateur** et **mot de passe** champs, l’adaptateur se connecte à SQL Server à l’aide de l’authentification Windows.|  
  
8.  Cliquez sur **OK**.  
  
## <a name="enter-credentials-from-the-biztalk-server-administration-console"></a>Entrez les informations d’identification à partir de la Console Administration de BizTalk Server  
 À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez spécifier les informations d’identification dans le cadre de la configuration du port WCF-Custom ou WCF-SQL.  
  
### <a name="enter-credentials-for-the-wcf-custom-port"></a>Entrez les informations d’identification pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Si vous créez un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
5.  Si vous créez un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez le **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
6.  Cliquez sur **OK**.  
  
### <a name="enter-credentials-for-the-wcf-sql-port"></a>Entrez les informations d’identification pour le port WCF-SQL  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SQL que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Si vous créez un port d’envoi dans la boîte de dialogue des propriétés de transport, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
6.  Si vous créez un port de réception dans la boîte de dialogue des propriétés de transport, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
        > [!NOTE]
        >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    -   Sélectionnez le **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)