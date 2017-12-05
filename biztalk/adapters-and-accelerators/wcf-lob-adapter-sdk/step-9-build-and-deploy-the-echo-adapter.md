---
title: "Étape 9 : Créer et déployer l’adaptateur Echo | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ead10ab-1acf-47c5-ad16-dc6938601906
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b9a4985629427e44b8ca85f324c89ab719cf249
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-9-build-and-deploy-the-echo-adapter"></a>Étape 9 : Créer et déployer l’adaptateur d’écho
![Étape 9 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 **Durée :** 10 minutes  
  
 Dans cette étape, vous allez effectuer les tâches nécessaires au déploiement de l’adaptateur de l’écho. Cela implique de tous les éléments suivants :  
  
-   Créer un fichier de nom fort et l’assigner à l’assembly d’adaptateur d’écho  
  
-   Générez l’adaptateur d’écho  
  
-   Publication de l’assembly dans le Global Assembly Cache  
  
-   Inscrire l’adaptateur d’écho avec le[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour réussir cette étape, vous devez être familiarisé avec les fichiers de nom fort et dans le GAC. Une compréhension de base [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] configuration est utile, mais n’est pas requis.  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>Pour affecter un nom fort à votre assembly  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **EchoAdapter** de projet, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés EchoAdapter, sélectionnez **signature** dans le volet gauche.  
  
3.  Cliquez sur le **signer l’assembly** onglet.  
  
4.  Choisissez  **\<nouveau... \>**  pour le fichier de nom fort. Lorsque vous y êtes invité pour un nom de fichier, tapez **EchoAdapter.snk**et la protéger mon fichier de clé avec une option de mot de passe, puis cliquez sur **OK**.  
  
5.  Cliquez sur le **Application** onglet.  
  
6.  Remplacez le nom de l’assembly par **Microsoft.Adapters.Samples.EchoV2**.  
  
7.  Cliquez sur **fichier** dans le menu Visual Studio, puis choisissez **Enregistrer tout**.  
  
### <a name="to-build-and-deploy-echo-adapter"></a>Pour générer et déployer l’adaptateur d’écho  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **EchoAdapter** de projet, puis cliquez sur **Build**. Si la build échoue, corrigez les erreurs et essayez de régénérer l’adaptateur de l’écho.  
  
2.  Ouvrez une invite de commandes Visual Studio.  
  
3.  Tapez la commande suivante :  
  
     **Gacutil.exe /if «\<**  *chemin d’accès au assembly\Microsoft.Adapters.Samples.EchoV2.dll*  **\>»**  
  
     Cette procédure installe l'assembly dans le GAC, en remplaçant tout autre assembly existant sous le même nom.  
  
### <a name="to-register-the-echo-adapter-with-windows-communication-foundation"></a>Pour inscrire l’adaptateur de l’écho de Windows Communication Foundation  
  
1.  Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **bloc-notes \<chemin d’installation de Windows\>\Microsoft.NET\Framework\\< version\>\CONFIG\machine.config**, puis cliquez sur **OK**.  
  
2.  Mettre à jour le fichier machine.config. Si votre fichier machine.config ne contient pas de section system.serviceModel, ajoutez la section suivante à la fin du fichier de configuration, mais avant la fermeture de balise racine.  
  
    > [!NOTE]
    >  Remplacez la version, culture, jeton de clé publique et autres informations spécifiques à l’assembly avec les informations de votre carte.  
  
    ```  
    <system.serviceModel>  
      <client>  
        <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
          name="echov2" />  
      </client>  
      <extensions>  
        <bindingElementExtensions>  
          <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingElementExtensions>  
        <bindingExtensions>  
          <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
     - - OU -  
  
     Si votre fichier machine.config contient une section system.serviceModel, déterminer quels éléments sont manquants et les ajoutant.  
  
    > [!NOTE]
    >  Remplacez la version, culture, jeton de clé publique et autres informations spécifiques à l’assembly avec les informations de votre carte.  
  
    ```  
    <client>  
      <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
        name="echov2" />  
    </client>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingElementExtensions>  
      <bindingExtensions>  
        <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingExtensions>  
    </extensions>  
    ```  
  
3.  Enregistrez le fichier machine.config.  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Dans cette étape finale du didacticiel Echo adaptateur, ajouté un nom fort à l’adaptateur d’écho, générés et déployés de l’adaptateur, puis modifié le fichier Machine.config pour inclure des informations sur la carte. À ce stade, l’adaptateur Echo doit être disponible pour les applications consommatrices.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ce didacticiel est terminé. Si vous souhaitez tester le fonctionnement de l’adaptateur de l’écho dans un projet .NET, consultez [didacticiel 2 : utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)   
 [Didacticiel 2 : Utiliser l’adaptateur Echo à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)