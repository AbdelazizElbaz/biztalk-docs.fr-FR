---
title: Comment configurer la forme lever Exception | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Throw Exception shape [Orchestration Designer]
- orchestrations, errors
- Orchestration Designer, errors
ms.assetid: d3190f1b-db5e-4988-bff6-f7a276760ece
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07d156572484ba4fbe71533252ce4fe956136699
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-throw-exception-shape"></a>Configuration de la forme Lever exception
Vous pouvez lever explicitement des exceptions dans une orchestration à l’aide de la **lever Exception** forme. Lorsqu'une exception est levée, le moteur d'exécution recherche le gestionnaire d'exceptions le plus proche, capable de traiter le type d'exception concerné.  
  
 En premier lieu, une étendue intégrée est recherchée dans l'orchestration active, puis les gestionnaires d'exception associés à l'étendue sont pris en compte pour la localisation du gestionnaire approprié au type d'exception levée.  
  
 Si aucun gestionnaire d'exceptions n'est trouvé, l'étendue qui comprend le point d'appel de l'orchestration active est recherchée dans l'orchestration qui a appelé l'orchestration active. Cette recherche se poursuit jusqu'à ce qu'un gestionnaire d'exceptions capable de gérer l'exception soit trouvé.  
  
 La correspondance exacte d'une exception est une classe d'exception qui est la même, ou une classe de base, que le type d'exécution de l'exception levée.  
  
 Une fois le gestionnaire d'exceptions trouvé, le contrôle est transféré à la première instruction de ce gestionnaire.  
  
 Si aucun gestionnaire d'exceptions n'est trouvé, l'orchestration s'arrête. Les transactions peuvent vous aider à limiter l'impact d'un tel événement.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-configure-a-throw-exception-shape"></a>Pour configurer une forme Lever exception  
  
-   Dans la fenêtre Propriétés, sélectionnez un type d’objet disponible à lever à partir de la **objet Exception** liste déroulante.  
  
    > [!NOTE]
    >  Sélectionnez Exception générale dans le **lever Exception** uniquement si de forme le **lever Exception** forme se trouve dans un gestionnaire d’exceptions et que vous souhaitez lever l’exception interceptée dans le Gestionnaire d’exceptions en cours à. Vous recevez une erreur pendant la compilation si vous utilisez une Exception générale pour une **lever Exception** forme dans un autre contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Exceptions](../core/exceptions.md)