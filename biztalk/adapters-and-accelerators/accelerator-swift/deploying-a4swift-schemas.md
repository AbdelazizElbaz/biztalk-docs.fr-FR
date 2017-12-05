---
title: "Déploiement de schémas d’A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, A4SWIFT
- deploying, A4SWIFT schemas
- A4SWIFT, deploying schemas
- schemas, deploying
ms.assetid: a6aed2cd-3578-442e-ab1e-8284cc5f7b72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc89b26d0eee970268d5e9084cd0827d3100fd7b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-a4swift-schemas"></a>Déploiement de schémas d’A4SWIFT
Vous devez déployer les schémas des messages SWIFT à échanger.  
  
 **Résumé**  
  
 Déployer les schémas suivants :  
  
-   Types.xsd Base SWIFT  
  
-   SWIFT Types.xsd données communes  
  
-   Schéma spécifique pour un type de message, par exemple, MT103.xsd  
  
### <a name="to-create-a-strong-named-swift-project"></a>Pour créer un projet SWIFT avec nom fort  
  
1.  Dans Visual Studio, cliquez sur **fichier**, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **types de projet** volet, sélectionnez le **projets BizTalk** dossier.  
  
3.  Dans le **modèles** volet, sélectionnez **projet BizTalk Server vide**.  
  
4.  Dans le **nom** , tapez le nom souhaité pour le nom du projet.  
  
5.  Dans le **Solution** boîte, sélectionnez **créer une nouvelle Solution**. Dans le **emplacement** , entrez l’emplacement du projet que vous ajoutez au projet de schéma.  
  
6.  Cliquez sur **OK** pour ouvrir le nouveau projet.  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]Ajoute un nouveau projet à l’Explorateur de solutions et crée le dossier du projet et les fichiers dans le dossier spécifié.  
  
7.  Démarrez l’invite de commandes de Visual Studio.  
  
8.  À l’invite de commandes Visual Studio, accédez à  **\<* lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT **.  
  
9. À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur ENTRÉE. Vérifiez qu’un message s’affiche dans la fenêtre d’invite de commandes qui indique qu’une paire de clés a été écrite dans key.snk.  
  
10. Dans l’Explorateur de solutions, cliquez sur le nom de votre projet, puis cliquez sur **propriétés**.  
  
11. Dans le volet gauche de la **Pages de propriétés** boîte de dialogue, cliquez sur **Assembly**.  
  
12. Dans le volet droit de la **Pages de propriétés** boîte de dialogue, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le points de suspension ().  
  
13. Dans le **fichier de clé d’Assembly** boîte de dialogue, accédez à  **\<* lecteur*\>: \Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)], cliquez sur **key.snk**, puis cliquez sur **ouvrir**.  
  
14. Dans le **Pages de propriétés** boîte de dialogue, cliquez sur **OK** pour enregistrer vos modifications.  
  
### <a name="to-add-a-swift-schema"></a>Pour ajouter un schéma SWIFT  
  
1.  Dans l’Explorateur de solutions de Visual Studio, ouvrez votre projet.  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
3.  Dans le **ajouter un élément existant** boîte de dialogue du :\\**programme Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Pack\SWIFT Messages\A4SWIFT-SRGMessage\<version\>\Base schémas**. Sélectionnez le **SWIFT Base Types.xsd** et **Types.xsd de données courantes SWIFT** schémas, puis cliquez sur **ajouter**.  
  
4.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **ajouter un élément existant**.  
  
5.  Dans le **ajouter un élément existant** boîte de dialogue le **Regarder dans** zone déroulante, accédez à  **\<lecteur\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category n\MTxxx**. Sélectionnez un schéma pour un type de message, par exemple **MT103.xsd**, puis cliquez sur **ajouter**.  
  
    > [!NOTE]
    >  A4SWIFT ajoute le schéma pour votre projet, comme indiqué dans l’Explorateur de solutions.  
  
6.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.  
  
7.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.