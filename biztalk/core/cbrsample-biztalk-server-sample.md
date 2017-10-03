---
title: CBRSample (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, routing
- messages, filters
- outbound maps
- examples, messages
- messages, routing
- examples, outbound maps
- examples, filters
- messages, examples
ms.assetid: 8fba494c-9257-4eed-8b6a-867056147c2c
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b772bc44d4a745d5bfa330e7df7fcadcf2c020db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cbrsample-biztalk-server-sample"></a>CBRSample (exemple BizTalk Server)
L'exemple CBRSample présente l'application de filtres et d'un mappage sortant pour transformer et acheminer des messages d'instance sur la base de leur contenu.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre l'acheminement d'un message contenant le nom, l'adresse et les informations de contact vers l'un des deux dossiers en fonction du code pays. Plus précisément, cet exemple effectue les opérations suivantes :  
  
1.  Définition d'un exemple de format de message contenant des informations de base sur une personne, notamment son identité avec l'ID d'utilisateur et le nom complet, son adresse avec le code pays et ses coordonnées téléphoniques.  
  
2.  Promeut la **CountryCode** propriété dans le document d’entrée afin qu’elle peut être utilisée dans un filtre de port pour contrôler la transformation et le routage.  
  
3.  Transforme le message en une version canadienne lorsque **CountryCode** est égal à 200 ou une version américaine lorsque **CountryCode**est égal à 100. Les deux transformations transmettent toutes les données à l’exception de milieu initiales (**initiale**). La version canadienne mappe également **état** à **Province** et **ZipCode** à **PinCode**.  
  
4.  Acheminement des messages américains vers le répertoire US et des messages canadiens vers le répertoire CAN.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 La conception s'appuie sur les pipelines d'envoi et de réception XML par défaut, la promotion des propriétés, les filtres d'abonnement et les mappages sortants dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour acheminer les messages. Le tableau suivant répertorie les éléments de conception et leur justification.  
  
|Élément de conception|Raison(s) sélectionnée(s)|  
|--------------------|--------------------------|  
|Pipeline XML de réception par défaut|-Le pipeline XMLReceive prend en charge la promotion de propriétés ; le pipeline PassThruReceive ne fait pas.<br />-Le message entrant est déjà au format XML et ne nécessite pas de traitement dépasse le désassemblage de base et la résolution du tiers.|  
|Promotion des propriétés|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]dépend des champs de propriété pour effectuer le routage. Des champs distinctifs sont utilisés par les orchestrations et ne peuvent pas être utilisés à des fins de routage.|  
|Filtre d'abonnement|-Le filtre d’abonnement réalise l’acheminement réel en capturant les messages qui répondent aux critères d’un ou plusieurs en fonction des champs de propriété.|  
|Mappage sortant|-Mappages convertissent les données d’un format vers un autre. L'exemple mappe un message entrant à un format américain ou canadien.|  
|XMLTransmit|-Effectue l’assemblage de base de messages XML sortants ; le pipeline PassThruTransmit ne fournit aucune prise en charge supplémentaire.|  
  
 Ce modèle de base peut être étendu et utilisé pour des scénarios plus complexes.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Cet exemple se trouve dans <`Samples Path>`\Messaging\CBRSample\\.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|CBRDataCAN.Xml, CBRDataUS.Xml|Exemples de fichiers d'entrée conformes au schéma défini dans le fichier CBRInputSchema.xsd.|  
|CBRInput2CANMap.btm, CBRInput2USMap.btm|Fichiers de mappage pour les transformations de format canadien et américain, respectivement.|  
|CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd|Fichiers de schéma du format d'entrée, du format de sotie canadien et du format de sortie américain, respectivement.|  
|CBRPromotedPropertySchema.xsd|Fichier de schéma pour la propriété promue qui correspond à la **CountryCode** élément dans le fichier XML des fichiers d’entrée.|  
|CBRSample.btproj, CBRSample.sln|Fichiers de projet et de solution BizTalk pour cet exemple.|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels de Services Internet (IIS) si nécessaire.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez cet exemple comme exemple de travail des actions requises pour acheminer un message sur la base de son contenu.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 Pour créer et initialiser l'exemple CBRSample, vous devez créer et déployer le projet BizTalk pour cet exemple, configurer le port et l'emplacement de réception et configurer deux ports d'envoi différents.  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a>Pour créer et déployer le projet BizTalk pour cet exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     `<Samples Path>`**\Messaging\CBRSample**  
  
2.  Exécutez **Setup.bat**, qui effectue les actions suivantes :  
  
    -   Crée l’entrée (**dans**) et les dossiers de sortie (**américain** et **pouvez**) pour cet exemple.  
  
    -   Compilation et déploiement du projet Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] utilisé dans l'exemple.  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
    > [!NOTE]
    >  Cet exemple affiche l’avertissement suivant lors de la création et la liaison des ports :  
    >   
    >  **Avertissement : Réception non spécifié pour le Gestionnaire de réception « CBRReceiveLocation » ; mise à jour avec le premier gestionnaire de réception avec type de transport correspondant.**  
    >   
    >  Vous pouvez ignorer cet avertissement sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    > [!NOTE]
    >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
    > [!NOTE]
    >  Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
#### <a name="to-prepare-to-configure-the-receive-port-and-location-and-the-send-ports"></a>Pour préparer la configuration du port et de l'emplacement de réception et des ports d'envoi  
  
1.  Dans **Microsoft SQL Management Studio**, sélectionnez la base de données de gestion BizTalk correcte.  
  
    > [!NOTE]
    >  La base de données de gestion BizTalk est également appelée « base de données de configuration BizTalk ».  
  
#### <a name="to-configure-enlist-and-start-the-us-send-port"></a>Pour configurer, inscrire et démarrer le port d'envoi américain  
  
1.  Dans la console Administration de BizTalk Server, développez **Ports d’envoi**, avec le bouton droit **CBRUSSendPort**, puis cliquez sur **modifier**.  
  
2.  Dans le **statique propriétés du Port d’envoi unidirectionnel** boîte de dialogue, dans l’arborescence des dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Filtres**, puis ajoutez une nouvelle ligne en définissant **propriété** à **CBRSample.CountryCode**, laissant le **opérateur** colonne définie sur  **==** et en définissant le **valeur** colonne **100**.  
  
3.  Dans l’arborescence de dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Mappages sortants**, définissez le **mappage à appliquer** propriété **CBRSample.CBRInput2USMap**, puis cliquez sur **OK**. Vous devrez peut-être cliquer sur le bouton de défilement pour afficher le mappage.  
  
#### <a name="to-configure-enlist-and-start-the-canadian-send-port"></a>Pour configurer, inscrire et démarrer le port d'envoi canadien  
  
1.  Dans la console Administration de BizTalk Server, développez **Ports d’envoi**, avec le bouton droit **CBRCANSendPort**, puis cliquez sur **modifier**.  
  
2.  Dans le **statique propriétés du Port d’envoi unidirectionnel** boîte de dialogue, dans l’arborescence des dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Filtres**, puis ajoutez une nouvelle ligne en définissant **propriété** à **CBRSample.CountryCode**, laissant le **opérateur** colonne définie sur  **==** et en définissant le **valeur** colonne **200**.  
  
3.  Dans l’arborescence de dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Mappages sortants**, définissez le **mappage à appliquer** propriété **CBRSample.CBRInput2CANMap**, puis cliquez sur **OK**.  
  
 Ces étapes connectent le port d'envoi au port de réception. L'exemple utilise les propriétés promues pour acheminer les documents.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est maintenant prêt à travailler avec cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple CBRSample.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Copiez les fichiers d’entrée, **CBRDataCAN.xml** et **CBRDataUS.xml**, dans le dossier d’entrée suivant :  
  
     `<Samples Path>`**\Messaging\CBRSample\In**  
  
2.  Observez la façon dont chacun de ces fichiers est transformé et acheminé vers une de ces deux sortie dossiers en fonction de la valeur de leur **CountryCode** élément (100 ou 200) :  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]transforme et achemine le fichier d’entrée **CBRDataCAN.xml** dans le dossier :  
  
         `<Samples Path>`**\Messaging\CBRSample\CAN**  
  
    -   BizTalk Server transforme et achemine le fichier d’entrée **CBRDataUS.xml** dans le dossier :  
  
         `<Samples Path>`**\Messaging\CBRSample\US**  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines par défaut](../core/default-pipelines.md)   
 [Comment configurer les mappages sortants pour un Port d’envoi](../core/how-to-configure-outbound-maps-for-a-send-port.md)   
 [Messagerie (dossier d’exemples BizTalk Server)](../core/messaging-biztalk-server-samples-folder.md)