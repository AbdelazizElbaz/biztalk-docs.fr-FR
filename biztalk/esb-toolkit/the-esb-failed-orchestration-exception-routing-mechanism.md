---
title: "Mécanisme de routage d’Orchestration Exception d’échec de l’architecture ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa05f44b-7fb2-48fd-886d-c6d179904e6d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afda61ea19587b327f0fe773b150eeb8f88a4f7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-failed-orchestration-exception-routing-mechanism"></a>Échec de l’architecture ESB mécanisme de routage d’Orchestration (Exception)
Le mécanisme d’ESB Échec de l’Orchestration Exception routage offre les fonctionnalités suivantes :  
  
-   **Création de messages d’erreur qui capturent les propriétés ambiantes.** Le **CreateFaultMessage** méthode génère un message d’erreur qui contient l’orchestration nom du service et l’ID d’instance de service, la forme d’orchestration actuellement activée, le nom de l’application à laquelle l’orchestration est déployé, le nom du serveur de traitement de l’orchestration, la date de l’exception et l’heure (format UTC). Il ajoute également implicitement actuel **System.Exception** objet généré dans le Gestionnaire d’exceptions de la forme d’orchestration en cours.  
  
-   **Ajout de messages d’orchestration existante à un message d’erreur**. Le **AddMessage** méthode conserve le paramètre XLANG du message d’orchestration et de toutes les propriétés de contexte de message dans le message d’erreur.  
  
-   **Ajouter explicitement un objet d’Exception existant à un message d’erreur**. Le **SetFaultMsgException** méthode sérialise l’objet comme un **System.Exception** et la conserve dans le message d’erreur.  
  
-   **La récupération d’une collection énumérée de type sans les messages à partir d’un message d’erreur reçu par un abonné**. Le **GetMessages** méthode récupère tous les messages persistants à partir de l’orchestration a échoué en tant que messages XLANG. Il retourne toutes les propriétés de contexte d’origine de chaque message persistante dans chaque message XLANG.  
  
-   **La récupération d’un message d’orchestration XLANG fortement typé à partir d’un message d’erreur reçu par un abonné**. Le **GetMessage** méthode récupère un message persistant d’un type spécifique à partir du message d’erreur sous forme de message XLANG. Il retourne toutes les propriétés de contexte d’origine du message persistante dans le message XLANG. Prend également en charge la récupération de la **System.Exception** objet généré par l’orchestration a échoué et récupère un persistante **System.Exception** objet à partir du message d’erreur.