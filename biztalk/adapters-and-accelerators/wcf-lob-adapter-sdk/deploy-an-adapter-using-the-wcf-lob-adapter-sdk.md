---
title: "Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 376b4dcf-2d2c-4872-a394-67edc0c3d088
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72c83998bbe16899055c839a73795d456a132381
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a>Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK
Pour déployer un adaptateur, vous devez installer l’assembly de l’adaptateur dans le global assembly cache (GAC) et puis inscrire l’adaptateur dans le fichier machine.config.  
  
## <a name="install-the-adapter-assembly-into-the-gac"></a>Installer l’Assembly d’adaptateur dans le GAC  
 Avant l’utilisation d’un adaptateur à l’aide de Visual Studio le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] commande ou dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] fonctionnalité, vous devez installer l’assembly dans le GAC. Seuls les assemblys qui sont dotés de nom fort peuvent être installés dans le GAC.  
  
> [!NOTE]
>  Pour effectuer cette procédure, vous devez être connecté avec un compte qui dispose des autorisations d’écriture sur le GAC. Le compte des administrateurs de l'ordinateur local dispose de ces autorisations.  
  
#### <a name="configure-a-strong-name-assembly-key-file"></a>Configurer un fichier de clé de nom fort assembly  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], chargez le fichier de projet d’adaptateur qui requiert un nom fort.  
  
2.  Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.  
  
3.  À l'invite de commandes, à partir du dossier dans lequel vous voulez stocker le fichier de clé, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
     **sn /k***nom_fichier* **.snk**   
  
     Exemple : **sn /k EchoAdapter.snk**  
  
     Un message de confirmation, **paire écrite dans la clé** \< *nom_fichier*>**.snk** `,` affiche sur la ligne de commande.  
  
4.  Dans l’Explorateur de solutions Visual Studio, cliquez sur le projet, puis cliquez sur **propriétés**.  
  
5.  Dans le volet gauche, développez **propriétés communes**, puis cliquez sur **Assembly**.  
  
6.  Dans le volet droit, faites défiler vers le **nom fort** boîte.  
  
7.  Dans le **nom fort** , cliquez sur le champ à côté **fichier de clé d’Assembly**, cliquez sur le bouton Parcourir (**...** ), puis accédez au fichier de clé.  
  
8.  Cliquez sur le fichier de clé, cliquez sur **ouvrir**, puis cliquez sur **OK**.  
  
9. Dans le menu Visual Studio, cliquez sur **générer**, puis choisissez **générer la Solution**.  
  
> [!NOTE]
>  Si votre assembly d’adaptateur dépend des autres assemblys, assurez-vous de ces assemblys référencés sont signés avec un nom fort ; Sinon, vous obtiendrez une erreur.  
  
 Si vous disposez de la source, vous pouvez le recompiler avec un nom fort comme indiqué précédemment. Si l’assembly de référence appartient à un tiers, et vous ne pouvez pas vous assurer qu’il a un nom fort, vous pouvez démonter et puis réassembler l’assembly avec un nom fort.  
  
 Votre assembly d’origine sera remplacé, par conséquent, si vous souhaitez conserver la version d’origine, veillez à effectuer une copie de sauvegarde avant de procéder aux étapes suivantes.  
  
 Utilisez le désassembleur de langage MSIL (Microsoft Intermediate) pour désassembler l’assembly :  
  
-   ILDASM thirdparty.dll /out:thirdparty.il  
  
 Utilisez l’assembleur MSIL pour réassembler l’assembly avec un nom fort :  
  
-   ILASM thirdparty.il /dll /key=strongkeyfile.snk  
  
#### <a name="install-an-assembly-in-the-gac"></a>Installer un assembly dans le GAC  
  
1.  Vérifiez que votre adaptateur a été signé.  
  
2.  Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.  
  
3.  Tapez la commande suivante :  
  
     **Gacutil.exe /if «\<**  *chemin d’accès du fichier d’assembly .dll* **> »**  
  
4.  Cette procédure installe l'assembly dans le GAC, en remplaçant tout autre assembly existant sous le même nom.  
  
## <a name="register-the-adapter-in-machineconfig"></a>Inscrire l’adaptateur dans Machine.config  
 Un adaptateur développées à l’aide du [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est présenté comme une liaison WCF.  Pour plus d’informations, consultez Microsoft.ServiceModel.Channels.Common.AdapterBinding.  La liaison de l’adaptateur est inscrit avec WCF à l’aide de \<bindingExtensions > section \<système. ServiceModel > et l’élément de liaison de transport de l’adaptateur est enregistré avec WCF à l’aide de \<bindingElementExtensions > section \<système. ServiceModel >.  
  
 Vous pouvez modifier manuellement le fichier machine.config à l’aide d’un éditeur de texte.  
  
#### <a name="manually-edit-the-machineconfig-file"></a>Modifier manuellement le fichier machine.config  
  
1.  Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad \<Windows le chemin d’installation > \Microsoft.NET\Framework\\< version\>\CONFIG\machine.config, puis cliquez sur **OK**.  
  
2.  Mettre à jour le fichier machine.config. Si le fichier ne contient pas de section system.serviceModel, ajoutez la section suivante à la fin du fichier de configuration, mais avant la fermeture de balise racine.  
  
    > [!NOTE]
    >  Remplacez « myAdapterBinding », version, culture et autres informations spécifiques à l’assembly avec les informations de votre carte.  
  
    ```  
    \<system.serviceModel>  
      <extensions>  
        <bindingExtensions>  
            <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
        </bindingExtensions>      <bindingElementExtensions>  
            <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
          </bindingElementExtensions>  
      </extensions>  
    \</system.serviceModel>  
    ```  
  
     - - OU -  
  
     Si le fichier machine.config contient une section system.serviceModel, déterminer quels éléments sont manquants et les ajouter, en remplaçant « MyAdapter » et autres informations avec les informations de votre carte.  
  
    ```  
    <extensions>  
      <bindingExtensions>  
            <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
      </bindingExtensions>  
          <bindingElementExtensions>  
            <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
          </bindingElementExtensions>  
    </extensions>  
    ```  
  
3.  Fermez et enregistrez le fichier machine.config.  
  
 Vous pouvez également utiliser le [éditeur de Configuration de Service](https://msdn.microsoft.com/library/ms732009.aspx) pour modifier le fichier machine.config.
  
#### <a name="edit-the-machineconfig-file-using-the-service-configuration-editor"></a>Modifier le fichier machine.config à l’aide de l’éditeur de Configuration de Service  
  
1.  Ouvrez le **éditeur de Configuration de Service**. Consultez [éditeur de Configuration de Service](https://msdn.microsoft.com/library/ms732009.aspx) pour plus d’informations.
  
2.  Dans le volet d’arborescence (étiqueté **Configuration**), développez l’arborescence de nœuds. Cliquez sur le **avancé** dossier, cliquez sur le **Extensions** dossier et sélectionnez l’élément d’extensions de liaison.  
  
     ![Éditeur de configuration de service. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0a44a070-b788-4287-bd9e-c946fafcf11c.gif "0a44a070-b788-4287-bd9e-c946fafcf11c")  
  
3.  Créer une nouvelle extension de liaison. Cliquez sur le **nouveau** bouton pour ouvrir l’Extension **Éditeur des éléments de Configuration** boîte de dialogue. Dans **nom de la Configuration**, entrez un nom unique pour les extensions, par exemple *MyAdapterExtension*.  
  
     ![Éditeur de configuration d’élément d’extension](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/1398a256-00fa-4591-99ee-54298a8cf6e3.gif "1398a256-00fa-4591-99ee-54298a8cf6e3")  
  
4.  Cliquez sur le **Type** champ, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la **Explorateur de types d’Extension de liaison** boîte de dialogue.  
  
5.  Cliquez sur global assembly cache (GAC) pour répertorier les DLL dans le GAC.  
  
6.  Cliquez sur votre assembly d’adaptateur.  
  
     ![Explorateur de types d’extension de génération. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7528e218-8930-4b01-b29d-8ec125a9b818.gif "7528e218-8930-4b01-b29d-8ec125a9b818")  
  
7.  Cliquez sur le **ouvrir** pour sélectionner l’assembly.  
  
8.  Dans le **Explorateur de types d’Extension de liaison** boîte de dialogue, cliquez sur le nom de type qui implémente l’élément de collection de liaison.  
  
     ![Explorateur de types d’extension de génération. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce.gif "a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce")  
  
9. Cliquez sur le **ouvrir** pour sélectionner le type.  
  
10. Cliquez sur **OK** pour fermer la **éditeur de Configuration d’élément d’Extension** boîte de dialogue.  
  
11. Dans le volet détails de la **Éditeur d’Extensions de liaison**, vérifiez que votre extension de liaison s’affiche. Dans l’illustration suivante, MyAdapterExtension est mis en surbrillance.  
  
     ![Éditeur de configuration de service avec ajout d’extension. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")  
  
12. Fermer le **éditeur de Configuration de Service**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)