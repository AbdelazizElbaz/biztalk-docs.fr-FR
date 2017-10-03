---
title: "Gestion de l’extérieur soumis les Exceptions à l’aide d’un gestionnaire personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53fa661e-d391-47c0-92d5-1d0c45b5963d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba3fc49756619f77188f0a311ff46eb18e7f0b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-externally-submitted-exceptions-using-a-custom-handler"></a>Gestion de l’extérieur soumis les Exceptions à l’aide d’un gestionnaire personnalisé
Dans ce cas de figure, un client externe envoie un message d’exception via un service Web. Un port d’envoi, préconfiguré avec le composant de pipeline encodeur d’Exception ESB, s’abonne au message d’erreur ; Il traite et l’enregistre dans un fichier de disque que vous pouvez consulter à l’aide de Microsoft InfoPath, comme indiqué dans la Figure 1.  
  
 ![Gestion des Exceptions externes](../esb-toolkit/media/ch3-handlingexternalexceptions.gif "Ch3-HandlingExternalExceptions")  
  
 **Figure 1**  
  
 **La gestion des messages entrants d’exception ou une erreur et la persistance dans un fichier de disque**  
  
 L’exemple Exception la gestion des services fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment utiliser le Service d’Exception ESB comme un mécanisme universel pour envoyer des messages d’erreur à partir d’applications externes qui seront stockés dans le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] base de données de gestion des exceptions. Pour plus d’informations, consultez [exécution de l’exemple de Service de la gestion des exceptions](../esb-toolkit/running-the-exception-handling-service-sample.md).