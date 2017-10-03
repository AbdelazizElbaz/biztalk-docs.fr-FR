---
title: "Configurer un port à l’aide de l’adaptateur WCF-SAP dans BizTalk | Documents Microsoft"
description: "Créer un port de SAP de WCF pour envoyer ou recevoir des messages à partir de SAP à l’aide de l’adaptateur mySAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 420683f8-2516-4c65-895d-fe535824d450
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 967ad68fb32cb8787ae02d4e6fe878c5bb78da2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-sap-adapter"></a>Configurer un port à l’aide de l’adaptateur WCF-SAP
Cette rubrique fournit des instructions sur la configuration WCF SAP d’envoi et ports de réception pour effectuer des opérations entrantes et sortantes sur le système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## <a name="deploy-adapters-to-send-messages-to-sap"></a>Déployer des adaptateurs pour envoyer des messages à SAP  
Complète les étapes suivantes pour configurer un SAP de WCF un port d’envoi pour envoyer des messages à l’aide de système SAP le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
4.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
5.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre BizTalk Server et le système SAP.  
  
6.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
7.  À partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SAP que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
8.  Dans la boîte de dialogue Propriétés du transport, procédez comme suit :  
  
    1.  Cliquez sur le **général** , cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) pour obtenir la liste des actions pour chaque opération. Par exemple, l’action à appeler le RFC_CUSTOMER_GET serait :  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    3.  Cliquez sur le **liaison** onglet et spécifier des valeurs pour la liaison des propriétés exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
        > [!NOTE]
        >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les opérations associées à des messages de propriétés de liaison ne sont pas disponibles lors de la configuration d’un port d’envoi, car les opérations entrantes nécessitent une configuration de port de réception.  
  
    4.  Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système SAP.  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application d’authentification unique associée.  
  
         Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).  
  
         Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
9. À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
10. Si vous avez choisi de créer un **Port d’envoi unidirectionnel statique** à l’étape 5, spécifiez un pipeline d’envoi. À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
11. Si vous avez choisi de créer un **Port statique avec sollicitation-réponse** à l’étape 5, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
    2.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.  
  
12. Cliquez sur **OK**.  
  
## <a name="deploy-adapters-to-receive-messages-from-sap"></a>Déployer des adaptateurs pour recevoir des messages à partir de SAP  
Complète les étapes suivantes pour configurer un SAP de WCF port de réception pour recevoir des messages de système SAP à l’aide du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
4.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
5.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse** en fonction de la mode de communication entre BizTalk Server et le système SAP.  
  
6.  Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.  
  
7.  Sur le **emplacements de réception** , cliquez sur **nouveau**. Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.  
  
8.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :  
  
    1.  Spécifiez un nom pour l’emplacement de réception.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SAP que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
9. Dans la boîte de dialogue Propriétés du transport, procédez comme suit :  
  
    1.  Cliquez sur le **général** , cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
    2.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
        > [!NOTE]
        >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les opérations associées à des messages de propriétés de liaison ne sont pas disponibles lors de la configuration d’un port d’envoi, car les opérations entrantes nécessitent une configuration de port de réception.  
  
    3.  Cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur**et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système SAP.  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application associée.  
  
         Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).  
  
         Cliquez sur **OK** pour revenir à la **propriétés de l’emplacement de réception** boîte de dialogue.  
  
10. À partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
11. Si vous avez choisi de créer **Port de réception unidirectionnel** à l’étape 5, spécifiez un pipeline de réception. À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.  
  
12. Si vous avez choisi de créer **Receive Port requête-réponse** à l’étape 5, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.  
  
    2.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
13. Cliquez sur **OK** dans les **propriétés de l’emplacement de réception** boîte de dialogue.  
  
14. Cliquez sur **OK** dans les **propriétés du Port de réception** boîte de dialogue.

## <a name="see-also"></a>Voir aussi
[Configurer manuellement une liaison de port physique à l’adaptateur SAP](manually-configure-a-physical-port-binding-to-the-sap-adapter.md)