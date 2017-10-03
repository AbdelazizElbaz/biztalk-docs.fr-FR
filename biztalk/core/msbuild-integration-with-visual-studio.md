---
title: "Intégration de MSBUILD avec Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aedcabf7-b2cf-482a-9ade-7311e104bff9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4a639945881625dd697798080c913ec0e5e3a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msbuild-integration-with-visual-studio"></a>Intégration de MSBUILD avec Visual Studio
Visual Studio utilise le format de fichier de projet MSBUILD pour stocker les informations de version des projets gérés, y compris des projets BizTalk. Les paramètres de projet ajoutés et modifiés dans Visual Studio sont spécifiés dans le fichier .btproj généré pour chaque projet. Visual Studio utilise une instance hébergée de MSBUILD pour développer des projets BizTalk. Ainsi, il est possible de générer un projet BizTalk dans Visual Studio ou à partir de la ligne de commande en obtenant un résultat identique.  
  
 Pour plus d’informations sur MSBUILD, consultez [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).  
  
 Les procédures suivantes présentent l'utilisation de MSBUILD pour développer un exemple de projet BizTalk à partir de la ligne de commande.  
  
## <a name="to-build-a-biztalk-project-from-a-command-line"></a>Pour générer un projet BizTalk à partir d'une ligne de commande  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  Accédez au répertoire du projet, puis exécutez une commande MSBUILD pour créer la solution BizTalk.  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!NOTE]
    >  La solution peut contenir des projets BizTalk et non-BizTalk, tels qu'une bibliothèque de classes C#.