---
title: "L’échange comportait une erreur structurelle-avant le premier groupe fonctionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ab490de214f53e85ea32c1b243456f837c72e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-a-structural-error-in-before-the-first-functional-group"></a>L’échange comportait une erreur structurelle-avant le premier groupe fonctionnel
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12InterchangeStructuralErrorBefore1stGroup|  
|Texte du message|L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle dans/avant le premier groupe fonctionnel|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, pour l'une des raisons suivantes :  
  
-   Une erreur structurelle s'est produite dans les segments ISA et IEA ou dans le premier groupe fonctionnel de l'échange, de sorte que ce dernier n'était plus conforme au schéma applicable.  
  
-   Le X12ServiceSchema (dans BaseArtifacts.dll) n'était pas déployé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Demandez à l'expéditeur de l'échange de modifier les segments ISA et/ou IEA ou le premier groupe fonctionnel de sorte qu'il soit conforme au schéma applicable, puis renvoyez l'échange.  
  
-   Assurez-vous que le fichier BaseArtifacts.dll inclut le X12ServiceSchema et que ce dernier est déployé. Pour ce faire, ouvrez la console Administration de BizTalk Server, puis le nœud Application BizTalk EDI et le nœud Schémas, en vérifiant que X12ServiceSchema est répertorié.