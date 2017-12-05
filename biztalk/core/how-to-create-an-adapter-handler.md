---
title: "Comment créer un gestionnaire d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, handlers [adapters]
- handlers [adapters], creating
- adapters, handlers
ms.assetid: 09569417-dce6-473d-891f-6fd12347bcf0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e26caf02978006040e52ed3c62e520f51362e2c4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-an-adapter-handler"></a>Comment créer un gestionnaire d’adaptateur
Vous pouvez créer un gestionnaire d'adaptateur d'envoi ou de réception à l'aide de la console Administration de BizTalk Server.  
  
> [!NOTE]
>  Vous devez être membre du groupe Administrateurs SSO pour créer un gestionnaire d'adaptateur.  
  
### <a name="to-create-an-adapter-handler"></a>Pour créer un gestionnaire d'adaptateur  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur la carte pour laquelle vous souhaitez ajouter un envoi ou Gestionnaire de réception, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi** pour créer un gestionnaire d’envoi ou sur  **Gestionnaire de réception** pour créer un gestionnaire de réception.  
  
3.  Dans le  **\<nom d’hôte\> propriétés** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel l’adaptateur gestionnaire sera associé.  
  
4.  Si vous créez un gestionnaire d’envoi de l’adaptateur, sélectionnez l’option à **transformer en gestionnaire par défaut** si vous souhaitez que cette le Gestionnaire d’envoi par défaut pour cette carte.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et suppression de gestionnaires d’adaptateur](../core/creating-and-deleting-adapter-handlers.md)