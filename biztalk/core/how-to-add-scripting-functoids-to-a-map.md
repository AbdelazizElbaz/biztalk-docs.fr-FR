---
title: Comment ajouter des fonctoids de script à un mappage | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.functiod.script
ms.assetid: eb96814a-b3fb-48f6-a947-ab595a270faa
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e66e6ed25fd44b1e89fe5500346a7ad01d5d7ff0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-scripting-functoids-to-a-map"></a>Ajout de fonctoids Script à un mappage
Le **script** fonctoid permet d’utiliser le script personnalisé ou un code en cours d’exécution pour exécuter des fonctions non disponibles. Par exemple, vous pouvez appeler un objet COM en cours d’exécution à l’aide de la **script** fonctoid et l’écriture de votre propre script personnalisé.  
  
 Pour obtenir des informations conceptuelles sur le **script** fonctoid, consultez [le fonctoid script](../core/scripting-functoid.md).  
  
### <a name="to-add-the-scripting-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Script à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **script** fonctoid ![](../core/media/bts-tls-scripting.gif "bts_tls_scripting") à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur emplacement relatif de gauche à droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Sélectionnez le **script** fonctoid que vous venez d’ajouter à la page de grille affichée.  
  
4.  Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) associés à la **Script** propriété.  
  
    > [!NOTE]
    >  Ou bien, cliquez sur le fonctoid, puis cliquez sur **configurer le Script du fonctoid** dans le menu contextuel. Le **configurer le fonctoid script** boîte de dialogue s’affiche avec le **Configuration du fonctoid Script** onglet sélectionné.  
  
5.  Dans le **configurer le fonctoid script** boîte de dialogue le **sélectionner le type de script** liste déroulante, sélectionnez le type de votre script.  
  
    > [!NOTE]
    >  Selon votre sélection, différents sous-ensembles des autres champs de la boîte de dialogue seront activés et désactivés.  
  
6.  Si vous avez sélectionné **Assembly externe** comme type de script, utilisez la **Script de l’assembly**, **Script classe**, et **méthode de Script** liste déroulante listes, dans cet ordre, pour sélectionner l’assembly, la classe et la méthode, respectivement, à associer à ce **script** fonctoid.  
  
    > [!WARNING]
    >  Le code contenu dans l’assembly externe doit être exempt de tout thread. Dans les situations de forte charge, il est possible d’exécuter plusieurs instances d’un mappage en même temps.  
  
    > [!NOTE]
    >  Après avoir sélectionné un assembly, le **Script classe** liste de déroulante sera remplie avec les classes de cet assembly. De même, après avoir sélectionné une classe, le **méthode de Script** liste de déroulante sera remplie avec les méthodes de cette classe.  
  
    > [!NOTE]
    >  Le **script Inline** zone de texte est désactivée lorsque vous sélectionnez **Assembly externe** comme type de script.  
  
     Si vous avez sélectionné un élément autre que **Assembly externe** comme type de script (une des options inline), utilisez la **script Inline** zone de texte pour entrer votre script dans la langue sélectionnée.  
  
    > [!NOTE]
    >  Les options de langage inline pour la **script** fonctoid incluent Visual C# .NET, JScript.NET, Visual Basic .NET, XSLT et le modèle d’appel XSLT.  
  
     La création de scripts à l'aide du langage C# n'autorise pas les instructions « using ». Si le script doit utiliser des classes .Net spéciales, les assemblys correspondants et leurs dépendances doivent être ajoutés aux « Références » du projet BizTalk ; en outre, le code de script doit utiliser des noms complets. Si vous écrivez un script pour effectuer une conversion en minuscules sensible à la culture, le fragment de code correspondant doit être écrit comme suit. Des restrictions similaires s'appliquent à tous les langages de création de scripts pris en charge.  
  
    ```  
    string x = y.ToLower(System.Globalization.CultureInfo.CurrentCulture);  
    ```  
  
     Pour utiliser les classes d'un assembly dans le script, assurez-vous d'ajouter l'assembly correspondant et ses dépendances aux « Références » du projet BizTalk contenant votre mappage.  
  
    > [!NOTE]
    >  Vous pouvez créer votre script personnalisé directement dans le **script Inline** zone de texte, ou vous pouvez créer votre script ailleurs et le coller dans le **script Inline** zone de texte.  
  
    > [!NOTE]
    >  Le **Script de l’assembly**, **Script classe**, et **méthode de Script** listes déroulantes sont désactivées lorsque vous sélectionnez une des options inline (quelque chose que **Assembly externe**) comme type de script.  
  
    > [!IMPORTANT]
    >  Si vous créez un script contenant plusieurs fonctions, la première fonction sera considérée comme fonction principale, tandis que les autres sont uniquement appelées dans l’exécution de la fonction principale.  
  
     Cliquez sur **OK**.  
  
7.  Si votre script ou la méthode associée d’un assembly externe requiert des paramètres d’entrée, créez le nombre et le type appropriés de liens d’entrée comme pour un fonctoid de base.  
  
8.  Dans la plupart des cas, votre **script** fonctoid produira une valeur de sortie utilisée pour remplir un champ du schéma de destination ou en tant qu’entrée à un autre fonctoid, à peu près la même façon que les fonctoids. procédez.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)