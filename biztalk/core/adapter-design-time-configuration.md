---
title: "Configuration de l’adaptateur au moment du Design | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5e7b63c-6e17-4c54-9bbf-6964668a2420
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1427500f174df3f8f1003a2adb3e9b558c2d9fd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-design-time-configuration"></a>Configuration de la conception de l'adaptateur
Les adaptateurs contiennent à la fois un composant de conception et un composant d'exécution. Le composant d'exécution n'est pas not visible pour les utilisateurs. Il est chargé, de façon transparente, de la transmission, de la réception et du traitement des messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Le composant de conception d'un adaptateur est visible par l'intermédiaire d'interfaces utilisateur administratives. Il affiche les propriétés disponibles, accepte les saisies administratives et valide ces saisies dans un objectif de configuration de l'adaptateur. Il est indispensable que ce composant de conception permette une configuration appropriée des propriétés de l'adaptateur afin que le composant d'exécution puisse ensuite remplir sa fonction d'échange de messages.  
  
 Cette section décrit uniquement le composant de conception des adaptateurs. Elle s'attache principalement à expliquer comment afficher et définir la configuration de ces adaptateurs. Il existe deux façons de configurer un adaptateur :  
  
-   **Explorateur de propriétés.** Propriétés de l’adaptateur pour un envoi ou réception de port ou un envoi ou Gestionnaire de réception, sont configurés via le menu de propriétés à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pendant la configuration de ces artefacts, l'adaptateur (transport) est sélectionné et ses propriétés sont configurées grâce à un explorateur de propriétés. Les propriétés applicables sont affichées par l'intermédiaire d'un schéma avec un nom de groupe. Par exemple, pour un gestionnaire d'envoi (transmission), les propriétés figurent dans le fichier TransmitHandler.xsd. Pour un emplacement de réception, elles figurent dans le fichier ReceiveLocation.xsd.  L’adaptateur implémente les **IAdapterConfig** pour localiser et charger le schéma approprié afin d’exposer les propriétés spécifiques dans l’Explorateur de propriétés. Le **IAdapterConfigValidation** interface est utilisée pour valider ces entrées et apportez les modifications de dernières aux valeurs avant d’enregistrer les données de configuration.  
  
-   **Assistant Ajout d’adaptateur métadonnées.** Dans le cas d’application et les adaptateurs de base de données, vous devrez peut-être importer des schémas de prise en charge qui décrivent les types de messages et les types de ports dont a besoin de l’adaptateur dans le projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Il est également parfois nécessaire de consommer les services fournis par l'adaptateur. L'Assistant Ajouter les métadonnées de l'adaptateur vous permet de visualiser les services qu'un adaptateur prend en charge et d'importer les types de messages et de ports associés dans vos projets. Ce processus est appelé « récolte de métadonnées ». En tant que développeur d’adaptateurs, vous créez un fichier XML décrivant ces services et l’exposer à l’Assistant au moment du design par le biais du **IStaticAdapterConfig** ou **IDynamicAdapterConfig** interface, avec les résultats suivants :  
  
    -   **Adaptateur statique.** L'Assistant fournit une arborescence hiérarchique par défaut standard pour présenter les services de l'adaptateur. Un adaptateur statique est un adaptateur qui utilise l'interface utilisateur de l'arborescence standard fournie par l'Assistant. Utilisez le **IStaticAdapterConfig.GetServiceOrganization** et **GetServiceDescription** méthodes afin de permettre des services sélectionnés à ajouter au projet BizTalk. Il s'agit de l'option de configuration la plus simple pour un développeur d'adaptateur. Cependant, l'inconvénient est la rigidité du format d'affichage.  
  
    -   **Adaptateur dynamique.** Si l'interface utilisateur de sélection de service de base fournie par l'Assistant n'est pas assez souple pour vous, vous pouvez créer une interface personnalisée, affichée de façon dynamique par l'Assistant. Utilisez le **IDynamicAdapterConfig.DisplayUI** méthode pour afficher l’interface utilisateur personnalisée pour autoriser la sélection de services à ajouter à un projet BizTalk.  
  
 Cette section propose deux ensembles d'instructions pour gérer la configuration de la conception de façon statique ou dynamique.  
  
 Le kit de développement logiciel (SDK) Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un exemple d'adaptateur File que vous pouvez utiliser en tant que modèle pour créer et personnaliser vos propres solutions de configuration de conception d'adaptateur. Des notes et références portant sur cet exemple d'adaptateur sont fournies dans chaque rubrique de configuration de la conception pour vous aider à modifier vos propres exigences de configuration personnalisées. Pour mieux comprendre ces instructions, vous pouvez installer, créer et exécuter l'exemple d'adaptateur File fourni dans le kit. Consultez [l’adaptateur File (exemple BizTalk Server)](../core/file-adapter-biztalk-server-sample.md) pour plus d’informations.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration de l’adaptateur de conception statique](../core/static-design-time-adapter-configuration.md)  
  
-   [Configuration de l’adaptateur dynamique au moment du Design](../core/dynamic-design-time-adapter-configuration.md)  
  
-   [Schémas de Configuration de l’adaptateur](../core/adapter-configuration-schemas.md)  
  
-   [Fichiers WSDL de l’adaptateur](../core/adapter-wsdl-files.md)  
  
-   [Méthode GetSchema de l’adaptateur](../core/adapter-getschema-method.md)  
  
-   [Fichier d’inscription de carte](../core/adapter-registration-file.md)  
  
-   [Installer l’adaptateur dans BizTalk Server](../core/install-the-adapter-into-biztalk-server.md)  
  
-   [Générer et tester le projet d’adaptateur](../core/build-and-test-the-adapter-project.md)