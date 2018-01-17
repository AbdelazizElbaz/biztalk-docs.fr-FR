---
title: "Fichier d’adaptateur (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, File adapters
- File adapters, examples
ms.assetid: d59cecb4-6353-44d5-b8d6-316446758536
caps.latest.revision: "46"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de68c57c6b435f85edf630a7b224c5d58ffd0cd6
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="file-adapter-biztalk-server-sample"></a>Adaptateur file (exemple BizTalk Server)
L’exemple d’adaptateur de fichier est écrit en Microsoft Visual c# .NET pour fonctionner avec Microsoft BizTalk Server. Il fournit un code pour créer un adaptateur dynamique ou un adaptateur statique.  La procédure suivante ne présente cependant que l'adaptateur statique. Un adaptateur statique est un adaptateur comprenant un jeu statique de schémas et aucune interface utilisateur personnalisée. Un adaptateur dynamique possède une interface utilisateur personnalisée et, potentiellement, un jeu dynamique de schémas. Les adaptateurs statiques et dynamiques utilisent tous deux l'assistant Ajout d'adaptateur pour ajouter leurs schémas à un projet BizTalk.  
  
> [!NOTE]
>  L’exemple d’adaptateur de fichier n’est pas le même que l’adaptateur de fichier natif fourni avec BizTalk Server. Par conséquent, lorsque vous sélectionnez le type de transport pour utiliser cet exemple, sélectionnez "statique" au lieu de FICHIER.  
  
 L'adaptateur dynamique comprenant une interface utilisateur personnalisée et, potentiellement, un jeu dynamique de schémas nécessite un code supplémentaire côté gestion de l'adaptateur. Pour mieux comprendre l’utilisation de l’ensemble dynamique de schémas, consultez [Configuration dynamique de l’adaptateur au moment du Design](../core/dynamic-design-time-adapter-configuration.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple d'adaptateur copie des fichiers d'un dossier de fichiers et les soumet à BizTalk en tant que messages ou prend des messages de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les dépose dans un dossier de fichiers. Il fournit un code pour créer un adaptateur dynamique ou un adaptateur statique ; la procédure suivante ne présente cependant que l'adaptateur statique. Un adaptateur statique est un adaptateur comprenant un jeu statique de schémas et aucune interface utilisateur personnalisée. Un adaptateur dynamique possède une interface utilisateur personnalisée et, potentiellement, un jeu dynamique de schémas. Les adaptateurs statiques et dynamiques utilisent tous deux l'assistant Ajout d'adaptateur pour ajouter leurs schémas à un projet BizTalk.  
  
 Vous pouvez utiliser l'exemple d'adaptateur de fichiers comme modèle à partir duquel vous pourrez créer d'autres adaptateurs personnalisés.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>**\AdaptersDevelopment\File carte**  
  
> [!NOTE]
>  L’emplacement par défaut \< *exemples de chemin* \> est *% ProgramFiles%*\Microsoft BizTalk Server\SDK\Samples lorsque BizTalk Server est installé sur un ordinateur exécutant une version 32 bits version de Windows. L’emplacement par défaut \< *exemples de chemin* \> est *(x 86) %*\Microsoft BizTalk Server\SDK\Samples lorsque BizTalk Server est installé sur un ordinateur exécutant un 64 - version de bits de Windows. Pour déterminer les valeurs associées à la *% ProgramFiles%* ou *(x 86) %* type variables d’environnement **echo %ProgramFiles%** ou **echo % (X 86) %** à l’invite de commandes et appuyez sur ENTRÉE. Si l’exécution de cet exemple sur un système d’exploitation de 64 bits, vous devez modifier toutes les références dans un des fichiers .reg de **% ProgramFiles%** à **(x 86) %** avant d’exécuter les fichiers .reg.  
  
 Les tableaux suivants montrent les fichiers de cet exemple et décrivent leur finalité.  
  
|\Fichiers d'adaptateur de fichiers| Description|  
|--------------------------|-----------------|  
|\Fichiers de projet BizTalk|Contient le projet d'atelier de test d'adaptateur, utilisé pour tester l'exemple d'adaptateur.|  
|\Fichiers de phase de conception|Contient le projet de phase de conception et de gestion (AdapterManagement.csproj).|  
|\Fichiers exécutables|Contient les projets de réception et de transmission de copie de fichier exécutable (DotNetFile.csproj).|  
|DynamicAdapterManagement.reg|Inscrit l'exemple d'adaptateur dynamique.|  
|Instance.xml|Fichier d'exemple à passer dans l'adaptateur de fichiers.|  
|StaticAdapterManagement.reg|Inscrit l'exemple d'adaptateur statique.|  
  
|\Projet BizTalk\Fichiers d'atelier de test d'adaptateur| Description|  
|----------------------------------------------|-----------------|  
|AdapterHarness.odx, AdapterHarness.sln, AdapterHarnessProject.btproj|Fournit un projet, une solution, et des fichiers associés pour le projet BizTalk.|  
|mySchema.xsd|Fournit le schéma Instance.xml attendu par l'orchestration d'atelier de test en provenance de la partie réception de l'adaptateur, ainsi que le schéma de l'Instance.xml transmis à la partie envoi de l'adaptateur par l'orchestration.|  
  
|\Phase de conception\Fichiers de gestion d'adaptateur| Description|  
|---------------------------------------------|-----------------|  
|AdapterManagement.cs, AdapterManagement.csproj, AdapterManagement.sln|Projet, solution, et fichiers associés pour la phase de conception de l'adaptateur.|  
|AssemblyInfo.cs|Contient des informations d'assembly pour cet exemple.|  
|CategorySchema2.xml|Pas utilisé par l'exemple d'adaptateur.|  
|CategorySchema.xml|Contient l'arborescence d'organisation du service pour l'adaptateur statique.|  
|DotNetFileResource.resx|Contient des ressources.|  
|ReceiveHandler.xsd, ReceiveLocation.xsd|Contient un gestionnaire côté réception et des schémas de propriétés personnalisées de point de terminaison|  
|service1.wsdl|Contient des définitions d'opérations pour l'adaptateur.|  
|TransmitHandler.xsd, TransmitLocation.xsd|Contient un gestionnaire côté transmission et des schémas de propriétés personnalisées de point de terminaison|  
  
|\Fichiers exécutables| Description|  
|---------------------|-----------------|  
|DotNetFile.csproj, DotNetFile.sln,<br /><br /> AssemblyInfo.cs,<br /><br /> DotNetFileExceptions.cs, DotNetFileProperties.cs, DotNetFileReceiver.cs, DotNetFileReceiverEndPoint.cs, DotNetFileTransmitter.cs,<br /><br /> DotNetFileTransmitterEndpoint.cs,<br /><br /> DotNetFileAsyncTransmitterBatch.cs,<br /><br /> BatchMessage.cs|Fichiers pour les adaptateurs d'envoi et de réception de copie de fichiers exécutables. Vous pouvez modifier et enregistrer ces fichiers sous un nouveau nom pour des composants personnalisés.<br /><br /> DotNetFile.csproj et DotNetFile.sln sont les fichiers projet et solution.<br /><br /> AssemblyInfo.cs contient des informations d'assembly pour cet exemple.<br /><br /> DotNetFileReceiver.cs lit les fichiers à partir des emplacements de réception et les soumet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].<br /><br /> DotNetFileExceptions.cs implémente un code pour gérer les exceptions survenant pendant le traitement du message<br /><br /> DotNetFileProperties.cs contient des propriétés communes aux opérations de réception et d'envoi<br /><br /> BatchMessage.cs implémente une messagerie par lot.<br /><br /> DotNetFileReceiverEndPoint.cs est une classe correspondant à un emplacement de réception/URI.  Il gère l'interrogation du dossier donné quant à de nouveaux messages<br /><br /> DotNetFileTransmitter.cs est une classe singleton pour un adaptateur d'envoi DotNetFile. Tous les messages allant vers divers ports d'envoi de ce type d'adaptateur passent par cette classe<br /><br /> DotNetFileTransmitterEndpoint.cs gère la transmission des messages.|  
  
|\SDK\Samples\AdaptersDevelopment\BaseAdapter\v1.0.2 files| Description|  
|--------------------------------------------------------------------|-----------------|  
|Adapter.cs, AdapterException.cs, AsyncTransmitter.cs, batch.cs, ConfigProperties.cs, ControlledTermination.cs, IManageEndpoints.cs, Receiver.cs, ReceiverEndpoint.cs|Fournit des classes qui constituent l'adaptateur de base. Vous pouvez utiliser celles-ci pour créer vos propres adaptateurs.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez l'exemple d'adaptateur de fichiers comme modèle à partir duquel vous pourrez créer d'autres adaptateurs personnalisés.  
  
## <a name="building-this-sample"></a>Création de cet exemple  
  
> [!IMPORTANT]
>  Si l'installation BizTalk est 64 bits ou si son emplacement a été modifié, les valeurs OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath doivent être modifiées en conséquence.  
  
 Utilisez la procédure suivante pour créer et initialiser l'exemple d'adaptateur de fichiers.  
  
#### <a name="to-create-a-strong-name-key-for-the-dotnetfileadapter-projects-and-the-base-adapter-project"></a>Pour créer une clé de nom fort pour les projets DotNetFileAdapter et le projet d'adaptateur de base  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
    > [!NOTE]
    >  Exécutez l'invite de commandes en tant qu'administrateur.  
  
2.  Changez de répertoire en cours pour le \< *exemples de chemin*\>**\AdaptersDevelopment\BaseAdapter\v1.0.2** active.  
  
3.  À l’invite de commandes, tapez **sn – k BaseAdapter.snk** puis appuyez sur ENTRÉE. Ce fichier .snk peut déjà exister si d'autres exemples ont été exécutés auparavant. Si c'est le cas, vous pouvez aller directement à l'étape 4 et sauter cette étape.  
  
4.  Changez de répertoire en cours pour le \< *exemples de chemin*\>\\**AdaptersDevelopment\File Adapter\Runtime** active.  
  
5.  À l’invite de commandes, tapez **sn – k DotNetFileAdapter.snk** puis appuyez sur ENTRÉE.  
  
6.  À l’invite de commandes, tapez **quitter** puis appuyez sur ENTRÉE pour fermer la fenêtre d’invite de commandes.  
  
#### <a name="to-build-the-receiver-run-time-project"></a>Pour créer le projet exécution de récepteur  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.  
  
2.  Accédez à la \< *exemples de chemin*\>**« \AdaptersDevelopment\File Adapter\Runtime »** active et double-cliquez sur **DotNetFile.sln**.  
  
3.  Pour régénérer le projet d’exécution de récepteur d’adaptateur, dans l’Explorateur de solutions, cliquez sur **DotNetFile**, puis cliquez sur **reconstruire**.  
  
4.  À partir de la **fichier** menu, cliquez sur **Exit** pour fermer Visual Studio.  
  
#### <a name="to-build-the-adapter-design-time-project"></a>Pour créer le projet de phase de conception d'adaptateur  
  
1.  Dans l’Explorateur Windows, accédez à la \< *exemples de chemin*\>**« \AdaptersDevelopment\File Adapter\Design Time\Adapter Management »** active et double-cliquez sur **AdapterManagement.sln**.  
  
2.  Dans l’Explorateur de solutions, cliquez sur **AdapterManagement**, puis cliquez sur **reconstruire**.  
  
3.  À partir de la **fichier** menu, cliquez sur **Exit** pour fermer Visual Studio.  
  
#### <a name="to-register-the-sample-static-adapter"></a>Pour inscrire l'exemple d'adaptateur statique  
  
1.  Dans l’Explorateur Windows, accédez à la \< *exemples de chemin*\>**« \AdaptersDevelopment\File carte »** active.  
  
2.  Pour ajouter l’exemple d’adaptateur au Registre, double-cliquez sur **StaticAdapterManagement.reg**.  
  
    > [!NOTE]
    >  StaticAdapterManagement.reg comprend des chemins codés en dur vers C:\Program Files\Microsoft BizTalk Server\\. Si vous n’avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans %ProgramFiles%\Microsoft BizTalk Server\ répertoire, une mise à niveau votre installation de BizTalk Server à partir de BizTalk Server 2009 ou BizTalk Server 2006 R2, ou si vous avez installé BizTalk Server sur un ordinateur qui exécute un version 64 bits de Windows, vous devez modifier le fichier StaticAdapterManagement.reg avec les chemins d’accès appropriés. Par défaut, BizTalk Server est installé dans le % ProgramFiles(x86) %\Microsoft active BizTalk Server\ sur les ordinateurs qui exécutent une version 64 bits de Windows. Mettez à jour les chemins associés aux valeurs "InboundAssemblyPath", "OutboundAssemblyPath" et "AdapterMgmtAssemblyPath" afin de pointer vers l'emplacement correct des fichiers spécifiés.  
  
    > [!IMPORTANT]
    >  Si vous installez BizTalk sur un ordinateur 64 bits, modifiez toutes les instances de l’entrée de Registre HKEY_CLASSES_ROOT\CLSID\ à HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ dans le **StaticAdapterManagement.reg** fichier de Registre.  
  
3.  Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK**.  
  
4.  Pour fermer l’Explorateur Windows, dans le **fichier** menu, cliquez sur **fermer**.  
  
#### <a name="to-install-the-sample-static-adapter"></a>Pour installer l’exemple d’adaptateur statique  
  
1.  Cliquez sur **Démarrer**, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, cliquez pour développer **Administration de BizTalk Server**, cliquez pour développer **groupe BizTalk**et développez **paramètres de plateforme**.  
  
3.  Bouton droit sur **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.  
  
4.  Dans le **ajouter un adaptateur** boîte de dialogue zone, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **statique**.|  
    |**Adaptateur**|Sélectionnez **Static DotNetFile** dans la liste déroulante.|  
    |**Commentaireaire**|Type **exemple d’adaptateur**.|  
  
5.  Cliquez sur **OK**.  
  
     L'adaptateur statique apparaît maintenant dans la liste des adaptateurs dans la fenêtre de droite de la console Administration de BizTalk.  
  
#### <a name="to-stop-and-restart-the-host-instance"></a>Pour arrêter et redémarrer l'instance de l'hôte  
  
1.  Cliquez sur **Démarrer**, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, cliquez pour développer **Administration de BizTalk Server**, cliquez pour développer **groupe BizTalk**, cliquez pour développer **paramètres de plateforme** Cliquez sur **Instances d’hôte**. Sélectionnez l'application BizTalkServer dans le volet de droite.  
  
3.  Dans le volet de résultats, cliquez sur l’instance d’hôte (en règle générale, le nom d’ordinateur), puis cliquez sur **redémarrer**.  
  
### <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
##### <a name="to-run-the-file-adapter-sample"></a>Pour exécuter l'exemple d'adaptateur de fichiers  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.  
  
2.  Créez les dossiers suivants sur le lecteur d’installation de BizTalk Server :  
  
    -   *\<drive\>*:**\Temp**  
  
    -   *\<drive\>*:**\Temp\Send**  
  
    -   *\<drive\>*:**\Temp\Receive**  
  
3.  Pour fermer l’Explorateur Windows, dans le **fichier** menu, cliquez sur **fermer**.  
  
4.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
5.  Cliquez sur le **Administration de BizTalk Server** nœud et sélectionnez **se connecter au groupe existant**.  
  
6.  Dans le **se connecter à la base de Configuration BizTalk existante** boîte de dialogue zone, procédez comme suit.  
  
    > [!NOTE]
    >  La base de données de gestion BizTalk est également appelée « base de données de configuration BizTalk ».  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**SQL Server**|Type **.** (un point).|  
    |**Base de données**|Sélectionnez le nom de la base de données de gestion BizTalk qui a été créée par l'assistant Configuration. Le nom de base de données par défaut utilisé par l’Assistant de Configuration est **BizTalkMgmtDb**.|  
  
7.  Cliquez sur **OK**.  
  
8.  Développez le **groupe BizTalk [*nom du serveur*]** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez le **Applications** nœud, développez le  **BizTalk Application 1** nœud.  
  
9. Avec le bouton droit le **Ports d’envoi** nœud, puis cliquez sur **nouveau**, sélectionnez **Port d’envoi unidirectionnel statique**, puis cliquez sur **OK**.  
  
10. Dans le **propriétés de Port d’envoi** boîte de dialogue, sélectionnez **général**, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **AdapterSend**.|  
    |**Type de transport**|Sélectionnez **statique** dans la liste déroulante, cliquez sur **configurer**.<br /><br /> -Dans le **active** , tapez ***\<lecteur\>*:\Temp\Send**.<br />-Dans le **Mode fichier** boîte, sélectionnez **CreateNew**.<br />-Dans le **nom de fichier** , tapez **%MessageID%.xml**.<br />-Cliquez sur **OK**.<br />-La **URI** champ doit afficher ***\<lecteur\>*:\Temp\Send\\%MessageID%.xml**.|  
    |**Pipeline d’envoi**|Sélectionnez **PassThruTransmit (Microsoft.BizTalk.DefaultPipelines.PassThruTransmit)**, puis cliquez sur **OK**.|  
  
11. Sous le **BizTalk Application 1** cliquez sur le nœud **Ports de réception**, puis sélectionnez **Port de réception unidirectionnel / nouveau**.  
  
12. Dans le **créer un Port de réception** boîte de dialogue le **spécifier le type de Port de réception** boîte, sélectionnez **Port de réception unidirectionnel** à partir de la liste déroulante de liste, puis cliquez sur  **OK**.  
  
13. Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , tapez **AdapterReceive**, puis cliquez sur **OK**.  
  
14. Sous le **BizTalk Application 1** nœud bouton droit sur **emplacements de réception**, puis sélectionnez **emplacement de réception unidirectionnel / nouveau**.  
  
15. Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez **AdapterReceive** puis cliquez sur **OK**.  
  
16. Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **AdapterReceiveLocation**|  
    |**Type de transport**|Sélectionnez **statique** à partir de la liste déroulante et appuyez sur **configurer** pour accéder à ces propriétés restantes.|  
    |**URI**|-Cliquez sur le bouton de sélection (**...** ).<br />-Dans le **nombre de fichiers dans le lot** , tapez **20**.<br />-Dans le **active** , tapez ***\<lecteur\>*:\Temp\Receive**.<br />-Vérifiez les **masque de fichier** est définie sur  **\*.xml**.<br />-Dans le **fréquence d’interrogation** , tapez **5**, puis cliquez sur **OK**.<br />-Vérifiez les **URI** étiquette contienne ***\<lecteur\>*:\Temp\Receive\\\*.xml**.|  
    |**Gestionnaire de réception**|Sélectionnez **BizTalkServerApplication** dans la liste déroulante.|  
    |**Pipeline de réception**|Sélectionnez **XMLReceive** dans la liste déroulante.|  
  
17. Cliquez sur **OK**.  
  
     Passez à *génération, déploiement et liaison de l’exemple d’adaptateur*.  
  
### <a name="building-deploying-and-binding-the-sample-adapter"></a>Création, déploiement et liaison de l'exemple d'adaptateur  
 Avant que l'adaptateur ne fonctionne, vous devez construire le projet, lier l'orchestration aux ports, et inscrire l'adaptateur.  
  
##### <a name="to-create-a-strong-name-key-for-the-static-adapter"></a>Pour créer une clé de nom fort pour l'adaptateur statique  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  À l’invite de commandes, accédez au répertoire en cours à la \< *exemples de chemin*\>**\AdaptersDevelopment\File Adapter\BizTalk Project\Adapter atelier** active.  
  
3.  À l’invite de commandes, tapez **sn – k AdapterHarness.snk**, puis appuyez sur ENTRÉE.  
  
4.  Cliquez sur **OK**.  
  
##### <a name="to-build-the-adapter-harness-project"></a>Pour créer le projet d'atelier de test d'adaptateur  
  
-   Dans l’Explorateur de solutions, cliquez sur **AdapterHarnessProject**, puis cliquez sur **reconstruire**.  
  
##### <a name="to-deploy-the-adapter-harness-project"></a>Pour déployer le projet d'atelier de test d'adaptateur  
  
1.  Dans l’Explorateur de solutions, lorsque le projet a été reconstruit, avec le bouton droit **AdapterHarnessProject**, puis cliquez sur **déployer**.  
  
2.  Dans la console Administration de BizTalk Server, sélectionnez le projet que vous avez déployé, puis cliquez sur **Actualiser**.  
  
##### <a name="to-bind-the-orchestration-with-the-ports"></a>Pour lier l'orchestration aux ports  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, sous approprié [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, développez le **Orchestrations** nœud.  
  
2.  Avec le bouton droit **AdapterHarness.AdapterHarnessType**, puis cliquez sur **lier**.  
  
3.  Dans le **propriétés de liaison de Port - AdapterHarness.AdapterHarnessType - Configurations de liaison** boîte de dialogue zone, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**AdapterFileReceivePort**|Sélectionnez **AdapterReceive** dans la liste déroulante.|  
    |**AdapterFileSendPort**|Sélectionnez **AdapterSend** dans la liste déroulante.|  
  
4.  Dans le volet gauche, cliquez sur **hôte**.  
  
5.  Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication** dans la liste déroulante, puis cliquez sur **OK**.  
  
 Passez à *administration de l’exemple d’adaptateur*.  
  
### <a name="administering-the-sample-adapter"></a>Administration de l'exemple d'adaptateur  
 Vous terminez les tâches d'administration pour l'exemple d'adaptateur dans la console Administration de BizTalk.  
  
##### <a name="to-administer-the-file-adapter-sample"></a>Pour administrer l'exemple d'adaptateur de fichiers  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le volet gauche, cliquez pour développer **Applications**, cliquez pour développer **BizTalk Application 1**, puis cliquez sur **emplacements de réception**.  
  
3.  Vérifiez le **AdapterReceive** état est **activé**.  
  
     Si l’état n’est pas **activé**, avec le bouton droit **AdapterReceive** dans le volet droit, puis cliquez sur **activer**.  
  
4.  Dans le volet gauche, cliquez sur **Orchestrations** et vérifiez que **AdapterHarness.AdapterHarnessType** est **inscrite**. Bouton droit sur **AdapterHarness.AdapterHarnessType**, puis cliquez sur **Enlist** (si AdapterHarness.AdapterHarnessType est déjà inscrit, le **Enlist** est de l’option de menu non disponible).  
  
5.  Avec le bouton droit **AdapterHarness.AdapterHarnessType** et sélectionnez **Démarrer**. L’état de cette orchestration doit passer à **en cours d’exécution**.  
  
 Passez à *l’exemple d’adaptateur de test*.  
  
### <a name="testing-the-sample-adapter"></a>Test de l'exemple d'adaptateur  
 Après avoir déployé l'exemple d'adaptateur, vous devez arrêter et redémarrer l'instance d'hôte. Il est extrêmement important que vous testiez l'exemple d'adaptateur avant de le mettre en production.  
  
##### <a name="to-stop-and-restart-the-host-instance"></a>Pour arrêter et redémarrer l'instance de l'hôte  
  
1.  Dans le **Administration de BizTalk Server** console, développez **Administration de BizTalk Server**, cliquez pour développer **groupe BizTalk**, cliquez pour développer  **Paramètres de plateforme** et cliquez sur **Instances d’hôte**. Sélectionnez l'application BizTalkServer dans le volet de droite.  
  
2.  Cliquez sur l’instance d’hôte (en règle générale, le nom d’ordinateur), puis cliquez sur **arrêter**.  
  
     L’état de l’instance d’hôte devient **arrêté**.  
  
3.  Cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.  
  
     L’état de l’instance d’hôte devient **en cours d’exécution**.  
  
##### <a name="to-test-the-sample-static-adapter-runtime"></a>Pour tester l'exécution de l'exemple d'adaptateur statique  
  
1.  Dans l’Explorateur Windows, accédez à la \< *exemples de chemin*\>**\AdaptersDevelopment\File adaptateur** active et copier le fichier InstanceXML.xml dans le Presse-papiers.  
  
2.  Accédez à  *\<lecteur\>*:**\Temp\Receive** et collez le fichier Instance.xml dans le dossier.  
  
     Si la transmission et de réception adaptateurs fonctionnent, le fichier doit se déplacer le  *\<lecteur\>*:**\Temp\Receive** dossier pour le  *\<lecteur \>* :**\Temp\Send** dossier.  
  
##### <a name="to-test-the-sample-add-adapter-wizard-functionality-for-the-sample-static-adapter"></a>Pour tester l'exemple de fonctionnalité d'assistant Ajout d'adaptateur pour l'exemple d'adaptateur statique  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **AdapterHarnessProject**, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés - AdapterHarnessProject** boîte de dialogue, cliquez sur **ajouter les métadonnées de l’adaptateur**, puis cliquez sur **ouvrir**.  
  
     La liste des adaptateurs inscrits apparaît.  
  
3.  Sélectionnez **Static DotNetFile**, puis cliquez sur **suivant**.  
  
     L'organisation de service exposée par l'adaptateur apparaît.  
  
4.  Développez **Service organisation**, **soins de santé**, puis cliquez sur **administration**.  
  
     Notez que **éligibilité** affiche différemment des autres nœuds. **Éligibilité** est un nœud de service que vous pouvez sélectionner. Les autres nœuds sont des nœuds d'organisation qui ne décrivent pas de service spécifique.  
  
5.  Sélectionnez le **éligibilité** nœud, puis cliquez sur **Terminer**.  
  
     BizTalk importe un fichier .odx et un fichier .xsd dans le projet.  
  
     Vous pouvez maintenant utiliser les schémas, les types de port, les opérations et les types de messages importés depuis l'adaptateur dans la planification du projet BizTalk.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans cet exemple  
 Interfaces : IBaseMessage, IPropertyBag, IBTTransportProxy  
  
 Classes (En provenance de l'adaptateur de base) : AsyncTransmitterEndpoint, AsyncTransmitter, BatchMessage, ControlledTermination, ReceiverEndpoint, DotNetFileCommonProperties, BatchOperationType  
  
### <a name="comments"></a>Commentaires  
 À l’issue de l’exemple d’adaptateur, vous pouvez modifier l’exemple d’adaptateur pour créer un adaptateur statique ou dynamique personnalisé pour plus d’informations, consultez [Configuration au moment du Design de la carte](../core/adapter-design-time-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs - utilisation](../core/adapter-samples-usage.md)   
 [Inscription d’un adaptateur](../core/registering-an-adapter.md)