---
title: "Étape 1 : Attribution d’un nom fort à l’Assembly Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, assigning strong-names
- strong-named assemblies
ms.assetid: c8ec4593-5a4d-47ab-8799-7b2cd3d15ffc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7124561b9f842a7cc980c7a54230cd122ae32856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-assigning-a-strong-name-to-the-contoso-assembly"></a>Étape 1 : Attribution d’un nom fort à l’Assembly Contoso
Au cours de cette étape, vous allez créer un nom fort et l'affecter à votre assembly BizTalk. Un nom fort affecte une signature numérique et une paire de clés unique à un assembly pour garantir son unicité. Par ailleurs, il est possible de vérifier l'intégrité d'un nom pour s'assurer que le contenu de l'assembly n'a pas changé depuis sa dernière génération.  
  
### <a name="to-create-a-strong-name-assembly-key-file"></a>Pour créer un fichier de clé d'assembly de nom fort  
  
1.  Démarrez une **invite de commandes Visual Studio 2012**.  
  
2.  À l'invite de commandes, passez à l'emplacement de la solution Contoso.  
  
    > [!NOTE]
    >  Par défaut, l’emplacement de la solution Contoso est  *\<lecteur >*: \Documents and Settings\\*\<nom d’utilisateur >*documents\Visual Studio \<version > \Projects.  
  
3.  À l'invite de commandes, tapez **sn -k FabConPriceAvail.snk**, puis appuyez sur **Entrée**.  
  
4.  À l'invite de commandes, tapez **Exit**, puis appuyez sur **Entrée**.  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>Pour affecter un nom fort à votre assembly  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **ContosoPriceAndAvailability** , puis cliquez sur **Propriétés**.  
  
2.  Dans Pages de propriétés, cliquez sur **Signature** dans le volet gauche.  
  
3.  Dans le volet droit, sélectionnez **Signer l'assembly**.  
  
4.  Cliquez sur **Parcourir** dans le champ Choisir un fichier de clé de nom fort.  
  
5.  Recherchez le dossier de votre projet, sélectionnez le fichier **FabConPriceAvail.snk** créé précédemment, puis cliquez sur **Ouvrir**.  
  
6.  Cliquez sur **OK** pour enregistrer les modifications.  
  
7.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **ContosoPriceAndAvailability** , puis cliquez sur **Générer**. Une fois la génération réussie, cliquez à nouveau avec le bouton droit sur le projet, puis cliquez sur **Déployer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Création de Ports pour le prix 3A2 de Contoso et le scénario de requête/réponse de disponibilité](step-2-create-ports-for-contoso-3a2-price-and-availability-query.md)