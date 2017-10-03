---
title: "Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur POP3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, POP3 adapters
- configuring [POP3 adapters], mailboxes
- configuring [POP3 adapters], tutorials
- POP3 adapters, mailboxes
- POP3 adapters, tutorials
- configuring [POP3 adapters], Outlook Express
ms.assetid: b44c3b1d-7b4f-425c-831a-1ce5f6379595
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1af0d60eab23a3cbfff67a8b4b11dc73fb49afe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter"></a>Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur POP3
Cette section vous guide tout au long de la création d'une simple application Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur POP3.  
  
> [!NOTE]
>  L'application implique que vous avez accès à un ordinateur exécutant Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] avec des services de messagerie installés et configurés. Pour plus d'informations sur la configuration de [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] avec les services de messagerie, consultez l'aide de Windows Server.  
  
> [!NOTE]
>  Dans cet exemple, Microsoft Outlook Express est utilisé comme client de messagerie et [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] comme serveur de messagerie. Toutefois, n'importe quel client de messagerie POP3 et serveur POP3 compatible RFC pourraient être utilisés dans ce scénario.  
  
 Cette application suppose que vous n'avez pas encore créé de ports d'envoi ou d'emplacements de réception. Si vous avez des ports d'envoi ou emplacements de réception existants, remplacez par les noms appropriés lorsque vous avancez dans la procédure.  
  
 Il s'agit d'une application de routage simple basé sur le contenu utilisant uniquement un emplacement de réception et un port d'envoi. L’emplacement de réception lit à partir d’une boîte aux lettres sur le serveur exécutant [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)](« Windows server »\). Le port d'envoi prend le message de l'emplacement de réception et l'envoie dans un dossier sur le système de fichiers local de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour créer l'application, vous devez créer la boîte aux lettres, configurer l'emplacement de réception et le port d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], démarrer le port d'envoi et activer l'emplacement de réception et envoyer un message de test à la boîte aux lettres. Suivez les étapes ci-après pour créer l'application.  
  
## <a name="create-a-mailbox-on-windows-server-2003"></a>Création d'une boîte aux lettres sous Windows Server 2003  
 Pour créer une boîte aux lettres sous Windows Server 2003 avec les services de messagerie installés, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **Service POP3**.  
  
2.  Développez  *\<nom_serveur >* et cliquez sur le domaine dans lequel vous souhaitez créer une boîte aux lettres.  
  
3.  Dans le **Service POP3** boîte de dialogue, dans le volet droit, cliquez sur le **ajouter une boîte aux lettres** option.  
  
4.  Dans le **ajouter une boîte aux lettres** boîte de dialogue le **nom de la boîte aux lettres** , tapez **EmailTest**.  
  
5.  Sélectionnez le **créer un utilisateur associé pour cette boîte aux lettres** case à cocher.  
  
6.  Dans le **mot de passe** et **confirmer le mot de passe** zones, tapez un mot de passe, puis cliquez sur **OK**.  
  
7.  Prenez note de la **nom de compte** et **serveur de messagerie** ouvrir une session sur les informations affichées pour une utilisation avec l’authentification en texte clair dans le **Service POP3** boîte de dialogue, puis cliquez sur **OK**. Ces informations sont utilisées par l'emplacement de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que vous configurez avec le type de transport POP3.  
  
## <a name="create-the-receive-location"></a>Pour créer un emplacement de réception  
 Suivez ces étapes pour créer l'emplacement de réception :  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration double-cliquez sur la base de données par défaut  **\<**  *Nom_Ordinateur***>. BizTalkMgmtDb.dbo**, où *Nom_Ordinateur* est le nom de votre ordinateur. Cliquez sur **Applications**, puis cliquez sur **BizTalk.Application.1**.  
  
2.  Avec le bouton droit **Ports de réception**, cliquez sur **nouveau**, cliquez sur **unidirectionnel port de réception**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , tapez **POP3Receive**.  
  
4.  Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **POP3Receive**.  
  
5.  Dans le **Type de Transport** boîte, sélectionnez **POP3**.  
  
6.  Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.  
  
7.  Dans le **Pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
8.  Dans le **Transport** , cliquez sur le **configurer** bouton.  
  
9. Dans le **propriétés du Transport POP3** boîte de dialogue le **appliquer le décodage MIME** boîte, sélectionnez **False**.  
  
10. Dans le **serveur de messagerie** , tapez le nom du serveur Windows Server où vous avez créé une boîte aux lettres.  
  
11. Dans le **schéma d’authentification** boîte, sélectionnez **base**.  
  
12. Dans le **mot de passe** zone, cliquez sur la flèche déroulante et tapez le mot de passe pour la boîte aux lettres.  
  
13. Dans le **nom d’utilisateur** , tapez le nom d’utilisateur complet pour la boîte aux lettres, par exemple  *username@host.domain.toplevel_domain.*  
  
14. Dans le **fréquence d’interrogation** , tapez **1**, cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
## <a name="create-the-send-port-and-destination-folder-on-the-biztalk-server"></a>Création du port d'envoi et du dossier de destination sur le serveur BizTalk  
 Suivez ces étapes pour créer le port d'envoi et le dossier de destination sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
1.  Créez un dossier sur le système de fichiers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il s'agit de la destination du port d'envoi.  
  
2.  Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau,** puis cliquez sur **Port d’envoi unidirectionnel statique.**  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **Type de Transport** boîte, sélectionnez **fichier**.  
  
4.  Dans le **nom** , tapez **SendToFile**.  
  
5.  Dans le **Transport** , cliquez sur le **configurer** bouton.  
  
6.  À côté du **dossier de Destination** , cliquez sur **Parcourir**, sélectionnez le dossier que vous avez créé sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis cliquez sur **OK**.  
  
7.  Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.  
  
8.  Dans le **Pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
9. Cliquez sur **Filtres**.  
  
10. Dans le **propriété** boîte, sélectionnez **BTS. ReceivePortName**.  
  
11. Dans le **valeur** , tapez **POP3Receive**, puis cliquez sur **OK**.  
  
## <a name="enable-the-receive-location-and-start-the-send-port"></a>Activer l’emplacement de réception et de démarrer le port d’envoi  
 Procédez comme suit pour activer l'emplacement de réception et démarrer le port d'envoi :  
  
1.  Cliquez sur le **POP3Receive** emplacement de réception, puis cliquez sur **activer**.  
  
2.  Cliquez sur le **SendToFile** port d’envoi, puis cliquez sur **Démarrer**.  
  
 La prochaine étape consiste à tester l'application en envoyant un message de test à la boîte aux lettres surveillée par l'emplacement de réception.  
  
## <a name="configure-outlook-express-to-send-an-e-mail-message-to-the-mailbox"></a>Configuration d'Outlook Express pour envoyer un message électronique à la boîte aux lettres  
 Procédez comme suit pour configurer Outlook Express pour envoyer un message électronique à la boîte aux lettres :  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, puis cliquez sur **Outlook Express**.  
  
2.  Dans Outlook Express, sur le **outils** menu, cliquez sur **comptes**.  
  
3.  Cliquez sur **ajouter** puis cliquez sur **Mail**.  
  
4.  Dans le **nom d’affichage** zone, tapez un nom d’affichage, puis cliquez sur **suivant**.  
  
5.  Dans le **adresse de messagerie Internet** boîte de dialogue le **adresse de messagerie** , tapez **EmailTest @< nom_domaine >**, puis cliquez sur **suivant**.  
  
     Veillez à entrer la valeur appropriée pour *< nom_domaine >*. Cette valeur doit correspondre au nom du domaine sous lequel cette boîte aux lettres a été créée dans l'interface Administration du service POP3 sur le serveur Windows.  
  
6.  Dans le **les noms de serveur de messagerie** boîte de dialogue le **courrier entrant** et **courrier sortant** zones, tapez le nom du serveur ou l’adresse IP du serveur Windows, puis cliquez sur  **Suivant**.  
  
7.  Dans le **connexion à la messagerie Internet** boîte de dialogue le **nom de compte** , tapez **EmailTest**.  
  
8.  Dans le **mot de passe** , tapez le mot de passe du compte EmailTest, sélectionnez le **Mémoriser le mot de passe** , cliquez sur **suivant**, puis cliquez sur **Terminer**.  
  
9. Cliquez pour sélectionner le compte que vous venez de créer, puis cliquez sur **propriétés**.  
  
10. Dans le **propriétés** boîte de dialogue, cliquez sur le **avancé** onglet, sélectionnez l’option à **laisser un exemplaire des messages sur le serveur**, puis cliquez sur **OK**.  
  
11. Dans le **comptes Internet** boîte de dialogue, cliquez sur **fermer**.  
  
12. Utilisez Outlook Express pour composer un message de test, type **Test** dans les **sujet** champ et le type **EmailTest @< nom_domaine >** dans le **à** champ.  
  
13. Cliquez sur **envoyer** pour envoyer le message de test. Pour vous assurer qu’Outlook Express envoie le message de test immédiatement, cliquez sur le **Envoyer/Recev** bouton dans la barre d’outils Outlook Express.  
  
## <a name="view-the-message"></a>Affichage du message  
 Procédez comme suit pour afficher le message :  
  
1.  Utilisez l’Explorateur Windows pour ouvrir le dossier que vous avez spécifié comme le **dossier de Destination** pour le port d’envoi.  
  
2.  Double-cliquez sur le document dans le dossier pour afficher le contenu du document dans le Bloc-notes.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur POP3 ?](../core/what-is-the-pop3-adapter.md)