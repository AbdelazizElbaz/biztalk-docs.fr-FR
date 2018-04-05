---
title: Portée des variables dans les Orchestrations | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
ms.assetid: 5856cdca-0ebd-4e16-8739-7bd50753b9f9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82803cd7f2b0beb8349e978fdd7b9e453dca31ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="variable-scope-in-orchestrations"></a>Portée des variables dans les Orchestrations
Il y a quelques points importants à bien comprendre à propos de la visibilité et de l'état des variables et des paramètres d'orchestration en plusieurs endroits de votre orchestration et notamment concernant les gestionnaires d'exception et les blocs de compensation.  
  
-   Les paramètres d'orchestration sont visibles dans tout le corps de l'orchestration ainsi que dans son bloc de compensation.  
  
-   Les variables de niveau d'étendue sont visibles dans le corps de l'étendue ainsi que dans l'ensemble de ses gestionnaires d'exception et de son bloc de compensation. Dans les gestionnaires d'exception, les variables sont considérées comme non initialisées dès lors qu'il n'est pas déterminé si l'exception qui a conduit à un gestionnaire donné a eu lieu avant ou après toute initialisation dans le corps. C'est pour cette raison que, si vous déclarez une variable dans une étendue et que vous l'initialisez dans le corps, vous ne pourrez pas la lire dans un gestionnaire d'exceptions ou obtiendrez une erreur du compilateur. Il est possible de contourner ce problème avec les transactions à long terme. L'exemple suivant illustre comment l'opérateur succeeded() peut être utilisé pour garantir un comportement correct à l'exécution.  
  
    > [!NOTE]
    >  Le code ci-dessous est un pseudo-code qui décrit un processus logique. Il ne peut pas être employé dans une forme Expression d'orchestration.  
  
    ```  
    scope longrunning transaction L  
    {  
       System.Int32 i;  
       System.Int32 v;  
       body  
       {  
          i = 3;  
          scope longrunning transaction T  
          {  
             body  
             {  
                i = 5;  
             }  
          }  
       }  
       exceptions  
       {  
          catch  
          {  
             if(succeeded(T))  
             {  
                v = i;  // OK to read from it here — no compiler errors!  
             }  
          }  
       }  
    }  
    ```  
  
-   À l'intérieur d'un bloc de compensation, toutes les variables endossent les valeurs qu'elles avaient lorsque le corps de l'étendue a été validé. Remarquez que le bloc de compensation d'une étendue ne s'exécute jamais immédiatement après la fin de son corps. Il y a toujours un code intermédiaire. Si ce code intermédiaire met à jour quelques variables d'étendue externe et que le bloc de compensation s'exécute ensuite, les mises à jour effectuées ne seront pas visibles dans le bloc de compensation. Les variables reprendront temporairement les valeurs qu'elles avaient au moment où l'étendue à laquelle appartient cette compensation avait été validée.  
  
-   Si une transaction est imbriquée dans une boucle, elle sera compensée autant de fois que la boucle s'exécutera. Dans le bloc de compensation de chaque itération, les variables d'étendue externe endossent les valeurs qui étaient les leurs lorsque l'itération de la transaction a été validée.  
  
-   Toutes les mises à jour apportées aux variables d'étendue externe ou aux paramètres d'orchestration figurant dans les blocs de compensation des étendues internes ne seront plus visibles une fois que le bloc de compensation aura terminé. En d'autres termes, le bloc de compensation ne peut pas être utilisé pour modifier directement les valeurs des variables d'étendue externe.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XLANG-s](../core/xlang-s-data-types.md)