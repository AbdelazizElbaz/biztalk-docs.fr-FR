---
title: "Convertisseur de Type personnalisé pour la Configuration de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60e94dde-d29d-43ff-84b0-b2ba86851151
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6285cd61fd0738fb97c6192cd52b812d96ede7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-type-converter-for-adapter-configuration"></a>Convertisseur de Type personnalisé pour la Configuration de l’adaptateur
Comme l’éditeur personnalisé, le convertisseur de type personnalisé remplace le **System.ComponentModel.TypeConverter** classe de l’un de ses enfants. À ce niveau, le convertisseur ajoute le formatage à la valeur à conserver mais n'apparaît pas sur la page des propriétés. Le **ConvertFrom** méthode ajoute des crochets autour de la valeur de chaîne et le **ConvertTo** méthode les supprime.  
  
 Le code suivant correspond à la définition de classe pour l'éditeur de type personnalisé :  
  
```  
using System;  
using System.ComponentModel;  
  
namespace AdapterManagement.ComponentModel {  
  
   public class DesignerTypeConverter : StringConverter {  
  
      public override bool CanConvertTo(ITypeDescriptorContext context, Type destinationType) {  
         return (typeof(String) == destinationType) || base.CanConvertTo (context, destinationType);  
      }  
  
      public override object ConvertTo(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object value, Type destinationType) {  
         if (typeof(String) == destinationType && value is String) {  
            return ((String)value).TrimStart('[').TrimEnd(']');  
         }  
         return base.ConvertTo (context, culture, value, destinationType);  
      }  
  
      public override bool CanConvertFrom(ITypeDescriptorContext context, Type sourceType) {  
         return (typeof(String) == sourceType) || base.CanConvertFrom (context, sourceType);  
      }  
  
      public override object ConvertFrom(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object value) {  
         if (value is String) {  
            return "["+(String)value+"]";  
         }  
         return base.ConvertFrom (context, culture, value);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de Configuration d’adaptateur personnalisé](../core/custom-adapter-configuration-designer.md)   
 [Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [Éditeur de boîte de dialogue modales personnalisé pour la Configuration de l’adaptateur](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [Composants de Configuration avancée pour les cartes](../core/advanced-configuration-components-for-adapters.md)