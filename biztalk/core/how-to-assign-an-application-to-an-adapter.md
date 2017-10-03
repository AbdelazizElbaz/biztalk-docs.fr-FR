---
title: "Comment attribuer une Application à un adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ea2773-c53c-40a0-a312-015191746451
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5052d06576988ed71da8458a9d55115fb0b1c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-an-application-to-an-adapter"></a>Comment attribuer une Application à une carte
Une ou plusieurs applications doivent être affectées à un adaptateur pour qu'il puisse traiter les informations entre une application locale et un serveur distant.  
  
### <a name="to-assign-an-application-to-an-adapter"></a>Pour affecter une application à un adaptateur  
  
1.  Ajoutez l'application à l'adaptateur à l'aide d'`ISSOPSAdmin.AssignApplicationToAdapter`.  
  
2.  Vous pouvez extraire la liste d'applications actuelle affectée à un adaptateur en utilisant `ISSOAdmin.GetApplicationsForAdapter`.  
  
3.  Lorsque vous avez terminé, vous pouvez supprimer une application de l'adaptateur à l'aide d'`ISSOPSAdmin.RemoveApplicationFromAdapter`.