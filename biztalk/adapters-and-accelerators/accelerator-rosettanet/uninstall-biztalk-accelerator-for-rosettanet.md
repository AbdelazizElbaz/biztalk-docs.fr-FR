---
title: "Désinstallez l’accélérateur BizTalk RosettaNet (BTARN) sur le serveur BizTalk | Documents Microsoft »"
description: "Annuler le déploiement des artefacts et annuler la configuration de BTARN pour supprimer l’accélérateur BizTalk Server"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 8d289a3705eb0c127dc4d2637c2d6ffd3c122b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="uninstall-the-rosettanet-accelerator"></a>Désinstallez l’accélérateur RosettaNet

## <a name="before-you-begin"></a>Avant de commencer
  
* Si vous n’exécutez **Setup.exe**, le processus de désinstallation ne supprime pas les artefacts de l’analyse BAM (Business Activity), les artefacts BizTalk, les répertoires virtuels Internet Information Services (IIS) et pools d’applications.  
  
* Si vous avez utilisé le **bouclage** utilitaire permettant de créer des accords miroirs pour un déploiement sur un seul ordinateur, puis exécutez l’outil avec la **/désactiver <** **organisation d’accueil**  **>**  option avant de supprimer les partenaires dans le **Console d’Administration BTARN**.  
  
* Si ce serveur fait partie d’un déploiement sur plusieurs ordinateurs, n’exécutez pas le **BtarnClean** utilitaire ou annuler manuellement le déploiement d’assemblys BTARN. La suppression des artéfacts sur un ordinateur d’arrête la fonctionnalité des autres ordinateurs.  Si vous souhaitez désinstaller BTARN sur tous les serveurs, puis exécutez le **BtarnClean** utilitaire. 

  
## <a name="undeploy-the-artifacts"></a>Annuler le déploiement des artefacts  

Nous vous recommandons de sauvegarder des vos artefacts BAM avant l’annulation du déploiement. 

1. Annuler le déploiement des artéfacts BAM que vous avez déployé :  
  
    1.  À l’invite de commandes, exécutez la commande suivante :  
  
         ```cd %ProgramFiles%\\<BizTalk Server installation directory\>\Tracking```
  
    2.  À l'invite de commande où l'interface utilisateur de suivi était installée, exécutez la commande suivante :  
  
         ```bm remove-all DefinitionFile:"%ProgramFiles%\\<installation directory\>\BAMTracking\tracking.xml"```
  
        > [!NOTE]
        >  Pour plus d’informations sur BAM, consultez [la gestion de l’analyse BAM](../../core/managing-bam.md) 
  
2.  Sauvegardez et supprimez tous les contrats, les partenaires et les organisations de base à partir de la Console de gestion BTARN. Consultez la rubrique « Gestion de la Configuration BTARN » (dans le nœud des opérations de l’aide sur BTARN) pour plus d’informations sur l’utilisation de la **BtarnConfig** utilitaire pour sauvegarder les accords et les partenaires.  
  
    > [!NOTE]
    >  * Arrêter et annuler le déploiement des artefacts BizTalk créés par BTARN à l’aide de la [BtarnClean](btarnclean.md) utilitaire.
    >  * Supprimer les artéfacts supplémentaires que vous avez déployé. Consultez [annulation du déploiement des Applications BizTalk](../../core/undeploying-biztalk-applications.md) .
  
3.  À partir de l’installation de BTARN, recherchez le dossier MSI\Program Files\Microsoft BizTalk Accelerator pour RosettaNet\SDK dossier. Dans le dossier SDK, double-cliquez sur **BTARNClean.exe**, puis sélectionnez **Y** à se poursuivre, ou **N** pour annuler l’exécution de l’utilitaire.  
  
    > [!NOTE]
    >  Si votre serveur fait partie d’un scénario de déploiement de plusieurs ordinateurs, vous pouvez ignorer l’étape 3. Annulation du déploiement de toutes les ressources partagées, la fonctionnalité s’arrête sur les autres serveurs dans le déploiement.  
  
4.  Annulez le déploiement d'éventuels assemblys que vous aviez créés et déployés.  
  
5.  À l’invite de commandes, accédez à \Program Files\Microsoft BizTalk Server <your version>\Tracking. Exécutez la commande suivante : 

    ```BM UNDEPLOY ALL <drive\>:\Program Files\\<installation directory\>\BAMTracking\tracking.xml```
  
## <a name="unconfigure-btarn"></a>Annuler la configuration de BTARN
  
1.  Recherchez et exécutez ce qui suit pour annuler la configuration de BTARN :  
  
     ***< lecteur\>*****: \Program Files\\< répertoire d’installation\>\Configuration.exe /u**   
  
2.  Dans le panneau de configuration, double-cliquez sur **Ajout / Suppression de programmes**.  
  
3.  Dans le **programmes actuellement installés** , cliquez sur **Microsoft BizTalk Accelerator for RosettaNet**, puis cliquez sur **modifier/supprimer**.  
  
4.  Dans le **Maintenance du programme** boîte de dialogue, sélectionnez **supprimer**, puis cliquez sur **suivant**.  
  
5.  Dans le **Résumé** boîte de dialogue, cliquez sur **désinstallation**.  
  
6.  Dans le **désinstallation terminée** boîte de dialogue, cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Le processus de désinstallation ne supprime pas les bases de données BTARN (BTARNARCHIVE, BTARNCONFIG et BTARNDATA). Vous devez les supprimer manuellement.  
  
7.  Ouvrez **SQL Server Management Studio**.  
  
8.  Dans le **se connecter au serveur** boîte de dialogue, cliquez sur **connexion**.  
  
9. Développez le **bases de données** nœud dans le volet gauche. Cliquez sur une des bases de données BTARN, puis cliquez sur **supprimer**.  
  
10. Dans le **supprimer un objet** boîte de dialogue, sélectionnez **fermer les connexions existantes**, puis cliquez sur **OK**.  
  
