---
title: Lots de messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f893d16-2670-4463-9a89-6f5be912a045
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25866ac076d77eae13d2ab5378a7582f584b6670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-batches"></a>Lots de messages
Lorsque votre adaptateur possède un groupe de messages devant être traités en même temps, il est préférable de les regrouper par lot afin d'optimiser les performances. Dans le contexte de la programmation, les lots de messages sont des ensembles de messages associés à une opération. En regroupant les messages dans un lot au lieu de l’envoi de chaque message individuellement, vous optimisez l’utilisation des ressources et des tâches de traitement. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise le traitement par lot pour :  
  
-   amortir le coût de la transaction sur plusieurs messages ;  
  
-   augmenter la vitesse en réduisant le nombre interne d'allers-retours vers une base de données ;  
  
-   optimiser l'utilisation de la réserve de threads de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en traitant les messages de manière asynchrone.  
  
 Un lot est une unité de travail atomique. En d'autres termes, soit toutes les opérations qu'il contient réussissent, soit elles échouent toutes. Si une opération d'un lot réussit mais qu'une autre opération échoue, toutes les opérations qui constituent ce lot sont invalidées et les messages doivent être resoumis. Cela signifie qu'un adaptateur doit effectuer trois actions lorsqu'un lot échoue :  
  
-   déterminer les messages ayant échoué ;  
  
-   décider de ce qu'il doit advenir des messages ayant échoué ;  
  
-   resoumettre les messages qui n'ont pas échoué.