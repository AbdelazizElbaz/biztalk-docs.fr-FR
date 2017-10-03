---
title: "Balises d’ornement adaptateur Framework Configuration schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d5d7f6b-2273-45a6-ba9d-43201760cf22
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b834482b70e75d12bb6786dac2a5d9eb6f9fef40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-framework-configuration-schema-decoration-tags"></a>Balises d’ornement adaptateur Framework Configuration schéma
Vous pouvez utiliser les balises décrites dans cette rubrique dans les fichiers de schéma de configuration afin d'afficher et d'organiser les données sur les pages de propriétés de l'adaptateur.  
  
 La capture d'écran suivante montre comment la page de propriétés de l'emplacement de réception FTP implémente certaines de ces balises.  
  
 ![](../core/media/ebiz-prog-custad-tags.gif "ebiz_prog_custad_tags")  
Le \<description >, \<displayname >, et \<catégorie > balises dans la page de propriétés de l’adaptateur FTP  
  
## <a name="designer"></a>\<Concepteur >  
 Les ornements de l’infrastructure d’adaptateurs BizTalk s’affichent entre un \<baf : Designer > balise et \</baf:designer > balise de fin. Le \<baf : Designer > balise permet de faire la distinction entre l’infrastructure d’adaptateurs \<appinfo > et autres adaptateur fournie \<appinfo > plus d’informations.  
  
## <a name="category"></a>\<catégorie >  
 Le \<catégorie > décoration contient la chaîne utilisée pour séparer les entrées dans la grille des propriétés en groupes. Il affiche toutes les entrées de la même chaîne de catégorie sous forme d'entrées subordonnées.  
  
 Vous pouvez localiser \<catégorie > entrées.  
  
## <a name="description"></a>\<Description >  
 Le \<description > décoration contient la chaîne utilisée pour fournir le texte descriptif pour les entrées au bas de la grille des propriétés.  
  
 Vous pouvez localiser \<description > entrées.  
  
## <a name="displayname"></a>\<DisplayName >  
 Le \<displayname > décoration contient la chaîne utilisée pour afficher le nom d’une entrée. Cela vous permet d’utiliser des espaces, des expressions et ainsi de suite, lorsqu’il ne sont pas autorisé pour un \<élément > ou \<attribut > nom.  
  
 Vous pouvez localiser \<displayname > entrées.  
  
## <a name="readonly"></a>\<ReadOnly >  
 Le \<readonly fixée = » « > décoration contrôle si un champ peut être modifié. Une valeur d'attribut « fixed » correspondant à `true` (valeur par défaut) signifie que le champ est en lecture seule.  
  
 Lors de l’implémentation d’un éditeur externe, implémentez un externe **TypeConverter** classe et substituer les **GetStandardValuesExclusive** méthode à la place. Si la valeur `true` est renvoyée, le champ est en lecture seule, mais l'accès à l'éditeur personnalisé est possible.  
  
## <a name="browsable"></a>\<Browsable >  
 Le \<browsable show = " » > décoration contrôle si un champ s’affiche dans la grille des propriétés. Une valeur d'attribut « show » correspondant à `True` (valeur par défaut) signifie que le champ apparaît dans la grille.  
  
## <a name="converter"></a>\<convertisseur >  
 Le \<assembly de convertisseur = » « > décoration spécifie souhaité **TypeConverter** nom de classe pour le \<élément > ou \<attribut >. La valeur d’attribut « assembly » facultative indique le chemin d’accès à l’assembly contenant le texte souhaité **TypeConverter**. Si la valeur « assembly » n'est pas spécifiée, le nom de la classe doit inclure les valeurs de version, culture, clé et nom d'assembly du GAC.  
  
## <a name="editor"></a>\<Éditeur >  
 Le \<assembly de l’éditeur = » « > décoration spécifie souhaité **UITypeEditor** nom de classe pour le \<élément > ou \<attribut >. La valeur d’attribut « assembly » facultative indique le chemin d’accès à l’assembly contenant le texte souhaité **UITypeEditor**. Si la valeur « assembly » n'est pas spécifiée, le nom de la classe doit inclure les valeurs de version, culture, clé et nom d'assembly du GAC.  
  
## <a name="null-values-for-optional-enumerations"></a>Valeurs Null pour les énumérations facultatives  
 Lorsque vous utilisez une énumération facultative, une des valeurs doit être \<none > pour indiquer une valeur null. Il ne s'agit pas d'une balise intégrée, mais d'une valeur obtenue en indiquant une valeur d'énumération considérée comme étant « none » si l'énumération est dérivée de xsd:string. Cela n'est pas possible pour les énumérations dérivées de xsd:int, car le nombre entier doit comporter une valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md)