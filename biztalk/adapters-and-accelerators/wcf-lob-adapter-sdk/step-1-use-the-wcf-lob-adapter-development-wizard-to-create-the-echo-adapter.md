---
title: "Étape 1 : Utiliser l’Assistant de développement de l’adaptateur LOB WCF pour créer le projet d’adaptateur Echo | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634a6498-55b0-462d-a5ca-16507b3787f5
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffad8f817cf3a13b3d3af3264438bafa639181a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter-project"></a>Étape 1 : Utiliser l’Assistant de développement de l’adaptateur LOB WCF pour créer le projet d’adaptateur écho
![Étape 1 sur 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")  
  
 **Durée :** 15 minutes  
  
 Dans cette étape, vous allez créer un projet à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]. Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] vous guide à travers les étapes impliquées dans le développement d’un adaptateur personnalisé pour le système. Il collecte des informations sur les modèles d’échange de messages, les fonctions de métadonnées, propriétés de l’adaptateur et les propriétés de connexion. Une fois l’Assistant terminé avec succès, il génère un ensemble de fichiers.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer de la base de connaissances décrit dans [avant de commencer le didacticiel](../../core/before-you-begin-the-tutorial.md) et avoir correctement configuré votre ordinateur pour le développement de votre adaptateur à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
## <a name="choose-wcf-lob-adapter-plug-in-in-visual-studio"></a>Choisissez l’adaptateur WCF LOB plug-in Visual Studio  
  
1.  Démarrez Visual Studio et, à la **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **l’adaptateur WCF LOB**.|  
    |**Nom**|Type **EchoAdapter**.|  
    |**Emplacement**|Type **C:\Tutorials**.|  
    |**Créer le répertoire pour la solution**|Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.|  
    |**Nom de solution**|Type **EchoAdapterSampleV2**.|  
  
     L’illustration suivante montre le **nouveau projet** boîte de dialogue.  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3a349be4-1a7d-480a-8e9d-cfcba63cd14a.gif "3a349be4-1a7d-480a-8e9d-cfcba63cd14a")  
  
3.  Cliquez sur **OK**.  
  
4.  Sur le **Bienvenue** , cliquez sur **suivant**. L’illustration suivante montre le **Bienvenue** page.  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0b8ef97f-044d-481f-8c7c-0d034fdba37d.gif "0b8ef97f-044d-481f-8c7c-0d034fdba37d")  
  
5.  Cliquez sur **Suivant**.  
  
## <a name="enter-the-scheme-and-namespace-information"></a>Entrez les informations de schéma et l’espace de noms  
  
1.  Sur le **schéma Namespace et informations de l’URI** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Schéma**|Type **echov2**.|  
    |**Espace de noms de projet**|Type **Microsoft.Adapters.Samples.EchoV2**.|  
  
     L’illustration suivante montre le **schéma Namespace et informations de l’URI** page.  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0d72dab2-7992-47e4-bc4e-3e720b1cde38.gif "0d72dab2-7992-47e4-bc4e-3e720b1cde38")  
  
2.  Cliquez sur **Suivant**.  
  
## <a name="enter-the-data-flow-and-metadata-features"></a>Entrez les fonctionnalités métadonnées et les flux de données  
  
1.  Sur le **données circulent** et **fonctions de métadonnées** page, procédez comme suit :  
  
     **Modèles d’échange de message**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Synchrone sortant**|Sélectionnez la case à cocher.|  
    |**Synchrone entrant**|Sélectionnez la case à cocher.|  
  
     **Fonctions de métadonnées**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Récupération**|Sélectionnez la case à cocher.|  
    |**Parcourir**|Sélectionnez la case à cocher.|  
    |**Recherche**|Sélectionnez la case à cocher.|  
  
    > [!NOTE]
    >  Flux de données dans ce contexte signifie le même que les modèles d’échange de message, le terme utilisé dans les rubriques conceptuelles.  
  
     L’illustration suivante montre le **données circulent** et **fonctions de métadonnées** page.  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/4fa6f67d-4703-41db-b5f3-28cf9d6a40d2.gif "4fa6f67d-4703-41db-b5f3-28cf9d6a40d2")  
  
2.  Cliquez sur **Suivant**.  
  
## <a name="enter-the-adapter-properties"></a>Entrez les propriétés de l’adaptateur  
  
1.  Sur le **propriétés de l’adaptateur** page, procédez comme suit :  
  
2.  Ajouter une propriété appelée **nombre**. Ce numéro est utilisé par chaque opération de l’adaptateur de l’écho. Chaque opération renvoie la valeur d’entrée le **nombre** nombre de fois.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **nombre**.|  
    |**Type de données**|Sélectionnez **System.Int32**.|  
    |**Valeur par défaut**|Type **5**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
3.  Ajouter une propriété appelée **EnableConnectionPooling**. Cet indicateur est utilisé par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] pour activer ou désactiver le regroupement de connexions de runtime.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **EnableConnectionPooling**.|  
    |**Type de données**|Sélectionnez **System.Boolean**.|  
    |**Valeur par défaut**|Type **true**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
4.  Ajouter une propriété appelée **InboundFileFilter**. Cette propriété est utilisée par le FileSystemWatcher pour analyser les fichiers de cette extension. Cette propriété est applicable pour le scénario entrant uniquement.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **InboundFileFilter**.|  
    |**Type de données**|Sélectionnez **System.String**.|  
    |**Valeur par défaut**|Type  **\*.txt**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
5.  Ajouter une propriété appelée **InboundFileSystemWatcherFolder**. Cette propriété est utilisée pour définir le dossier où les fichiers sont supprimés pour FileSystemWatcher déclencher la notification à l’adaptateur. Cette propriété est applicable pour le scénario entrant uniquement.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **InboundFileSystemWatcherFolder**.|  
    |**Type de données**|Sélectionnez **System.String**.|  
    |**Valeur par défaut**|Type **C:\\\inbound\\\watcher**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
     L’illustration suivante montre le **propriétés de l’adaptateur** page.  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/84de11a5-a737-4aa5-96c8-61922e704f2b.gif "84de11a5-a737-4aa5-96c8-61922e704f2b")  
  
6.  Cliquez sur **Suivant**.  
  
## <a name="enter-the-connection-properties"></a>Entrez les propriétés de connexion  
  
1.  Sur le **propriétés de connexion** page, procédez comme suit :  
  
2.  Ajouter une propriété appelée **Application**. Cette propriété est uniquement à des fins d’illustration. L’adaptateur echo n’implique pas de n’importe quel système LOB.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **Application**.|  
    |**Type de données**|Sélectionnez **System.String**.|  
    |**Valeur par défaut**|Type **lobapplication**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
3.  Ajouter une propriété appelée **EnableAuthentication**. Lorsque `true`, l’adaptateur attend une valeur dans le champ nom d’utilisateur dans les informations d’identification du client.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **EnableAuthentication**.|  
    |**Type de données**|Sélectionnez **System.Boolean**.|  
    |**Valeur par défaut**|Type **false**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
4.  Ajouter une propriété appelée **nom d’hôte**. Cette propriété est uniquement, à des fins d’illustration est similaire à la propriété **Application**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **nom d’hôte**.|  
    |**Type de données**|Sélectionnez **System.String**.|  
    |**Valeur par défaut**|Type **lobhostname**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
5.  Ajouter une propriété appelée **EchoInUpperCase**. Cette propriété détermine si certaines opérations convertissent en écho les chaînes en majuscules ou les laisser à leur format d’origine.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la propriété**|Type **EchoInUpperCase**.|  
    |**Type de données**|Sélectionnez **System.Boolean**.|  
    |**Valeur par défaut**|Type **False**.|  
    |**Ajouter**|Cliquez pour ajouter la nouvelle propriété de l’adaptateur.|  
  
6.  Cliquez sur **Suivant**.  
  
## <a name="end-the-wizard"></a>Fin de l’Assistant  
  
1.  Sur le **Résumé** , cliquez sur **Terminer**. L’illustration suivante montre **l’Explorateur de solutions** avec la **EchoAdapter** projet.  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/06b45c3e-d056-48f4-a246-642d9ac5e23e.gif "06b45c3e-d056-48f4-a246-642d9ac5e23e")  
  
     Votre projet doit contenir les mêmes fichiers. Si elle n’est pas le cas, quittez Visual Studio, supprimez le **EchoAdapterSampleV2** dossier, puis redémarrez cette étape du didacticiel.  
  
2.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
    > [!NOTE]
    >  Vous avez enregistré votre travail. Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Dans cette étape, vous avez créé la solution d’adaptateur echo à l’aide de Visual Studio et le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]. Le tableau suivant contient le jeu de fichiers et chaque fichier de.  
  
|**Nom de fichier**|**Description**|  
|-------------------|---------------------|  
|EchoAdapter.cs|C’est la classe d’adaptateur principal qui hérite de `Microsoft.ServiceModel.Channels.Common.Adapter`.<br /><br /> Aucune modification n’est nécessaire pour l’adaptateur de l’écho.|  
|EchoAdapterBinding.cs|Il s’agit de la classe utilisée lors de la création d’une liaison pour un adaptateur.<br /><br /> Aucune modification n’est nécessaire pour l’adaptateur de l’écho.|  
|EchoAdapterBindingCollectionElement.cs|C’est la classe d’élément de liaison de la Collection qui implémente le `System.ServiceModel.Configuration.StandardBindingCollectionElement`.<br /><br /> Aucune modification n’est nécessaire pour l’adaptateur de l’écho.|  
|EchoAdapterBindingElement.cs|Cela fournit une classe de base pour les éléments de configuration.<br /><br /> Pour classer les propriétés de l’adaptateur et la connexion de l’adaptateur d’écho, suivez [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).|  
|EchoAdapterBindingElementExtensionElement.cs|Cette classe est fournie pour représenter l’adaptateur sous la forme d’un élément de liaison afin qu’il peut être utilisé au sein d’une liaison personnalisée WCF définis par l’utilisateur.<br /><br /> Pour classer les propriétés de l’adaptateur et la connexion de l’adaptateur d’écho, suivez [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).|  
|EchoAdapterHandlerBase.cs|Il s’agit de la classe de base pour les gestionnaires utilisé pour stocker les fonctions de propriétés / d’assistance communes exposées par la classe de base.<br /><br /> Pour classer les propriétés de l’adaptateur et la connexion de l’adaptateur d’écho, suivez [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).|  
|EchoAdapterConnection.cs|Définit la connexion au système cible.<br /><br /> Pour prendre en charge la connexion de l’adaptateur echo sur le système cible, suivez [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).|  
|EchoAdapterConnectionFactory.cs|Définit la fabrique de connexion pour le système cible.<br /><br /> Pour prendre en charge la connexion de l’adaptateur echo sur le système cible, suivez [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).|  
|EchoAdapterConnectionUri.cs|Il s’agit de la classe pour représenter un Uri de connexion de l’adaptateur.<br /><br /> Pour prendre en charge la connexion de l’adaptateur echo sur le système cible, suivez [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)).|  
|EchoAdapterMetadataBrowseHandler.cs|Cette classe est utilisée lors de l’exécution d’une recherche basée sur une connexion pour les métadonnées à partir du système cible.<br /><br /> Pour prendre en charge les métadonnées de fonction de l’adaptateur de l’écho de navigation, suivez [étape 4 : implémenter le Gestionnaire de parcourir des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).|  
|EchoAdapterMetadataSearchHandler.cs|Cette classe est utilisée pour effectuer une recherche basée sur une connexion pour les métadonnées à partir du système cible.<br /><br /> Pour prendre en charge les métadonnées de recherche de la fonctionnalité de l’adaptateur echo, suivez [étape 5 : implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).|  
|EchoAdapterMetadataResolve.cs|Cette classe est utilisée pour effectuer une récupération basée sur une connexion de métadonnées à partir du système cible.<br /><br /> Pour prendre en charge les métadonnées de la fonctionnalité de l’adaptateur de l’écho de résolution, suivez [étape 6 : implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).|  
|EchoAdapterOutboundHandler.cs|Cette classe est utilisée pour envoyer des données vers le système cible.<br /><br /> Pour prendre en charge l’échange de messages sortants pour la carte echo, suivez [étape 7 : implémenter le Gestionnaire de sortie synchrone pour l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).|  
|EchoAdapterInboundHandler.cs|Cette classe implémente une interface pour l’écoute ou d’interrogation pour les données.<br /><br /> Pour prendre en charge l’échange de messages entrants de l’adaptateur echo, suivez [étape 8 : implémenter le Gestionnaire d’entrée synchrone de la carte d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md).|  
|EchoAdapterTrace.cs|Cette classe implémente le suivi des adaptateurs, de débogage et de dépannage.|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous catégoriser les propriétés d’adaptateur et de la connexion pour leur regroupement logique de l’interface utilisateur et ensuite implémentez la connexion, exploration des métadonnées, rechercher et résoudre les fonctionnalités et les échanges de messages entrants et sortants. Enfin, vous générez et déployez l’adaptateur de l’écho.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)   
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)