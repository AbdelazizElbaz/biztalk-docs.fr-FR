---
title: "Méthodes définies par l’utilisateur des composants Interface | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, user-defined methods
- user-defined methods, component interface
- custom component interfaces, limitations
- collection limitations
- custom methods, samples
- samples, custom methods
- component interfaces, limitations for custom CI
ms.assetid: e4b15889-35ff-44aa-819d-eade9690bdd6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 139117ffb26c8fec355dcfe481657817bc64bc0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="component-interface-user-defined-methods"></a>Méthodes définies par l’utilisateur des composants Interface
L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise prend en charge les méthodes définies par l'utilisateur dans les interfaces de composant. Les signatures ont la forme suivante :  
  
```  
myRet=myCI.myMethod(parameter1, parameter2, ...)  
```  
  
 où :  
  
-   `parameter1` et `parameter2` sont des paramètres d'entrée.  
  
-   `myRet` est la valeur renvoyée.  
  
 Les paramètres ne peuvent être que des paramètres d'entrée pour la méthode. Une seule valeur peut être renvoyée de la méthode comme paramètre de renvoi.  
  
> [!NOTE]
>  L'interface de composant qui contient les méthodes définies par l'utilisateur doit uniquement avoir la fonction `Get` de PeopleSoft activée. Si l'interface de composant inclut des clés, les méthodes personnalisées ne fonctionnent pas.  
  
## <a name="custom-ci-limitation"></a>Limitation des interfaces de composant personnalisées  
 L'adaptateur BizTalk pour PeopleSoft Enterprise peut gérer les méthodes PeopleSoft personnalisées à condition que l'interface de composant n'inclut pas de clés. Si l’interface de composant inclut des clés, des méthodes personnalisées ne fonctionnera pas.  
  
### <a name="workaround"></a>Pour contourner le problème  
 Créez une interface de composant sans clé et écrivez une nouvelle méthode personnalisée qui incorpore les clés dans le cadre des paramètres d'appel. Par exemple, vous pouvez utiliser la méthode personnalisée SetPassword dans l'interface de composant USER_PROFILE. USER_PROFILE inclut toutefois des clés. Vous pouvez créer une interface de composant sans clé, puis créer une méthode personnalisée dans votre nouvelle interface de composant. Cette méthode accepte deux paramètres : l'ID d'utilisateur et le mot de passe. La méthode personnalisée peut ensuite appeler USER_PROFILE à l'aide de la fonction `Get`, puis appeler `SetPassword`. Pour plus d’informations, consultez la documentation de PeopleSoft.  
  
 En raison d'une limitation dans PeopleSoft, les types `Date`, `DateTime` et `Time` qui apparaissent dans les méthodes définies par l'utilisateur sont mappés sous la forme de chaînes dans le code client.  
  
## <a name="collection-limitation"></a>Limitation des collections  
 Les méthodes définies par l'utilisateur ne peuvent pas renvoyer de collection, ou plus généralement, d'objet API. Vous pouvez uniquement renvoyer des types simples (par exemple, chaînes et nombres). Vous pouvez contourner cette limitation en envoyant une collection sous la forme d'une chaîne XML et en programmant le client pour analyser les chaînes et extraire les éléments au format correct. Pour consulter un exemple de ce contournement, vous pouvez examiner l'interface de composant personnalisée GET_CI_INFO.  
  
## <a name="sample-custom-method"></a>Exemple de méthode personnalisée  
 Vous pouvez utiliser la méthode personnalisée de base suivante (SayHello) pour tester les fonctionnalités de votre interface de composant à l'aide de méthodes personnalisées.  
  
 La fonction PeopleCode suivante est une méthode définie par l'utilisateur d'une interface de composant PeopleSoft nommée ACB_EMPLOYEE. L’exemple retourne une chaîne où la valeur de retour est **Hello** suivi par la valeur du paramètre d’entrée.  
  
```  
Function SayHello(&sName As string) Returns string  
      &EOL = Char(10);  
      &sResult = "Hello " | &sName | &EOL;  
      Return &sResult;  
End-Function;  
```  
  
> [!NOTE]
>  Pour modifier plusieurs tables simultanément (à l'aide d'une commande), vous pouvez créer une autre interface de composant ou une méthode définie par l'utilisateur d'une interface de composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)