---
title: "Configurer l’Adaptateurs FileAct et interagir adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3876ff-e8e4-47f4-9ca8-d4dad419ed67
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca2bc3aa739bf6914ea9943d84d58d44b1506323
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="configure-the-fileact-and-interact-adapter"></a>Configurer l’Adaptateurs FileAct et interagir de carte
Configurer les différents artefacts utilisés par le [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] runtime. 

  
## <a name="prerequisites"></a>Configuration requise  
   
-   Installer le[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]
  
-   Connectez-vous en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs
  
-   Vérifiez que SQL Server est en cours d’exécution.
  
## <a name="step-1-configure-the-fileact-and-interact-adapter"></a>Étape 1 : Configurer l’adaptateur FileAct et InterAct  
  
1.  Dans le **Microsoft BizTalk FileAct et Configuration de l’adaptateur interagir** Assistant, accédez à **vue d’ensemble**. Dans le volet gauche, sélectionnez **Runtime** pour configurer les composants d’exécution des adaptateurs.  
  
2.  Dans **Configuration d’exécution**, sous **compte**, sélectionnez les points de suspension [...] pour entrer le COM ainsi que la configuration pour le mode magasin et le transfert.  
  
3.  Dans **informations d’identification utilisateur**, entrez le nom d’utilisateur (dans le *domaine\nom d’utilisateur* format) et le mot de passe pour le compte utilisé dans le COM plus de la configuration. Sélectionnez **OK**.  
  
    > [!NOTE]
    >  A **informations d’identification utilisateur** avertissement s’affiche si le compte que vous avez entré a des privilèges plus élevés à sont recommandées. Sélectionnez **Oui** pour continuer.
  
4.  Sélectionnez **appliquer configuration** pour appliquer la COM + configuration aux adaptateurs FileAct et interagir de carte.  
  
5.  Dans le **Résumé**, passez en revue, puis sélectionnez **suivant**.  
  
6.  Une fois la configuration terminée, passez en revue la liste des composants. Une coche signifie que le composant est correctement configuré. Un « X » signifie qu’il existe un problème avec ce composant.  
  
    > [!NOTE]
    >  Utilisez le **Logfile** lien pour afficher les événements de configuration.  
  
7.  Sélectionnez **Terminer** pour terminer la configuration. Le **vue d’ensemble** affiche l’état actuel de la configuration pour les composants d’exécution.  

Ensuite, créez l’hôte et les instances d’hôte pour exécuter ces adaptateurs.

## <a name="step-2-create-the-host-and-host-instances"></a>Étape 2 : Créer l’hôte et les instances d’hôte

Nous vous recommandons de créer un hôte dédié de l’adaptateur FileAct et un hôte dédié distinct pour l’adaptateur InterAct. Pour chaque adaptateur, créez au moins une instance de l’hôte.  

[La gestion des hôtes BizTalk et les Instances d’hôte](../../core/managing-biztalk-hosts-and-host-instances.md) répertorient les étapes pour créer des ordinateurs hôtes et les instances d’hôte. 

Une fois créé, l’étape suivante consiste à ajouter le Gestionnaire d’envoi, utilisez le partenaire de Message Client que vous avez créé dans la passerelle de Alliance SWIFT (trous).

## <a name="step-3-create-the-send-handler"></a>Étape 3 : Créer le Gestionnaire d’envoi

Vous utilisez le FileAct et InterAct envoyez propriétés du gestionnaire en tant que l’envoi les valeurs de configuration de port, si les propriétés ne sont pas définies sur le FileAct individuel ou un port d’envoi interagir. 
  
1.  Dans le **Administration de BizTalk Server** de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **cartes**.  
  
2.  Sélectionnez le **FileAct** ou **interagir** carte. Dans le volet droit, double-cliquez sur le Gestionnaire d’envoi.  
  
3.  Dans le **nom d’hôte** liste déroulante, sélectionnez l’hôte que vous avez créé dans la section précédente. Puis sélectionnez **propriétés**.  
  
4.  Dans le **propriétés du Transport**, sélectionnez le **Argument** propriété, puis entrez l’argument suivant en tant que :  
  
     `-SagMessagePartner <Client Message Partner created in SAG\>`
  
    > [!NOTE]
    >  Remplacez <`Client Message Partner created in SAG`> avec le nom du partenaire de message client. Laissez les valeurs par défaut pour le Mode de chiffrement, FACrypto Mode et les propriétés LogMessages.  
  
5.  Sélectionnez **OK** pour enregistrer vos modifications, puis fermez la fenêtre Propriétés. 
  
6.  Sous **paramètres de plateforme**, sélectionnez **Instances d’hôte**.  
  
7. Redémarrez les instances d’hôte : 

  - Cliquez sur l’instance d’hôte FileAct, et **redémarrer**
  - Cliquez sur l’instance d’hôte interagir, et **redémarrer**.  

Ensuite, entrez les partenaires de message de serveur dans le paramfile SWIFTNet pour activer la FileAct et InterAct des adaptateurs de réception.
  
## <a name="step-4-configure-the-swiftnet-param-file"></a>Étape 4 : Configurer le fichier param SWIFTNet

Pour activer les adaptateurs FileAct et InterAct adaptateurs de réception pour initialiser les valeurs, le message de serveur partenaires créés dans les trous doivent être entrés dans le paramfile SWIFTNet. Le paramfile se trouve généralement dans `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`. Après avoir configuré le paramfile, démarrer **SnlReceiver.exe**.  
  
1. Ouvrez le **SWIFTNet paramfile**. Dans l’emplacement marqué avec « *** « ajoutez le code suivant. Notez que la `AdapterType` valeur peut être `Interact` ou `Fileact`.  
  
     ```spawn "snlreceiver -SagMessagePartner <Server MessagePartnerName\> -AdapterMode <AdapterType\>"```  
       
  
   ```  
    username:snlowner  
    subsystem_name:SampleSubsystem  
    #subsystem_group: SampleSubsystem  
    #subsystem_dependency:Support,Swarm  
    subsystem_nature:critical  
    subsystem_start:  
    ***  
    *END  
    subsystem_stop:  
    *KILL9:snlreceiver  
    *END  
    subsystem_status:  
    *NB:1:snlreceiver  
    *END  
    start_event:SNL001:subsystem SampleSubsystem is up  
    stop_event:SNL002:subsystem SampleSubsystem is down  
   ```  
  
   > [!NOTE]
    >  Avant de commencer, SNLreceiver, activer les ports de réception de la carte que vous utilisez (FileAct ou interagir).  
  
2. Démarrer et arrêter les SnlReceiver.exe :

    1.  Sur le bureau, sélectionnez le **API distant** icône pour ouvrir l’invite de commandes à distance d’API.  
  
    2.  À l’invite de commandes, tapez `Swiftnet start`. Sélectionnez l’entrée pour démarrer SnlReceiver.exe.  
  
    3.  À l’invite de commandes, tapez `Swiftnet stop`. Sélectionnez l’entrée pour arrêter SnlReceiver.exe.  

  
Ensuite, mettez à jour le fichier **autoexec.bat** pour définir des variables d’environnement la SWIFT.

## <a name="step-5-update-autoexecbat-to-configure-the-receive-adapters"></a>Étape 5 : Mise à jour autoexec.bat pour configurer les adaptateurs de réception

Mise à jour la **autoexec.bat** fichier pour définir des variables d’environnement la SWIFT sur l’ordinateur où vous avez installé le [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] des adaptateurs de réception. Les variables d’environnement sont générés à partir du système qui a installé dans le chemin de l’adaptateur de réception `c:\SWIFTAlliance` avec une instance de l’adaptateur de réception nommé **Ra1**. Mettre à jour les variables d’environnement SWIFT appropriée pour votre configuration.  
  
 Voici un exemple de fichier autoexe.bat :
  
```  
SET COMPUTERNAME=<Machine Name>  
SET GENLOG_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET GENUTIL_DIR=C:\SWIFTAlliance\RA\bin  
SET HOMEDRIVE=C:  
SET LOGONSERVER=\\SERVERNAME  
SET OSA_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET OSA_INSTANCE=Ra1  
SET PKIEXECDIR=C:\SWIFTAlliance\RA  
SET SAGRA_HOME=C:\SWIFTAlliance\RA  
SET SESSIONNAME=RDP-Tcp#1  
SET SLP_ENV=DEFAULT  
SET SLP_FILE=server.slp  
SET SNL_DOMAIN_NAME=Ra1  
SET SPK_DATA_DIR=C:\SWIFTAlliance\RA\data\pki  
SET SWNET_BIN_PATH=C:\SWIFTAlliance\RA\Ra1\bin  
SET SWNET_CFG_PATH=C:\SWIFTAlliance\RA\Ra1\cfg  
SET SWNET_HOME=C:\SWIFTAlliance\RA  
SET SWNET_HOST=HOSTNAME  
SET SWNET_INST=Ra1  
SET SWNET_LOG_PATH=C:\SWIFTAlliance\RA\Ra1\log  
SET SWNET_SLP_PATH=C:\SWIFTAlliance\RA\data\  
SET SWNET_VERSION=5.0.20  
SET SWTRACE=C:\SWIFTAlliance\RA\Ra1\log  
SET Path=%PATH%;C:\SWIFTAlliance\RA\bin  
SET Path=%PATH%;C:\SWIFTAlliance\RA\lib  
  
```  
  
## <a name="see-some-examples"></a>Voir des exemples
Pour obtenir des exemples de messages des adaptateurs FileAct et InterAct, consultez [exemple interagir et les Messages de FileAct](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md).  
  
## <a name="see-also"></a>Voir aussi  

[Installer les adaptateurs FileAct et InterAct](../../adapters-and-accelerators/fileact-interact/install-the-fileact-and-interact-adapter.md)  
[Désinstaller ou réparer l’adaptateur FileAct et InterAct](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[Découvrir les problèmes d’installation connus](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
