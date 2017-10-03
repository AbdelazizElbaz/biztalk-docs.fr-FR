---
title: "Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur Siebel dans BizTalk | Documents Microsoft"
description: "Création d’envoi WCF-custom et ports de réception pour utiliser l’adaptateur des Applications Siebel eBusiness dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53c5ee07-36ae-474b-9241-8b53c9066ca1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 485bfaf7bd958528630e96a64ca0129a56ec330d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-siebel-adapter"></a>Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur Siebel
Cette rubrique fournit des instructions sur la configuration WCF-Custom ports d’envoi pour effectuer des opérations sortantes sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## <a name="deploying-adapters-for-sending-messages-to-a-siebel-system"></a>Déploiement des adaptateurs d’envoi de Messages à un système Siebel  
 Procédez comme suit pour configurer un port d’envoi WCF-Custom pour envoyer des messages à un système Siebel en utilisant le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
4.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre BizTalk Server et le système Siebel.  
  
5.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
6.  À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom** et cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur le **général** onglet et dans le **adresse (URI)** champ spécifier l’URI de connexion pour se connecter à un système Siebel. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) pour obtenir la liste des actions pour chaque opération. Par exemple, l’action à appeler l’opération d’insertion sur le composant de gestion de compte est :  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    3.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **siebelBinding**. Vous pouvez également spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
    4.  Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :  
  
        -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.  
  
        -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.  
  
         Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).  
  
    5.  Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
8.  À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
9. Si vous avez choisi de Port d’envoi unidirectionnel statique à l’étape 4, spécifiez un pipeline d’envoi. À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
10. Si vous avez choisi de Port statique avec sollicitation-réponse à l’étape 4, spécifiez l’envoi et les pipelines de réception.  
  
    1.  À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.  
  
    2.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.  
  
11. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Configurer manuellement une liaison de port physique à l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)