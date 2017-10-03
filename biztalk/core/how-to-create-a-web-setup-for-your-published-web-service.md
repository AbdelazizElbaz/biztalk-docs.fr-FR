---
title: "Comment créer un programme d’installation Web pour votre Service Web publié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
- Web services, .msi file
- .msi files, Web services
ms.assetid: 77c86242-1d27-4d99-ae00-fe2614bc13ef
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87c5ec4fe61c8649fe951460917cfde8788f2e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-web-setup-for-your-published-web-service"></a>Création d'un projet d'installation Web pour votre service Web publié
Vous pouvez créer un package d'installation pour simplifier la configuration de votre service Web dans un environnement de production. Cette opération génère un fichier .MSI.  
  
### <a name="to-create-an-installation-package-to-produce-an-msi-file-using-visual-studio"></a>Pour créer un package d’installation afin de générer un fichier .MSI à l’aide de Visual Studio  
  
1.  Ouvrez le projet de service Web ASP.NET publié.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le nœud solution, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
3.  Dans le **ajouter un nouveau projet** boîte de dialogue le **Types de projets** zone, développez **autres Types de projets**, développez **le programme d’installation et les projets de déploiement**, puis sélectionnez **le programme d’installation de Visual Studio**. Dans le **modèles** zone, sélectionnez **projet d’installation Web**.  
  
4.  Dans le **nom** zone de texte, tapez un nom pour le projet d’installation Web. Vous pouvez utiliser le même nom que le projet de Service Web ASP.NET, ajoutez « _Setup » comme suffixe, puis cliquez **OK**.  
  
5.  Dans l’Explorateur de solutions, cliquez sur le nœud du projet d’installation Web nouvellement créé, puis pointez sur **vue**, puis cliquez sur **système de fichiers**.  
  
6.  Dans le **système de fichiers** fenêtre, avec le bouton droit le **dossier d’Application Web** nœud et pointez sur **ajouter**, puis cliquez sur **sortie du projet**.  
  
7.  Dans le **ajouter un groupe de sorties de projet** boîte de dialogue, sélectionnez **sortie principale** et **les fichiers de contenu** du Service Web ASP.NET du projet, puis cliquez sur **OK**.  
  
8.  Dans l’Explorateur de solutions, développez le **dépendances détectées** nœud sous le projet d’installation Web.  
  
9. Sélectionnez toutes les dépendances. Dans le **propriétés** , configurez la **exclure** propriété **True**.  
  
10. Générez le projet d'installation Web.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création de projets d’installation Web, consultez « Comment pour créer ou ajouter un projet d’installation Web » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection d’aide à [http://go.microsoft.com/fwlink/?LinkId=62268](http://go.microsoft.com/fwlink/?LinkId=62268).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)