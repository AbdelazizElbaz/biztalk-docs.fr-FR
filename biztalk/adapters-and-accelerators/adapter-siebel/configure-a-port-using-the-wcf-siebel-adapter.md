---
title: "Configurer un port à l’aide de l’adaptateur WCF-Siebel | Documents Microsoft"
description: "Créer des ports d’envoi WCF-Siebel pour utiliser l’adaptateur des Applications Siebel eBusiness dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6314104-c742-440c-b530-b5a82295353a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486e33b6c8f61a315548a84f145dc45824300710
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-siebel-adapter"></a>Configurer un port à l’aide de l’adaptateur WCF-Siebel
Comment configurer les ports d’envoi WCF-Siebel pour effectuer des opérations sortantes sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## <a name="deploy-adapters-for-sending-messages-to-a-siebel-system"></a>Déployer les adaptateurs d’envoi de messages à un système Siebel  
 Procédez comme suit pour configurer un port d’envoi WCF-Siebel pour envoyer des messages à un système Siebel en utilisant le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
4.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
5.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre BizTalk Server et le système Siebel.  
  
6.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
7.  À partir de la **Type** liste déroulante, sélectionnez le WCF-Siebel adaptateur vous ajouté précédemment, puis cliquez sur **configurer**.  
  
8.  Dans la boîte de dialogue Propriétés du transport, procédez comme suit :  
  
    1.  Cliquez sur le **général** , cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) pour obtenir la liste des actions pour chaque opération. Par exemple, l’action à appeler l’opération d’insertion sur le composant de gestion de compte est :  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    3.  Cliquez sur le **liaison** onglet et spécifier des valeurs pour les propriétés de liaison. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
    4.  Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.  
  
        -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.  
  
         Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).  
  
    5.  Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
9. À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
10. Si vous avez choisi de Port d’envoi unidirectionnel statique à l’étape 5, spécifiez un pipeline d’envoi. À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
11. Si vous avez choisi de Port statique avec sollicitation-réponse à l’étape 5, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
    2.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.  
  
12. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Configurer manuellement une liaison de port physique à l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)