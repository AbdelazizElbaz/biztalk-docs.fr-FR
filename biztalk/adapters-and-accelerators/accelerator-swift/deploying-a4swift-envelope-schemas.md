---
title: "Déploiement des schémas d’enveloppe A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, envelope schemas
- A4SWIFT, deploying envelope schemas
- envelope schemas
- schemas, envelope schemas
ms.assetid: 6440608c-d30d-4d82-827a-8a4b2738db85
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8811f1dd056ca5a4ea4582d593af30e2ffc879f
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="deploying-a4swift-envelope-schemas"></a>Déploiement des schémas d’enveloppe A4SWIFT
Chaque fois que vous configurez Message Repair et New Submission, vous devez inclure les schémas d’enveloppe dans les projets de schéma. Un schéma d’enveloppe, tels que EnvelopeMT103.xsd, est requis pour écrire sur site MRSR.  
  
 **Résumé**  
  
 Ajoutez les schémas d’enveloppe à votre projet, comme suit :  
  
-   Dans Visual Studio, pour le projet qui contient vos schémas de message, ajoutez un schéma d’enveloppe pour chaque schéma de message.  
  
-   Ajoutez une référence à RuntimeSchemas.dll à un projet qui contient un ou plusieurs schémas d’enveloppe.  
  
    > [!NOTE]
    >  Ajout d’une référence à RuntimeSchemas.dll est requis pour un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] uniquement lorsque vous avez ajouté un schéma d’enveloppe pour Message Repair et New Submission au projet du projet.  
  
-   Ajoutez le schéma d’enveloppe de Message non analysé (EnvelopeUnparsedMessage.xsd) au projet.  
  
### <a name="to-add-a-swift-envelope-schema"></a>Pour ajouter un schéma d’enveloppe SWIFT  
  
1.  Dans l’Explorateur de solutions de Visual Studio, ouvrez votre projet de schémas.  
  
2.  Avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.  
  
3.  Dans la boîte de dialogue Ajouter une référence, cliquez sur le **Parcourir** balise.  
  
4.  Dans la boîte de dialogue Sélectionner le composant, ouvrez le **Regarder dans** liste déroulante. Déplacer vers ***\<lecteur\>*:\Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\Assemblies**. Sélectionnez **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** dans la liste des assemblys, puis cliquez sur **ajouter**.  
  
5.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur **OK**.  
  
6.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **ajouter un élément existant**.  
  
7.  Dans la zone Ajouter un élément existant boîte de dialogue, dans le **Regarder dans** zone déroulante, accédez à  **\<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\>Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Categoryn\MTxxx**. Sélectionnez le schéma d’enveloppe, par exemple, **EnvelopeMT103.xsd**, puis cliquez sur **ajouter**.  
  
     Dans la zone Ajouter un élément existant boîte de dialogue, dans le **Regarder dans** zone déroulante, accédez à. Sélectionnez le schéma d’enveloppe, par exemple, EnvelopeMT103.xsd et puis cliquez sur Ajouter.  
  
    > [!NOTE]
    >  A4SWIFT ajoute le schéma d’enveloppe pour votre projet, comme indiqué dans l’Explorateur de solutions.  
  
8.  Dans l’Explorateur de solutions, cliquez sur votre projet, pointez sur **ajouter**, puis cliquez sur **ajouter un élément existant**.  
  
9. Si vous utilisez la fonctionnalité de Message Repair et New Submission, dans la boîte de dialogue Ajouter un élément existant dans le **Regarder dans** zone déroulante, accédez à  **\< *lecteur*\>: \ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Unparsed Message**. Sélectionnez **EnvelopeUnparsedMessage.xsd**, puis cliquez sur **ajouter**.  
  
10. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.  
  
11. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.