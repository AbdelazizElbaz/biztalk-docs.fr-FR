---
title: "Procédure pas à pas : Module 1 - envoi et réception de Messages avec Windows SharePoint Services adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, creating sites
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, receiving messages
- security, Windows SharePoint Services
- creating, Windows SharePoint Services site
- Windows SharePoint Services, security
- Windows SharePoint Services, document libraries
- Windows SharePoint Services adapters, security
- Windows SharePoint Services
- Windows SharePoint Services adapter tutorials, sending messages
ms.assetid: 6494aef5-bb1d-4a41-8186-1d49625a1013
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8e83297233c4f8ac51ad90f488437a6c259691a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="walkthrough-module-1---sending-and-receiving-messages-with-the-windows-sharepoint-services-adapter"></a>Procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services
Cette procédure décrit la configuration de Windows SharePoint Services et de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à ce que vous puissiez envoyer et recevoir un message via l'adaptateur Windows SharePoint Services et le routage basé sur le contenu. Ce dernier dispense de l'inscription aux messages pour les messages liés à des ports spécifiques. Il offre également plus de souplesse aux utilisateurs souhaitant acheminer des messages en se basant sur les propriétés d'enveloppe ou simplement sur les propriétés de configuration des ports de réception. Pour une présentation de l’adaptateur Windows SharePoint Services, consultez [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez disposer d’un déploiement de serveur unique avec une installation complète de BizTalk Server s’exécutant [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
 Pour plus d’informations sur l’utilisation de l’adaptateur Windows SharePoint Services dans un déploiement multiserveur, consultez [configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).  
  
## <a name="configure-windows-sharepoint-services"></a>Configurer Windows SharePoint Services  
 Cette procédure permet de créer un site Web de niveau supérieur SharePoint contenant trois bibliothèques de documents. L'adaptateur Windows SharePoint Services utilise ces bibliothèques pour déplacer un message d'une bibliothèque source vers une bibliothèque de destination. Ce message est également archivé dans une bibliothèque de documents. Cette procédure permet de créer le site Windows Sharepoint Services auquel accède l'adaptateur Windows Sharepoint Services au cours de cette procédure pas à pas, ainsi que de définir les droits d'accès des utilisateurs à celui-ci.  
  
#### <a name="create-a-windows-sharepoint-services-site"></a>Pour créer un site Windows SharePoint Services  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint.**  
  
2.  Sous **Configuration du serveur virtuel**, cliquez sur **créer un site Web de niveau supérieur**.  
  
3.  Sous **liste des serveurs virtuels**, sélectionnez le site Web que vous avez installé l’adaptateur Windows SharePoint Services sur. Par exemple, `Default Web Site`.  
  
4.  Dans le **adresse de Site Web** section, dans le **nom de l’URL** , tapez `WSSAdapterWalkthrough`.  
  
5.  Dans le **Site propriétaire de la Collection** section, dans le **champ nom d’utilisateur,** tapez un nom d’utilisateur. Cet utilisateur correspond au propriétaire du site Web et n'a besoin d'aucune autorisation spéciale dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
6.  Dans le **Site propriétaire de la Collection** section, dans le **messagerie** , tapez une adresse de messagerie.  
  
7.  Cliquez sur **OK**.  
  
8.  Sur le **premier niveau Site créé avec succès** , cliquez sur le nouveau site Web de niveau supérieur vous venez de créer. Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
9. Sélectionnez le **Site d’équipe** modèle dans la liste des modèles, puis cliquez sur **OK**. La page d'accueil du site Web d'équipe s'affiche.  
  
#### <a name="create-a-source-document-library"></a>Pour créer une bibliothèque de documents « sources »  
  
1.  Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **créer**.  
  
2.  Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.  
  
3.  Dans le **nom et Description** section, dans le **champ nom,** type `Source`.  
  
4.  Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.  
  
5.  Dans le **modèle de Document** section, dans le **modèle de Document** la liste déroulante, sélectionnez `None`.  
  
6.  Cliquez sur **Créer**. La bibliothèque de documents est créée et vous êtes redirigé vers la bibliothèque vide.  
  
#### <a name="create-a-destination-document-library"></a>Pour créer une bibliothèque de documents de « destination »  
  
1.  Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **créer**.  
  
2.  Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.  
  
3.  Dans le **nom et Description** section, dans le **champ nom**, type `Destination`.  
  
4.  Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.  
  
5.  Dans le **modèle de Document** section, dans le **modèle de Document** la liste déroulante, sélectionnez `None`.  
  
6.  Cliquez sur **Créer**. La bibliothèque de documents est créée et vous êtes redirigé vers la bibliothèque vide.  
  
#### <a name="create-an-archive-document-library"></a>Pour créer une bibliothèque de documents « d'archive »  
  
1.  Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **créer**.  
  
2.  Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.  
  
3.  Dans le **nom** et la section de Description, dans le **champ nom**, type `Archive`.  
  
4.  Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.  
  
5.  Dans le **modèle de Document** section, dans le **modèle de Document** la liste déroulante, sélectionnez `None`.  
  
6.  Cliquez sur **Créer**. La bibliothèque de documents est créée et vous êtes redirigé vers la bibliothèque vide.  
  
7.  Fermez le site Web `WSSAdapterWalkthrough`.  
  
8.  Fermer le **Administration centrale de SharePoint** site Web.  
  
#### <a name="configure-windows-security"></a>Pour configurer la sécurité de Windows  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
2.  Dans l’arborescence de la console, développez **utilisateurs et groupes locaux**, puis cliquez sur **groupes**.  
  
3.  Avec le bouton droit le **hôtes avec SharePoint activé** , cliquez sur **ajouter au groupe**, puis cliquez sur **ajouter**.  
  
4.  Dans le **boîte de dialogue Sélectionnez utilisateurs, ordinateurs ou groupes**, sous **Entrez les noms des objets à sélectionner**, tapez le nom du compte que vous avez configuré l’Instance d’hôte BizTalk Server pour s’exécuter sous, puis cliquez sur **OK**.  
  
5.  Dans l’arborescence de la console, développez **Services et Applications**, puis cliquez sur **Services**.  
  
6.  Avec le bouton droit **groupe BizTalk des services BizTalk : < Nom_hôte_biztalk >**, puis cliquez sur **redémarrer**.  
  
    > [!NOTE]
    >  <Nom_hôte_BizTalk> correspond au nom de l'hôte. Par défaut, il s’agit de `BizTalkServerApplication`.  
  
    > [!NOTE]
    >  L'adhésion ne prend pas effet tant que le service n'a pas été redémarré.  
  
7.  Fermer **gestion de l’ordinateur**.  
  
#### <a name="configure-sharepoint-security"></a>Pour configurer la sécurité de SharePoint  
  
1.  Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  Dans la page accueil du Site Web Team, dans la barre de navigation supérieure, cliquez sur **paramètres du Site**.  
  
3.  Sous **Administration**, cliquez sur **gérer les utilisateurs**.  
  
4.  Cliquez sur **Ajouter des utilisateurs**.  
  
5.  Dans **étape 1 : choisissez les utilisateurs**, tapez le nom du compte que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Instance d’hôte est en cours d’exécution sous.  
  
6.  Dans **étape 2 : choisissez les groupes de sites**, sélectionnez le **lecteur** et **collaborateur** cases à cocher.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Désactivez le **envoyer le message suivant pour informer ces utilisateurs qu’ils ont été ajoutés à présent** case à cocher, puis cliquez sur **Terminer**.  
  
9. Fermez le site Web `WSSAdapterWalkthrough`.  
  
## <a name="create-and-configure-the-biztalk-server-ports"></a>Pour créer et configurer les ports BizTalk Server  
 Cette procédure permet de créer et de configurer les ports de réception, les emplacements de réception et les ports d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'adaptateur Windows SharePoint Services. Ces ports représentent des points d'entrée allant vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sortant de celui-ci dont disposent les documents reçus et envoyés par l'adaptateur Windows Sharepoint Services.  
  
#### <a name="create-the-receive-port"></a>Créer le port de réception  
  
1.  Cliquez sur **Démarrer**, **tous les programmes**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server.**  
  
2.  Développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, avec le bouton droit **Ports de réception**, cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel...**  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue **général**, type `FromSource` dans les **nom** champ.  
  
4.  Cliquez sur **OK**.  
  
#### <a name="create-the-receive-location"></a>Pour créer un emplacement de réception  
  
1.  Dans le **Console Administration de BizTalk**, avec le bouton droit le **emplacements de réception** nœud, cliquez sur **nouveau**, puis cliquez sur **l’emplacement de réception unidirectionnel**.  
  
2.  Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez `FromSource`, puis cliquez sur **OK**.  
  
3.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue **général**, type `SourceLocation` dans les **nom** champ.  
  
4.  Dans le **Transport** section, dans le **Type** la liste déroulante, sélectionnez `Windows``SharePoint``Services`.  
  
5.  Cliquez sur **configurer** pour configurer les propriétés de l’adaptateur Windows SharePoint Services.  
  
6.  Dans le **Port du Service Web adaptateur** propriété, tapez le numéro de port du serveur virtuel sur lequel le service Web de l’adaptateur Windows SharePoint Services a été installé. Par défaut, il s’agit de port 80.  
  
7.  Type `Archive` dans les **emplacement d’Archive** propriété.  
  
8.  Type `10` dans les **fréquence d’interrogation** propriété.  
  
9. Tapez l’URL de votre site SharePoint dans le **ShareP**oint propriété Url du Site. Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
10. Type `Source` pour le **bibliothèque de documents Source** propriété.  
  
11. Cliquez sur **OK**.  
  
12. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, sélectionnez `BizTalkServerApplication` comme le **Gestionnaire de réception**.  
  
13. Dans le **pipeline de réception** la liste déroulante, sélectionnez `PassThruReceive`.  
  
14. Cliquez sur **OK**.  
  
#### <a name="create-the-send-port"></a>Pour créer un port d'envoi  
  
1.  Dans le **Console Administration de BizTalk**, avec le bouton droit le **Ports d’envoi** nœud, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique** .  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue **général**, type `SendToDestination` dans les **nom** champ.  
  
3.  Dans le **Transport** section, sélectionnez `Windows SharePoint Services` pour le type.  
  
4.  Cliquez sur **configurer** pour configurer les propriétés de l’adaptateur Windows SharePoint Services.  
  
5.  Dans le **Port du Service Web adaptateur** propriété, tapez le numéro de port du serveur virtuel sur lequel le service Web de l’adaptateur Windows SharePoint Services a été installé. Par défaut, il s’agit de port 80.  
  
6.  Tapez dans `Destination` pour le **dossier de Destination** propriété.  
  
7.  Tapez dans `PurchaseOrder1-%MessageID%.xml` pour le **nom de fichier** propriété.  
  
8.  Définir le **remplacer** propriété `Yes`.  
  
9. Tapez l’URL de votre site SharePoint dans le **Url du Site SharePoint** propriété. Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
10. Définir le **intégration de Microsoft Office** propriété `No`.  
  
11. Cliquez sur **OK**.  
  
12. Dans le **boîte de dialogue Propriétés de Port d’envoi**, dans le **Gestionnaire d’envoi** la liste déroulante, sélectionnez `BizTalkServerApplication`.  
  
13. Dans le **pipeline d’envoi** la liste déroulante, sélectionnez `PassThruTransmit`.  
  
14. Cliquez sur le **filtres** onglet.  
  
15. Sélectionnez `WSS.InListName` dans les **propriété** champ.  
  
16. Sélectionnez `==` dans les **opérateur** champ.  
  
17. Type `Source` dans les **valeur** champ.  
  
18. Cliquez sur **OK**.  
  
## <a name="enable-and-start-the-receive-location-and-receive-port"></a>Pour activer et démarrer l'emplacement et le port de réception  
 Ces procédures permettent d'activer l'emplacement de réception et de démarrer le port de réception. Vous devez mener à bien cette procédure afin de permettre à l'adaptateur Windows Sharepoint Services d'envoyer et de recevoir des messages via le port d'envoi et l'emplacement de réception spécifiés.  
  
#### <a name="enable-the-receive-location"></a>Pour activer l'emplacement de réception  
  
1.  Dans le **Console Administration de BizTalk**, cliquez sur le **emplacements de réception** nœud.  
  
2.  Avec le bouton droit `SourceLocation`, puis cliquez sur **activer**.  
  
#### <a name="start-the-send-port"></a>Pour démarrer le port d'envoi  
  
1.  Dans le **Console Administration de BizTalk**, cliquez sur le **Ports d’envoi** nœud.  
  
2.  Avec le bouton droit `SendToDestination`, puis cliquez sur **Démarrer**.  
  
3.  Fermer le **Console Administration de BizTalk**.  
  
## <a name="sending-a-message-through-the-system"></a>Pour envoyer un message via le système  
 Cette procédure permet de créer un document XML et de le télécharger sur le site Web Windows SharePoint Services. L'adaptateur Windows SharePoint Services prend ce message, l'archive dans la bibliothèque de documents d'archive, puis l'envoie dans la bibliothèque de documents de destination. Cette procédure montre comment un document circule depuis un site Web SharePoint, via [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vers un site Web SharePoint Services, à l'aide de l'adaptateur Windows SharePoint Services.  
  
#### <a name="create-a-working-directory"></a>Pour créer un répertoire de travail  
  
-   Créez un répertoire sur votre ordinateur appelé **WSSAdapterWalkthrough**. Par exemple, `C:\WSSAdapterWalkthrough`.  
  
#### <a name="create-an-xml-file"></a>Pour créer un fichier XML  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **le bloc-notes.**  
  
2.  Tapez la commande suivante :  
  
    ```  
    <?xml version="1.0"?>  
    <PurchaseOrder>  
        <ID>1001</ID>  
        <FirstName>John</FirstName>  
        <LastName>Doe</LastName>  
        <Amount>750</Amount>  
    </PurchaseOrder>  
    ```  
  
3.  Enregistrez le fichier dans votre répertoire de travail sous le nom `PurchaseOrder1.xml` Par exemple, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`.  
  
#### <a name="upload-the-xml-file"></a>Pour télécharger le fichier XML  
  
1.  Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé lors de la tâche précédente Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  Sur le côté gauche, sous **Documents**, cliquez sur **Source**.  
  
3.  Cliquez sur **télécharger un Document**.  
  
4.  Dans le **nom** , tapez ou accédez au fichier XML que vous avez créé précédemment. Par exemple, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`, puis cliquez sur **enregistrer et fermer**. Le fichier doit s'afficher dans la liste.  
  
5.  Actualisez la fenêtre du navigateur. Le fichier `PurchaseOrder1.xml` n'apparaît plus dans cette bibliothèque.  
  
    > [!NOTE]
    >  Comme la fréquence d'interrogation est définie sur 10 secondes, il peut être nécessaire d'actualiser plusieurs fois le navigateur.  
  
6.  Dans la barre de navigation supérieure, cliquez sur **Documents et listes**.  
  
7.  Sous **bibliothèques de documents**, cliquez sur **Destination**.  
  
8.  Dans la bibliothèque de documents de Destination, vous voyez maintenant votre message répertorié. Vous trouverez également une copie archivée dans la bibliothèque de documents d'archive.  
  
    > [!NOTE]
    >  Si le message n'apparaît pas dans la bibliothèque de documents de destination, consultez la rubrique « Dépannage de l'adaptateur Windows SharePoint Services » dans l'Aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="summary"></a>Résumé  
 Au cours de cette procédure, vous avez découvert la configuration de Windows SharePoint Services et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à envoyer et recevoir un message via l'adaptateur Windows SharePoint Services et le routage basé sur le contenu.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) procédure pas à pas, ce qui permet de compléter le travail que vous avez terminé avec cette procédure pas à pas et l’affiche vous l’intégration d’Office à l’adaptateur Windows SharePoint Services.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Procédures pas à pas relatives à l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-walkthroughs.md)