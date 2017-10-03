---
title: Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, JScript
- Scripting functoids, warnings
- Scripting functoids, Visual Basic .NET
- Scripting functoids, inline C#
- Scripting functoids, .NET
ms.assetid: dda60024-58bd-483f-a750-31b21059eded
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68fe19b4616e23066603995b6403654fa3960789
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-inline-c-jscript-net-and-visual-basic-net"></a>Scripts utilisant Inline C#, Jscript .NET et Visual Basic .NET
Les scripts Inline peuvent s’avérer pratiques pour le code personnalisé que vous risquez de ne pas réutiliser dans votre application.  
  
 BizTalk enregistre les scripts Inline dans la feuille de style XSLT (Extensible Stylesheet Language Transformations) définissant le mappage. Pour cette raison, les scripts Inline peuvent utiliser les mêmes espaces de noms que n’importe quel autre script de feuille de style XSLT. Le tableau suivant indique les espaces de noms disponibles.  
  
|Espace de noms| Description|  
|---------------|-----------------|  
|Système|La classe System.|  
|System.Collection|Les classes de regroupement.|  
|System.Text|Les classes de texte.|  
|System.Text.RegularExpressions|Les classes d’expressions régulières.|  
|System.Xml|Les classes XML principales.|  
|System.Xml.Xsl|Les classes XSLT.|  
|System.Xml.Xpath|Les classes XPath.|  
|Microsoft.VisualBasic|Les classes de script Visual Basic.|  
  
 Pour plus d’informations sur les espaces de noms et types de données, effectuez une recherche sur « à l’aide de XSLT Stylesheet Scripting \<msxsl : script > » et « System.Xml.Xsl.XslCompiledTransform » dans la collection du .NET Framework.  
  
> [!CAUTION]
>  Veillez à ne pas utiliser la même signature de méthode plusieurs fois. Lorsque plusieurs fonctoids Script ont la même signature de méthode, BizTalk sélectionne la première implémentation et ignore les autres.  
  
 Outre leur facilité d’utilisation pour les scripts à usage unique, les scripts Inline sont également utiles pour déclarer des variables globales à utiliser avec un certain nombre de scripts. Par exemple, dans un script C# inline, vous pourriez placer la ligne de code suivante en dehors de toute classe.  
  
```  
ArrayList statusList = new ArrayList();  
```  
  
 Cette opération crée un **ArrayList**, `statusList`, disponible à tous les scripts inline dans le mappage.  
  
 Pour un exemple de script inline, consultez [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid script](../core/scripting-functoid.md)   
 [Écriture de scripts à l’aide des assemblys externes](../core/scripting-using-external-assemblies.md)   
 [Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [Comment configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md)