---
title: "Comment créer des Ports d’envoi pour JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: 858425ef-bdb7-4d2d-90ca-b3655e389749
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc77fd72171983ab2fbc7de42ddf36d770d045c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a>Création de ports d'envoi pour JD Edwards OneWorld
La procédure suivante permet de créer un port d'envoi.  
  
### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis accédez à la application requise.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
    > [!NOTE]
    >  Vous pouvez également utiliser **Port statique unidirectionnel**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez le nom du port d’envoi (par exemple, tapez **SendToJDE**.)  
  
4.  Dans le **Type** la liste déroulante, sélectionnez **JDEOneWorld**.  
  
5.  Dans le **URI** liste déroulante, sélectionnez le Gestionnaire d’envoi.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md)