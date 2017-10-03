---
title: Comment utiliser le mot de passe des filtres | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb429f8b-c301-45a3-8a4f-bbe6f2c566a3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ad35e2c3bec5b2ece69911b8de8c7fd13c9b790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-password-filters"></a>Utilisation des filtres de mot de passe
La fonctionnalité de synchronisation de mot de passe de l'authentification unique de l'entreprise synchronise les mots de passe entre Microsoft Windows Active Directory et les systèmes non Windows. De nombreux systèmes externes utilisent toutefois des stratégies de mot de passe différentes de celles applicables dans Active Directory. Par exemple, un système IBM peut exiger un mot de passe en majuscules et limité à 8 caractères. L'authentification unique de l'entreprise est donc contrainte d'utiliser le « plus petit dénominateur commun » entre les deux systèmes, ce qui limite la sécurité des mots de passe.  
  
 La fonctionnalité de filtre de mot de passe de l'authentification unique de l'entreprise permet de résoudre cette limitation. Un filtre de mot de passe est un simple adaptateur de synchronisation de mot de passe avec des propriétés supplémentaires définies. Celles-ci (longueur maximale ou minimale, restrictions de casse et de caractères, etc.) permettent de filtrer les mots de passe pour garantir leur conformité aux critères du système externe.  
  
 Lorsque vous créez un filtre de mot de passe, le groupe Administrateurs spécifié est automatiquement utilisé comme compte d'administrateur de l'authentification unique. Si vous modifiez le groupe Administrateurs de l'authentification unique, vous devez vous assurer que le filtre de mot de passe est également mis à jour avec le nouveau compte d'administrateur de l'authentification unique.  
  
> [!NOTE]
>  Comme pour les autres éléments du système d'authentification unique de l'entreprise, les filtres de mot de passe contiennent des informations sensibles et doivent être exposés le moins possible.  
  
### <a name="to-create-a-password-filter"></a>Pour créer un filtre de mot de passe  
  
1.  Dans le **Console de gestion de l’authentification unique**, avec le bouton droit le **gestion de mot de passe** nœud, puis cliquez sur **créer un filtre**.  
  
     Le **Assistant Filtre de mot de passe** s’affiche.  
  
2.  Suivez les instructions de l'Assistant pour créer le filtre de mot de passe.  
  
### <a name="to-assign-an-affiliate-application-to-a-password-filter"></a>Pour assigner une application associée à un filtre de mot de passe  
  
1.  Cliquez sur le filtre approprié, puis cliquez sur **affecter**...  
  
2.  Sélectionnez la **Application associée**.