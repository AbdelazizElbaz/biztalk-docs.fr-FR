---
title: "L’exécution de JD Edwards OneWorld requête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b060d383-a2df-472f-90cc-e79078b0bcfd
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35d05dfe719a9b199d7422f99ef80e888126f01f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executing-a-jd-edwards-oneworld-sample-query"></a>Exécution d'un exemple de requête JD Edwards OneWorld
Le système JD Edwards OneWorld (JDEOW) est accessible à partir d'un système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur JD Edwards OneWorld. Ce dernier fait partie des 8 adaptateurs sectoriels fournis par Microsoft à des fins d'utilisation avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
 Il s'agit de la deuxième partie de l'atelier JD Edwards OneWorld. Au cours de la première partie (Atelier 1), vous avez consulté les données du système JD Edwards OneWorld sans utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou d'autres technologies Microsoft. Dans la deuxième partie (Atelier 2), vous allez créer une orchestration BizTalk au sein d'un projet BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous allez configurer les ports de cette orchestration de manière à ce qu'ils utilisent l'adaptateur JD Edwards OneWorld pour extraire des données du système JD Edwards OneWorld.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]  
  
-   Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   Logiciel client JD Edwards OneWorld  
  
-   Connectivité réseau à un système JD Edwards OneWorld sur un autre serveur  
  
-   Adaptateurs Microsoft BizTalk pour les applications d'entreprise  
  
> [!NOTE]
>  Pour plus d’informations sur l’installation et la configuration des adaptateurs Microsoft BizTalk pour les Applications d’entreprise, consultez [lien hypertexte « http://go.microsoft.com/fwlink/?LinkId=196039 » \t « _blank » http://go.microsoft.com/fwlink/?LinkId=196039](http://go.microsoft.com/fwlink/?LinkId=196039). Ce document inclut des informations de configuration importantes pour les adaptateurs sectoriels JD Edwards, PeopleSoft, JD Edwards OneWorld, TIBCO et Siebel.  
  
## <a name="lab-2---executing-a-jd-edwards-oneworld-sample-query"></a>Atelier 2 : l’exécution de JD Edwards OneWorld requête  
 Dans cet atelier, vous allez exécuter un **obtenir** opération sur le système JD Edwards OneWorld. Vous allez effectuer les tâches suivantes :  
  
-   vérification des composants requis pour JD Edwards OneWorld ;  
  
-   configuration d'un port d'envoi JD Edwards OneWorld dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;  
  
-   création d'un projet d'orchestration BizTalk ;  
  
-   création et déploiement du projet ;  
  
-   test de l'application et affichage de la sortie XML.  
  
 Vous allez utiliser l'adaptateur JD Edwards OneWorld pour accéder aux données du système JD Edwards OneWorld à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Cet adaptateur permet de traiter les objets JD Edwards OneWorld à l'aide de requêtes et de réponses exécutées par une orchestration. De nombreuses méthodes sont disponibles pour un objet de schéma. Cet atelier montre comment utiliser le **Address Book MBF** (méthode).  
  
 Avant d'exécuter une requête de service, vous devez créer des schémas associés aux requêtes et aux réponses de service pour l'objet JD Edwards OneWorld spécifique. L'Assistant Ajouter les éléments générés/Ajout d'adaptateur crée ces schémas en interrogeant directement l'objet de métadonnées de support dans JD Edwards OneWorld. Cet atelier présente les étapes requises pour créer des schémas pour le **Address Book MBF** (méthode) et de traiter une requête.  
  
## <a name="procedures-for-lab-2--executing-a-jd-edwards-oneworld-sample-query"></a>Atelier 2 : exécution d'un exemple de requête JD Edwards OneWorld  
  
### <a name="verifying-the-jd-edwards-oneworld-prerequisites"></a>Vérification des composants requis pour JD Edwards OneWorld  
 Avant de commencer la création d'un projet BizTalk à des fins d'utilisation avec l'adaptateur JD Edwards OneWorld, vous devez vous assurer que les fichiers et l'adaptateur permettant d'accéder au système JD Edwards OneWorld sont configurés correctement. Sur l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'adaptateur JD Edwards OneWorld communique avec le système JD Edwards OneWorld à l'aide de l'interface Java.  
  
 Quatre fichiers sont nécessaires pour l’accès de l’interface appropriée pour un système JD Edwards OneWorld à l’aide de l’adaptateur JD Edwards OneWorld : Connector.jar, Kernel.jar, BTSLIBinterop.jar et JDEJAccess.jar.  
  
-   Les fichiers Connector.jar et Kernel.jar sont fournis avec le système JD Edwards OneWorld et sont obtenus auprès d'un administrateur JD Edwards OneWorld. Ces fichiers se trouvent dans le dossier C:\JDEOWJars.  
  
-   Le fichier BTSLIBinterop.jar est généré par le système JD Edwards OneWorld en suivant les instructions indiquées dans le guide d'installation associé aux adaptateurs. Il se trouve dans le dossier C:\JDEOWJars.  
  
-   Le fichier JDEJAccess.jar fait partie de l'adaptateur JDEOW et est inclus dans l'installation de l'adaptateur. Par défaut, il se trouve dans le C:\Program Files\Microsoft BizTalk Adapters pour applications\j.d d’entreprise. Dossier de \Classes Edwards.  
  
##### <a name="to-verify-the-jd-edwards-oneworld-prerequisites"></a>Pour vérifier les composants requis pour JD Edwards OneWorld  
  
1.  Assurez-vous que les fichiers Connector.jar, Kernel.jar et BTSLIBinterop.jar sont présents dans le dossier C:\JDEOWJars de l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Vérifiez que le fichier JDEJAccess.jar existe sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur dans le C:\Program Files\Microsoft BizTalk Adapters pour applications\j.d d’entreprise. Dossier de \Classes Edwards.  
  
3.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
### <a name="configuring-biztalk-send-ports"></a>Configuration des ports d'envoi de BizTalk  
 À présent, vous allez vérifier que l'adaptateur JD Edwards OneWorld est installé et vous allez créer le port d'envoi de JD Edwards OneWorld.  
  
##### <a name="to-verify-that-the-jd-edwards-oneworld-adapter-is-installed-in-includepragueincludesprague-mdmd"></a>Pour vérifier que l'adaptateur JD Edwards OneWorld est installé dans [!INCLUDE[prague](../includes/prague-md.md)]  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez  **Paramètres de plateforme**, puis développez **cartes**.  
  
     Vérifiez que le **JDE_OneWorld** adaptateur est installé et sur la liste. Si l’adaptateur JD Edwards OneWorld n’est pas installé, installez les adaptateurs BizTalk pour les Applications d’entreprise (voir la section « Conditions préalables » plus haut). Une fois que les adaptateurs sont installés, cliquez sur **cartes** puis cliquez sur **nouveau - adaptateur** pour installer l’adaptateur JD Edwards OneWorld. Pour que cette opération soit prise en compte, vous devez redémarrer l'instance d'hôte.  
  
##### <a name="to-create-the-jd-edwards-oneworld-send-port"></a>Pour créer le port d'envoi de JD Edwards OneWorld  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez  **Applications**, puis développez **BizTalk Application 1**.  
  
2.  Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**. Pour ces champs, entrez les valeurs suivantes :  
  
    1.  **Nom :**  `JDE_OneWorldPort`  
  
    2.  **Type :**  `JDE_OneWorld`  
  
    3.  **Gestionnaire d’envoi :**  `BizTalkServerApplication`  
  
    4.  **Pipeline d’envoi :**  `XMLTransmit`  
  
    5.  **Pipeline de réception :**  `XMLReceive`  
  
3.  Cliquez sur **Configurer**, puis entrez les valeurs de propriété suivantes :  
  
    1.  **Hôte :** \<Entrez votre nom d’hôte JDEOW >  
  
    2.  **JAVA_HOME :**`C:\j2sdk1.4.2_08`  
  
    3.  **Environnement JDEdwards :** \<Entrez votre environnement JDEOW >  
  
    4.  **Fichiers JAR JDEdwards :** \<Entrez le chemin d’accès complet des fichiers JAR >  
  
         `C:\JDEOWJars\BTSLIBInterop.jar; C:\JDEOWJars\Connector.jar; C:\JDEOWJars\Kernel.jar;C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D. Edwards OneWorld®\Classes\JDEJAccess.jar`  
  
    5.  **Mot de passe :** utilisez la liste déroulante, puis entrez votre mot de passe JD Edwards OneWorld.  
  
    6.  **Port :**  `6009`  
  
    7.  **Nom d’utilisateur :** \<Entrez votre nom d’utilisateur JD Edwards >  
  
     ![](../core/media/jdeow-transportproperties-configurebutton.gif "JDEOW_TransportProperties_ConfigureButton")  
  
4.  Cliquez sur **OK** à deux reprises pour fermer la **propriétés de Port d’envoi** boîte de dialogue.  
  
### <a name="creating-a-biztalk-orchestration-project"></a>Création d'un projet d'orchestration BizTalk  
 Vous allez à présent créer un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et y configurer une orchestration pour gérer les communications entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le système JD Edwards OneWorld. Vous allez ajouter des ports d'envoi et de réception, créer le projet, puis le déployer.  
  
##### <a name="to-create-the-biztalk-orchestration-project-in-visual-studio"></a>Pour créer le projet d'orchestration BizTalk dans Visual Studio  
  
1.  Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis créez un projet BizTalk dans le dossier C:\LABS. Dans le menu **Fichier** , cliquez sur **Nouveau**. La boîte de dialogue **Nouveau projet** s'affiche. Dans la boîte de dialogue **Modèles** , sélectionnez **Projet BizTalk Server vide** Entrez `JDE_OW_Test` comme le nom unique du projet, puis cliquez sur **OK**.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter**, puis sur **Ajouter les éléments générés**. Dans le volet des catégories, sélectionnez **ajouter les métadonnées de l’adaptateur**, dans le volet Modèles, sélectionnez **ajouter les métadonnées de l’adaptateur**, puis cliquez sur **ajouter**.  
  
3.  Dans l’Assistant Ajout d’adaptateur, sélectionnez le **JD Edwards OneWorld** carte, sélectionnez le **JDE_OneWorldPort** port d’envoi qui vous avez créé dans la procédure précédente, puis cliquez sur **suivant**.  
  
     ![](../core/media/jdeow-addadapterwizardselectadapter.gif "JDEOW_AddAdapterWizardSelectAdapter")  
  
4.  Sur le **sélectionner les Services à importer** page, ouvrez **JD Edwards OneWorld**. Le système JDEOW est contacté via l'adaptateur à l'aide du programme BrowsingAgent. BrowsingAgent renvoie les services suivants.  
  
     ![](../core/media/jdeow-callbsfn.gif "JDEOW_CALLBSFN")  
  
5.  Développez **CALLBSFN** et faites défiler jusqu'à **N0100041 - Address Book MBF**. Sélectionnez N0100041, puis cliquez sur **Terminer**.  
  
6.  L'Explorateur de solutions inclut une nouvelle orchestration BizTalk comprenant deux nouveaux fichiers de schémas associés. Ces derniers sont créés par l'Assistant Ajout d'adaptateur. Double-cliquez sur le fichier **BizTalk Orchestration.odx** pour ouvrir l'orchestration.  
  
     ![](../core/media/jdeow-solution-explorer-jde-ow-test-schemas.gif "JDEOW_Solution_Explorer_JDE_OW_TEST_Schemas")  
  
 Celle-ci accepte comme entrée en provenance de l'adaptateur FILE un fichier XML mis en forme pour le système JD Edwards OneWorld. L'orchestration fait appel à l'adaptateur JD Edwards OneWorld pour envoyer le fichier XML au système JD Edwards OneWorld. JD Edwards OneWorld traite la requête et génère un fichier XML de sortie qui contient les résultats. Ce fichier XML est renvoyé à l'orchestration via l'adaptateur JD Edwards OneWorld, et l'adaptateur FILE écrit le fichier XML à l'emplacement de sortie sur le disque.  
  
 Pour terminer l'orchestration, vous devez créer et configurer les ports pour recevoir et envoyer les fichiers XML. Commencez par configurer un port de réception que l'adaptateur FILE utilisera pour entrer le XML contenant la requête dans l'orchestration sur le disque.  
  
##### <a name="to-configure-a-receive-port-to-accept-the-input-xml-file"></a>Pour configurer un port de réception afin d'accepter le fichier d'entrée XML  
  
1.  Double-cliquez sur le fichier **BizTalk Orchestration.odx** pour ouvrir l'orchestration.  
  
2.  Dans le fichier Biztalkorchestration.odx, avec le bouton droit de la surface du port de gauche, puis **nouveau Port configuré**. L'Assistant Configuration du port démarre. Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
3.  Sur le **propriétés de Port** , entrez `JDE_File_In` pour **nom**, puis cliquez sur **suivant**.  
  
4.  Dans la page **Sélectionner un type de port** , sélectionnez **Créer un type de port**, puis entrez ou sélectionnez les valeurs de propriété suivantes :  
  
     **Nom du Type de port**:`JDE_FileIn_Port`  
  
     **Modèle de communication**: **Unidirectionnel**  
  
     **Restrictions d'accès**: **Interne - limité au projet**  
  
5.  Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :  
  
     **Direction de communication du port**: **Toujours recevoir les messages sur ce port**  
  
     **Liaison de port**: **Spécifier plus tard**  
  
6.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
 Créez ensuite un port d'envoi/réception pour envoyer le fichier d'entrée XML initial contenant la requête passée au système JD Edwards OneWorld. Ce port reçoit également un fichier XML de sortie contenant les résultats de la requête issus de l'appel auprès du système JD Edwards OneWorld.  
  
##### <a name="to-configure-a-sendreceive-port-to-interface-with-jd-edwards-oneworld"></a>Pour configurer un port d'envoi/réception pour interagir avec JD Edwards OneWorld  
  
1.  Dans le fichier Biztalkorchestration.odx, avec le bouton droit de la surface du port de droite, puis **nouveau Port configuré**. L'Assistant Configuration du port démarre. Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
2.  Dans la page **Sélectionner un type de port** , sélectionnez **Utiliser un type de port existant**. Sous **Types de ports disponibles**, sélectionnez **JD_OW_Test.N0100041**, puis cliquez sur **suivant**.  
  
     ![](../core/media/a421358c-6e90-4fe0-b243-6beb1b51955a.gif "a421358c-6e90-4fe0-b243-6beb1b51955a")  
  
3.  Sélectionnez les valeurs de propriété suivantes :  
  
     **Direction de communication du port**: **puis-je envoyer une demande et recevoir une réponse**  
  
     **Liaison de port**: **Spécifier plus tard**  
  
4.  Cliquez sur **Suivant**, puis sur **Terminer**. Sur la surface de port, le port et les méthodes disponibles s'affichent.  
  
 Pour terminer, configurez un port d'envoi que l'adaptateur FILE utilisera pour transmettre en sortie le XML contenant les résultats de la requête vers le disque.  
  
##### <a name="to-configure-a-send-port-to-output-the-xml-file-to-disk"></a>Pour configurer un port d'envoi pour transmettre en sortie le fichier XML vers le disque  
  
1.  Dans le fichier Biztalkorchestration.odx, avec le bouton droit de la surface du port de gauche, puis **nouveau Port configuré**. L'Assistant Configuration du port démarre. Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
2.  Sur le **propriétés de Port** , entrez `JDE_FileOut` pour **nom**, puis cliquez sur **suivant**.  
  
3.  Dans la page **Sélectionner un type de port** , sélectionnez **Créer un type de port**, puis entrez ou sélectionnez les valeurs de propriété suivantes :  
  
     **Nom du Type de port**:`JDE_FileOut_Port`  
  
     **Modèle de communication**: **Unidirectionnel**  
  
     **Restrictions d'accès**: **Interne - limité au projet**  
  
4.  Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :  
  
     **Direction de communication du port**: **Toujours envoyer les messages sur ce port**  
  
     **Liaison de port**: **Spécifier plus tard**  
  
5.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
 Les nouveaux ports et les méthodes disponibles pour les services JD Edwards OneWorld s'affichent sur la surface du port. Lors d'une étape ultérieure, vous indiquerez à l'adaptateur JD Edwards OneWorld d'envoyer et de recevoir des fichiers à partir du système JD Edwards OneWorld.  
  
 Le **JDE_File_In** et **JDE_File_Out** ports que vous venez de créer nécessitent des types de messages associés.  
  
##### <a name="to-assign-message-types-to-the-ports"></a>Pour attribuer des types de messages aux ports  
  
1.  Sur la surface du port de gauche, sur le **JDE_File_In** de port, cliquez sur **demande**. Dans la fenêtre Propriétés, développez **Type de Message**, développez **messages à parties multiples**, puis cliquez sur **JDE_OW_TestAddressBookMasterMBF**.  
  
2.  Sur la surface du port de gauche, sur le **JDE_File_Out** de port, cliquez sur **demande**. Dans la fenêtre Propriétés, développez **Type de Message**, développez **messages à parties multiples**, puis cliquez sur **JDE_OW_TestAddressBookMasterMBFResponse**.  
  
 Insérez deux **envoyer** formes et deux **réception** formes dans l’orchestration à lier aux ports.  
  
##### <a name="to-add-send-and-receive-shapes"></a>Pour ajouter des formes Envoi et Réception  
  
1.  Faites glisser un composant **Réception** à partir de la Boîte à outils, puis déposez-le sous le début de l'orchestration (cercle vert). Cliquez sur le **réception** mettre en forme et dans la fenêtre Propriétés, entrez `Get_File` pour le **nom**et la valeur **activer** à `true`. Cette opération permet d'activer l'orchestration lorsque ce port de réception reçoit un document entrant.  
  
2.  Faites glisser un **envoyer** composant à partir de la boîte à outils et déposez-le sous le **GetFileReceive** forme. Cliquez sur la nouvelle **envoyer** mettre en forme et dans la fenêtre Propriétés, entrez `SendToJDEOW` pour le **nom**.  
  
3.  Faites glisser un **réception** composant à partir de la boîte à outils et déposez-le sous le **SendToJDEOWSend** forme. Cliquez sur le **réception** mettre en forme et dans la fenêtre Propriétés, entrez `JDEOW_Resp` pour le **nom**.  
  
4.  Faites glisser un **envoyer** composant à partir de la boîte à outils et déposez-le sous le **JDEOW_RespReceive** forme. Cliquez sur la nouvelle **envoyer** mettre en forme et dans la fenêtre Propriétés, entrez `FileToDisk` pour le **nom**.  
  
     ![](../core/media/jdeow-orchestration-multipartmessages.gif "JDEOW_Orchestration_MultiPartMessages")  
  
5.  Connecter le **JDE_FileIn** port pour le **GetFileReceive** composant.  
  
6.  Connecter le **JDE_FileOut** port pour le **FileToDiskReceive** composant.  
  
7.  Accédez à **Vue Orchestration** et développez **Messages**. L’identificateur **Message_1** à `MsgToJDEOW`et pour **Message_2** à`JDEOW_Resp.`  
  
8.  Mettez en surbrillance le **SendToJDEOWSend** composant et définissez son **Message** propriété **MsgToJDEOW**.  
  
9. Mettez en surbrillance le **JDEOW_RespReceive** composant et définissez son **Message** propriété **JDEOW_Resp**.  
  
10. Se connecter **SendToJDEOW** à la **demande** partie de la **JDE_OW_Port** port.  
  
11. Se connecter **JDEOW_Resp** à la **réponse** partie de la **JDE_OW_Port** port.  
  
     ![](../core/media/jdeow-portsurface-connectcomponentstoports.gif "JDEOW_PortSurface_ConnectComponentsToPorts")  
  
### <a name="building-and-deploying-the-project"></a>Création et déploiement du projet  
 Le projet BizTalk étant à présent terminé, vous pouvez le créer et le déployer dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
##### <a name="to-build-and-deploy-the-project"></a>Pour créer et déployer le projet  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  Pour créer le projet, un fichier de clé de nom fort est nécessaire. Pour en créer un, à l'invite de commandes, entrez le code suivant :  
  
     **sn -k labs.snk**  
  
3.  Dans l’Explorateur de solutions, cliquez sur le **JD_OW_Test** de projet, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
4.  Cliquez sur l'onglet **Signature** .  
  
5.  Sélectionnez l'option **Signer l'assembly** , cliquez sur l'option **Choisir un fichier de clé de nom fort** dans la liste déroulante, puis sur **Parcourir**.  
  
6.  Recherchez puis sélectionnez le fichier de clé : **labs.snk**, puis cliquez sur **Ouvrir**.  
  
7.  Dans le Concepteur de projet, cliquez sur l'onglet **Déploiement** .  
  
8.  Définir le **nom de l’Application** à `JDE_OW_Test`.  
  
9. Dans l’Explorateur de solutions, cliquez sur le **JDE_OW_Test** de projet, puis cliquez sur **générer.**  
  
     ![](../core/media/jdeow-buildcompleteoutput.gif "JDEOW_BuildCompleteOutput")  
  
10. Une fois la build terminée, cliquez sur le **XX_JD Edwards OneWorldQuery** de projet, puis cliquez sur **déployer**. La sortie suivante s'affiche dans la fenêtre Sortie :  
  
     ![](../core/media/jdeow-deployoutput.gif "JDEOW_DeployOutput")  
  
### <a name="testing-the-application-and-viewing-the-xml-output"></a>Test de l'application et affichage de la sortie XML  
 Vous allez à présent tester l'application que vous avez créée et déployée. Vous allez créer le fichier XML qui démarre le processus d'orchestration, puis vous allez configurer les dossiers afin qu'ils reçoivent et envoient des fichiers XML au sein de l'application. Une fois l'application configurée, vous allez l'exécuter et afficher les fichiers XML qu'elle renvoie.  
  
##### <a name="to-generate-the-xml-file-for-the-query"></a>Pour générer le fichier XML pour la requête  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur **N0100041Service_N0100041.xsd** pour ouvrir le fichier.  
  
2.  Avec le bouton droit **N0100041Service_N0100041.xsd** puis cliquez sur **propriétés**. Pour **Nom de fichier d'instance de sortie** , entrez les chemin d'accès et nom suivants pour l'exemple de fichier XML :  
  
     `C:\LABS\JDE_OW_TEST\SAMPLE.XML`  
  
3.  Cliquez sur **OK.** Dans la fenêtre Propriétés, sélectionnez  **\<schéma >** et **référence de racine :** à `AddressBookMasterMBF`. Cela entraîne le code XML généré inclure uniquement les **requête** xml.  
  
     ![](../core/media/jdeow-jde-ow-test-msvisualstudio-schemas.gif "JDEOW_JDE_OW_Test_MSVISUALSTUDIO_SCHEMAS")  
  
4.  Avec le bouton droit **N0100041Service_N0100041.xsd** puis cliquez sur **générer l’Instance**. Cette opération génère le **Sample.xml** fichier. Ce fichier sera transmis à l'emplacement de réception en tant qu'entrée de l'adaptateur pour démarrer le processus d'orchestration.  
  
##### <a name="to-configure-and-start-the-biztalk-application"></a>Pour configurer et démarrer l'application BizTalk  
  
1.  Configurez les dossiers afin qu'ils reçoivent les fichiers entrants et envoient les fichiers sortants. Accédez à **C:\LABS\JDE_OW_Test** et créez deux sous-dossiers nommés `FileIn` et `FileOut`.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez**Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.  
  
3.  Avec le bouton droit **JDE_OW_Test**, puis cliquez sur **configurer**.  
  
     ![](../core/media/jdeow-configureapplicationjde-ow-test.gif "JDEOW_ConfigureApplicationJDE_OW_Test")  
  
4.  Sélectionnez **Orchestration_1** , puis cliquez sur la zone déroulante **Hôte** . Sélectionnez **BizTalkServerApplication**.  
  
5.  Sous **Ports de réception**, cliquez sur  **\<aucun >**. Dans la liste déroulante, sélectionnez **Nouveau port de réception**.  
  
6.  Pour **nom**, type `JDE_FileIn_Port`, puis cliquez sur **OK**. Le message qui s'affiche indique que vous devez désigner un emplacement de réception. Cliquez sur **OK**, puis sur **Nouveau**.  
  
     ![](../core/media/jdeow-filein-port-receiveportproperties.gif "JDEOW_FileIn_Port_ReceivePortProperties")  
  
7.  Tapez ou sélectionnez les valeurs de propriété suivantes :  
  
     **Nom**: JDE_`FileInLoc`  
  
     **Type**: **Fichier**  
  
     **Gestionnaire de réception**: **BizTalkServerApplication**  
  
     **Pipeline de réception**: **XMLReceive**  
  
     ![](../core/media/jdeow-filein-loc-receivelocationproperties.gif "JDEOW_FileIn_Loc_ReceiveLocationProperties")  
  
8.  Cliquez sur **configurer**, type `C:\LABS\JDE_OW_Test\FileIn` pour **dossier de réception**, puis cliquez sur **OK** trois fois.  
  
     ![](../core/media/jdeow-file-transport-properties-filein.gif "JDEOW_File_Transport_Properties_FileIn")  
  
9. Cliquez sur  **\<aucun >** pour **JDE_OW_Port** dans la liste déroulante.  
  
10. Sélectionnez **nouveau Port d’envoi** , puis sélectionnez ou tapez les valeurs suivantes pour les propriétés :  
  
     **Nom de**:`JDE_OW_Port`  
  
     **Type**: **JDE_OneWorld**  
  
     **Gestionnaire d'envoi**: **BizTalkServerApplication**  
  
     **Pipelines**: **XMLTransmit** et **XMLReceive**  
  
11. Cliquez sur **Configurer**, puis entrez les valeurs de propriété suivantes :  
  
     **Hôte :** \<Entrez votre nom d’hôte JDEOW >  
  
     **JAVA_HOME :**`C:\j2sdk1.4.2_08`  
  
     **Environnement JDEdwards :** \<Entrez votre environnement JDEOW >  
  
     **Fichiers JAR JDEdwards :**<enter full path of JAR files>  
  
     `C:JDEOWJarsBTSLIBInterop.jar; C:JDEOWJarsConnector.jar; C:JDEOWJarsKernel.jar;C:Program FilesMicrosoft BizTalk Adapters for Enterprise ApplicationsJ.D. Edwards OneWorld®ClassesJDEJAccess.jar`  
  
     **Mot de passe :** utilisez la liste déroulante, puis entrez votre mot de passe JD Edwards OneWorld.  
  
     **Port :**  `6009`  
  
     **Nom d’utilisateur :**<enter your JD Edwards User Name>  
  
     ![](../core/media/jdeow-transportproperties-configurebutton2.gif "JDEOW_TransportProperties_ConfigureButton2")  
  
12. Cliquez sur **OK** à deux reprises pour fermer les boîtes de dialogue.  
  
13. Dans la Applicationwindow configurer, cliquez sur  **\<aucun >** pour **JDE_FileOut** dans la liste déroulante.  
  
14. Sélectionnez **Nouveau port d'envoi** , puis sélectionnez ou tapez les valeurs de propriété suivantes :  
  
     **Nom de**:`FileOutPort`  
  
     **Type**: **Fichier**  
  
     **Gestionnaire d'envoi**: **BizTalkServerApplication**  
  
     **Pipeline d'envoi**: **XMLTransmit**  
  
15. Cliquez sur **configurer** et type`C:\Labs\JDE_OW_Test\FileOut` pour **dossier de Destination.** . Conservez le **Nom de fichier** sur **%MessageID%.xml** because this results in a unique file sur each message.  
  
     ![](../core/media/jdeow-file-transport-properties-fileout.gif "JDEOW_File_Transport_Properties_FileOut")  
  
16. Cliquez sur **OK** à trois reprises pour fermer les boîtes de dialogue.  
  
17. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez à droite la **JDE_OW_Test** application, puis sur **Démarrer**.  
  
##### <a name="to-test-the-orchestration"></a>Pour tester l'orchestration  
  
1.  Dans le **C:\Labs\JDE_OW_Test** Active le **Sample.xml** fichier apparaîtront en tant que :  
  
     ![](../core/media/jdeow-samplexml-notepad-addressbookmastermbf.gif "JDEOW_SampleXML_Notepad_AddressBookMasterMBF")  
  
2.  Modifier la **Sample.xml** fichier à supprimer tout sauf la **cActionCode** et **mnAddressBookNumber** éléments.  
  
     ![](../core/media/jdeow-samplexml-notepad-cactioncode.gif "JDEOW_SampleXML_Notepad_cActionCode")  
  
3.  Pour le **cActionCode** élément insérer la lettre `i`.  
  
4.  Pour **mnAddressBookNumber** insérer le nombre `500`.  
  
5.  Enregistrer les modifications et copiez le fichier dans le **C:\Labs\JDE_OW_Test\FileIn** dossier. Il s'agit de l'emplacement de réception qui démarre le processus d'orchestration.  
  
6.  En quelques secondes, un fichier XML doit apparaître dans le **C:\Labs\JDE_OW_Test\FileOut** dossier. Il doit contenir tous les enregistrements dans lesquels l'adresse est définie sur 500.  
  
     ![](../core/media/jdeow-xml-output-jde-callbsfn.gif "JDEOW_XML_Output_JDE_CALLBSFN")  
  
     Ces données d’enregistrement retourné doivent correspondre à des données retournées par la requête sur le système JD Edwards OneWorld dans l’atelier 1. En comparant les enregistrements que vous avez obtenue dans l’atelier 1, vous pouvez vérifier que le **obtenir** a fonctionné correctement.  
  
## <a name="summary"></a>Résumé  
 Au cours de cet atelier, vous avez vérifié que tous les composants permettant d'accéder au système JD Edwards OneWorld étaient correctement installés. Puis vous avez utilisé [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour créer un projet BizTalk contenant une orchestration. Vous avez configuré l'orchestration BizTalk de manière à ce qu'elle utilise l'adaptateur JD Edwards OneWorld pour extraire des données du système JD Edwards OneWorld. Pour configurer l'orchestration, vous avez créé des ports d'envoi, des ports de réception et des ports d'envoi/réception. Vous avez lié ces ports à l'adaptateur JD Edwards OneWorld, puis affecté des messages aux ports appropriés.  
  
 Une fois le projet BizTalk configuré, vous l'avez créé et déployé à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous avez ensuite configuré la nouvelle application, puis vous l'avez exécutée de manière à ce qu'elle extraie des données du système JD Edwards OneWorld. Pour vérifier qu'elle fonctionnait correctement, vous avez comparé le fichier XML de sortie au fichier reçu du système JD Edwards OneWorld au cours de l'atelier 1.