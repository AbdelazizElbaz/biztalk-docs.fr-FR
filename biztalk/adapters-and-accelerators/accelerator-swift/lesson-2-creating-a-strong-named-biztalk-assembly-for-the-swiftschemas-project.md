---
title: "Leçon 2 : Création d’un Assembly BizTalk avec nom fort pour le projet SWIFTSchemas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, creating strong-names
- strong-named assemblies
ms.assetid: 2aacbf38-8b1d-46ea-89ae-5207327bedc1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8ff979c7b6915f53ebc7144cf0774ab1ffb779a
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-2-creating-a-strong-named-biztalk-assembly-for-the-swiftschemas-project"></a>Leçon 2 : Création d’un Assembly BizTalk avec nom fort pour le projet SWIFTSchemas
Dans cette leçon, vous créez un nom fort sur lequel les assemblys BizTalk sont compilés et déployés. Un assembly avec nom fort présente plusieurs avantages de sécurité :  
  
-   Un nom fort garantit l’unicité de l’assembly en assignant une signature numérique et une paire de clés unique.  
  
-   Un nom fort protège le lignage de l’assembly en veillant à ce que personne d’autre ne peut générer une version ultérieure de l’assembly.  
  
-   Un nom fort fournit un contrôle d’intégrité fort pour garantir que le contenu de l’assembly n’a pas changé depuis la dernière génération.  
  
 Vous pouvez générer un fichier de clé à l’aide de l’outil strong name (sn.exe) fourni avec [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] ou [!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)].  
  
### <a name="to-create-a-strong-named-biztalk-assembly"></a>Pour créer un assembly avec nom fort de BizTalk  
  
1.  Démarrez l’invite de commandes de Visual Studio.  
  
2.  À l’invite de commandes Visual Studio, accédez à la \< *lecteur*\>: \labs dossier.  
  
3.  À l’invite de commandes, tapez **sn – k swift.snk**, puis appuyez sur ENTRÉE. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez Visual Studio pour résoudre les problèmes de votre assembly.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le **SWIFTSchemas** de projet, puis cliquez sur **propriétés**.  
  
5.  Dans la boîte de dialogue Pages de propriétés SWIFTSchemas, vérifiez que **propriétés communes** est développé, puis sélectionnez **Assembly**.  
  
6.  Défilement vers le bas les propriétés de l’assembly dans le volet droit et dans le **nom fort** , cliquez sur la zone à droite de **fichier de clé d’Assembly**. Cliquez sur le bouton de sélection.  
  
7.  Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à  **\< *lecteur*:\>\labs**.  
  
8.  Sélectionnez le **swift.snk** de fichiers en tant que le fichier de clé, puis cliquez sur **ouvrir**.  
  
9. Dans la boîte de dialogue Pages de propriétés SWIFTSchemas, cliquez sur **OK**.  
  
10. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.  
  
 Passez à [leçon 3 : ajout de schémas SWIFT à un projet](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md).