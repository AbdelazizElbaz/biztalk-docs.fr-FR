---
title: "Leçon 1 : Ajout de code XML Port de réception et emplacement | Documents Microsoft"
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
- receive ports, creating
- creating, receive ports
ms.assetid: 252bc080-3820-44cc-8749-715869f3f684
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 186cbb4e021a281ab834f04097f005c2597fbd37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-adding-xml-receive-port-and-location"></a>Leçon 1 : Ajout de Port et l’emplacement de réception XML
un port de réception est un groupe logique d'emplacements de réception similaires. Un emplacement de réception définit une adresse spécifique (par exemple, un emplacement de fichier ou URL) pour un message entrant et le pipeline est utilisé pour traiter le message.  
  
### <a name="to-add-a-receive-port"></a>Pour ajouter un port de réception  
  
1.  Démarrer **Administration de BizTalk Server** console.  
  
    > [!NOTE]
    >  La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.  
  
2.  Dans la Console Administration de BizTalk Server, développez le **Administration de BizTalk Server** nœud, puis le **groupe BizTalk** nœud, puis le **Applications** nœud, puis le **BizTalk Application 1** nœud.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **MT103_XML_ReceivePort**.  
  
5.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK.**  
  
6.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
7.  Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **MT103_XML_ReceivePort**, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **MT103_XML_ReceiveLocation**.  
  
9. Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.  
  
10. Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
11. Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**. Déplacer vers le  **\<lecteur > : \Labs** dossier, puis cliquez sur **créer un nouveau dossier**.  
  
12. Dans la boîte de dialogue Rechercher un dossier, créez un **entrant** dossier  **\<lecteur > : \Labs**, puis créez une **XMLFile** dossier dans  **\<lecteur > : \Labs\Inbound**. Cliquez sur **OK**.  
  
13. Dans la boîte de dialogue Propriétés du Transport FILE, vérifiez que  **\*.xml** est entré dans le **masque de fichier** zone, puis cliquez sur **OK**.  
  
14. Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.  
  
15. Pour le **Pipeline de réception** boîte, sélectionnez **XMLReceive** dans la liste déroulante.  
  
16. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
17. Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, avec le bouton droit **MT103_XML_ReceiveLocation**, puis cliquez sur **activer**.  
  
    > [!NOTE]
    >  Une fois que l’emplacement de réception, BizTalk interroge activement votre dossier de fichiers.  
  
 Passez à [leçon 2 : ajout du Port d’envoi de fichier plat](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md).