---
title: "Développement d’un fonctoid Inline personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4533f09f-b62d-4b09-b7de-44541c6cf053
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a742e6a53b5fb81d92922ff94e7754239f723ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-custom-inline-functoid"></a>Développement d'un fonctoid Inline personnalisé
Les fonctoids Inline personnalisés fonctionnent en copiant le code d'implémentation directement dans un mappage et non pas en référençant un assembly, une classe et un nom de méthode comme le ferait un fonctoid référencé personnalisé.  
  
## <a name="building-inline-script"></a>Création d’un script Inline   
 Il existe deux manières de créer du script afin de l'inclure dans le mappage. Choisissez parmi les méthodes suivantes, en fonction du nombre variable de paramètres que votre fonctoid personnalisé prend en charge ou non :  
  
-   Substituer **GetInlineScriptBuffer** lorsque votre fonctoid personnalisé accepte un nombre variable de paramètres d’entrée et que vous avez défini le **HasVariableInputs** propriété `true`. Par exemple, utilisez cette méthode si vous voulez concaténer un nombre variable de chaînes ou trouver la valeur la plus grande dans une série de valeurs.  
  
-   Utilisez **SetScriptBuffer** lorsque vous n’avez pas besoin de prendre en charge un nombre variable de paramètres d’entrée. Vous pouvez toujours utiliser des paramètres facultatifs, mais le nombre total de paramètres est fixe.  
  
 Ces deux méthodes impliquent des implémentations différentes.  
  
### <a name="providing-inline-code-with-setscriptbuffer"></a>Code Inline avec SetScriptBuffer  
 Pour configurer votre fonctoid personnalisé de sorte qu’il utilise le script Inline :  
  
1.  Appelez **AddScriptTypeSupport** avec [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) pour activer le code inline et définir le type de script pris en charge.  
  
2.  Appeler **SetScriptBuffer** pour définir le code à utiliser pour le fonctoid personnalisé. Vous appellerez cette fonction trois fois avec le paramètre `functionNumber` pour les fonctoids cumulés personnalisés et une fois pour les fonctoids non cumulés personnalisés.  
  
3.  Utilisez **SetScriptGlobalBuffer** pour déclarer des variables globales que votre code inline utilise.  
  
4.  Utilisez **RequiredGlobalHelperFunctions** pour indiquer les fonctions d’assistance nécessitant votre fonctoid inline personnalisé.  
  
 Vous pouvez générer votre script en utilisant StringBuilder ou des constantes. Pour écrire du code de script, une des possibilités consiste à écrire d'abord un fonctoid référencé personnalisé puis, lorsque tous les bogues sont éliminés, à le convertir en un fonctoid Inline en copiant toutes vos fonctions dans des constantes de chaîne.  
  
### <a name="providing-inline-code-with-getinlinescriptbuffer"></a>Code Inline avec GetInlineScriptBuffer  
 Si votre fonctoid inline personnalisé prend en charge un nombre variable de paramètres, vous remplacera **GetInlineScriptBuffer**. Pour configurer votre fonctoid personnalisé de sorte qu’il utilise le script Inline :  
  
1.  Dans le constructeur, déclarez que votre fonctoid personnalisé dispose d’entrées variables en définissant **HasVariableInputs** à `true`.  
  
2.  Dans le constructeur, appelez **AddScriptTypeSupport** avec [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) pour activer le code inline et définir le type de script pris en charge.  
  
3.  Substituer **GetInlineScriptBuffer** pour construire et renvoyer le code à utiliser dans le mappage de votre fonctoid personnalisé. Utilisez les paramètres pour créer le code correct en vérifiant le `scriptType` et le `numParams`. Le dernier paramètre, `functionNumber`, doit être 0. Il s’agit, car les fonctions cumulées ont un nombre fixe d’entrées et n’utilisent pas ce mécanisme.  
  
4.  Utilisez **SetScriptGlobalBuffer** pour déclarer des variables globales que votre code inline utilise.  
  
5.  Utilisez **RequiredGlobalHelperFunctions** pour indiquer les fonctions d’assistance nécessitant votre fonctoid inline personnalisé.  
  
 Le fragment de code suivant crée une fonction C# avec le nombre de paramètres transmis dans `numParams`, mais sans corps. Pour utiliser ce fragment de code, copiez l'exemple dans votre solution et ajoutez du code avec les paramètres pour qu'une valeur soit renvoyée.  
  
```  
// Override GetInlineScriptBuffer  
protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
{  
    // Is this one of the supported script types?  
    if(ScriptType.CSharp == scriptType)  
    {  
        // Assume functionNumber == 0  
        StringBuilder builder = new StringBuilder();  
        // Function declaration   
        builder.Append("public string MyFunction("  
        // Declare parameters using numParams  
        for(int i=0; i<numParams; i++)  
        {  
            // Separate params with a comma  
            if(i > 0)  
                builder.Append(", ");  
            // Declare parameters, param0 to paramNUMPARAM  
            builder.Append("string param" + i.ToString());  
        }  
        builder.Append(")\n");  
        // Function body; process params as needed  
        builder.Append("{\n");  
        builder.Append("}\n");  
        // Return script  
        return builder.ToString();  
    }  
    // scriptType is unsupported  
    return string.Empty;  
}  
```  
  
## <a name="testing-an-inline-script"></a>Test d’un script Inline  
 Le test est un aspect important de tout effort de développement. Les fonctoids Inline personnalisés peuvent être soumis à un test. Pour simplifier le processus, utilisez l'une des techniques suivantes ou les deux :  
  
-   Examinez le XSLT d’un mappage qui utilise le fonctoid inline personnalisé.  
  
-   Vérifiez l'entrée et la sortie d'un mappage qui utilise le fonctoid Inline personnalisé.  
  
### <a name="examine-the-xslt-of-a-map-that-uses-the-custom-inline-functoid"></a>Examinez le XSLT d'un mappage qui utilise le fonctoid Inline personnalisé.  
 Cette technique révèle souvent des problèmes de syntaxe subtiles ou de logique. Elle vous aide également à comprendre ce qui se passe dans le mappage.  
  
 Pour afficher le XSLT pour un mappage  
  
1.  À partir d’un projet BizTalk Visual Studio, cliquez sur le **l’Explorateur de solutions** onglet, cliquez sur un mappage qui utilise votre fonctoid inline personnalisé, puis cliquez sur **valider le mappage**.  
  
2.  Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier XSLT. Appuyez sur CTRL et cliquez sur l'URL pour afficher le fichier.  
  
> [!NOTE]
>  Gardez à l’esprit qu'aucune modification apportée au fichier XSLT ne sera répercutée dans votre fonctoid personnalisé.  
  
### <a name="test-a-map-that-uses-the-custom-inline-functoid"></a>Test d'un mappage qui utilise le fonctoid Inline personnalisé  
 Ce test permet de vérifier que le mappage et le fonctoid Inline personnalisé fonctionnent comme prévu.  
  
 Pour tester un mappage  
  
1.  À partir d’un projet BizTalk Visual Studio, cliquez sur le **l’Explorateur de solutions** onglet, cliquez sur un mappage qui utilise votre fonctoid inline personnalisé, puis cliquez sur **Test Map**.  
  
2.  Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier de sortie. Appuyez sur CTRL et cliquez sur l'URL pour afficher le fichier.  
  
 Vous pouvez vérifier les valeurs d’entrée et de sortie pour vous assurer que le mappage s'est comporté comme prévu.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer un fonctoid Inline personnalisé pour concaténer deux chaînes. Il repose sur un fichier de ressources contenant trois ressources de chaîne et une ressource bitmap 16 x 16 pixels.  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    /// <summary>  
    /// Performs a string concatenation using inline code.  
    /// </summary>  
    public class CustomStringConcatFunctoid : BaseFunctoid  
    {  
        public CustomStringConcatFunctoid()  
            : base()  
        {  
            //ID for this functoid  
            this.ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUSTOMSTRINGCONCATFUNCTOID_NAME");  
            SetTooltip("IDS_CUSTOMSTRINGCONCATFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUSTOMSTRINGCONCATFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUSTOMSTRINGCONCATFUNCTOID_BITMAP");  
  
            // Put this string handling function under the String   
            // Functoid tab in the Visual Studio toolbox for functoids  
            this.Category = FunctoidCategory.String;  
  
            // 2 required parameters, no optional parameters  
            this.SetMinParams(2);  
            this.SetMaxParams(2);  
  
            // Functoid accepts two inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            this.OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Declare support for CSharp inline function and  
            // pass the method implementation to the buffer  
            AddScriptTypeSupport(ScriptType.CSharp);  
            SetScriptBuffer(ScriptType.CSharp, GetCSharpBuffer());  
        }  
  
        private string GetCSharpBuffer()  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string ConCatStrings(string val1, string val2)\n");  
            builder.Append("{\n");  
            builder.Append("    return val2+val1;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de BaseFunctoid](../core/using-basefunctoid.md)   
 [Développement personnalisé référencé fonctoid](../core/developing-a-custom-referenced-functoid.md)   
 [Fonctoid personnalisé (exemple BizTalk Server)](../core/custom-functoid-biztalk-server-sample.md)