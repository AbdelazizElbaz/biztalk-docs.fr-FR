---
title: "Port de réception Ajout MX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4818d6af-df1d-481e-becf-1af633735248
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69123b876bdda4b5f999277a1710cdeb1cb61fe7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-mx-receive-port"></a>Ajout de MX Port de réception
**Pour ajouter un MX port de réception :**  
  
1.  Démarrer **Administration de BizTalk Server** console.  
  
2.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans la boîte de dialogue Propriétés du Port de réception, dans la zone Nom, tapez **MX_ le Port de réception**.  
  
5.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.  
  
6.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
7.  Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **le Port de réception MX_**, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans la zone Nom, tapez **MX_ un emplacement de réception**.  
  
9. Dans la section de Transport pour la zone de texte Type, cliquez sur la liste déroulante et sélectionnez **fichier**.  
  
10. Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
11. Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**, puis sélectionnez un emplacement de fichier.  
  
12. Dans la boîte de dialogue Propriétés du Transport FILE, vérifiez que \*.xml est entré dans la zone de masque de fichier, puis cliquez sur **OK**.  
  
13. Dans la boîte de dialogue Propriétés de l’emplacement de réception, assurez-vous que BizTalkServerApplication est entrée pour la zone d’un gestionnaire de réception.  
  
14. Dans la boîte de Pipeline de réception, sélectionnez **Pipeline de réception** (le pipeline de réception qui a été déployé dans le projet de Pipeline) dans la liste déroulante, cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
15. Avec le bouton droit à l’emplacement que vous venez de configurer, puis cliquez sur **activer**.