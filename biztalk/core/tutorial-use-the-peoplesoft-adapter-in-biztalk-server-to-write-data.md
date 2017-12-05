---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour PeopleSoft Enterprise pour écrire des données vers PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837dd4db-576d-41c1-9fe8-e1e46861270b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b38c1f5a0bd442404e832274d13ace2b0660c2e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-write-data-to-peoplesoft-enterprise"></a>Didacticiel : écriture de données vers PeopleSoft Enterprise à l'aide de l'adaptateur BizTalk pour PeopleSoft Enterprise
L'adaptateur BizTalk pour PeopleSoft Enterprise permet d'écrire des données dans un système PeopleSoft à l'aide des informations reçues d'un partenaire commercial ou d'une application interne. Cette procédure pas à pas décrit un exemple de Kit de développement logiciel (SDK) qui illustre ces fonctionnalités.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   La plateforme Java 2 doit être installée sur la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur BizTalk pour PeopleSoft Enterprise est exécuté.  
  
-   Le fichier JAR de l’adaptateur d’objet Java PeopleSoft, **psjoa.jar** doivent être copiés vers un dossier qui est accessible à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que l’adaptateur BizTalk pour PeopleSoft Enterprise est en cours d’exécution.  
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] doit être installé sur la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur BizTalk pour PeopleSoft Enterprise est exécuté afin de créer et de déployer l'exemple.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour PeopleSoft Enterprise pour créer un enregistrement dans le système PeopleSoft pour les données dans le fichier XML.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple a été conçu dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et créé pour illustrer les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour PeopleSoft Enterprise avec une orchestration BizTalk.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans le dossier suivant :  
  
 \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftOneWaySend  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|**Nom de fichier de projet d’exécution**|**Description du fichier de projet d’exécution**|  
|----------------------------------|------------------------------------------|  
|OneWaySend.btproj,<br /><br /> OneWaySend.sln|Fichiers de projet et de solution de l'application.|  
|LOCATIONService.xsd,<br /><br /> LOCATIONService_1.xsd,<br /><br /> LOCATIONService_2.xsd|Fichiers de schéma de l'application. **Remarque :** les fichiers de schéma de l’adaptateur dans le projet ont été créés à l’aide de la **Assistant Ajouter les métadonnées de l’adaptateur**. Pour plus d'informations sur l'Assistant Ajouter les métadonnées de l'adaptateur, consultez la rubrique « Ajout de métadonnées d'adaptateur à un projet BizTalk » de la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|PeopleSoftOneWaySend.odx|Orchestration utilisée par l'application.|  
|PeopleSoftOneWaySend.snk|Fichier de clé de nom fort.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
  
#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a>Pour créer une instance de l'adaptateur PeopleSoft Enterprise  
  
1.  Lancer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Cliquez sur **Démarrer**, **tous les programmes**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.  
  
3.  Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...** Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **PeopleSoft**.  
  
5.  Sélectionnez **PeopleSoft Enterprise (r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.  
  
#### <a name="create-a-biztalk-send-port"></a>Pour créer un port d'envoi BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.  
  
2.  Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftOneWaySP**.  
  
4.  Sélectionnez l’adaptateur PeopleSoft dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport**boîte de dialogue.  
  
    > [!NOTE]
    >  Cette valeur correspond au nom spécifié lors de la création de l'adaptateur PeopleSoft Enterprise dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
5.  Entrez les valeurs suivantes pour le **propriétés obligatoires de l’adaptateur**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Chemin d'accès au serveur de l'application|Emplacement de l'ordinateur et du port du serveur de PeopleSoft, par exemple //PSServer:8888 **Remarque :** si vous ne spécifiez pas un numéro de port, le port par défaut (9000) est utilisé pour l’exemple ci-dessus, vous pouvez entrer la valeur //psserver si le serveur de PeopleSoft utilise la valeur de port par défaut (9000).|  
    |JAVA_HOME|Chemin d'accès au répertoire de base associé aux fichiers du Kit de développement logiciel de la plateforme Java 2, par exemple C:\j2sdk1.4.2_08|  
    |Mot de passe|Mot de passe de connexion au système PeopleSoft.|  
    |Fichiers JAR PeopleSoft 8.x|Emplacement du fichier JAR de l’adaptateur d’objet Java PeopleSoft, **psjoa.jar**, par exemple C:\JARS\psjoa.jar.|  
    |Nom d'utilisateur|Nom d'utilisateur pour la connexion au système PeopleSoft.|  
  
6.  Cliquez sur **OK**.  
  
7.  Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.  
  
8.  Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.  
  
#### <a name="create-a-file-receive-port"></a>Pour créer un port de réception du fichier  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.  
  
2.  Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftOneWayFileRP**, puis cliquez sur **OK**.  
  
#### <a name="create-a-file-receive-location"></a>Pour créer un emplacement de réception du fichier  
  
1.  Créez un dossier à surveiller par l'emplacement de réception du fichier (par exemple, C:\Filesource).  
  
2.  Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftOneWayFileRL**.  
  
4.  Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.  
  
5.  Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.  
  
6.  Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.  
  
7.  Cliquez sur l’emplacement de réception, sur **activer**.  
  
#### <a name="modify-the-adapter-schema-target-namespace-property"></a>Pour modifier la propriété d'espace de noms cible du schéma de l'adaptateur  
  
1.  Lancez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et ouvrez le fichier OneWaySend.sln. Cliquez sur **fichier**, **ouvrir**, **projet/Solution...** Pour afficher le **ouvrir le projet** boîte de dialogue.  
  
2.  Accédez au fichier OneWaySend.sln, sélectionnez-le et cliquez sur **ouvrir** pour ouvrir la solution qui contient l’exemple de projet.  
  
3.  Cliquez sur le **vue** menu et sélectionnez **l’Explorateur de solutions** pour afficher l’Explorateur de solutions.  
  
4.  Double-cliquez sur le fichier LOCATIONService_1.xsd dans l'Explorateur de solutions pour l'ouvrir.  
  
5.  Avec le bouton droit le **schéma** nœud de locationservice_1.xsd, puis sélectionnez le **propriétés** option de menu pour afficher les propriétés pour le schéma.  
  
6.  Modifier la **cible Namespace** propriété à utiliser les valeurs appropriées pour le nom de l’adaptateur, par exemple le **cible Namespace** propriété doit se présenter comme suit :  
  
    ```  
    http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
    ```  
  
     Où *PeopleSoft* est le nom de l’adaptateur PeopleSoft, tel qu’affiché dans la Console Administration de BizTalk.  
  
    > [!IMPORTANT]
    >  Si la valeur configurée pour **cible Namespace** ne correspond pas à l’espace de noms spécifié dans l’instance de document d’entrée, un échec de routage se produit lorsque l’instance de document d’entrée est traitée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a>Pour générer une instance de document à partir du schéma de l'adaptateur  
  
1.  Double-cliquez sur **LOCATIONService_1.xsd** dans l’Explorateur de solutions pour ouvrir le fichier dans l’éditeur de schéma.  
  
2.  Avec le bouton droit le  **\<schéma\>**  nœud dans l’éditeur de schéma, puis cliquez sur **propriétés** pour afficher les propriétés du nœud.  
  
3.  Sélectionnez **CreateEx** dans la liste des nœuds disponibles dans le **référence de racine** zone de liste déroulante. Cela doit être fait afin que lorsque vous générez un exemple d’instance de document, il sera générée depuis le **CreateEx** nœud du schéma.  
  
4.  Cliquez sur LOCATIONService_1.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
5.  Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** section.  
  
6.  Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.  
  
7.  Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.  
  
    > [!NOTE]
    >  Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.  
  
8.  Cliquez sur LOCATIONService_1.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.  
  
9. Avec le bouton droit le  **\<schéma\>**  nœud dans l’éditeur de schéma, puis cliquez sur **propriétés** pour afficher les propriétés du nœud.  
  
10. Sélectionnez (**par défaut)** dans la liste des nœuds disponibles dans le **référence de racine** zone de liste déroulante.  
  
#### <a name="modify-the-generated-document-instance"></a>Pour modifier l'instance de document générée  
  
1.  Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez le contenu de telle sorte que les données de ces champs génèrent un enregistrement unique dans le système PeopleSoft : par exemple, le fichier XML ci-dessous décrit les champs d'un enregistrement qui définit un emplacement :  
  
    ```  
    <ns0:CreateEx xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>9991</ns0:LOCATION>  
      <ns0:interactiveMode>true</ns0:interactiveMode>  
       <ns0:properties>  
        <ns0:LOCATION_TBL_sequence>  
          <ns0:LOCATION_TBL>  
            <ns0:COUNTRY>USA</ns0:COUNTRY>  
            <ns0:DESCR>Adapter Test</ns0:DESCR>  
            <ns0:EFFDT>2006-05-31</ns0:EFFDT>  
            <ns0:EFF_STATUS>A</ns0:EFF_STATUS>  
            <ns0:SETID>SHARE</ns0:SETID>  
          </ns0:LOCATION_TBL>  
        </ns0:LOCATION_TBL_sequence>  
      </ns0:properties>  
    </ns0:CreateEx>  
    ```  
  
    > [!NOTE]
    >  Dans l’exemple ci-dessus, *PeopleSoft* est un espace réservé pour le nom réel de la carte tel qu’affiché dans la Console Administration de BizTalk.  
  
2.  Enregistrez l'instance de document modifiée.  
  
#### <a name="build-and-deploy-the-project"></a>création et déploiement du projet ;  
  
1.  Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet.  
  
2.  Cliquez sur le **déploiement** onglet.  
  
3.  Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk**.  
  
4.  Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.  
  
#### <a name="bind-and-enlist-the-orchestration"></a>Pour lier et inscrire l'orchestration  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.  
  
2.  Cliquez sur le **Actualiser** bouton dans la barre d’outils MMC ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la Console d’Administration.  
  
3.  Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.  
  
4.  Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.  
  
5.  Spécifiez les valeurs appropriées pour les options de liaison, par exemple :  
  
    |**Paramètre**|**Valeur**|  
    |-------------------|---------------|  
    |Hôte|BizTalkServerApplication|  
    |FileReceivePort|PeopleSoftOneWayFileRP|  
    |PeopleSoftOneWaySendPort|PeopleSoftOneWaySP|  
  
6.  Cliquez sur OK.  
  
#### <a name="start-the-orchestration"></a>Démarrer l'orchestration  
  
-   Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a>Pour placer une instance de document dans le dossier surveillé par l'emplacement de réception du fichier  
  
-   Copiez l'instance de document créée précédemment dans le dossier surveillé par l'emplacement de réception du fichier.  
  
#### <a name="verify-that-the-peoplesoft-system-is-updated"></a>Pour vérifier la mise à jour du système PeopleSoft  
  
-   Utilisez l'interface Web PeopleSoft pour vérifier que l'enregistrement a été créé à partir des données du fichier XML.  
  
 La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :  
  
1.  L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.  
  
2.  L'orchestration s'abonne à ce message publié et le moteur de messagerie BizTalk active une instance de l'orchestration avant d'envoyer le message à l'instance d'orchestration.  
  
3.  L'instance d'orchestration traite le message à l'aide de la logique spécifiée dans l'orchestration, puis republie le message dans la base de données MessageBox.  
  
4.  Le port d'envoi PeopleSoft s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi PeopleSoft.  
  
5.  Le port d'envoi remet le message à l'adaptateur BizTalk pour PeopleSoft Enterprise.  
  
6.  L'adaptateur BizTalk pour PeopleSoft Enterprise appelle la méthode CreateEx pour créer un enregistrement à l'aide des données du fichier XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels : Utilisation de l’adaptateur BizTalk pour PeopleSoft Enterprise](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)