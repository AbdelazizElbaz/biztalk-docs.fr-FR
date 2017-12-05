---
title: "Concepteur de Configuration d’adaptateur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b231c3-3948-4db8-b4f0-d9c21c31b168
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cff46f95062eff856653b6114f76f89ac17efd1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="custom-adapter-configuration-designer"></a>Concepteur de Configuration d’adaptateur personnalisé
Les concepteurs personnalisés doivent être créés dans une bibliothèque de classes .NET. Vous pouvez les incorporer dans la DLL de l'adaptateur ou créer une DLL distincte. Une fois que vous avez créé un assembly de concepteur, vous devez le référencer par le biais de décorations, tout comme une description ou une catégorie. La référence inclut une spécification de l'assembly et un nom de classe complet.  
  
 Ces décorations prend en charge deux moyens pour référencer le concepteur personnalisé : sous la forme d’un assembly global dans le global assembly cache ou un assembly externe situé sur le disque.  
  
> [!NOTE]
>  Il existe deux chemins d’accès possibles au moment du design assembly : vous pouvez spécifier le chemin d’accès absolu pour les éditeurs de type et les convertisseurs utilisés dans la configuration XSD dans le XSD lui-même (le chemin d’accès relatif n’est pas prise en charge), ou vous pouvez stocker les convertisseurs et éditeurs de type dans la liste globale cache d’assembly et de ne pas avoir un chemin d’accès absolu.  
  
## <a name="global-assembly-cache-designer-use"></a>Utilisation du concepteur du Global Assembly Cache  
 Le Global Assembly Cache stocke les assemblys en fonction de leur nom, clé publique, version et culture. Il est donc recommandé de :  
  
1.  générer un fichier de clé publique et de l'ajouter au fichier AssemblyInfo.cs ;  
  
2.  spécifier une version spécifique du fichier AssemblyInfo.cs.  
  
 Vous pouvez faire glisser l'assembly dans le Global Assembly Cache ou utiliser GACUTIL pour l'ajouter au GAC.  
  
 Pour utiliser ce concepteur, indiquez le nom de classe complet, une virgule et l'entrée de l'assembly dans le Global Assembly Cache (nom de l'assembly, version, culture et jeton de clé publique) en tant que valeur de la décoration. Utilisez \<éditeur\> décorations pour **UITypeEditor** implémentations et \<convertisseur\> décorations pour **TypeConverter** implémentations .  
  
 Le code ci-dessous indique comment initialiser les concepteurs personnalisés dans un fichier XSD :  
  
```  
<xs:element name="Global" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>GAC Designer Component</baf:category>  
            <baf:editor>AdapterManagement.ComponentModel. PasswordUITypeEditor, AdapterManagement, Version=1.0.1.0, Culture=neutral, PublicKeyToken=f0db50abb0615c18</baf:editor>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
      </xs:sequence>  
```  
  
## <a name="external-assembly-installation-and-use"></a>Installation et utilisation d'un assembly externe  
 Pour les assemblys externes, la décoration contient un assembly d'attribut facultatif qui spécifie le chemin d'accès complet et le nom de l'assembly contenant le concepteur souhaité.  
  
 Le code ci-dessous indique comment initialiser les concepteurs personnalisés contenus dans des assemblys externes :  
  
```  
<xs:element name="External" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>External Designer Component</baf:category>  
            <baf:converter assembly="C:\source\private\Adapter\Framework\Designer\bin\Debug\Designer.External.dll">Designer.External.DesignerTypeConverter</baf:converter>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [Éditeur de boîte de dialogue modales personnalisé pour la Configuration de l’adaptateur](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [Convertisseur de Type personnalisé pour la Configuration de l’adaptateur](../core/custom-type-converter-for-adapter-configuration.md)   
 [Composants de configuration avancée pour les adaptateurs](../core/advanced-configuration-components-for-adapters.md)