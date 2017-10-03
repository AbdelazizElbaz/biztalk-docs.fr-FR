---
title: "Architecture de l’adaptateur de réception SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16f32689-0b70-4389-8596-991fd776f185
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aca9b5ef1fd1130feeebad3ec6fdf072d3bf88d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-architecture"></a>Architecture de l’adaptateur de réception SWIFT
Dans BizTalk Server, l’adaptateur de réception est hébergé dans son propre espace mémoire, ce qui signifie que la création d’un processus distinct pour exécuter l’ordinateur hôte. Cet ordinateur hôte est généré en définissant un sous-système dans la configuration de liaison SWIFTNet (SNL).  
  
 L’exécutable du serveur est configuré comme un sous-système dans la configuration de SNL (paramfile) et est généré en exécutant la commande de démarrage de SWIFTNet. L’application du serveur SNL se termine par l’exécution de la commande d’arrêt de SWIFTNet. SNL gère la durée de vie de l’exécutable du serveur.  
  
> [!NOTE]
>  Le scénario de bureau de service requiert la carte à plusieurs membres SWIFT s’exécutant sous leurs propres contextes de sécurité de service. Cela peut être pris en charge en configurant un individu emplacement par des membres et la génération automatique de plusieurs instances de l’exécutable du serveur de réception, chacun d’eux dédié à un emplacement de réception.  
  
 Dans BizTalk Server, l’adaptateur de réception prend en charge les modèles de communication suivants pour interagir avec le moteur de messagerie BizTalk :  
  
-   Une façon : ce mode est requis lorsque l’adaptateur de réception (serveur) fonctionne en mode différé. En mode différé, l’adaptateur envoie un accusé de réception par défaut pour les messages entrants. Les valeurs par défaut pour l’accusé de réception peuvent être configurés dans les propriétés de l’adaptateur. Réponse de niveau entreprise peut être envoyé plus tard par l’application LOB via l’adaptateur d’envoi.  
  
    > [!NOTE]
    >  En cas de mode différé, toutes les valeurs doivent être remplies dans la configuration de la carte, étant donné que la carte consiste à construire la réponse.  
  
-   Demande de réponse, dans ce mode, l’adaptateur soumet la demande du SWIFT de BizTalk et attend la réponse. L’adaptateur est le délai d’attente s’il n’existe aucune réponse de l’application métier. La valeur de délai d’expiration est configurable dans la configuration de l’adaptateur. La valeur par défaut est 60 secondes.  
  
     L’adaptateur de réception peut recevoir le rappel SNL uniquement sur un thread. Cela signifie que l’adaptateur de réception peut recevoir davantage les messages à partir de SNL uniquement après l’envoi du premier message. Par conséquent, la taille de lot par défaut est définie sur 1.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [URI d’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)  
  
-   [Initialisation de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)  
  
-   [Contexte de sécurité de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)  
  
-   [Les Modes synchrone et différé de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)  
  
-   [Magasin de l’adaptateur et le transfert de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)