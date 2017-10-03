---
title: "Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Création d’envoi WCF-custom et ports de réception pour utiliser l’adaptateur SQL Server dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d44d9932-0a5e-4072-a480-2f8dc544ca79
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c2a47cf267bd3316600ad68a241a204090f3da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter"></a>Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SQL
Étapes de configuration d’envoi WCF-Custom et de ports de réception pour effectuer des opérations de trafic entrantes et sortantes sur SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx). 
  
## <a name="deploy-adapters-to-send-messages-to-sql-server"></a>Déployer des adaptateurs pour envoyer des messages à SQL Server  
 Procédez comme suit pour configurer un port d’envoi WCF-Custom pour envoyer des messages à l’aide de SQL Server le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.    
 
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
4.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis pointez sur le type de port que vous souhaitez configurer en fonction du mode de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et SQL Server.  
  
5.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
6.  À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour SQL Server. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) pour obtenir la liste des actions pour chaque opération. Par exemple, l’action à appeler l’opération d’insertion sur une table dans une base de données SQL Server est :  
  
        ```  
        TableOp/Insert/dbo/Employee  
        ```  
  
        > [!NOTE]
        >  Employé est le nom d’une table de base de données SQL Server.  
  
    3.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** liste, sélectionnez **sqlBinding**. Vous pouvez spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
    4.  Cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
            > [!NOTE]
            >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
        -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
             Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).  
  
    5.  Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
8.  À partir de la **Gestionnaire d’envoi** liste, sélectionnez **BizTalkServerApplication**.  
  
9. Si vous avez choisi **Port d’envoi unidirectionnel statique** à l’étape 4, spécifiez un pipeline d’envoi. À partir de la **pipeline d’envoi** , sélectionnez le pipeline qui correspond à XMLTransmit.  
  
10. Si vous avez choisi **Port statique avec sollicitation-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.  
  
    2.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline qui correspond à XMLReceive.  
  
11. Cliquez sur **OK**.  
  
## <a name="deploy-adapters-to-receive-messages-from-sql-server"></a>Déployer des adaptateurs pour recevoir des messages à partir de SQL Server
 Effectuez les tâches suivantes étapes de configuration WCF-Custom port de réception pour recevoir des messages à partir de SQL Server à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
4.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse**, en fonction de la mode de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et SQL Server.  
  
5.  Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.  
  
6.  Sur le **emplacements de réception** , cliquez sur **nouveau**. Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :  
  
    1.  Spécifiez un nom pour l’emplacement de réception.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour SQL Server. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
    2.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sqlBinding**. Vous pouvez spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
    3.  Cliquez sur le **comportement** onglet pour définir le niveau d’isolation de transaction. Pour plus d’informations sur la définition du niveau d’isolation de transaction, consultez [configurer Transaction Isolation Level et délai de Transaction SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
    4.  Cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez **compte d’utilisateur**et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse.  
  
            > [!NOTE]
            >  Si vous souhaitez vous connecter à SQL Server à l’aide de l’authentification Windows, spécifiez un nom d’utilisateur vide et un mot de passe. Avant cela, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
        -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
             Pour plus d’informations sur la sécurité au niveau [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).  
  
    5.  Pour revenir à la **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
9. À partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
10. Si vous avez choisi **Port de réception unidirectionnel** à l’étape 4, spécifiez un pipeline de réception. À partir de la **pipeline de réception** , sélectionnez le pipeline XMLReceive correspondant.  
  
11. Si vous avez choisi **Receive Port requête-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline qui correspond à XMLReceive.  
  
    2.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.  
  
12. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
13. Dans le **propriétés du Port de réception** boîte de dialogue, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)