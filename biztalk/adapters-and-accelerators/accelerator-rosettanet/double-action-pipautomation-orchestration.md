---
title: Double Orchestration Action PIPAutomation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9159f7b1-cb83-41f1-8637-39c5ddcc63ae
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf1e7bf6f0dbfcaec97b9cc988a46d012e4ae18f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="double-action-pipautomation-orchestration"></a>Orchestration Action PIPAutomation double
L’exemple DoubleAction.odx montre comment implémenter une orchestration pour générer automatiquement des réponses pour les processus d’Interface double action partenaires (PIP) 0, C 2, 0c4, 3A2 et 3 a 4. Vous pouvez étendre cet exemple de projet pour prendre en charge des PIP double action supplémentaires.  
  
> [!NOTE]
>  Les cartes fournies dans le dossier d’exemples sont des exemples. Pour les utiliser, vous devez les modifier selon vos besoins spécifiques.  
  
> [!NOTE]
>  Vous devez étendre cet exemple de projet pour prendre en charge des PIP double action PIP uniquement, pas action unique. Cette orchestration retournera une erreur si vous étendez pour traiter un PIP action unique. Pour vous assurer que cette orchestration ne traitera pas PIP d’action unique, consultez la section de filtrage des Messages d’Action unique ci-dessous.  
  
 Par défaut, le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] programme d’installation installe à cet exemple dans \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] 2013 de Microsoft BizTalk Accelerator pour RosettaNet\SDK\PIPAutomation\DoubleAction.  
  
 Cet exemple de projet inclut :  
  
-   Une procédure stockée (`PipAutomationGetAction)` pour récupérer les nouveaux messages d’action pour le PIP 0 C 2, 0c4, 3A2 et 3 a 4.  
  
-   Un emplacement de réception (MessagesToLOB_Receive_Location) lié à la procédure stockée SQL.  
  
-   Une orchestration (DoubleAction.odx) qui traite chaque PIP, génère la réponse adéquate basée sur une carte pour chaque PIP et enregistre la réponse de la table MessagesFromLOB de la base de données BTARNDATA. L’orchestration utilise la `RNIFSubmit` méthode à partir de Microsoft.Solutions.BTARN.Shared.dll pour envoyer le message.  
  
-   Un fichier de liaison (DoubleActionBinding.xml) utilisée par le fichier Setup.bat pour créer le MessagesToLOB_Receive_Port pour une utilisation avec l’orchestration DoubleAction.  
  
-   Un fichier d’installation pour créer et initialiser l’exemple. Si BizTalk Server est en cours d’exécution sur un ordinateur 32 bits, exécutez le fichier setup.bat le \<lecteur\>: \Program Files\Microsoft 2013 de Microsoft BizTalk Accelerator pour RosettaNet \SDK\PIPAutomation\DoubleAction dossier. Si BizTalk Server est en cours d’exécution sur un ordinateur 64 bits, exécutez setupx64.bat dans le même dossier.  
  
 L’orchestration reçoit des messages à l’aide de la procédure PipAutomationGetAction stockée dans la base de données BTARNData (le fichier source est DoubleAction.sql dans le répertoire DoubleAction). Cette procédure stockée récupère les messages à partir de la table MessagesToLOB.  
  
 Pour étendre cet exemple de projet pour prendre en charge des PIP double action supplémentaires, ajoutez un chemin d’accès dans l’orchestration pour le PIP double action. Ce chemin d’accès inclut une carte qui construit un message de réponse à un message de demande. Par exemple les cartes, consultez le [demande 3A2 à un exemple de mappage de réponse 3A2](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md) et [demande 3 a 4 pour un exemple de mappage de réponse 3 a 4 &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md).  
  
### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  À l’invite de commandes, recherchez le  *\<lecteur\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour RosettaNet 2013 \SDK\PIPAutomation\DoubleAction dossier.  
  
    > [!NOTE]
    >  Avant d’exécuter le programme d’installation, ouvrez le fichier DoubleAction.sql (situé dans le dossier ci-dessus) dans le bloc-notes. Dans le menu **Fichier** , cliquez sur **Enregistrer sous**. Dans le **codage** liste, sélectionnez **ANSI**, puis cliquez sur **enregistrer**. Sélectionnez **Oui** pour remplacer les fichiers existants.  
  
2.  Si votre serveur BizTalk Server est en cours d’exécution sur un ordinateur 32 bits, exécutez le fichier setup.bat le \<lecteur\>: \Program Files\Microsoft BizTalk Accelerator pour RosettaNet 2013 \SDK\PIPAutomation\DoubleAction dossier. Si votre installation de BizTalk Server 2013 est en cours d’exécution sur un ordinateur 64 bits, exécutez setupx64.bat dans le même dossier. Le fichier de commandes effectuera les actions suivantes :  
  
    -   Crée une procédure stockée SQL (`PipAutomationGetAction`) dans la base de données BTARNDATA pour récupérer le message d'action à partir de la table MessagesToLOB. Cela garantit également que les enregistrements récupérés ne seront pas lue à nouveau.  
  
    -   Compile le HeaderHelper [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] de projet et inscrit l’assembly dans le global assembly cache.  
  
    -   Crée et lie le SQL Server de BizTalk (MessagesToLOB_Receive_Port) de port de réception.  
  
    -   Active l'emplacement de réception (MessagesToLOB_Receive_Location).  
  
    -   Compilation et déploiement de l’Orchestration de Double-Action PIPAutomation (DoubleAction.odx).  
  
    -   Lie et démarre l’orchestration de BizTalk Server.  
  
        > [!NOTE]
        >  L'exemple affiche des avertissements pendant la compilation. Vous pouvez ignorer ces avertissements.  
  
        > [!NOTE]
        >  L’exemple utilise le nom d’hôte par défaut **BizTalkServerApplication** lors du déploiement du projet. Si vous souhaitez exécuter l’exemple sous un autre ordinateur hôte, vous devez modifier les noms d’hôte par défaut trouvés dans DoubleActionBinding.xml sous \<SDK\>\PIPAutomation\DoubleAction dossier.  
  
### <a name="to-run-the-double-action-pipautomation-sample"></a>Pour exécuter l’exemple Double Action PIPAutomation  
  
1.  Créez un accord de 3 a 4 où le rôle de base est un initiateur. La valeur 123456789 GBI pour l’organisation d’origine et définissez GBI 987654321 aux partenaires. Cela vous permet d’utiliser les exemples fournis dans le dossier SampleInstances sous le dossier LOBApplication dans le Kit de développement.  
  
2.  À l’aide de l’utilitaire de mise en miroir de contrat de bouclage, de créer un miroir pour le PIP 3 a 4 créé à l’étape 1.  
  
3.  À l’aide de l’utilitaire LOBApplication.exe SDK, envoyer un message de demande d’adresse PIP 3 a 4. Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut un exemple d’entrée dans le dossier \< *répertoire d’Installation*\>\SDK\LOBApplication\SampleInstances\3A4_Request.xml.  
  
4.  Exécutez la requête suivante sur la base de données BTARNDATA :  
  
    ```  
    Select * from MessagesToLOB  
    ```  
  
5.  Après quelques secondes, quatre nouveaux messages s’affichent dans cette table. Deux d'entre eux sont des signaux d’accusé de réception. Un signal est le Message de demande Async 3 a 4. Un signal est le Message de réponse 3 a 4 Async.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d’exécuter à nouveau le fichier Setup.bat.  
  
## <a name="remarks"></a>Notes  
 L’orchestration publique génère automatiquement des accusés de réception (ACK et NACK signaler des messages). Celle-ci line-of-business (LOB) n’a pas besoin de les générer.  
  
 Le format du message est routé vers la table MessagesFromLOB est appelé LOBMessage. Le schéma est disponible dans C:\Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour RosettaNet 2013 \SDK\RNIFSchemas\GlobalSchemas\LOBMessage.xsd. Si vous utilisez le `RNIFSubmit` (méthode), il est inutile travailler avec le format du message. Vous devez uniquement soumettre la ServiceContent avec les informations supplémentaires. `RNIFSubmit`remplit l’enregistrement dans la table MessagesFromLOB.  
  
## <a name="filtering-out-single-action-messages"></a>Filtrage des Messages d’Action unique  
 Cette orchestration doit-elle recevoir uniquement les messages de double action. Vous ne devez pas étendre cet exemple de projet pour prendre en charge des PIP d’action unique. BTARN génère des erreurs si vous utilisez cette orchestration pour traiter les messages d’action unique. Afin d’éviter l’orchestration de recevoir un message d’action unique, remplacez la ligne suivante dans la procédure stockée de PIPAutomationGetAction :  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB  
```  
  
 À la ligne ci-dessus, ajoutez une clause WHERE qui filtre les messages d’action unique. Inclure tous les messages d’action unique que vous allez traiter dans la clause WHERE. La ligne doit être comme suit :  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB WHERE PIPCode NOT IN ( '0A1', '3B2', '3C3', '0C1', '0C3' )  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Demande de 3A2 d’exemple de mappage de réponse 3A2](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)   
 [Demande de 3 a 4 pour un exemple de mappage de réponse 3 a 4](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)   
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)