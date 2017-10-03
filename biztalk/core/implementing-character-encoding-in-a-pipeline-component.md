---
title: "Implémentation d’encodage de caractères dans un composant de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- pipeline components [custom], code samples
- pipeline components [custom], encoding
ms.assetid: 862b56da-ec14-41f9-b63c-42d81124e167
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bc95dc44fa4a4905affaad969c248aa4b76d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-character-encoding-in-a-pipeline-component"></a>Implémentation d’encodage de caractères dans un composant de Pipeline
Pour prendre en charge le codage des caractères personnalisés, vous devez implémenter une classe de codage personnalisée en dérivant de Microsoft .NET Framework **codage** classe, puis créer un composant de pipeline de fichier plat personnalisé en héritant de la plate standard Composant désassembleur de fichier ou l’assembleur de fichier plat. Vous pouvez fournir une nouvelle instance de codage au moteur d’analyse en substituant la méthode virtuelle protégée **FFDasmComp.GetDataReader** comme indiqué dans l’exemple suivant.  
  
```  
/// <summary>  
/// Gets a data reader instance  
/// </summary>  
/// <param name="dataStream">Data stream</param>  
/// <param name="dataEncoding">Data encoding</param>  
/// <param name="detectEncodingFromByteOrderMarks">Detect encoding from a byte order mark</param>  
/// <returns>IDataReader instance</returns>  
      protected override IDataReader GetDataReader(Stream dataStream, Encoding dataEncoding, bool detectEncodingFromByteOrderMarks)  
      {  
         // Delegate call to the base implementation passing fixed UTF-7 encoding  
         return base.GetDataReader(dataStream, new CustomEncoding(), false);  
      }  
```  
  
## <a name="using-predefined-encoding-classes"></a>Utilisation des classes de codage prédéfinies  
 Les types de codage suivants sont prédéfinis par Microsoft .NET Framework et permettent de construire l'analyseur :  
  
-   ASCII  
  
-   UTF7  
  
-   UTF8  
  
-   Unicode (UTF16)  
  
```  
XmlReader xr = docspec.Parse(new DataReader(System.Text.Encoding.UTF8));  
```  
  
## <a name="using-supported-code-pages"></a>Utilisation des pages de code prises en charge  
 Utilisez le code suivant pour prendre en charge Shift-JIS (codepage 932).  
  

```  
XmlReader xr = docspec.Parse(new DataReader(System.Text.Encoding.GetEncoding(932)));  
```  
  
## <a name="using-a-private-encoding-class"></a>Utilisation d'une classe de codage privée  
 Vous pouvez créer votre propre classe d’encodage qui dérive de la **System.Text.Encoding** classe abstraite et effectuer votre propre codage et décodage.  
  
```  
class MyEncoding : System.Text.Encoding  
{  
   // overriding methods omitted  
}  
  
XmlReader xr = docspec.Parser(new DataReader(new MyEncoding()));  
```  
  
## <a name="using-a-private-datareader-class"></a>Utilisation d'une classe DataReader privée  

 Vous pouvez créer vos propres [DataReader](https://msdn.microsoft.com/library/microsoft.biztalk.parsingengine.datareader.aspx) classe qui implémente le `IDataReader` de l’interface et effectue la lecture sans créer n’importe quel encodage classes.  
  
```  
class MyDataReader : IDataReader  
{  
   // Implement data reader functions  
   // ...  
}  
  
XmlReader xr = docspec.Parse(new MyDataReader());  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de moteurs d’analyse et de sérialisation](../core/using-the-parsing-and-serializing-engines.md)