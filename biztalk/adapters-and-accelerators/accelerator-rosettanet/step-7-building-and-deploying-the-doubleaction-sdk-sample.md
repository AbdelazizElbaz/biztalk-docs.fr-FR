---
title: "Étape 7 : Création et déploiement de l’exemple du Kit de développement DoubleAction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- deploying, solutions
- building solutions
- double action tutorial, deploying solutions
ms.assetid: f67f8aee-1004-48ee-a6fd-881097382888
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9ebd9fe513e302c5bee83e902ed0d275c8785b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-7-building-and-deploying-the-doubleaction-sdk-sample"></a>Étape 7 : Création et déploiement de l’exemple du Kit de développement DoubleAction
L'exemple DoubleAction.odx montre comment implémenter une orchestration pour générer automatiquement des réponses pour les processus PIP (Partner Interface Processes) double action 0C2, 0C4, 3A2 et 3A4. Vous pouvez étendre cet exemple de projet pour prendre en charge des PIP double action supplémentaires.  
  
 Cet exemple vous permet d'envoyer une réponse automatique à Fabrikam chaque fois que Fabrikam effectue une demande à l'aide de l'un des quatre PIP.  
  
### <a name="to-build-and-initialize-the-doubleaction-sample"></a>Pour créer et initialiser l'exemple DoubleAction  
  
1.  Sur l'ordinateur Contoso, dans une fenêtre d'invite de commandes, accédez au dossier suivant :   
    *\<lecteur\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction\\.  
  
    > [!NOTE]
    >  Avant d'exécuter le programme d'installation, ouvrez le fichier DoubleAction.sql (situé dans le dossier ci-dessus) dans le Bloc-notes. Dans le menu **Fichier** , cliquez sur **Enregistrer sous**. Dans la zone **Codage** , sélectionnez **ANSI** dans la liste déroulante, puis cliquez sur **Enregistrer**. Sélectionnez **Oui** pour remplacer les fichiers existants.  
  
2.  Si votre installation de BizTalk Server est en cours d’exécution sur SQL Server 2008 R2/2008 SP1, exécutez setupx64.bat dans le même dossier. Le fichier de commandes effectuera les actions suivantes :  
  
    -   Crée une procédure stockée SQL (`PipAutomationGetAction`) dans la base de données BTARNDATA pour récupérer le message d'action à partir de la table MessagesToLOB.  
  
    -   Compile le projet .NET HeaderHelper et inscrit l'assembly dans le GAC (Global Assembly Cache).  
  
    -   Crée et lie le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL receive port (MessagesToLOB_Receive_Port).  
  
    -   Active l'emplacement de réception (MessagesToLOB_Receive_Location).  
  
    -   Compile et déploiement l'orchestration double action PIPAutomation (DoubleAction.odx).  
  
    -   Lie et démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
        > [!NOTE]
        >  L'exemple affiche des avertissements pendant la compilation. Vous pouvez ignorer ces avertissements.  
  
        > [!NOTE]
        >  Vérifiez que DoubleAction.odx a été lié à **MessagesToLOB_Receive_Port**et que l'orchestration a été démarrée.  
  
3.  Dans la Console Administration de BizTalk Server, développez le **groupe BizTalk**, **Applications**, et **BizTalk Application 1** nœuds. Cliquez sur le nœud **Orchestrations** . Cliquez avec le bouton droit sur l'orchestration **DoubleAction** , puis cliquez sur **Propriétés**. Dans la boîte de dialogue Propriétés, cliquez sur le nœud **Liaisons** , puis affectez à **Hôte** la valeur **BizTalkServerApplication** et affectez à **Port de réception** la valeur **MessageToLOB_ReceivePort**. Cliquez sur **OK**. Cliquez avec le bouton droit sur l'orchestration **DoubleAction** , puis cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration de la solution Fabrikam](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)