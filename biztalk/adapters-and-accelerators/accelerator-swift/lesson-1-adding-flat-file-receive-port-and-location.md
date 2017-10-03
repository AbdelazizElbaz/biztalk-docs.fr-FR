---
title: "Leçon 1 : Ajout de fichier plat Port de réception et emplacement | Documents Microsoft"
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
ms.assetid: 881f58d8-f541-4a85-b534-cb1ca627c002
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fcd41cd38074377fa179e3a414b278521c31f26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-adding-flat-file-receive-port-and-location"></a>Leçon 1 : Ajout d’un fichier plat Port de réception et emplacement
Le port de réception a toujours un emplacement de réception associés que vous devez configurer lorsque vous ajoutez le port de réception. Un emplacement de réception définit une adresse spécifique pour un message entrant et le pipeline que vous utilisez pour traiter le message.  
  
### <a name="to-add-a-receive-port"></a>Pour ajouter un port de réception  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
2.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **MT103_FlatFile_ReceivePort**.  
  
3.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.  
  
4.  Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
5.  Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **MT103_FlatFile_ReceivePort**, puis cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **MT103_FlatFile_ReceiveLocation**.  
  
7.  Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.  
  
8.  Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
9. Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.  
  
10. Dans la boîte de dialogue Rechercher un dossier, déplacer vers le  **\<lecteur > : \Labs\Inbound** dossier, puis cliquez sur **créer un nouveau dossier**.  
  
11. Créer un **FlatFile** dossier  **\<lecteur > : \Labs\Inbound**, puis cliquez sur **OK**.  
  
12. Dans le **masque de fichier** , tapez  **\*.txt**, puis cliquez sur **OK**.  
  
13. Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.  
  
14. Pour le **Pipeline de réception** boîte, sélectionnez **MT103ReceivePipeline** dans la liste déroulante.  
  
15. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
16. Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, avec le bouton droit **MT103_FlatFile_ReceiveLocation**, puis cliquez sur **activer**.  
  
 Passez à [leçon 2 : ajout d’un Port d’envoi XML](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).