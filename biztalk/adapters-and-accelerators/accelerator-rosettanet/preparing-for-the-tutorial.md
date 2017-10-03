---
title: "Conditions préalables pour le didacticiel RosettaNet Loopback dans BizTalk Server | Documents Microsoft"
description: "Conditions préalables pour parcourir le didacticiel de bouclage de l’accélérateur RosettaNet (BTARN) dans BizTalk Server"
caps.latest.revision: "9"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e26696c-86c5-448b-9cd6-bfd4a279151a
ms.author: mandia
ms.openlocfilehash: 9767f7823e80d4de67345ba0fbf59c1435adb8e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-tutorial"></a>Préparer pour le didacticiel

## <a name="prerequisites"></a>Conditions préalables
Avant de commencer le didacticiel de bouclage :
  
-   [Installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md) l’accélérateur. Vous devrez peut-être ajouter le répertoire virtuel btarnhttpreceive à la liste d’exclusion de chemin d’accès géré Windows SharePoint dans l’Administration centrale de SharePoint.  
  
-   Vérifiez que l’hôte BizTalkServerIsolatedHost l’hôte BizTalkServerApplication ont le **approuvé par authentification** option est activée. Pour vérifier, ouvrez la console Administration de BizTalk Server, développez **hôtes**. Cliquez sur l’ordinateur hôte, sélectionnez **propriétés**et vérifiez **approuvé par authentification** s’il n’est pas activé.  

    Si vous avez plusieurs instances d’hôte, puis supprimez tous les mais une instance de l’hôte. Par exemple, supprimez l’instance d’hôte isolé BizTalk Server et conserver l’instance de l’hôte BizTalkServerApplication). Permet de sélectionner **approuvé par authentification** sur l’hôte associé à cette instance et puis recréer les instances d’hôte supplémentaires.  
  
## <a name="next-step"></a>Étape suivante
 [Étape 1 : Créer l’organisation d’origine](step-1-create-the-home-organization.md)