---
title: L’initialisation des Variables d’Orchestration | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
ms.assetid: 770e4e55-1fb9-4b43-854c-63aec5a3c5ba
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a90fbc33343e3576d6199a0a97a7a57ca881f720
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="initializing-orchestration-variables"></a>Variables d'initialisation d'orchestration
Vous pouvez initialiser la valeur d'une variable en la définissant dans la fenêtre Propriétés. Par exemple, vous pouvez définir le **valeur initiale** sur 32 pour initialiser la variable de type System.Int32. Lorsque vous ajoutez une valeur initiale à une variable de type chaîne, vous devez placer cette valeur entre guillemets dans la fenêtre Propriétés. Si la chaîne doit contenir une apostrophe, utilisez la barre oblique inverse comme caractère d'échappement et utilisez ensuite deux barres obliques inverses consécutives si vous souhaitez insérer une barre oblique inverse littérale dans votre chaîne. Si vous ne spécifiez pas une valeur pour vos variables, vos variables recevront les valeurs par défaut dès qu’une instance de l’orchestration est créée.  
  
 Si la variable est une instance d'une classe, vous pouvez spécifier un constructeur pour l'initialiser. Par défaut, le **utiliser le constructeur par défaut** est définie sur **True** si un constructeur par défaut est disponible ; par conséquent, le constructeur par défaut est appelé. Si vous envisagez uniquement d’utiliser le constructeur par défaut, vous n’avez pas besoin initialiser les variables à nouveau dans le **Expression** forme pour éviter d’appeler le constructeur à deux reprises. Si le **utiliser le constructeur par défaut** est définie sur **False**, le constructeur par défaut ne sera pas appelé ; vous devez appeler un constructeur dans une expression ou réaliser une assignation à la variable avant que vous puissiez l’utiliser dans l’orchestration. En outre, si le constructeur requiert des paramètres d’entrée, vous devez définir **utiliser le constructeur par défaut** à **False** , puis appelez le constructeur d’une **Expression** forme ; pour exemple, `myVariable = myNamespace.myClass (param1, param2)`.  
  
 Le seul cas dans lequel vous devez explicitement initialiser vos variables est lorsque votre orchestration contient plus de l’activation de réception, que possible dans un **étendue**, **Actions parallèles** , ou **écouter** forme. Dans ce cas, l’initialisation automatique est désactivée, et vous devez utiliser un **Expression** forme pour initialiser vos variables. Vous devez placer un **Expression** forme après chaque réception avec activation, et avant d’accéder à n’importe quelle variable dans l’orchestration.