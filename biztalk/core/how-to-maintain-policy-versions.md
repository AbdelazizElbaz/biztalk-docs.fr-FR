---
title: "Comment mettre à jour les Versions de stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, publishing
- publishing policies
- updating, policies
- versioning, policies
- policies, versioning
- policies, updating
ms.assetid: 6e35b2bd-1ecd-45ea-aff3-4ad2437568a4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09c73b3575ec484ab611fccac920cef6d96d3800
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-maintain-policy-versions"></a>Comment mettre à jour les Versions de stratégie
Une fois que vous avez ajouté des règles à une version de votre stratégie, vous pouvez soit enregistrer cette version dans le magasin de règles pour un développement ultérieur, soit la publier afin de créer un ensemble de règles bien défini et immuable pouvant être déployé afin d'être utilisé dans une application basée sur des règles.  
  
 Cette rubrique contient les procédures des tâches suivantes :  
  
-   Pour créer une version vide de stratégie  
  
-   Pour enregistrer une version de stratégie  
  
-   Pour publier une version de stratégie  
  
-   Pour créer une version mise à jour de stratégie  
  
-   Pour mettre à jour une stratégie afin d'utiliser un assembly mis à jour  
  
### <a name="to-create-an-empty-new-version-of-a-policy"></a>Pour créer une version vide de stratégie  
  
-   Cliquez sur le dossier de stratégie, puis cliquez sur **ajouter une nouvelle Version**.  
  
### <a name="to-save-a-policy-version"></a>Pour enregistrer une version de stratégie  
  
-   Avec le bouton droit de la version de stratégie, puis cliquez sur **enregistrer**.  
  
### <a name="to-publish-a-policy-version"></a>Pour publier une version de stratégie  
  
-   Avec le bouton droit de la version de stratégie, puis cliquez sur **publier**.  
  
### <a name="to-create-an-updated-version-of-a-policy"></a>Pour créer une version mise à jour de stratégie  
  
1.  Cliquez sur une version de stratégie existante, puis cliquez sur **copie**.  
  
2.  Cliquez sur le dossier de stratégie, puis cliquez sur **coller**.  
  
     Une nouvelle version est alors créée. Ses éléments sont les mêmes que ceux de la version copiée.  
  
    > [!NOTE]
    >  Si votre stratégie utilise un assembly .NET et que cet assembly est mis à jour, vous devrez la lier à la dernière version de l'assembly.  
  
### <a name="to-update-a-policy-to-use-an-updated-assembly"></a>Pour mettre à jour une stratégie afin d'utiliser un assembly mis à jour  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, pointez sur **.NET Framework Configuration**, puis cliquez sur **assemblys configurés** .  
  
2.  Accédez aux propriétés de l’assembly cible et cliquez sur le **stratégie de liaison** onglet.  
  
3.  Dans le Global Assembly Cache, remplacez le numéro de version par celui de la nouvelle version.  
  
    > [!NOTE]
    >  Tous les assemblys utilisés par les stratégies doivent être ajoutés au Global Assembly Cache.