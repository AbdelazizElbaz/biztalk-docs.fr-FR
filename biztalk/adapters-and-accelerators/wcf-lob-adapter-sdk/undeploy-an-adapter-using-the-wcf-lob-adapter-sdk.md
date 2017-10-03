---
title: "Annuler le déploiement d’un adaptateur à l’aide de l’adaptateur LOB WCF SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98f9a124-9e63-4451-af0e-ffee752fbeac
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a8da6ff335460cbd957a33ac5074f65205dfb77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="undeploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a>Annuler le déploiement d’un adaptateur à l’aide de l’adaptateur LOB WCF SDK
Pour annuler le déploiement d’une carte à partir d’un ordinateur, l’utilisateur doit effectuer les deux tâches suivantes :  
  
1.  Désinstaller l’assembly d’adaptateur (et tous les assemblys dépendants) dans le global assembly cache (GAC).  
  
2.  Supprimer la liaison de l’adaptateur et d’un élément de liaison de l’adaptateur dans le fichier machine.config.  
  
## <a name="uninstall-an-assembly-from-the-gac"></a>Désinstaller un Assembly du GAC  
  
#### <a name="use-the-windows-interface"></a>Utiliser l’interface Windows  
  
1.  Ouvrez l’Explorateur Windows comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **l’Explorateur Windows**.  
  
2.  Recherchez dans le GAC, ce qui se trouve dans % systemdrive%\Windows\Assembly.  
  
3.  Sur chaque fichier d’assembly qui est inclus dans votre application, cliquez **désinstallation**, puis cliquez sur **Oui** pour confirmer.  
  
#### <a name="use-the-command-line"></a>Utilisez la ligne de commande  
  
1.  Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.  
  
2.  À l'invite de commandes, tapez la commande suivante :  
  
     **gacutil /u** \< *complet**nom de l’assembly*>  
  
     Dans cette commande, le nom de l’assembly est le nom de l’assembly à désinstaller à partir du GAC.  
  
     L'exemple suivant supprime un assembly nommé hello.dll du GAC.  
  
     `gacutil /u "MyAdapter,Version=1.0.0.0, Culture=neutral, PublicKeyToken=fafafafafafafafa"`
  
## <a name="remove-the-adapter-binding-from-the-machineconfig-file"></a>Supprimer la liaison de l’adaptateur à partir du fichier Machine.config  
 Vous pouvez manuellement modifier le fichier machine.config pour supprimer la liaison de la carte, ou utilisez l’éditeur de Configuration de Service. Cette section répertorie les deux étapes. 
  
#### <a name="manually-edit-the-machineconfig-file"></a>Modifier manuellement le fichier machine.config  
  
1.  Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **bloc-notes \<Windows le chemin d’installation > \Microsoft.NET\Framework\\< version\>\CONFIG \MACHINE.config**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Effectuez une sauvegarde du fichier machine.config avant d’apporter des modifications pour vous prémunir contre les erreurs de modification.  
  
2.  Mettre à jour le fichier machine.config. Recherchez l’élément de bindingExtensions pour la carte que vous souhaitez supprimer. Basée sur les autres informations qui n’est présentes, effectuez l’une des opérations suivantes :  
  
    -   S’il existe des autres bindingExtensions, supprimez uniquement votre extension de carte.  
  
    -   S’il n’y a aucune autres bindingExtensions, vous pouvez supprimer la section bindingExtensions (y compris votre extension de carte).  
  
    -   S’il n’y a aucun autre bindingExtensions ou extensions, vous pouvez supprimer la section des extensions.  
  
    -   Enfin, si system.serviceModel contient uniquement votre extension de carte, vous pouvez supprimer la section system.serviceModel entière.  
  
3.  Répétez l’étape 2 pour l’élément bindingElementExtensions.  
  
4.  Fermez et enregistrez le fichier machine.config.  
  
#### <a name="use-the-service-configuration-editor-do-change-the-machineconfig-file"></a>Utilisez l’éditeur de Configuration de Service ne modifiez pas le fichier machine.config  
  
1.  Ouvrez l’éditeur de Configuration de Service. Consultez [éditeur de Configuration de Service](https://msdn.microsoft.com/library/ms732009.aspx) pour plus d’informations.
  
2.  Dans le volet d’arborescence (étiqueté **Configuration**), développez l’arborescence de nœuds. Cliquez sur le **avancé** dossier, cliquez sur le **Extensions** dossier et sélectionnez l’élément d’extensions de liaison.  
  
3.  Dans le volet détails de l’éditeur d’Extensions de liaison, cliquez sur l’extension de liaison que vous souhaitez supprimer, puis cliquez sur **supprimer**. Dans l’illustration suivante, MyAdapterExtension est mis en surbrillance et est supprimée.  
  
     ![Éditeur de configuration de service avec ajout d’extension. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")  
  
4.  Fermez l'éditeur de configuration de service.  
  
## <a name="see-also"></a>Voir aussi  
 [Limitations concernant le déploiement](../../core/deployment-limitations1.md)   
 [Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)