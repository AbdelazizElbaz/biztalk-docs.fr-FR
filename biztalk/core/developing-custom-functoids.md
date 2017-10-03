---
title: "Développement de fonctoids personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77419e1f-9f01-44ac-bf5b-a393f1d17f61
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5534f3209cb943fb3e2c2a63a18f9e29928be5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-functoids"></a>Développement de fonctoids personnalisés
Bien que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournisse plusieurs fonctoids permettant la prise en charge de diverses opérations, il est probable que vous rencontriez une situation requérant une approche différente. Les fonctoids personnalisés vous offrent un moyen pour étendre la gamme des opérations disponibles dans l'environnement de mappage de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Chaque fonctoid personnalisé est déployé comme un assembly .NET à l’aide des classes dérivées de **Microsoft.BizTalk.BaseFunctoids**. Un assembly peut contenir plusieurs fonctoids personnalisés.  
  
 Vous devez envisager d'utiliser un fonctoid personnalisé dans les situations suivantes :  
  
-   Vous possédez des règles de validation et de conversion pour un champ de code de caractère utilisant des données accessibles uniquement par l'intermédiaire d'une API héritée propriétaire.  
  
-   Vous devez chiffrer ou déchiffrer des champs à l'aide d'une gestion personnalisée de la logique métier et des clés.  
  
-   Vous devez générer un code de hachage à partir d'une partie du message pour l'utiliser dans une autre application.  
  
-   Le service Comptabilité demande que les messages qui lui sont transmis incluent des informations récapitulatives sur le total des ventes par type de produit.  
  
-   Vous souhaitez réduire la complexité d'un mappage en combinant plusieurs étapes liées, en utilisant une méthode différente ou de nouvelles bibliothèques de classes.  
  
-   Dans un fonctoid de script, plusieurs mappages utilisent le même code de script.  
  
-   Vous devez signaler tout échec d'opération dans le journal des événements.  
  
 Les fonctoids personnalisés peuvent être intégrés dans une solution directement à l'aide de code Inline ou indirectement par référence à une méthode d'une bibliothèque de classes déployée dans le Global Assembly Cache. Les deux types d’intégration s’appuient sur la **BizTalk.BaseFunctoid** classe et suivre le même ensemble d’étapes générales :  
  
1.  Créez un projet de bibliothèque de classes en utilisant le langage .NET de votre choix.  
  
2.  À l'aide de l'utilitaire d'attribution de noms forts sn.exe, créez un fichier clé et affectez-le au projet.  
  
3.  Ajoutez une référence à Microsoft.BizTalk.BaseFunctoids.dll. Cet assembly contient la **BaseFunctoid** classe de base.  
  
4.  Créez un fichier de ressources et ajoutez-le au projet. Ajoutez des ressources de chaîne pour le nom de fonctoid, l'info-bulle et la description. Ajoutez une ressource image de 16 x 16 pixels pour représenter le fonctoid dans la palette du concepteur de mappages.  
  
5.  Implémentez la classe de fonctoid par dérivation de **BaseFunctoid**, l’établissement des paramètres de base dans le constructeur, puis en écrivant la méthode fonctoid et toutes les méthodes de prise en charge. L'assembly peut contenir plusieurs fonctoids personnalisés.  
  
6.  Déployez l'assembly et assurez-vous que le nouveau fonctoid est disponible dans la palette de la boîte à outils. Consultez [Ajout et suppression de fonctoids personnalisés à partir de la boîte à outils Visual Studio](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md).  
  
 Voici une illustration du fonctoid Floor.  
  
```  
/// <summary>  
/// Floor Functoid - finds the floor of input  
/// </summary>  
public class FloorFunctoid : BaseFunctoid  
{  
    public FloorFunctoid()  
        : base()  
    {  
        this.ID = 11001;  
        SetupResourceAssembly("MultipleFunctoids.Resource", Assembly.GetExecutingAssembly());  
  
        SetName("NAME_FLOOR");  
        SetDescription("DESCRIPTION_FLOOR");  
        SetTooltip("DESCRIPTION_FLOOR");  
        SetBitmap("IMAGE_FLOOR");  
  
        SetExternalFunctionName(GetType().Assembly.FullName, " MultipleFunctoids.FloorFunctoid", "MathFloor");  
        this.RequiredGlobalHelperFunctions = InlineGlobalHelperFunction.IsNumeric;  
  
        AddScriptTypeSupport(ScriptType.CSharp);  
        SetMinParams(1);  
        SetMaxParams(1);  
  
        this.Category = FunctoidCategory.Math;  
        this.OutputConnectionType = ConnectionType.AllExceptRecord;  
        AddInputConnectionType(ConnectionType.AllExceptRecord);  
        this.HasSideEffects = false;  
    }  
  
    /// <summary>  
    /// To create the C# function  
    /// </summary>  
    /// <param name="scriptType">Script type</param>  
    /// <param name="numParams">Number of parameters</param>  
    /// <param name="functionNumber">Functoid number</param>  
    /// <returns>C# script</returns>  
    protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
    {  
        if (ScriptType.CSharp == scriptType)  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string MathFloor(string input)\n");  
            builder.Append("{\n");  
            builder.Append("  if(string.IsNullOrEmpty(input))\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("double d = 0.0;\n");  
            builder.Append("if (IsNumeric(input, ref d))\n");  
            builder.Append("    return Math.Floor(d).ToString(System.Globalization.CultureInfo.InvariantCulture);\n");  
            builder.Append("else\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
        else  
        {  
            return string.Empty;  
        }  
    }  
}  
  
```  
  
 Lorsque vous utilisez cet exemple de code dans le cadre d'un projet C#, « Nom de l'assembly » doit être défini sur « MultipleFunctoids ». Le projet C# (contenant ce code) doit inclure un fichier Resource.resx.  
  
```  
SetName("NAME_FLOOR");  
SetDescription("DESCRIPTION_FLOOR");  
SetTooltip("DESCRIPTION_FLOOR");  
SetBitmap("IMAGE_FLOOR");  
  
```  
  
 Dans le code ci-dessus, les valeurs « NAME_FLOOR », « DESCRIPTION_FLOOR » et « DESCRIPTION_FLOOR » sont les « clés » des chaînes de ressources incorporées dans le fichier Resource.resx. « IMAGE_FLOOR » est le nom d'une image incorporée dans le fichier Resource.resx. Celle-ci agira en tant qu'icône pour le fonctoid.  
  
 Si vous ne spécifiez pas de clés de ressources appropriées ou si vous supprimez la méthode SetName, un fonctoid personnalisé sans nom est créé, ce qui est déconseillé. Cela est vrai également pour les méthodes SetDescription et SetTooltip. Utilisez toujours ces méthodes de manière appropriée pour éviter tout comportement de nettoyage indésirable. Toutefois, vous pouvez ignorer la méthode SetBitmap si vous ne disposez pas d'images appropriées à utiliser comme icônes pour les fonctoids. Dans ce cas, une icône par défaut est utilisée par le fonctoid personnalisé. Ceci ne présente aucun danger sauf si plusieurs fonctoids sans icône sont présents.  
  
 Pour plus d’informations sur la création d’un fonctoid personnalisé, consultez [fonctoid personnalisé (exemple BizTalk Server)](../core/custom-functoid-biztalk-server-sample.md).  
  
> [!IMPORTANT]
>  Certains ID de fonctoids sont réservés par des fonctoids standard/intégrés du Mappeur. En règle générale, les fonctoids du Mappeur standards utilisent les ID de 1 à 10000. Lors de la création des fonctoids personnalisés, n’utilisez pas le fonctoid ID inférieurs à 10 000.  
  
## <a name="in-this-section"></a>Dans cette section  
 Contenu de cette section :  
  
-   [Utilisation de BaseFunctoid](../core/using-basefunctoid.md)  
  
-   [Développement personnalisé référencé fonctoid](../core/developing-a-custom-referenced-functoid.md)  
  
-   [Développement d’un fonctoid Inline personnalisé](../core/developing-a-custom-inline-functoid.md)  
  
-   [Développement d’un fonctoid cumulé personnalisé](../core/developing-a-custom-cumulative-functoid.md)  
  
-   [Ajout et suppression de fonctoids personnalisés à partir de la boîte à outils de Visual Studio](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md)