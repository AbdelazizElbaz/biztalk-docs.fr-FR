---
title: "À l’aide de routage dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caa3a35f-cafa-4524-8b96-f8a333b7ff87
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38b668f53ba87a461441b0dbb498ae0677fa5956
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-dynamic-routing"></a>À l’aide de routage dynamique
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge le routage dynamique de messages à l’aide d’un processus intégré et un agent de distribution générique ; elle prend également en charge le routage dynamique de messages sur la couche de messagerie à l’aide de composants de pipeline de répartiteur d’ESB ou désassembler le répartiteur ESB.  
  
## <a name="overview"></a>Vue d'ensemble  
 Le mécanisme de résolution dynamique [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] permet la découverte des points de terminaison lorsqu’un message arrive, ou immédiatement avant un message est remis.  
  
## <a name="how-it-works"></a>Fonctionnement  
 L’agent de distribution générique fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est un exemple et un guide de développement et de l’utilisation des techniques de routage dynamiques. Vous pouvez facilement créer des agents de remise supplémentaires ou implémenter des agents d’administration consistant à un port d’envoi (qui n’implémentent pas une orchestration). Par défaut, les composants de pipeline ESB Dispatch et désassembleur de Dispatch ESB offrent qu'aussi bien optimisé plus la fonctionnalité de routage dynamique.  
  
 L’agent de distribution générique lui-même implémente une orchestration qui s’abonne aux messages où le **nom** attribut actuelles **ServiceInstance** élément dans l’itinéraire est  **Microsoft.Practices.ESB.Services.Routing**. L’agent exécute la séquence d’opérations suivante :  
  
1.  Il reçoit un message non typé (System.Xml.XmlDocument).  
  
2.  Il tente de résoudre un nombre n de points de terminaison à l’aide du Gestionnaire de programme de résolution.  
  
3.  Il utilise le Gestionnaire d’adaptateur pour définir les propriétés de point de terminaison de contexte du message et le port dynamique logique.  
  
4.  Elle publie le message via le port d’envoi de la liaison directe, qui a déclenché l’abonnement de BizTalk Server sur le port d’envoi dynamique pour le routage des messages supplémentaires.  
  
## <a name="how-to-configure-dynamic-routing"></a>Comment configurer le routage dynamique  
 Pour plus d’informations sur la façon de configurer le routage dynamique à l’aide du Concepteur d’itinéraire, consultez Création d’itinéraires à l’aide du Concepteur de feuille de route.  
  
## <a name="dynamic-routing-errors"></a>Erreurs de routage dynamiques  
 Le mécanisme de routage dynamique sera créer et publier un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] message d’erreur dans les cas suivants :  
  
-   L’agent de remise ne peut pas déterminer le point de terminaison pendant la résolution juste-à-temps (JIT).  
  
-   Un échec de remise se produit.  
  
-   Aucun abonné n’existe pour le message de sortie.  
  
-   Toute exception système se produit.