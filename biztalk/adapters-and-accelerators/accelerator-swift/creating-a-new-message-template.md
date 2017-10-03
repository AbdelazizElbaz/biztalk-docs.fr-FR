---
title: "Création d’un modèle de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, templates
- templates, creating
- creating, templates
ms.assetid: 8c601d2b-b7a5-4ac4-9d98-fd9960038340
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a15e1c2a59635ca653e5a4817f29cdc918dca09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-new-message-template"></a>Création d’un modèle de Message
Vous pouvez créer un nouveau modèle de message à partir d’un modèle existant. Cela permet à un créateur de créer une nouvelle instance de message sur un formulaire personnalisé, par exemple une copie d’un formulaire SWIFT standard qui a déjà des données introduites dans ce dernier. À l’aide du nouveau modèle, le créateur ne dispose pas d’entrer toutes les données requises lors de l’utilisation d’un formulaire vide.  
  
 Vous créez un nouveau modèle à partir d’une instance de message que vous avez généré à l’aide du modèle existant correspondant. Ajouter des données aux champs de la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran (comme si vous créez une nouvelle instance de message), puis enregistrez le formulaire en tant que nouveau modèle.  
  
### <a name="to-save-a-modified-existing-template-as-a-new-template"></a>Enregistrer un modèle existant modifié sous la forme d’un nouveau modèle  
  
1.  Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.  
  
2.  Cliquez sur **Documents**.  
  
3.  Dans la page Documents, cliquez sur le **nouveaux SWIFT MT Messages** bibliothèque de documents.  
  
4.  Dans la page nouveaux Messages de MT SWIFT, cliquez sur la catégorie contenant le modèle que vous souhaitez baser votre nouveau modèle.  
  
5.  Pointez sur le modèle que vous souhaitez baser votre nouveau modèle et cliquez sur la flèche située à droite, puis cliquez sur **modifier dans Microsoft Office InfoPath**.  
  
6.  Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, sous la forme de message, entrez les données de message que vous souhaitez faire partie du modèle.  
  
7.  Cliquez sur **fichier**, puis cliquez sur **Enregistrer sous**.  
  
8.  Dans la fenêtre indiquant que le formulaire contient des erreurs de validation, cliquez sur **Oui**.  
  
9. Dans la boîte de dialogue Enregistrer sous, sélectionnez le dossier pour le modèle dans le **enregistrer dans** texte zone et entrez un nom de fichier dans le **nom de fichier** zone de texte. Cliquez sur **Enregistrer**.  
  
10. Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour le nouveau modèle.  
  
    > [!NOTE]
    >  Pour créer une instance de message à partir du nouveau modèle, consultez [création et envoi d’un nouveau Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md).