---
title: MSBUILD autonome | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21aa3693-3788-4874-b506-6f4584fb4fd5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcee1d06bf57eb2ea98c214501c2499f0ce83d95
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="standalone-msbuild"></a>MSBUILD autonome
Le **génération de projet** composant de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de créer des solutions BizTalk Server sans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour installer le **génération de projet** composant sur votre serveur, sélectionnez le **composant de création de projet** option dans le **catégorie logiciels supplémentaires** pendant l’installation. Vous devez désélectionner la **outils de développement et Kit de développement logiciel** lors de l’installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur sans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 Pour plus d’informations sur MSBUILD, consultez [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).  
  
## <a name="to-build-a-biztalk-project"></a>Pour générer un projet BizTalk  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
2.  Type **cmd**, puis appuyez sur ENTRÉE.  
  
3.  Accédez au répertoire du projet, puis exécutez une commande MSBUILD pour créer la solution BizTalk.  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!TIP]
    >  Vous pouvez définir la variable d’environnement PATH pour pointer vers le dossier dans lequel msbuild.exe réside (\<*répertoire d’installation windows*\>\Microsoft.NET\Framework\v4).