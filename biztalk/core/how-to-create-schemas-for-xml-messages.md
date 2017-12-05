---
title: "Comment créer des schémas pour les Messages XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0270293-fe23-42bd-b090-e877d5e9ce0b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6396d4607e93298961e6691ded2ca8d4566d819c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-schemas-for-xml-messages"></a>Création de schémas pour les messages XML
Il existe plusieurs manières de créer des schémas de message BizTalk. Cette rubrique contient des instructions détaillées concernant certaines d'entre elles.  
  
### <a name="to-create-a-new-schema"></a>Pour créer un nouveau schéma  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le projet BizTalk auquel vous souhaitez ajouter un schéma.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le  **ajouter un nouvel élément - \<* BizTalk ProjectName*\>** boîte de dialogue le **modèles** , cliquez sur **schéma**.  
  
4.  Dans le **nom** zone, tapez un nom pour le schéma, puis cliquez sur **ajouter**.  
  
5.  Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
6.  Dans l’arborescence du schéma, sélectionnez le **schéma** nœud, puis, dans la fenêtre Propriétés, sélectionnez le **cible Namespace** propriété et tapez un nom pour l’espace de noms cible. Il est important que vous définissez cette propriété dans cette phase initiale de création de schéma ; Évitez d’utiliser la valeur par défaut **cible Namespace** valeur de propriété.  
  
    > [!NOTE]
    >  Certains choix de noms effectués pour des fichiers de membre de projet tels que les fichiers de schéma peuvent provoquer des erreurs de compilation ultérieures en raison de conflits avec des mots réservés C# et des noms de type et d'espace de noms .NET Framework (« Système » par exemple). schema.xsd, XmlContent et RootNodes sont des exemples de schémas. C’est parce que le **nom de Type** propriété valeur par défaut est la partie de base (sans extension) de la **nom de fichier** propriété. Vous pouvez contourner ce type d’erreur de compilation en donnant explicitement la valeur de la **nom de Type** propriété à un élément qui n’est pas en conflit.  
  
    > [!NOTE]
    >  Vous devrez peut-être ajouter, supprimer et modifier les enregistrements et les champs de votre schéma ainsi que les propriétés qui leur sont associées. Pour plus d’informations, consultez [la gestion des nœuds dans un schéma](../core/managing-the-nodes-within-a-schema.md).  
  
### <a name="to-generate-a-schema-from-a-non-xsd-source"></a>Pour générer un schéma à partir d'une source non XSD  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit à un projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le  **ajouter les éléments générés - \<* BizTalk ProjectName*\>** boîte de dialogue le **modèles** , cliquez sur  **Générer des schémas**, puis cliquez sur **ajouter**.  
  
3.  Dans le **générer les schémas** boîte de dialogue le **type de Document** la liste déroulante, sélectionnez **schéma XDR**, **DTD schéma**, ou **XML bien formé**.  
  
     Si vous consultez une **DTD (non chargé)** ou **XML bien formé (non chargé)** dans la liste déroulante, sélectionnez le type de document approprié malgré tout, et vous serez guidé dans le processus d’installation de le DLL manquante. Répétez ensuite ces étapes.  
  
4.  Dans le **générer les schémas** boîte de dialogue, cliquez sur **Parcourir**, recherchez le fichier que vous souhaitez importer, puis cliquez sur **ouvrir**. Le fichier localisé doit correspondre au type de document que vous avez sélectionné à l'étape précédente.  
  
     Un nouveau schéma est généré à partir du fichier spécifié. Il porte le même nom que ce fichier ainsi que l'extension .xsd et est ouvert dans l'Éditeur BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)