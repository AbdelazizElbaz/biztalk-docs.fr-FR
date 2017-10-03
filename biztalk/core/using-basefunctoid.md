---
title: Utilisation de BaseFunctoid | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb26a54d-20bf-4302-a5cb-b38e4091002b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f2d1381b1babb26324730c301800d6b0909a411
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-basefunctoid"></a>Utilisation de BaseFunctoid
Tous les fonctoids personnalisés doivent être dérivés de la classe **BaseFunctoid** . Vous devez d'abord remplacer le constructeur et créer un ensemble d'objets qui informe le Mappeur BizTalk sur votre fonctoid personnalisé. Vous devez ensuite écrire la logique du fonctoid.  
  
## <a name="overriding-the-constructor"></a>Remplacement du constructeur  
 Vous devez effectuer des nombreuses tâches dans la méthode de remplacement de constructeur de classe pour caractériser votre fonctoid. Ces tâches s'ajoutent à tout code spécifique au fonctoid requis par votre solution. Le tableau suivant décrit les tâches principales.  
  
|Tâche|Utiliser ces méthodes ou ces propriétés|Commentaires|  
|----------|-------------------------------------|--------------|  
|Affecter un ID unique au fonctoid|**ID**|Utilisez une valeur supérieure à 6000 qui n'a pas été utilisée. Les valeurs inférieures à 6000 sont réservées aux fonctoids internes.|  
|Indiquer si le fonctoid a des effets secondaires|**HasSideEffects**|Utilisé par le mappeur pour optimiser le code XSLT généré. Cette propriété est définie par défaut sur true.|  
|Pointer vers l'assembly de ressources|**SetupResourceAssembly**|Incluez un fichier de ressources à votre projet. Si la génération avec [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l’assembly de ressources doit être **ProjectName.ResourceName**.|  
|Activer l'affichage du fonctoid personnalisé dans la palette du Mappeur BizTalk|**SetName**<br /><br /> **SetTooltip**<br /><br /> **SetDescription**<br /><br /> **SetBitmap**|Utilisez un ID de ressource pointant vers une chaîne pour le nom, l'info-bulle et la description ; utilisez un bitmap de 16 x 16 pixels.|  
|Affecter le fonctoid à une ou plusieurs catégories|**Catégorie**|Classez le fonctoid en utilisant une ou plusieurs valeurs [Microsoft.BizTalk.BaseFunctoids.FunctoidCategory](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.functoidcategory.aspx) .|  
|Spécifier le nombre de paramètres acceptés|**SetMinParams**<br /><br /> **SetMaxParams**<br /><br /> **HasVariableInputs**|Utilisez la méthode **SetMinParams** pour définir le nombre de paramètres requis et la méthode **SetMaxParams** pour définir le nombre de paramètres facultatifs. Respectez les consignes suivantes pour définir ces valeurs :<br /><br /> -Si vous n’avez aucuns paramètres facultatifs, définissez min = max.<br />-Si vous avez des paramètres facultatifs, définissez max = (nombre de paramètres facultatifs - nombre minimal de paramètres).<br />-Si vous souhaitez autoriser des paramètres facultatifs illimités, ne définissez pas max.<br />-Si vous avez un nombre variable d’entrées, ne définissez ne pas min ou max et définissez **HasVariableInputs** = `true`.|  
|Déclarer les éléments qui peuvent être connectés à votre fonctoid|**AddInputConnectionType**|Appelez **AddInputConnectionType** une fois pour chaque [Microsoft.BizTalk.BaseFunctoids.ConnectionType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.connectiontype.aspx) pris en charge par le fonctoid.|  
|Déclarer les éléments auxquels votre fonctoid peut se connecter|**OutputConnectionType**|Utilisez des valeurs de [Microsoft.BizTalk.BaseFunctoids.ConnectionType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.connectiontype.aspx) pour indiquer au Mappeur BizTalk les types d'objets qui peuvent recevoir une sortie de votre fonctoid. Utilisez **OR** pour spécifier plusieurs types de connexion.|  
|Indiquer à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les méthodes à appeler pour votre fonctoid|**SetExternalFunctionName**<br /><br /> **SetExternalFunctionName2**<br /><br /> **SetExternalFunctionName3**|Pour les fonctoids cumulés, utilisez **SetExternalFunctionName** pour définir la fonction d'initialisation, **SetExternalFunctionName2** pour définir la fonction de cumul et **SetExternalFunctionName3** pour spécifier la fonction qui renvoie la valeur cumulée. Pour les fonctoids non cumulés, utilisez **SetExternalFunctionName** pour définir la méthode du fonctoid.|  
|Spécifier l'utilisation par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de code Inline pour l'appel de votre fonctoid|**AddScriptTypeSupport SetScriptBuffer**|Appelez **AddScriptTypeSupport** avec [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) pour activer le code Inline. Appelez **SetScriptBuffer** pour transmettre le code à utiliser pour le fonctoid. Ce code sera copié dans le mappage.|  
|Déclarer des variables globales pour un fonctoid Inline|**SetScriptGlobalBuffer**|Toutes les déclarations effectuées seront visibles par les autres scripts Inline inclus dans le mappage.|  
|Indiquer les fonctions d'assistance requises par votre fonctoid Inline|**RequiredGlobalHelperFunctions**|Utilisez des valeurs de l'énumération **InlineGlobalHelperFunction** pour spécifier les fonctions d'assistance requises. Utilisez **OR** pour spécifier plusieurs fonctions d'assistance.|  
|Valider les paramètres transmis à votre fonctoid|**IsDate**<br /><br /> **IsNumeric**|Ces fonctions fournissent une réponse vrai/faux sans générer d'exception.|  
  
## <a name="implementing-functoid-logic"></a>Implémentation de la logique du fonctoid  
 Pour rendre le fonctoid utile, vous devez implémenter une ou plusieurs méthodes selon la catégorie du fonctoid. Si le fonctoid est cumulé, vous devez fournir trois méthodes ; une pour l'initialisation, une pour le cumul et une autre pour renvoyer la valeur cumulée. Si le fonctoid n'est pas cumulé, vous devez fournir une seule méthode qui renvoie une valeur.  
  
 Vous devez également décider si le code d'implémentation du fonctoid doit être copié en ligne dans le mappage ou conservé dans un assembly .NET compilé et utilisé par le biais d'une référence.  
  
 Envisagez d'utiliser un fonctoid Inline dans les cas suivants :  
  
-   Vous acceptez que d'autres utilisateurs puissent lire, voire modifier, votre logique d'entreprise.  
  
-   Votre fonctoid dépend uniquement de l'espace de noms .NET FRAMEWORK pris en charge par le mappage. Pour les espaces de noms disponibles, consultez [scripts utilisant Inline c#, JScript .NET et Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md).  
  
-   Vous ne voulez pas déployer et gérer un autre assembly avec votre solution BizTalk.  
  
-   Vous écrivez une série de fonctoids qui partagent des variables.  
  
 Envisagez d'utiliser un fonctoid référencé dans les cas suivants :  
  
-   Vous ne souhaitez pas que votre logique d'entreprise soit copiée dans le mappage où elle pourrait être vue ou modifiée par d'autres utilisateurs.  
  
-   Votre fonctoid dépend des classes .NET FRAMEWORK non prises en charge par le mappage.  
  
-   La fonctionnalité ajoutée fournie par le .NET Framework justifie le déploiement et la gestion d'un autre assembly avec votre solution BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement personnalisé référencé fonctoid](../core/developing-a-custom-referenced-functoid.md)   
 [Développement d’un fonctoid Inline personnalisé](../core/developing-a-custom-inline-functoid.md)   
 [Développement d’un fonctoid cumulé personnalisé](../core/developing-a-custom-cumulative-functoid.md)   
 [Microsoft.BizTalk.BaseFunctoids.BaseFunctoid](http://msdn.microsoft.com/library/Microsoft.BizTalk.BaseFunctoids.BaseFunctoid.aspx)