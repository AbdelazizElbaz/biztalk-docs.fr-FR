---
title: "Une exception s’est produite pendant l’exécution de l’orchestration de routage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ec8921-ba05-496e-8dcc-fd8994fcb8b7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e865ec091330a863cb2bab90bbafd9b891edb05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-routing-orchestration"></a>Une exception s'est produite lors de l'exécution de l'orchestration de routage
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|ExceptionOccuredDuringRouting|  
|Texte du message|Une exception s'est produite lors de l'exécution de l'orchestration de routage. Message d'erreur = {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de routage n'a pas pu traiter correctement chaque copie de l'élément de lot XML en raison de la condition d'erreur mentionnée dans le champ ErrorMessage.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, déterminer ce qui est la condition d’erreur à partir du champ ErrorMessage, résolvez l’erreur et soumettez à nouveau le message.