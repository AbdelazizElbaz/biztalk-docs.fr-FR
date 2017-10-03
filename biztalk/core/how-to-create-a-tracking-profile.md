---
title: "Comment créer un modèle de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, creating
- creating, tracking profiles
ms.assetid: 676ae7e8-f3eb-45f1-ad2e-807b434c0bf9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f5d6cbb210cb292cd8ae7d0e2f4ff811984377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-tracking-profile"></a>Création d'un modèle de suivi
La création de modèles de suivi vous permet de lier des définitions d'activités BAM à des assemblys déployés et à des propriétés de messagerie BizTalk Server. Lorsque vous ouvrez l’éditeur de modèle de suivi, vous pouvez créer un modèle de suivi en cliquant sur le lien de l’activité importation ou de l’élément de menu d’importation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   une base de données de gestion BizTalk existante pour laquelle vous disposez d'autorisations d'accès ;  
  
-   un Éditeur de modèle de suivi configuré de manière à pouvoir utiliser la base de données de gestion BizTalk ;  
  
-   une définition d'activité BAM existante dans la base de données d'importation principale BAM.  
  
### <a name="to-create-a-tracking-profile"></a>Pour créer un modèle de suivi  
  
1.  Sur l’ou les ordinateurs que vous avez identifiés en tant que le système source, ouvrez le **éditeur**. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **BTSTrkEditor.exe**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Au milieu du volet gauche de l’éditeur, cliquez sur **cliquez ici pour importer une définition d’activité BAM** lien. Cette opération ouvre le **importer une définition d’activité BAM** boîte de dialogue.  
  
3.  À partir de la **le nom de définition d’activité BAM** zone de liste Sélectionnez l’activité sur laquelle baser le suivi. Si votre liste contient plusieurs activités déployées, vous pouvez taper une partie du nom de l’activité dans le **dans la chaîne** zone de texte et cliquez sur le **recherche** bouton. Cela permet de limiter la liste aux seules activités dont le nom contient une partie de la chaîne entrée.  
  
4.  Une fois que vous avez sélectionné l’activité, cliquez sur le **OK** bouton. Un nouveau modèle de suivi basé sur l'activité sélectionnée s'affiche tandis que le modèle apparaît dans le volet gauche de l'Éditeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles de suivi](../core/creating-tracking-profiles.md)