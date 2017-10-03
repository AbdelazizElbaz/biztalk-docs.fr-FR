---
title: Comment BizTalk Server instancie un adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ebe7585-5939-4142-9281-990b4849e28d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32e6e40bf39c09e747391bba51a54143fc67e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-instantiates-an-adapter"></a>Instanciation d'un adaptateur par BizTalk Server
Lorsque le service BizTalk démarre, tous les adaptateurs de réception sont instanciés, à condition qu'ils disposent d'au moins un emplacement de réception configuré et actif. Par défaut, l'adaptateur d'envoi n'est instancié que lorsque le moteur de messagerie supprime de la file d'attente le premier message à envoyer par son intermédiaire (Cela est parfois appelé « création différée ».) Toutefois, si vous avez besoin instancier un adaptateur d’envoi au démarrage du service, vous pouvez utiliser la **InitTransmitterOnServiceStart** fonction d’adaptateur. Cette fonction entraîne la création, par le moteur de messagerie, de l'adaptateur d'envoi au démarrage du service et permet d'empêcher la création différée par défaut. Cette création différée permet de limiter la quantité de ressources système utilisées lorsque les adaptateurs ne sont pas configurés sur les points de terminaison.  
  
 Il est recommandé, lors de la création d'un adaptateur personnalisé, d'utiliser un code géré. Il n'est toutefois pas impossible d'avoir recours aux composants COM natifs. Pour les composants COM, l’adaptateur est instancié dans la manière normale à l’aide **CoCreateInstance**.  
  
 Pour le code managé, vous devez spécifier le .NET **type** dans le fichier de configuration ; le chemin d’accès de l’assembly est facultatif.  
  
 Les options de déploiement suivantes sont possibles :  
  
|Type .NET|Chemin de l'assembly|Méthode de déploiement des assemblys|  
|---------------|-------------------|--------------------------------|  
|Specified|Non spécifié|Copier l'assembly dans le répertoire de produit ou sous-répertoire du répertoire de produit portant le même nom que l'assembly|  
|Specified|Non spécifié|Assembly du GAC (Global Assembly Cache)|  
|Specified|Specified|Copier l'assembly dans le répertoire spécifié|  
  
 **Conseil de dépannage :** lorsque vous créez un adaptateur à l’aide de code managé, si la création échoue, utilisez l’outil fuslogvw.exe pour déterminer s’il existe des références aux assemblys qui ne peut pas être résolus. Il s'agit d'une erreur fréquemment rencontrée.  
  
 Le schéma suivant montre la logique de création des adaptateurs, en fonction de la configuration spécifiée :  
  
 ![](../core/media/initializingtheadapter.gif "InitializingTheAdapter")  
  
 Le tableau suivant montre un exemple de configuration pour un adaptateur de réception et un assembly d'exécution.  
  
|Méthode de déploiement des assemblys|InboundTypeName|InboundAssemblyPath|  
|--------------------------------|---------------------|-------------------------|  
|Spécifier l'emplacement de l'assembly|Microsoft.Samples.MyReceiveAdapter|C:\MyAdapter\MyAdapter.dll|  
|Spécifier le type .NET (inclure la clé publique, la version et les informations de culture)|Microsoft.Samples.MyReceiveAdapter, MyReceiveAdapter, Version = 1.0.2510.24622, Culture = neutral, PublicKeyToken = 077cf886a2d1c020|Néant|  
|Assembly GAC|Microsoft.Samples.MyReceiveAdapter, MyReceiveAdapter, Version = 1.0.2510.24622, Culture = neutral, PublicKeyToken = 077cf886a2d1c020|Néant|