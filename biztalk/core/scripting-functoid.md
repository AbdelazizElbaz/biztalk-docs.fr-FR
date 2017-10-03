---
title: Fonctoid script | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, about Scripting functoids
- Scripting functoids
- Scripting functoids, configuring
ms.assetid: ea8353da-049b-4e0c-a700-f51708db22a3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 822bdbc4482a7e16a7458c7c44d128967203f283
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-functoid"></a>Fonctoid script
Le **script** fonctoid permet d’utiliser le script personnalisé ou un code en cours d’exécution pour exécuter des fonctions non disponibles. Par exemple, vous pouvez appeler un assembly .NET au moment de l’exécution à l’aide de la **script** fonctoid et l’écriture de vos propres fonctions personnalisées.  
  
 Le **script** fonctoid prend en charge les langues suivantes :  
  
-   C# .NET  
  
-   JScript .NET  
  
-   Visual Basic .NET  
  
-   Langage de transformation de feuille de style extensible (XSLT)  
  
-   Modèles d'appel XSLT  
  
 Une autre différence importante entre actuel **script** fonctoid et les versions antérieures est que le script n’est plus doivent être créé et stocké dans le fonctoid lui-même. Au lieu de cela, vous pouvez créer le script dans un assembly .NET séparé et référencer l’assembly via la **Script** propriété. Le fait que le script se trouve dans un assembly séparé vous permet d’utiliser le même script dans plusieurs mappages. En outre, vous pourrez peut-être acheter **script** des ensembles de fonctoids à partir des fournisseurs tiers.  
  
 Vous pouvez utiliser **script** fonctoids créés dans les versions précédentes du Mappeur BizTalk avec la version actuelle du Mappeur BizTalk. Vous devez, néanmoins, commencer par migrer les fonctoids. Pour plus d’informations sur la migration **script** fonctoids, consultez [migration des fonctoids](../core/migrating-functoids.md).  
  
 Lorsque vous ajoutez un **script** fonctoid à un mappage, vous devez configurer le script du fonctoid utilise. Si vous sélectionnez un **script** fonctoid, le **Script** propriété est activée dans le **propriétés** fenêtre. Si vous cliquez sur le bouton de sélection (**...** ) bouton pour cette propriété, le **configurer le fonctoid script** boîte de dialogue s’ouvre. Vous pouvez également double-cliquer sur le **script** fonctoid.  
  
 Le tableau suivant affiche les champs de cette boîte de dialogue.  
  
|Configurez le champ de la boîte de dialogue Fonctoid Script| Description|  
|---------------------------------------------------|-----------------|  
|**Sélectionnez le type de script**|Ce champ permet de sélectionner le type de script que vous souhaitez utiliser dans ce **script** fonctoid.<br /><br /> Valeurs :<br /><br /> -   **Assembly externe**. Utilisez cette valeur si vous souhaitez associer le **script** fonctoid avec un assembly dans le global assembly cache (GAC). **Avertissement :** le code dans l’assembly externe doit être thread-safe. Dans les situations de forte charge, il est possible d’exécuter plusieurs instances d’un mappage en même temps.<br />-   **Inline c#**.  Utilisez cette valeur si vous souhaitez associer le **script** fonctoid avec le code c# dans le **script Inline** mémoire tampon.<br />-   **Inline JScript .NET**. Utilisez cette valeur si vous souhaitez associer le **script** fonctoid script JScript .NET dans le **script Inline** mémoire tampon.<br />-   **Inline Visual Basic .NET**. Utilisez cette valeur si vous souhaitez associer le **script** fonctoid avec code Visual Basic .NET dans le **script Inline** mémoire tampon.<br />-   **Inline XSLT**. Utilisez cette valeur si vous souhaitez associer le **script** fonctoid à XSLT dans le **script Inline** mémoire tampon.<br />-   **Modèle d’appel Inline XSLT**. Utilisez cette valeur si vous souhaitez associer le **script** fonctoid avec les modèles d’appel XSLT dans le **script Inline** mémoire tampon.|  
|**Assembly du script**|Sélectionnez l’assembly à associer à la **script** fonctoid. Seuls les assemblys référencés dans la fenêtre Projet figurent dans cette liste. Notez également que vous devez enregistrer les assemblys dans le GAC.<br /><br /> Ce champ est disponible uniquement lorsque **sélectionner le type de script** a la valeur **Assembly externe**.|  
|**Classe du script**|Sélectionnez la classe dans l’assembly choisi que vous souhaitez que ce **script** fonctoid à utiliser.<br /><br /> Ce champ est disponible uniquement lorsque **sélectionner le type de script** a la valeur **Assembly externe**.|  
|**Méthode de script**|Sélectionnez la méthode dans la classe choisie que vous souhaitez que ce **script** fonctoid à utiliser. **Remarque :** Assurez-vous que le nombre de paramètres d’entrée attendus par la méthode correspond au nombre de paramètres d’entrée spécifiés dans le **configurer le fonctoid script** boîte de dialogue.|  
|**Script inline**|Inscrivez ou copiez le script inline à utiliser dans cette zone de texte. Langues valides et scripts incluent : modèles d’appel c#, JScript .NET, Visual Basic .NET, XSLT et XSLT.<br /><br /> Ce champ est disponible uniquement lorsque **sélectionner le type de script** est défini sur l’un de le **Inline** paramètres. **Attention :** Évitez d’utiliser la même signature de méthode plusieurs fois. Lorsque plusieurs fonctoids Script ont la même signature de méthode, BizTalk sélectionne la première implémentation et ignore les autres.|  
  
 L’illustration suivante montre comment la **script** fonctoid apparaît dans un mappage à l’aide du script c# .net pour reformater un numéro de téléphone.  
  
 ![Mappage à l’aide de C &#35; Pour mettre en forme un numéro de téléphone. ] (../core/media/scriptingfunctoid.gif "scriptingfunctoid")  
Mappage du fonctoid Script  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Écriture de scripts à l’aide des assemblys externes](../core/scripting-using-external-assemblies.md)  
  
-   [Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)  
  
-   [Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)