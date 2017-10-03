---
title: "Comment utiliser l’Assistant mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35b96cea-ead7-43de-8411-62d2c7d6620e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6b016eb0599924d4927868b6a19d3b57389e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-mapping-wizard"></a>Utilisation de l'Assistant Mappage
Cette version de l'authentification unique de l'entreprise inclut l'Assistant Mappage, lequel vous permet de créer facilement des mappages pour les applications associées.  
  
> [!NOTE]
>  L'Assistant Mappage n'est utilisable que si l'ID utilisateur externe UserID a pour base le compte de domaine Windows.  
  
### <a name="to-start-the-mapping-wizard"></a>Pour démarrer l'Assistant Mappage  
  
1.  Ouvrez l'authentification unique de l'entreprise.  
  
2.  Dans le volet d’étendue, cliquez sur **Applications associées**.  
  
3.  Cliquez avec le bouton droit sur l'application associée appropriée.  
  
4.  Cliquez sur **créer des mappages**. L'Assistant Mappage s'affiche.  
  
5.  **Bienvenue dans l’Assistant mappage**  
  
    -   Vérifiez qu’il s’agit de l’application associée correcte, puis cliquez sur **suivant**.  
  
6.  **Option du fichier de mappage** page  
  
    -   L'authentification unique de l'entreprise (ENTSSO) gère les mappages au moyen d'un fichier XML. Vous pouvez décider de créer un fichier ou d'en utiliser un existant.  
  
7.  **Emplacement des fichiers** page  
  
    -   Sélectionnez les fichiers à utiliser.  
  
    -   Vous devez cliquer sur **Validate** pour valider les fichiers avant de continuer. L’état de validation s’affiche dans le **état** fenêtre.  
  
8.  **Comptes** page  
  
    -   Choisissez un ou plusieurs comptes pour générer les fichiers de mappage, puis cliquez sur **Validate**.  
  
9. **Nom d’utilisateur externe** page  
  
    -   Définissez la méthode de création du nom d'utilisateur externe à partir du compte d'utilisateur Windows. Lorsque vous apportez des sélections dans les zones, vous pouvez voir comment les noms apparaissent dans le **exemple** boîte.  
  
10. **Générer** page  
  
    -   Cliquez sur **Démarrer** pour générer le fichier de mappage. (Dans la page suivante, vous aurez l'occasion d'afficher et de modifier le fichier selon le besoin avant que les mappages ne soient créés.) Les résultats sont affichés dans les trois fenêtres ci-dessous.  
  
    -   Le **nombre** de mappages dans les comptes sélectionnés est une approximation car les comptes peuvent être imbriqués dans d’autres comptes.  
  
    -   Cliquez sur **afficher le fichier journal** pour examiner les erreurs ou avertissements qui se sont produites.  
  
11. **Options** page  
  
    -   Le fichier a été créé. Cliquez sur **afficher/modifier le fichier de mappage** si vous le souhaitez.  
  
    -   Cliquez sur **activer les mappages** si vous souhaitez que les mappages d’être activé automatiquement. (Si vous ne cliquez pas sur cette option, vous devrez les activer manuellement.)  
  
    -   Cliquez sur **définir le mot de passe** pour définir automatiquement le mot de passe pour ces mappages.  
  
12. **Créer** page  
  
    -   Avant de créer les mappages, cliquez sur **afficher le fichier de mappage** si vous le souhaitez.  
  
    -   Lorsque vous êtes prêt, cliquez sur **Démarrer** pour effectuer l’opération de mappage. L'état est affiché dans les trois zones ci-dessous.  
  
    -   Cliquez sur **afficher le fichier journal** pour examiner les erreurs ou avertissements qui se sont produites.  
  
13. **Fin de l’écran de l’Assistant mappage**  
  
14. Sélectionnez les options souhaitées, puis cliquez sur **Terminer**.