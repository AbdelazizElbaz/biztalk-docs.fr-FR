---
title: "Emplacement de réception de création d’un A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
ms.assetid: 712cf42f-8d71-47e9-b2bf-3da158b74fe4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3f0835c6d83efc9db91f5c1d63e91f4c143399d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-a4swift-receive-location"></a>Emplacement de réception de création d’un A4SWIFT
Vous devez créer un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] emplacement de réception pour activer la réception des messages à partir du réseau rapide par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], comme indiqué dans l’illustration suivante. L’emplacement de réception reçoit les messages de fichier plat à partir d’un dossier de fichiers entrant.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")  
  
 **Résumé**  
  
 Créer et lier un port de réception unidirectionnel, puis créer et activer un emplacement de réception avec les propriétés suivantes et les composants :  
  
|Composants/propriété|Paramètre|  
|--------------------------|-------------|  
|Port de réception|Port unidirectionnel|  
|Type de transport |FILE|  
|Adresse URI|Nom du dossier que vous souhaitez recevoir le message|  
|Masque de fichier|\*.  *\<extension >*, où \< *extension*> est l’extension d’entrant message de fichier plat|  
|Gestionnaire de réception|BizTalkServerApplication|  
|Pipeline de réception|Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline de réception qui vous avez créé|  
  
### <a name="to-add-the-receive-port-and-location"></a>Pour ajouter le port de réception et l’emplacement  
  
1.  Démarrer **Administration de BizTalk Server** console.  
  
    > [!NOTE]
    >  La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.  
  
2.  Dans la Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception.  
  
5.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.  
  
6.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
7.  Dans la boîte de dialogue un Port de réception, sélectionnez, cliquez sur le port de réception que vous venez de créer, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception.  
  
9. Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.  
  
10. Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
11. Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**. Déplacer vers le dossier que vous souhaitez recevoir le message. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.  
  
12. Dans la boîte de dialogue Propriétés du Transport FILE, dans le **masque de fichier** , entrez  **\*.\<* extension*>**, où \<* extension*> est l’extension d’entrant message de fichier plat, par exemple **.txt**. Cliquez sur **OK**.  
  
13. Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.  
  
14. Pour le **Pipeline de réception** , sélectionnez votre pipeline de réception personnalisé dans la liste déroulante.  
  
15. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
16. Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, cliquez sur l’emplacement de réception que vous venez de créée, puis cliquez sur **activer**.  
  
    > [!NOTE]
    >  Une fois que l’emplacement de réception, BizTalk interroge activement votre dossier de fichiers.