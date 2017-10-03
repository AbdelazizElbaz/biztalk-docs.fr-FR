---
title: "Création et déploiement des Pipelines d’A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- deploying, pipelines
- pipelines, deploying
- pipelines, creating
ms.assetid: 2a614510-7e15-4e88-9012-fc019d3aefee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bec21ebd5a3b32986969676a78109cad55d870cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-deploying-a4swift-pipelines"></a>Création et déploiement des Pipelines d’A4SWIFT
Procédez comme suit pour créer et déployer des pipelines SWIFT pour message repair et nouvelle soumission, comme indiqué dans l’illustration suivante.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-pipeline-configuration.gif "A4SWIFT_Pipeline_Configuration")  
  
 **Résumé**  
  
 Déployer les schémas suivants :  
  
-   Pipeline avec le désassembleur SWIFT de réception personnalisé. Définir les propriétés BRE Validation et de Validation XML sur True et la propriété de schéma d’en-tête SWIFT (None).  
  
-   Pipeline avec l’assembleur SWIFT d’envoi personnalisé  
  
### <a name="to-create-a-pipeline-project"></a>Pour créer un projet de pipeline  
  
1.  Dans Visual Studio, cliquez sur **fichier**, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **types de projet** volet, sélectionnez le **projets BizTalk** dossier.  
  
3.  Dans le **modèles** volet, sélectionnez **projet BizTalk Server vide**.  
  
4.  Dans le **nom** , tapez le nom souhaité pour le nom du projet.  
  
5.  Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**. Dans le **emplacement** , entrez l’emplacement du projet de schéma que vous avez créé dans la zone [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).  
  
6.  Cliquez sur **OK** pour ouvrir le nouveau projet.  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]Ajoute un nouveau projet à l’Explorateur de solutions et crée le dossier du projet et les fichiers dans le dossier spécifié.  
  
7.  Créez et affectez un fichier de clé fort au projet. Pour plus d’informations, consultez « pour créer un projet SWIFT fort » dans [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).  
  
### <a name="to-add-a-custom-receive-pipeline"></a>Pour ajouter un pipeline de réception personnalisé  
  
1.  Dans l’Explorateur de solutions, votre projet de pipeline avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, cliquez sur **fichiers de Pipeline** dans le volet des catégories, puis sélectionnez **Pipeline de réception** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez un nom pour le pipeline.  
  
4.  Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.  
  
5.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** , puis **boîte à outils**.  
  
6.  À partir de la **boîte à outils des composants de Pipeline BizTalk**, faites glisser le **SWIFT désassembleur** à la **Déposer ici** zone ci-dessous le **désassembler** étape mettre en forme **le Concepteur de Pipeline BizTalk**. Laissez le **SWIFT désassembleur** sélectionné dans le **le Concepteur de Pipeline BizTalk**.  
  
7.  Dans **propriétés**, vérifiez que le **BRE Validation** et **Validation XML** propriétés sont définies sur **True**.  
  
    > [!NOTE]
    >  La propriété de schéma d’en-tête SWIFT doit être définie **(aucun)**.  
  
8.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **fichier**, puis **Enregistrer tout**.  
  
### <a name="to-add-a-custom-send-pipeline"></a>Pour ajouter un pipeline d’envoi personnalisé  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **SWIFTPipelines** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, vérifiez que **fichiers de Pipeline** est sélectionné dans le volet des catégories, puis sélectionnez **Pipeline d’envoi** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez un nom pour le pipeline.  
  
4.  Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.  
  
    > [!NOTE]
    >  Un pipeline vide apparaît dans le Concepteur de Pipeline BizTalk. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Ajoute le nouveau pipeline à l’Explorateur de solutions sous le projet SWIFTPipelines.  
  
5.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** , puis **boîte à outils**.  
  
6.  Dans le **boîte à outils des composants de Pipeline BizTalk**, faites glisser **SWIFT assembleur** à la **Déposer ici** zone ci-dessous le **assemblage** forme dans l’étape **Le Concepteur de Pipeline BizTalk**.  
  
7.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **fichier**, puis **Enregistrer tout**.  
  
8.  Cliquez avec le bouton droit sur le projet de pipelines, puis cliquez sur **Build**.  
  
    > [!NOTE]
    >  Pendant le processus de compilation, vous ne devez pas voir les erreurs. Si vous le faites, vérifiez la source de l’erreur, corrigez-la et puis générez à nouveau le projet. Toutefois, vous voyez les avertissements. Vous pouvez corriger la condition des avertissements. Pour plus d’informations, consultez « Création d’un projet de pipeline peut générer des avertissements » dans [divers problèmes connus](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).  
  
9. Cliquez avec le bouton droit sur le projet de pipelines, puis cliquez sur **déployer**.