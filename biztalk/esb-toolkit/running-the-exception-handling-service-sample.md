---
title: "Exemple de Service de gestion des exceptions en cours d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d69e720c-89e4-42c2-b4d0-31f0b865ab7f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a224c985591801bc9622000c35587b7137f933
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-exception-handling-service-sample"></a>Exemple de Service de gestion des exceptions en cours d’exécution
L’exemple de Service de gestion des exceptions montre comment consommer le Service Web de gestion des exceptions afin d’envoyer une erreur dans l’infrastructure de gestion d’Exception ESB à partir d’une application externe. La procédure suivante pour exécuter cet exemple nécessite [installant les exemples de gestion des exceptions](../esb-toolkit/installing-the-exception-management-samples.md).  
  
 **Pour exécuter l’exemple de Service de gestion des exceptions**  
  
1.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ExceptionHandlingService, où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et ouvrez le fichier de solution Visual Studio nommé ExceptionHandlingService.sln.  
  
2.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], cliquez sur **démarrer le débogage** sur la barre d’outils.  
  
3.  Dans le formulaire qui charge, cliquez sur le **générer une Exception** bouton.  
  
4.  Dans l’Explorateur Windows, ouvrez le dossier \Samples\Exception Handling\Test\Filedrop\All_Exceptions et ouvrez le fichier le plus récent Exceptions_ {GUID} .xml.  
  
5.  Examinez le contenu de l’exception générée.  
  
 Pour plus d’informations sur la façon dont l’exemple de Service de gestion des exceptions utilise le service de gestion des exceptions, consultez [Exception gestion Service exemple fonctionnement](../esb-toolkit/how-the-exception-handling-service-sample-works.md).