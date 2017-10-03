---
title: "Le modèle de Message d’InfoPath | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb055b1-8480-44dd-8739-f2981bca63c3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b8ec04d16da25f39060540aa8a8205421397d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-infopath-message-template"></a>Le modèle de Message d’InfoPath
Comme alternative à l’affichage de messages d’erreur ESB dans le portail de gestion ESB, les utilisateurs peuvent tirer parti d’un modèle de message Microsoft InfoPath nommé l’Afficheur des messages d’Exception ESB, fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 L’infrastructure de gestion d’Exception ESB peut conserver les messages dans un format sérialisé affichant, ainsi que le modèle ESB Exception l’Afficheur des messages, plusieurs vues de message d’erreur et les messages d’origine qu’il contient. L’Afficheur des messages d’Exception ESB propose les vues suivantes :  
  
-   vue Général ;  
  
-   Vue de l’objet exception  
  
-   vue Messages  
  
 La figure 1 illustre la vue générale de l’Afficheur des messages d’Exception ESB, qui affiche plus les propriétés ambiantes de l’exception.  
  
 ![Vue générale du Message d’exception](../esb-toolkit/media/ch4-exceptionmessagegeneralview.gif "ExceptionMessageGeneralView de chapitre 4")  
  
 **Figure 1**  
  
 **L’Afficheur des messages d’Exception ESB affichant la vue générale**  
  
 La figure 2 illustre la vue de l’objet d’Exception, qui affiche les propriétés et la trace de pile à partir de la **System.Exception** objet.  
  
 ![Objet d’Exception exception Message](../esb-toolkit/media/ch4-exceptionmessageexceptionobject.gif "ExceptionMessageExceptionObject de chapitre 4")  
  
 **Figure 2**  
  
 **L’Afficheur des messages d’Exception ESB affichant la vue de l’objet Exception**  
  
 Figure 3 illustre l’affichage de Messages, qui fournit une liste déroulante à partir de laquelle l’utilisateur peut sélectionner à partir des messages persistants disponibles. La vue affiche les valeurs des propriétés de contexte du message persistant et le contenu du message XML.  
  
 ![Affichage des Messages de Message d’exception](../esb-toolkit/media/ch4-exceptionmessagemessagesview.gif "ExceptionMessageMessagesView de chapitre 4")  
  
 **Figure 3**  
  
 **L’Afficheur des messages d’Exception ESB affichant la vue Messages**