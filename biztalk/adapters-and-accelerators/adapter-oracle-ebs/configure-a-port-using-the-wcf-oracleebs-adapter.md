---
title: "Configurer un port à l’aide de l’adaptateur WCF-OracleEBS dans BizTalk | Documents Microsoft"
description: "Utilisez l’adaptateur WCF-OracleEBS à recevoir ou envoyer des messages à partir d’Oracle eBusiness Suite dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b4c5c10-79a6-48d3-b4ee-dddf837f020b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bebd38c72164da8e3a1a0e158232999b23b02fc0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-oracleebs-adapter"></a>Configurer un port à l’aide de l’adaptateur WCF-OracleEBS
La configuration WCF-OracleEBS envoyer et recevoir des ports pour effectuer des opérations de trafic entrantes et sortantes sur Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## <a name="deploy-adapters-to-send-messages-to-oracle-ebs"></a>Déployer des adaptateurs pour envoyer des messages à Oracle eBusiness Suite 
 Procédez comme suit pour configurer un port d’envoi WCF-OracleEBS pour envoyer des messages pour Oracle E-Business Suite à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.    
 
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. [Ajout de l’adaptateur Oracle E-Business Suite à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md) répertorie les étapes.
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
4.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
5.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis pointez sur le type de port que vous souhaitez configurer en fonction du mode de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et Oracle E-Business Suite.  
  
6.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
7.  À partir de la **Type** la liste déroulante, sélectionnez WCF-OracleEBS, puis cliquez sur **configurer**.  
  
8.  Dans la boîte de dialogue Propriétés du transport, procédez comme suit :  
  
    1.  Cliquez sur le **général** , cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion, consultez [configurer l’URI de connexion pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Consultez [Messages et des schémas de Message pour l’adaptateur Oracle eBusiness Suite](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md) pour obtenir la liste des actions pour chaque opération. Par exemple, l’action à appeler l’opération d’insertion sur une table d’interface (FA_BOOKS) sous l’application de ressource est :  
  
        ```  
        InterfaceTables/Insert/OFA/FA/FA_BOOKS  
        ```  
  
    3.  Cliquez sur le **liaison** onglet et spécifier des valeurs pour les propriétés de liaison exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
        > [!NOTE]
        >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.  
  
    4.  Cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
            |Utiliser|Pour effectuer cette opération|  
            |--------------|----------------|  
            |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
            |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
            |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
            |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
        -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
    5.  Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
9. À partir de la **Gestionnaire d’envoi** liste, sélectionnez **BizTalkServerApplication**.  
  
10. Si vous avez choisi **Port d’envoi unidirectionnel statique** à l’étape 5, spécifiez un pipeline d’envoi. À partir de la **pipeline d’envoi** , sélectionnez le pipeline qui correspond à XMLTransmit.  
  
11. Si vous avez choisi **Port statique avec sollicitation-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.  
  
    2.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline qui correspond à XMLReceive.  
  
12. Cliquez sur **OK**.  
  
## <a name="deploy-adapters-to-receive-messages-from-oracle-ebs"></a>Déployer des adaptateurs pour recevoir des messages à partir d’Oracle eBusiness Suite  
 Procédez comme suit les étapes pour configurer un WCF-OracleEBS port de réception pour recevoir des messages à partir d’Oracle E-Business Suite à l’aide du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur Oracle E-Business Suite à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
4.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
5.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse**, en fonction de la mode de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et Oracle E-Business Suite.  
  
6.  Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.  
  
7.  Sur le **emplacements de réception** , cliquez sur **nouveau**. Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.  
  
8.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :  
  
    1.  Spécifiez un nom pour l’emplacement de réception.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez WCF-OracleEBS, puis cliquez sur **configurer**.  
  
9. Dans la boîte de dialogue Propriétés du transport, procédez comme suit :  
  
    1.  Cliquez sur le **général** , cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion, consultez [configurer l’URI de connexion pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  
  
    2.  Cliquez sur le **liaison** onglet et spécifier des valeurs pour la liaison des propriétés exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
        > [!NOTE]
        >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.  
  
    3.  Cliquez sur le **comportement** onglet pour définir le niveau d’isolation de transaction. Pour plus d’informations sur la définition du niveau d’isolation de transaction, consultez [configurer au niveau d’Isolation de Transaction et le délai d’attente de Transaction avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  
  
    4.  Cliquez sur le **d’autres** onglet, puis effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
            |Utiliser|Pour effectuer cette opération|  
            |--------------|----------------|  
            |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
            |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
            |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
            |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
        -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
    5.  Pour revenir à la **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
10. À partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
11. Si vous avez choisi **Port de réception unidirectionnel** à l’étape 5, spécifiez un pipeline de réception. À partir de la **pipeline de réception** , sélectionnez le pipeline XMLReceive correspondant.  
  
12. Si vous avez choisi **Receive Port requête-réponse** à l’étape 5, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline qui correspond à XMLReceive.  
  
    2.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.  
  
13. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
14. Dans le **propriétés du Port de réception** boîte de dialogue, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)   
 [Connexion à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)