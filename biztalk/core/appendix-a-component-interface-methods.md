---
title: "Annexe a : méthodes d’Interface de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, methods
- methods, component interfaces
- component interface methods
ms.assetid: c8377589-fbdf-4287-b822-53263a00381d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cb5b87cb063f22c889291b8eff3b2be50d64a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-a-component-interface-methods"></a>Annexe a : méthodes d’Interface de composant
L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise offre des méthodes standard pour les interfaces de composant.  
  
> [!NOTE]
>  Le paramètre `interactiveMode`, dans la version Ex des méthodes, contribue au débogage d'un appel effectué au système principal (`Create/CreateEx`, `Update/UpdateEx` et `DeleteOnly`). Chaque élément de l'appel *Ex effectué au système principal est appelé séparément, de manière à ce que vous identifiez avec précision celui qui a échoué. Il existe une baisse des performances lorsque vous utilisez un \*Ex méthode étant donné que les éléments de chaque propriété reçoit un appel distinct. Vous pouvez développer avec \*Ex méthode et puis que vous passez à la méthode principale (par exemple, `Create`) pour la production. Vous pouvez également utiliser un commutateur de débogage au niveau de production pour basculer entre l’utilisation de la méthode et le \*Ex (méthode).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Méthode CreateEx](../core/createex-method.md)  
  
-   [Méthode DeleteOnly](../core/deleteonly-method.md)  
  
-   [Find (méthode)](../core/find-method.md)  
  
-   [Get (méthode)](../core/get-method.md)  
  
-   [Méthode UpdateEx](../core/updateex-method.md)  
  
-   [Méthodes définies par l’utilisateur des composants Interface](../core/component-interface-user-defined-methods.md)  
  
-   [Propriétés de la Date d’effet](../core/effective-date-properties.md)