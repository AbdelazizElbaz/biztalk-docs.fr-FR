---
title: L’exécution d’un exemple d’opération Get PeopleSoft Enterprise | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb54f14c-3fce-44d6-91bb-cb1ca38a20da
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29cf6bba03e6a43bb3fdedf0742741e48ac22dd6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="execute-a-peoplesoft-enterprise-sample-get"></a>Exécuter un exemple d’opération Get PeopleSoft Enterprise
Le système PeopleSoft est accessible à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur PeopleSoft. Cette carte est incluse avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].
  
 Il s'agit de la deuxième partie de l'atelier PeopleSoft. Au cours de la première partie (Atelier 1), vous avez consulté et modifié les données du système PeopleSoft sans utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou d'autres technologies Microsoft. Dans la deuxième partie (Atelier 2), vous allez créer une orchestration BizTalk au sein d'un projet BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous allez configurer les ports de cette orchestration de manière à ce qu'ils utilisent l'adaptateur PeopleSoft pour extraire des données du système PeopleSoft.  
  
## <a name="prerequisites"></a>Configuration requise  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]
  
-   Adaptateurs Microsoft BizTalk pour les applications d'entreprise  
  
-   Microsoft Visual Studio  
  
-   Sun Systems Java Development Kit (JDK) version 1.4 ou ultérieure  
  
> [!NOTE]
>  Consultez [installer et configurer les adaptateurs pour les applications d’entreprise](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) pour des informations de configuration de la clé pour les adaptateurs JD Edwards, PeopleSoft et TIBCO.  
  
## <a name="lab-2---executing-a-peoplesoft-sample-get"></a>Atelier 2 : exécution d'un exemple d'opération Get PeopleSoft  
 Au cours de cet atelier, vous allez exécuter une opération **Get** sur le système PeopleSoft. Vous allez effectuer les tâches suivantes :  
  
-   vérification de la configuration requise de PeopleSoft ;  
  
-   configuration d'un port d'envoi PeopleSoft dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;  
  
-   création d'un projet d'orchestration BizTalk ;  
  
-   création et déploiement du projet ;  
  
-   test de l'application et affichage de la sortie XML.  
  
## <a name="procedures-for-lab-2--executing-a-peoplesoft-sample-get"></a>Atelier 2 : exécution d'un exemple d'opération Get PeopleSoft  
 Les deux fichiers suivants sont nécessaires à l'interface pour accéder au système PeopleSoft : PSJOA.JAR et GET_CI_INFO.PC. Sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'adaptateur PeopleSoft communique avec le système PeopleSoft à l'aide de l'interface Java PeopleSoft. Celle-ci est fournie par le fichier PSJOA.JAR. Une copie de ce fichier est généralement placée dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par l'administrateur du système PeopleSoft auquel vous accédez. Dans le cadre de cet atelier, une copie du fichier PSJOA.JAR existe dans le dossier C:\PSJars\Ver841\ sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'emplacement de ce fichier est spécifié dans les propriétés de configuration de l'adaptateur PeopleSoft.  
  
 Sur le système PeopleSoft, vous devez installer une interface de composant personnalisée. Celle-ci permet à l'adaptateur de rechercher des objets PeopleSoft au cours de sa configuration. L'interface de composant personnalisée est appelée (à partir de l'étape Ajouter les éléments générés) afin d'obtenir la liste des objets PeopleSoft accessibles. Ceux-ci déterminent les fonctionnalités PeopleSoft exposées et accessibles par le système client.  
  
 Le composant personnalisé GET_CI_INFO doit être installé dans le système PeopleSoft au cours de l'installation initiale. Vous pouvez modifier ce fichier de manière à limiter les éléments exposés par GET_CI_INFO (à savoir, par défaut, toutes les interfaces de composant du système PeopleSoft). La source associée est située dans le fichier texte GET_CI_INFO.PC à l'emplacement par défaut suivant :  
  
 **C:\Program Files\Microsoft BizTalk Adapters pour Enterprise \Config**  
  
 Fournit des instructions générales sur l’installation de l’interface de composant GET_CI_INFO PeopleSoft [installer et configurer les adaptateurs pour les applications d’entreprise](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md). Ces instructions sont destinées à un administrateur PeopleSoft expérimenté.  
  
## <a name="step-1-confirm-the-peoplesoft-rerequisites"></a>Étape 1 : Vérifier la rérequis PeopleSoft  
 Avant de commencer la création d'un projet BizTalk à des fins d'utilisation avec l'adaptateur PeopleSoft, vous devez vous assurer que tous les composants permettant d'accéder à PeopleSoft sont correctement configurés.  
  
1.  Vérifiez que le PSJOA. Fichier JAR existe sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur dans le dossier C:\psjars\ver841. Bien que ce fichier puisse exister dans un autre emplacement sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la configuration indiquée ci-dessous part du principe que le fichier se trouve à cet emplacement.  
  
2.  Vérifier que le fichier get_ci_info.pc existe dans le C:\Program Files\Microsoft dossier BizTalk Adapters for Enterprise \Config.  
  
3.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **Administration**, développez **groupe BizTalk**, développez **Paramètres de plateforme**, puis développez **cartes**. Vérifiez que l'adaptateur PeopleSoft est installé et qu'il figure dans la liste.  
  
     S'il n'est pas installé, installez les adaptateurs BizTalk pour les applications d'entreprise (voir la section « Configuration requise » ci-dessus). Une fois ceux-ci installés, cliquez avec le bouton droit sur **Adaptateurs** , puis cliquez sur **Nouveau - Adaptateur** pour installer l'adaptateur PeopleSoft. Redémarrez l’instance d’hôte pour que cela prenne effet.  
  
## <a name="step-2-create-a-send-port-for-peoplesoft"></a>Étape 2 : Créer un Port d’envoi pour PeopleSoft  
 Pour communiquer avec le système PeopleSoft, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit disposer d'un port d'envoi, qui est généralement lié aux ports logiques de l'orchestration.  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez  **Applications**, puis développez **BizTalk.EnterpriseApplication.**  
  
2.  Cliquez avec le bouton droit sur **Ports d'envoi**, cliquez sur **Nouveau**, puis sélectionnez **Port d'envoi statique avec sollicitation-réponse**. Dans la boîte de dialogue **Propriétés de port d'envoi** , entrez les valeurs de propriété suivantes :  
  
    1.  **Nom :**  `PeopleSoftSamplePort`  
  
    2.  **Type:**  `PeopleSoft`  
  
    3.  **Gestionnaire d’envoi :**  `BizTalkServerApplication`  
  
    4.  **Pipeline d’envoi :**  `XMLTransmit`  
  
    5.  **Pipeline de réception :**  `XMLReceive`  
  
3.  Cliquez sur **Configurer**, puis entrez les valeurs de propriété suivantes :  
  
    1.  **Chemin d'accès au serveur de l'application**: **//Servername:9000**  
  
         NomServeur correspond au serveur d'applications. Il s'agit du nom du serveur ou de l'adresse IP et du numéro de port spécifiques à ce système PeopleSoft.  
  
    2.  **JAVA_HOME**: **C:\J2SDK1.4.2_08**  
  
         Ce chemin d'accès est spécifique à l'installation du Kit de développement logiciel Java sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    3.  **Mot de passe**: \<entrer votre mot de passe PeopleSoft\>  
  
    4.  **Fichiers JAR PeopleSoft 8.x**: **C:\PSJARS\VER841\PSJOA.JAR**  
  
    5.  **Nom d’utilisateur :** \<Entrez votre PeopleSoft UserID\>  
  
     ![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")  
  
4.  Cliquez sur **OK** à deux reprises pour fermer les boîtes de dialogue.  
  
## <a name="step-3-create-a-biztalk-orchestration-project"></a>Étape 3 : Créer un projet d’Orchestration BizTalk  
 Vous allez à présent créer un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et y configurer une orchestration pour gérer les communications entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le système PeopleSoft. Vous allez ajouter des ports d'envoi et de réception, créer le projet, puis le déployer.  
  
1.  Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis créez un projet BizTalk dans le dossier C:\LABS. Dans le menu **Fichier** , cliquez sur **Nouveau**. La boîte de dialogue **Nouveau projet** s'affiche. Dans la boîte de dialogue **Modèles** , sélectionnez **Projet BizTalk Server vide** . Entrez `PS_Test` comme nom unique du projet, puis cliquez sur **OK**.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter**, puis sur **Ajouter les éléments générés**. Sélectionnez **Ajouter les métadonnées de l'adaptateur** dans le volet **Catégories** et **Ajouter les métadonnées de l'adaptateur** dans la section **Modèles** , puis cliquez sur **Ajouter**.  
  
3.  Dans l'Assistant Ajout d'adaptateur, sélectionnez l'adaptateur **PeopleSoft Enterprise** , sélectionnez le port d'envoi **PeopleSoftSamplePort** que vous avez créé dans la procédure précédente, puis cliquez sur **Suivant**.  
  
     ![](../core/media/ed0dedc5-a8fb-444c-b884-e310cf56462c.gif "ed0dedc5-a8fb-444c-b884-e310cf56462c")  
  
4.  Dans la page **Sélectionner les services à importer** , développez **PeopleSoft**, puis **Interface de composant**.  
  
     Le système PeopleSoft est interrogé par l'adaptateur à l'aide de l'outil BrowsingAgent.exe. Lorsque vous développez **Interface de composant**, le processus BrowsingAgent.exe démarre (il est affiché comme étant en cours d'exécution dans le Gestionnaire des tâches) et renvoie les services affichés dans la figure suivante.  
  
     ![](../core/media/6988104c-6483-4df2-a637-3301628ea665.gif "6988104c-6483-4df2-a637-3301628ea665")  
  
    > [!NOTE]
    >  Les services PeopleSoft obtenus et affichés par le système PeopleSoft peuvent varier légèrement des services affichés ici.  
  
5.  Faites défiler vers le bas, sélectionnez **Emplacement**, puis cliquez sur **Terminer**.  
  
     ![](../core/media/0506affd-3caa-47cb-9c25-f49c8a0ad614.gif "0506affd-3caa-47cb-9c25-f49c8a0ad614")  
  
6.  L'Explorateur de solutions inclut une nouvelle orchestration BizTalk et deux nouveaux fichiers de schémas associés. Ces derniers sont créés par l'Assistant Ajout d'adaptateur. Double-cliquez sur le fichier **BizTalk Orchestration.odx** pour ouvrir l'orchestration.  
  
     ![](../core/media/825c5690-78eb-4048-9a47-cd3fc7310b7b.gif "825c5690-78eb-4048-9a47-cd3fc7310b7b")  
  
 Celle-ci accepte comme entrée un fichier XML mis en forme pour la méthode **Get** PeopleSoft et envoie celui-ci au système PeopleSoft. La méthode **Get** extrait les informations d'emplacement du système PeopleSoft et les renvoie à l'orchestration BizTalk. L'orchestration utilise des ports pour les communications entre l'adaptateur et le système PeopleSoft. Les ports que vous configurez ici sont utilisés à des fins d'envoi et de réception des fichiers XML. Le fichier XML sortant indique au système PeopleSoft qu'il s'agit d'une opération **Get** . Le fichier XML entrant renvoie les informations d'emplacement à l'orchestration.  
  
 Pour terminer l'orchestration, vous devez créer et configurer les ports pour recevoir et envoyer les fichiers XML. Commencez par configurer un nouveau port de réception pour accepter le fichier d'entrée XML initial contenant la méthode **Get** pour démarrer l'orchestration.  
  
#### <a name="configure-a-receive-port"></a>Configurer un port de réception  
  
1.  Dans le fichier BizTalk Orchestration.odx ouvert à l'étape précédente, cliquez avec le bouton droit sur la surface du port de gauche, puis cliquez sur **Nouveau port configuré**. L'Assistant Configuration du port démarre. Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
2.  Sur l'ordinateur **Propriétés du port** , définissez `FileIn` sur **FileIn**, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner un type de port** , sélectionnez **Créer un type de port**, puis entrez ou sélectionnez les valeurs de propriété suivantes :  
  
     **Nom du Type de port**: `FileInPort`  
  
     **Modèle de communication**: **Unidirectionnel**  
  
     **Restrictions d'accès**: **Interne - limité au projet**  
  
4.  Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :  
  
     **Direction de communication du port**: **Toujours recevoir les messages sur ce port**  
  
     **Liaison de port**: **Spécifier plus tard**  
  
5.  Cliquez sur **Suivant**, puis sur **Terminer**. Vous utiliserez l'adaptateur FILE pour accepter ce fichier en tant qu'entrée à partir du disque.  
  
 Créez ensuite un port d'envoi pour accepter le fichier XML contenant les résultats de l'emplacement provenant de l'appel à la méthode **Get** PeopleSoft. L'orchestration utilise l'adaptateur FILE pour enregistrer le fichier XML sur le disque via ce port d'envoi.  
  
#### <a name="configure-a-send-port"></a>Configurer un port d’envoi  
  
1.  Dans le fichier BizTalk Orchestration.odx, cliquez avec le bouton droit sur la surface du port de gauche, puis cliquez sur **Nouveau port configuré**. L'Assistant Configuration du port démarre. Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
2.  Sur l'ordinateur **Propriétés du port** , définissez `FileOut` sur **FileIn**, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner un type de port** , sélectionnez **Créer un type de port**, puis entrez ou sélectionnez les valeurs de propriété suivantes :  
  
     **Nom du Type de port**: `FileOutPort`  
  
     **Modèle de communication**: **Unidirectionnel**  
  
     **Restrictions d'accès**: **Interne - limité au projet**  
  
4.  Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :  
  
     **Direction de communication du port**: **Toujours envoyer les messages sur ce port**  
  
     **Liaison de port**: **Spécifier plus tard**  
  
5.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
 Pour terminer, créez un port d'envoi/réception pour envoyer le fichier d'entrée XML initial contenant la méthode **Get** au système PeopleSoft. Ce port reçoit également un fichier XML contenant les informations d'emplacement issues de l'appel de la méthode **Get** auprès du système PeopleSoft.  
  
#### <a name="configure-a-sendreceive-port"></a>Configurer un port d’envoi/réception  
  
1.  Dans le fichier BizTalk Orchestration.odx, cliquez avec le bouton droit sur la surface du port de droite, puis cliquez sur **Nouveau port configuré**. L'Assistant Configuration du port démarre. Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
2.  Sur l'ordinateur **Propriétés du port** , définissez `PeopleSoft_Port` sur **FileIn**, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner un type de port** , sélectionnez **Utiliser un type de port existant**. Sous **Types de ports disponibles**, sélectionnez **PS_Test.LOCATION**, puis cliquez sur **Suivant**.  
  
     ![](../core/media/d8b443ec-294d-4124-a29d-aeb42bbb107e.gif "d8b443ec-294d-4124-a29d-aeb42bbb107e")  
  
4.  Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :  
  
     **Direction de communication du port**: **Toujours envoyer une requête et recevoir une réponse**  
  
     **Liaison de port**: **Spécifier plus tard**  
  
5.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
 Le nouveau port et les méthodes disponibles pour le service Emplacement PeopleSoft s'affichent sur la surface du port. Lors d'une étape ultérieure, vous indiquerez à l'adaptateur PeopleSoft d'envoyer et de recevoir des fichiers à partir du système PeopleSoft.  
  
 Insérez deux formes **Envoi** et deux formes **Réception** dans l'orchestration afin de les lier aux ports que vous venez de créer.  
  
#### <a name="add-send-and-receive-shapes"></a>Ajouter d’envoyer et recevoir des formes  
  
1.  Faites glisser un composant **Réception** à partir de la Boîte à outils, puis déposez-le sous le début de l'orchestration (cercle vert). Cliquez sur la forme **Réception** , puis dans la fenêtre Propriétés, définissez `FromDisk` sur **FileIn**, puis **Activer** sur `true`. Cette opération permet d'activer l'orchestration lorsque ce port de réception reçoit un document entrant.  
  
2.  Faites glisser un **envoyer** composant à partir de la boîte à outils et déposez-le sous le **FromDiskReceive** forme. Cliquez sur la nouvelle forme **Envoi** , puis dans la fenêtre Propriétés, définissez `ToPS` sur **FileIn**.  
  
3.  Faites glisser un **réception** composant à partir de la boîte à outils et déposez-le sous le **To_PS *** envoyer** forme. Cliquez sur la forme **Réception** , puis dans la fenêtre Propriétés, définissez `FromPS` sur **FileIn**.  
  
4.  Faites glisser un **envoyer** composant à partir de la boîte à outils et déposez-le sous le **From_PSReceive** forme. Cliquez sur la nouvelle forme **Envoi** , puis dans la fenêtre Propriétés, définissez `ToDisk` sur **FileIn**.  
  
 Avant de pouvoir connecter ces formes aux ports logiques, vous devez définir les types de messages à traiter. L'adaptateur a besoin d'un message entrant (méthode**Request** ) et d'un message sortant (méthode**Response** ). Les messages associés à chaque méthode sont différents.  
  
 Dans cette orchestration, vous utiliserez uniquement des messages **Get-Request** et **Get-Response** . Si l'orchestration met à jour les données, par exemple à l'aide de la méthode **UpdateEx** , différents messages Request/Response sont nécessaires.  
  
#### <a name="define-and-assign-messages-to-ports"></a>Définir et affecter des messages aux ports  
  
1.  Sur la surface du port de gauche, cliquez sur **Request** sur le port **FileIn** . Dans la fenêtre Propriétés, développez **Type de message**et **Messages à parties multiples**, puis cliquez sur **PS_Test.Get**.  
  
2.  Sur la surface du port de gauche, cliquez sur **Request** sur le port **FileOut** . Dans la fenêtre Propriétés, développez **Type de message**et **Messages à parties multiples**, puis cliquez sur **PS_Test.GetResponse**.  
  
     ![](../core/media/6b844ca3-322a-47b3-8cfd-68652c950752.gif "6b844ca3-322a-47b3-8cfd-68652c950752")  
  
3.  Sélectionnez le port **FileIn** , puis faites glisser la flèche d'envoi sortante vers la flèche de réception inverse entrante sur la forme **FromDisk** .  
  
4.  Sélectionnez le port **FileOut** , puis faites glisser la flèche de réception inverse entrante vers la flèche d'envoi sortante sur la forme **ToDisk** .  
  
5.  Renommez les messages génériques existants à l'aide de noms descriptifs conformes aux principes de conception des applications. Dans l'Explorateur de solutions, cliquez sur l'onglet **Vue Orchestration** . Sous **Messages**, définissez l’identificateur **Message_1** à **PS_Msg**. et l'identificateur **Message_2** sur **PS_Resp**.  
  
     ![](../core/media/5ec92b81-4a55-4d44-a360-78a6aaa64255.gif "5ec92b81-4a55-4d44-a360-78a6aaa64255")  
  
     ![](../core/media/04b31c26-73a6-40a6-8d50-39c7c929d6a1.gif "04b31c26-73a6-40a6-8d50-39c7c929d6a1")  
  
6.  Sélectionnez la forme Envoi **To_PS** et définissez la propriété **Message** associée sur **PS_Msg**.  
  
7.  Sélectionnez la forme Réception **From_PS** et définissez la propriété **Message** associée sur **PS_Resp**.  
  
8.  Connectez la forme Envoi **To_PS** à la section **Request** de la méthode **Get** sur le port **PeopleSoft_Port** .  
  
9. Connectez la forme Envoi **From_PS** à la section **Response** de la méthode **Get** sur le port **PeopleSoft_Port** .  
  
     ![](../core/media/d16e02bc-954c-4aa2-99d6-3fee1222c730.gif "d16e02bc-954c-4aa2-99d6-3fee1222c730")  
  
## <a name="step-4-build-and-deploy-the-project"></a>Étape 4 : Créer et déployer le projet  
 Le projet BizTalk étant à présent terminé, vous pouvez le créer et le déployer dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
1.  Dans Visual Studio, pointez sur **Visual Studio Tools**, puis sélectionnez Visual Studio invite **.  
  
2.  Pour créer le projet, un fichier de clé de nom fort est nécessaire. Pour en créer un, à l'invite de commandes, entrez le code suivant :  
  
     **sn -k labs.snk**  
  
3.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **PS_Test** , puis cliquez sur **Propriétés** pour lancer le Concepteur de projet pour le projet.  
  
4.  Cliquez sur l'onglet **Signature** .  
  
5.  Sélectionnez l'option **Signer l'assembly** , cliquez sur l'option **Choisir un fichier de clé de nom fort** dans la liste déroulante, puis sur **Parcourir**.  
  
6.  Recherchez puis sélectionnez le fichier de clé : **labs.snk**, puis cliquez sur **Ouvrir**.  
  
7.  Dans le Concepteur de projet, cliquez sur l'onglet **Déploiement** .  
  
8.  Affectez au **Nom de l'application** sur `PS_Test`.  
  
9. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **PS_Test** , puis cliquez sur **Générer**.  
  
10. Une fois la génération correctement terminée, cliquez avec le bouton droit sur le projet **PS_Test** , puis cliquez sur **Déployer**.  
  
## <a name="step-5-test-the-application-and-viewing-the-xml-output"></a>Étape 5 : Tester l’Application et afficher la sortie XML  
 Vous allez à présent tester l'application que vous avez créée et déployée. Vous allez créer le fichier XML qui démarre le processus d'orchestration, puis vous allez configurer les dossiers afin qu'ils reçoivent et envoient des fichiers XML au sein de l'application. Une fois l'application configurée, vous allez l'exécuter et afficher les fichiers XML qu'elle renvoie.  
  
#### <a name="generate-the-xml-file-for-the-query"></a>Générer le fichier XML de la requête  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur **LOCATIONService_LOCATION_x5d.xsd** pour ouvrir le fichier.  
  
2.  Cliquez avec le bouton droit sur **LOCATIONService_LOCATION_x5d.xsd** , puis cliquez sur **Propriétés**. Pour **Nom de fichier d'instance de sortie** , entrez les chemin d'accès et nom suivants pour l'exemple de fichier XML :  
  
     `C:\LABS\PS_TEST\SAMPLEQUERY.XML`  
  
3.  Cliquez sur **OK.** Dans la fenêtre Propriétés, sélectionnez **\<schéma\>** et **référence de racine : obtenir**.  
  
4.  Cliquez avec le bouton droit sur **LOCATIONService_LOCATION_x5d.xsd** , puis cliquez sur **Générer l'instance**. Cette opération génère le fichier **SampleQuery.xml** . Ce fichier sera transmis à l'emplacement de réception en tant qu'entrée de l'adaptateur pour démarrer le processus d'orchestration.  
  
     ![](../core/media/ef65a96c-2daa-44db-ab95-d18b1fda934e.gif "ef65a96c-2daa-44db-ab95-d18b1fda934e")  
  
#### <a name="configure-and-start-the-biztalk-application"></a>Configurer et démarrer l’application BizTalk  
  
1.  Configurez les dossiers afin qu'ils reçoivent les fichiers entrants et envoient les fichiers sortants. Accédez au répertoire **C:\LABS\PS_TEST** , puis créez deux sous-dossiers nommés `FileIn` et `FileOut`.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **PS_Test** puis cliquez sur **configurer**.  
  
     ![](../core/media/e45f4c8b-fc8a-492a-9824-5232eb728d95.gif "e45f4c8b-fc8a-492a-9824-5232eb728d95")  
  
3.  Sélectionnez **Orchestration_1** , puis cliquez sur la zone déroulante **Hôte** . Sélectionnez **BizTalkServerApplication**.  
  
4.  Sous **Ports de réception**, cliquez sur  **\<aucun\>**. Dans la liste déroulante, sélectionnez **Nouveau port de réception**.  
  
5.  For **FileIn**, tapez `FileInPort`, puis cliquez sur **OK**. Le message qui s'affiche indique que vous devez désigner un emplacement de réception. Cliquez sur **OK**, puis sur **Nouveau**.  
  
     ![](../core/media/298638b6-0eb8-49c4-8a2e-485571d070cf.gif "298638b6-0eb8-49c4-8a2e-485571d070cf")  
  
6.  Tapez ou sélectionnez les valeurs de propriété suivantes :  
  
     **Nom de**:`FileInLoc`  
  
     **Type**: **Fichier**  
  
     **Gestionnaire de réception**: **BizTalkServerApplication**  
  
     **Pipeline de réception**: **XMLReceive**  
  
     ![](../core/media/613a5dbc-effe-4827-a72b-d16eef8d0e8a.gif "613a5dbc-effe-4827-a72b-d16eef8d0e8a")  
  
7.  Cliquez sur **Configurer** , tapez `C:\LABS\PS_TEST\FILEIN` sur **Dossier de réception**, puis cliquez sur **OK** à trois reprises.  
  
     ![](../core/media/513eebb0-58ca-4aaa-a33b-31700f9cf7a8.gif "513eebb0-58ca-4aaa-a33b-31700f9cf7a8")  
  
8.  Cliquez sur **\<aucun\>** pour **PeopleSoft_Port** dans la liste déroulante.  
  
9. Sélectionnez **Nouveau port d'envoi** , puis sélectionnez ou tapez les valeurs de propriété suivantes.  
  
     **Nom de**:`PS_Test_Port`  
  
     **Type**: **PeopleSoft**  
  
     **Gestionnaire d'envoi**: **BizTalkServerApplication**  
  
     **Pipelines**: **XMLTransmit** et **XMLReceive**  
  
10. Cliquez sur **Configurer**, puis entrez les valeurs de propriété suivantes :  
  
    1.  **Chemin d'accès au serveur de l'application**: **//Servername:9000**  
  
         NomServeur correspond au serveur d'applications. Il s'agit du nom du serveur ou de l'adresse IP et du numéro de port spécifiques à ce système PeopleSoft.  
  
    2.  **JAVA_HOME**: **C:\J2SDK1.4.2_08**  
  
         Ce chemin d'accès est spécifique à l'installation du Kit de développement logiciel Java sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    3.  **Mot de passe**: \<entrer votre mot de passe PeopleSoft\>  
  
    4.  **Fichiers JAR PeopleSoft 8.x**: **C:\PSJARS\VER841\PSJOA.JAR**  
  
     **Nom d’utilisateur :** \<Entrez votre PeopleSoft UserID\>  
  
11. Cliquez sur **OK** à deux reprises pour fermer les boîtes de dialogue.  
  
12. Dans la Applicationwindow configurer, cliquez sur **\<aucun\>** pour **FileOut** dans la liste déroulante.  
  
13. Sélectionnez **Nouveau port d'envoi** , puis sélectionnez ou tapez les valeurs de propriété suivantes :  
  
     **Nom de**:`FileOutPort`  
  
     **Type**: **Fichier**  
  
     **Gestionnaire d'envoi**: **BizTalkServerApplication**  
  
     **Pipeline d'envoi**: **XMLTransmit**  
  
14. Cliquez sur **Configurer** , tapez`C:\Labs\PS_Test\FileOut` sur **Dossier de destination** . Conservez le **Nom de fichier** sur **%MessageID%.xml** because this results in a unique file sur each message.  
  
15. Cliquez sur **OK** à trois reprises pour fermer les boîtes de dialogue.  
  
16. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez à droite la **PS_Test** application, puis sur **Démarrer**.  
  
     ![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")  
  
#### <a name="test-the-orchestration"></a>Tester l’orchestration  
  
1.  Dans le répertoire **C:\Labs\PS_Test** , modifiez le fichier **Samplequery.xml** comme suit :  
  
    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>AUS01</ns0:LOCATION>  
      <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  
  
    > [!NOTE]
    >  La valeur de données **SHARE** sera utilisée sur tous les systèmes. Toutefois, la valeur que vous utiliserez pour **Emplacement** dans ce fichier XML doit exister sur votre système (voir l'Atelier 1).  
  
2.  Enregistrez les modifications, puis copiez le fichier dans le dossier **C:\Labs\PS_Test\FileIn** . Il s'agit de l'emplacement de réception pour FileIn qui démarre le processus d'orchestration.  
  
3.  Après quelques secondes, un fichier XML doit apparaître dans le dossier **C:\Labs\PS_Test\FileOut** . Il doit contenir les données de l'enregistrement dans lequel l'emplacement est défini sur AUS01.  
  
     ![](../core/media/1320ea3c-b2bc-4717-b200-c3c550079ccb.gif "1320ea3c-b2bc-4717-b200-c3c550079ccb")  
  
     Ces données d'enregistrement retournées doivent correspondre à ce qui a été retourné par la requête sur le système PeopleSoft dans l'Atelier pratique 1 PeopleSoft. En comparant les valeurs obtenu à l’atelier 1, en particulier le **Address1** et **Address2** lignes, ce qui est présenté ici dans le **\<emplacement : ADDRESS1\>** et **\<emplacement : ADDRESS2\>** champs, vous pouvez vérifier que le **obtenir** a fonctionné correctement.  
  
## <a name="summary"></a>Résumé  
 Au cours de cet atelier, vous avez vérifié que tous les composants permettant d'accéder au système PeopleSoft étaient correctement installés. Puis vous avez utilisé [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour créer un projet BizTalk contenant une orchestration. Vous avez configuré l'orchestration BizTalk de manière à ce qu'elle utilise l'adaptateur PeopleSoft pour extraire des données du système PeopleSoft. Pour configurer l'orchestration, vous avez créé des ports d'envoi, des ports de réception et des ports d'envoi/réception. Vous avez lié ces ports à l'adaptateur PeopleSoft, puis affecté des messages aux ports appropriés.  
  
 Une fois le projet BizTalk configuré, vous l'avez créé et déployé à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous avez ensuite configuré la nouvelle application, puis vous l'avez exécutée de manière à ce qu'elle extraie des données du système PeopleSoft. Pour vérifier qu'elle fonctionnait correctement, vous avez comparé le fichier XML de sortie au fichier reçu du système PeopleSoft au cours de l'Atelier 1.