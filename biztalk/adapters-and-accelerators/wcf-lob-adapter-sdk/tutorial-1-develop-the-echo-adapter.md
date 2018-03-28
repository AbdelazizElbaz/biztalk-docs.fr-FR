---
title: 'Didacticiel 1 : Développer l’adaptateur Echo | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffb0df3c-cd07-4bcf-af69-971065081fd6
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 484452dc4ee624f4fa41e9387098f6f792c1de28
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="tutorial-1-develop-the-echo-adapter"></a>Didacticiel 1 : Développer l’adaptateur d’écho
Dans ce didacticiel, vous allez développer un adaptateur fonctionnel à l’aide du [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. L’adaptateur permet de simuler les opérations d’un système métier-fictive pour illustrer la plupart des fonctionnalités clés de la WCF LOB Adapter SDK, notamment :  
  
-   Synchrone entrant  
  
-   Synchrone sortant  
  
-   Recherche de métadonnées  
  
-   Recherche de métadonnées  
  
-   Résolution des métadonnées  
  
 Cette section contient diverses fonctionnalités de prise en charge par l’adaptateur de l’écho. Ils sont l’échange de messages, les métadonnées d’opération, les propriétés de connexion et les propriétés de l’adaptateur.  
  
## <a name="message-exchange-patterns"></a>Modèles d’échange de message  
 L’adaptateur d’écho prend en charge les modèles d’échange de deux messages suivants :  
  
-   Synchrone sortants, autrement dit, le client consommateur envoie le message de demande WCF via l’adaptateur au système cible et attend de recevoir un message de réponse WCF à partir du système cible via l’adaptateur. Il s’agit du modèle d’échange de messages plus courantes pour un adaptateur. Pour prendre en charge synchrone implémentent sortant, le `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` interface.  
  
-   Synchrone entrant, autrement dit, la consommation client écoute pour les données ou des événements à partir du système cible via l’adaptateur. Pour prendre en charge synchrone implémentent entrant, le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface.  
  
 Pour plus d’informations sur les modèles d’échange de message, consultez [présentation de l’Architecture](architecture-overview-of-the-wcf-lob-adapter-sdk.md).  
  
> [!NOTE]
>  Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] montre le modèle d’échange de messages en tant que flux de données dans l’interface utilisateur.  
  
## <a name="metadata-support"></a>Prise en charge des métadonnées  
 L’adaptateur d’écho prend en charge l’exploration des métadonnées, la recherche et la résolution des fonctionnalités. En règle générale, la navigation et la recherche de récupérer les opérations à partir d’un système métier. Pour la carte echo, un système métier est un ensemble d’opérations prédéfinies, comme indiqué ci-dessous :  
  
```  
EchoMainCategory  
        Echo/EchoStrings  
        Echo/EchoGreetings  
        Echo/EchoCustomGreetingFromFile  
        Echo/OnReceiveEcho  
```  
  
 Voici la définition de chaque opération :  
  
|**Nom**|**Définition d’opération**|**Description**|**Direction**|  
|--------------|------------------------------|---------------------|-------------------|  
|EchoMainCategory|Catégorie|Classe les opérations.|Néant|  
|Echo/EchoStrings|String [] EchoStrings(string data)|Renvoie la chaîne en entrante un nombre spécifié de fois au client appelant.|Sortant|  
|Echo/EchoGreetings|Message d’accueil [] EchoGreetings(Greeting greeting)|Renvoie l’objet de message d’accueil entrant un nombre spécifié de fois au client appelant.|Sortant|  
|Echo/EchoCustomGreetingFromFile|CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath)|Renvoie l’objet de message d’accueil en lisant son instance à partir d’un fichier. Métadonnées de l’objet de message d’accueil sont obtenue à partir d’un fichier XSD prédéfini.|Sortant|  
|Echo/OnReceiveEcho|void OnReceiveEcho (chemin d’accès Uri, durée pendant laquelle le contenu)|Renvoie l’emplacement et la longueur d’un fichier supprimé dans le dossier spécifié.|Trafic entrant|  
  
## <a name="adapter-properties"></a>Propriétés de l'adaptateur  
 L’adaptateur expose les propriétés suivantes de la carte.  
  
|**Nom**|**Catégorie**|**Type de données**|**Description**|  
|--------------|------------------|-------------------|---------------------|  
|Compter|Divers|System.Int32|Utilisé pour l’entrée du nombre de fois spécifié au client appelant d’écho.<br /><br /> Par défaut = 5|  
|EnableConnectionPooling|Divers|System.Boolean|Utilisé pour activer ou désactiver le regroupement de connexions pour la carte.<br /><br /> Par défaut = true, ce qui signifie que que le regroupement de connexions est activé dans le moteur d’exécution de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].|  
|InboundFileFilter|Trafic entrant|System.String|Utilisé pour le scénario de trafic entrant et utilisé par le FileSystemWatcher pour analyser les fichiers de l’extension.<br /><br /> Default=*.txt|  
|InboundFileSystemWatcherFolder|Trafic entrant|System.String|Utilisé pour définir le dossier où les fichiers sont supprimés pour FileSystemWatcher déclencher la notification à l’adaptateur.<br /><br /> Par défaut = c:\inbound\watcher.|  
  
## <a name="connection-properties"></a>Propriétés de connexion  
 L’adaptateur d’écho expose les propriétés suivantes de la connexion.  
  
|**Nom**|**Type de données**|**Description**|  
|--------------|-------------------|---------------------|  
|Application|System.String|Le nom de l’application dans le système métier. Cette propriété est pour des fins d’illustration. L’adaptateur echo n’implique pas de n’importe quel système LOB.<br /><br /> Par défaut = lobapplication|  
|EnableAuthentication|System.Boolean|Lorsque la valeur est true, l’adaptateur attend une valeur dans le champ nom d’utilisateur dans les informations d’identification du client.<br /><br /> Par défaut = false|  
|HostName|System.String|Le nom du serveur où se trouve un système métier. Cette propriété est pour des fins d’illustration. L’adaptateur echo n’implique pas de n’importe quel système LOB.<br /><br /> Par défaut = lobhostname|  
  
## <a name="interface-implementation"></a>Implémentation de l’interface  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] définit une collection de classes et interfaces qui doivent être implémentées pour prendre en charge des fonctionnalités spécifiques de la carte. Le tableau suivant décrit ces classes et interfaces, leurs descriptions et indique quand les implémenter.  
  
|**Class/Interface**|**Quand mettre en œuvre**|**Description**|  
|--------------------------|---------------------------|---------------------|  
|Microsoft.ServiceModel.Channels.Common.IConnection|Si vous avez besoin définir la connexion au système cible.|Définit la connexion au système cible.|  
|Microsoft.ServiceModel.Channels.Common.IConnectionFactory|Si vous avez besoin créer une connexion au système cible.|Crée la connexion au système cible.|  
|Microsoft.ServiceModel.Channels.Common.ConnectionUri|Si vous avez besoin gérer un Uri de connexion.<br /><br /> Si vous avez besoin classer par catégorie de la propriété de connexion dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil.|Gère un Uri de connexion pour le système cible.|  
|Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler|Votre adaptateur doit prendre en charge la fonctionnalité de résolution de métadonnées.|Résout l’opération et le type de métadonnées.|  
|Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler|Si votre carte prend en charge la fonctionnalité de recherche de métadonnées.|Recherche les opérations dans le système cible.|  
|Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler|Votre adaptateur doit prendre en charge la fonctionnalité de navigation|Recherche les opérations dans le système cible.|  
|Microsoft.ServiceModel.Channels.Common.IOutboundHandler|Si votre adaptateur doit en général prendre en charge la fonctionnalité sortante.|Transforme le message de demande WCF entrant en message système cible, appelle la fonction spécifique du système cible, puis convertit la réponse à un message de réponse WCF sortant.|  
|Microsoft.ServiceModel.Channels.Common.IInboundHandler|Si votre carte prend en charge la fonctionnalité de trafic entrante.|Écoute de données et/ou des événements à partir du système cible.|  
  
 Pour simplifier le développement de votre adaptateur, utilisez le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] pour générer votre projet d’adaptateur, ce qui crée un ensemble de classes dérivées adaptées à vos fonctionnalités de l’adaptateur.  
  
 Pour personnaliser les propriétés de l’adaptateur et la connexion via le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils, modifier les fichiers suivants, générés par [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].  
  
-   {Projectname} BindingElement.cs  
  
-   {Projectname} BindingElementExtensionElement.cs  
  
-   {Projectname}ConnectionUri.cs  
  
 Pour plus d’informations sur la marche à suivre, consultez [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels pour apprendre WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)