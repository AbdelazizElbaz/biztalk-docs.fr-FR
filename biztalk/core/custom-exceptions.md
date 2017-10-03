---
title: "Exceptions personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, compensation blocks
- compensation blocks, process management solutions
- process management solution tutorial, custom exceptions
- Terminate shape [Orchestration Designer], called orchestrations
- process management solution tutorial, errors
ms.assetid: 0c923303-82ad-4a20-9c7c-5e38c477993a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfead2aadc237d27e0fb8ed28a776dd1e4f5c6f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-exceptions"></a>Exceptions personnalisées
En cas d'erreur irrécupérable, la solution de gestion des processus d'entreprise utilise une combinaison de gestionnaires d'exception et d'exceptions personnalisées.  
  
## <a name="handling-exceptions"></a>La gestion des Exceptions  
 Au lieu d’utiliser **Terminate** formes dans les orchestrations appelées, vous pouvez utiliser le modèle de lever des exceptions qui sont gérées par l’orchestration racine. Ainsi, l'orchestration possédant la connaissance de contexte la plus étendue est en mesure de prendre une décision relative à la gestion de l'exception. Le fait que les orchestrations subordonnées lèvent des exceptions personnalisées permet de communiquer des informations plus spécifiques à l'orchestration racine.  
  
 La solution de gestion des processus d'entreprise suit ce modèle. Il existe quatre racine, ou les orchestrations recours, dans la solution : **OrderBroker**, **OrderManager**, **CableOrder1**, et **CableOrder2**. Trois orchestrations racines recevoir et de gérer des exceptions personnalisées : **OrderManager**, **CableOrder1**, et **CableOrder2**.  
  
 Notez que certaines orchestrations racines utilisent la **Terminate** forme et que le **Terminate** apparaît juste avant le point de terminaison normal de l’orchestration. L’orchestration utilise toujours le **Terminate** mettre en forme en cas d’erreur afin que l’orchestration est enregistrée comme terminée, plutôt que comme terminé, mais avec un message d’erreur. Ceci permet à la solution de suivre facilement les instances ayant échoué, en plus d'enregistrer l'erreur.  
  
 Pour plus d’informations sur la **Terminate** mettre en forme, consultez [comment configurer la forme Terminer](../core/how-to-configure-the-terminate-shape.md). Pour plus d’informations sur la **ThrowException** mettre en forme, consultez [comment configurer la forme lever d’Exception](../core/how-to-configure-the-throw-exception-shape.md).  
  
## <a name="the-custom-exceptions"></a>Exceptions personnalisées  
 Chacune des trois exceptions personnalisées suivantes suit le même modèle. Le fait d'avoir des types distincts permet au code de différencier les différentes exceptions.  
  
|Exception|Levée par (Orchestration)|  
|---------------|---------------------------------|  
|**ActivateException**|**Modification**|  
|**CableOrderException**|**Activer**, **CableOrder1**|  
|**InterruptException**|**CableOrder1**, **CheckInterrupt**, **ErrorHandlerOrch**|  
  
 Toutes les exceptions personnalisées sont définies dans le **utilitaires** assembly. et appartiennent à la classe .NET. Toutes les classes d’exceptions personnalisées héritent de .NET **ApplicationException** classe qui hérite à son tour à la **System.Exception** classe. Comme il est possible que les exceptions puissent être mises en attente (sérialisées et stockées dans la base de données), elles doivent implémenter un constructeur de désérialisation. Un constructeur de désérialisation est un constructeur qui accepte deux arguments : un objet SerializationInfo et un objet StreamingContext. Le constructeur de désérialisation est utilisé lors de la réactivation de l'exception. Étant donné que la **ApplicationException** classe implémente déjà un constructeur de désérialisation, le constructeur de l’exception personnalisée appelle simplement le constructeur de désérialisation base (ApplicationException). Par exemple, le **InterruptException** inclut le constructeur suivant :  
  
```  
// "info" is the object holding the serialized object data.  
// "context" is the contextual information about the source  
// or destination.  
public InterruptException(SerializationInfo info,  
                  StreamingContext context) : base(info, context) { }  
```  
  
 Pour plus d'informations sur la sérialisation personnalisée, consultez la rubrique Sérialisation personnalisée dans le Guide du développeur [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)].  
  
## <a name="nested-exception-handlers-and-compensation-blocks"></a>Gestionnaires d'exceptions imbriqués et blocs de compensation  
 Outre leur utilisation comme exceptions spécialisées, les exceptions personnalisées servent également d'indicateur de tri à plusieurs emplacements. Dans le **modification** orchestration, il existe deux emplacements que l’opération d’annulation doit être restaurée.  
  
> [!NOTE]
>  Vous pouvez souhaiter lire cette section avec les **modification** orchestration ouvrir dans Visual Studio.  
  
 En haut de l’orchestration, si l’appel à la **Annuler** orchestration échoue, le **CancelCompensation** bloc s’exécute et annule le **Annuler** transaction. Si tout se passe bien, l’orchestration appelle ensuite la **activer** orchestration.  
  
 Si le **activer** opération échoue, le **Annuler** transaction doit également être annulée. Toutefois, le Gestionnaire d’exceptions pour l’appel à **activer** ne sait rien sur le **Annuler** transaction. Afin de gérer ce genre de situation, un gestionnaire d'exceptions est disponible pour l'intégralité de l'orchestration. Ce gestionnaire, car il contient le **Annuler** étendue, il connaît la **Annuler** transaction. Intercepte l’exception levée à partir de la **activer** étendue (le **ActivateException**), restaure les **Annuler** transaction, puis lève à nouveau l’exception Pour que l’orchestration qui a appelé le **modification** orchestration peut effectuer un traitement supplémentaire.  
  
 Notez que cette conception compense uniquement le **Annuler** si le **activer** échoue. Si le **Annuler** échoue et lève une exception, le **Annuler** jamais a eu lieu et ne doit pas être compensé.  
  
 Pour plus d’informations sur les blocs de compensation et la **compenser** mettre en forme, consultez [comment configurer la forme compenser](../core/how-to-configure-the-compensate-shape.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions dans la Solution gestion des processus d’entreprise](../core/exception-handling-in-the-business-process-management-solution.md)   
 [L’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md)