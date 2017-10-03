---
title: "Paramètres de sortie de la spécification XSLT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c541432-fd4e-41cc-8bcc-f570ce5df439
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1aa3eea4c3f2f4696d3dc1fdf8109aeddec3ff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="set-map-compilation-and-output-settings"></a>Définissez compilation de mappage et de sortie
Définissez les propriétés de mappage dans le Mappeur BizTalk. 

L’utilisation de ces propriétés de mappage, vous pouvez définir comment les mappages sont compilés, inclure ou exclure une déclaration XML et l’encodage de jeu. 

Cette rubrique montre comment définir ces propriétés sur la carte.

## <a name="set-the-map-level-compilation"></a>Définir la compilation au niveau de la carte

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous choisissez la `XslTransform` ou `XslCompiledTransform` classe à compiler vos mappages. 

1. Ouvrez votre mappage dans l’affichage de grille.
2. Avec le bouton droit n’importe où dans la grille du mappeur, puis sélectionnez **propriétés**.  
3. Définir le **utiliser XSLT** propriété : 

    | Option |  Description |
    | --- | --- |
    | Indéfini | L’indicateur de Registre pour le paramètre XslTransform est utilisée : <ul><li>instances d’hôte 64 bits :`HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</li><li>instances d’hôte 32 bits et fonctionnalité de mappage de Test de Visual Studio :`HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</li></ul> | 
    | True | A la valeur de la propriété de niveau de compilation de mappage `XslTransform` (comportement hérité) | 
    | False | A la valeur de la propriété de niveau de compilation de mappage`XslCompiledTransform` | 

> [!NOTE] 
> À partir de BizTalk Server 2013, le comportement de compilation du Mappeur a été modifié à partir de `XslTransform` à `XslCompiledTransform`. Le [le mappeur de mises à jour de signification pour vous](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) billet de blog fournit une explication excellente du comportement et son impact potentiel. 
> 
> En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez choisir la classe à la compilation de vos mappages. 
  
## <a name="include-or-exclude-an-xml-declaration"></a>Inclure ou exclure une déclaration XML  
Vous pouvez choisir si une déclaration XML est sortie ou non. 

1. Ouvrez votre mappage dans l’affichage de grille.
2. Avec le bouton droit n’importe où dans la grille du mappeur, puis sélectionnez **propriétés**.  
3. Dans la liste déroulante pour le **omettre la déclaration XML** propriété, sélectionnez **Oui** pour omettre une déclaration XML. Sélectionnez **non** pour ne pas omettre une déclaration XML.  

Une déclaration XML apparaît (si vous avez sélectionné **non**) semblable au suivant.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## <a name="set-encoding-for-output-instance-data"></a>Définir le codage de données d’instance de sortie  
Le codage fournit au moteur d’exécution les informations nécessaires pour déterminer le jeu de caractères à utiliser lors de la création de la sortie d'un mappage.  
   
1. Ouvrez votre mappage dans l’affichage de grille.
2. Avec le bouton droit n’importe où dans la grille du mappeur, puis sélectionnez **propriétés**.    
3.  Dans la liste déroulante pour le **codage XSLT** propriété, sélectionnez le jeu de caractères vous souhaitez utiliser pour les données d’instance de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [La compilation et test des mappages](../core/compiling-and-testing-maps.md)   
 [À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md)   
 [Types de codages de XSLT valides du Mappeur BizTalk](../core/valid-biztalk-mapper-xslt-encoding-types.md)