---
title: Redéclarer | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Assert function [Business Rules Engine]
ms.assetid: 9cd640a2-bfeb-4c7a-b737-1c92cc122a9c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22fcc8be7760d85a12cb05c53137177703c0fa73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reassert"></a>Reassert
Pour *redéclarer* signifie appeler le **Assert** fonction sur un objet qui existe déjà dans le moteur de mémoire de travail. Une commande de redéclaration équivaut à émettre une commande Rétracter pour l'objet, suivie d'une commande Déclarer.  
  
## <a name="net-objects"></a>Objets .NET  
 L'objet est d'abord rétracté et toutes les actions sur l'agenda pour les règles qui utilisent cet objet (dans un prédicat ou une action) sont supprimées. L'objet est ensuite redéclaré dans la mémoire de travail et évalué comme tout objet nouvellement déclaré. Cela signifie que toutes les règles qui utilisent l'objet dans un prédicat sont réévaluées et que leurs actions sont ajoutées à l'agenda selon les nécessités. Toutes les règles qui auparavant **true** et utilisez uniquement l’objet dans leurs actions verront ces actions rajoutées à l’agenda.  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 Lorsqu’un niveau supérieur **TypedXmlDocument** (**TXD**) est redéclaré, l’enfant **TXD**s qui sont créés lorsque le niveau supérieur **TXD** est initialement assertion ont des comportements différents selon l’état de l’enfant **TXD**s. Dans le cas d’un nouvel enfant nœud ou un nœud enfant qui n’est pas intègre, ce qui signifie qu’au moins un de ses champs a été modifié dans la stratégie à l’aide d’une action de règle, une assertion, ou redéclarez action est effectué sur le nœud enfant. Tout nœud enfant existant dont les champs n'ont pas été modifiés reste dans la mémoire de travail. L'exemple suivant est un scénario simplifié qui décrit le comportement des nœuds enfants quand leur nœud parent est redéclaré.  
  
 Supposons que trois **TXD**s actuellement dans la mémoire de travail : **P**, **C**1, **C**2, et **C**3. **P** est le niveau supérieur **TXD**, le nœud parent ; chaque enfant nœud contient un champ **x**.  
  
 **P**  
  
 **C**1 (**C**1. **x** = 1)  
  
 **C**2 (**C**2. **x** = 1)  
  
 **C**3 (**C**3. **x** = 1)  
  
 Supposez ensuite que les opérations suivantes ont été effectuées suite à une action de règle :  
  
-   Le champ (**x**) pour la valeur **C**2 est mis à jour.  
  
-   **C**3 est supprimé à l’aide de code utilisateur.  
  
-   Un nœud enfant supplémentaire, **D**, est ajouté à **P** à l’aide de code utilisateur.  
  
> [!NOTE]
>  Le moteur des règles d'entreprise ne pourra pas identifier un nœud ayant perdu son intégrité à cause d'opérations que le moteur ne reconnaît pas, comme l'ajout, la suppression ou la modification d'un nœud, par programme, dans une application externe.  
  
 Dans la mémoire de travail, les objets adoptent la nouvelle représentation suivante.  
  
 **P**  
  
 **C**1 (**C**1. **x** = 1)  
  
 **C**2 (**C**2. **x** = *0*)  
  
 **D**  
  
 Maintenant, Redéclarez **P**. Les points suivants résument le comportement des nœuds enfants :  
  
-   Nœud **C**2 est redéclaré, car il a modifié après son champ mis à jour.  
  
-   Nœud **C**3 est rétracté de la mémoire de travail.  
  
-   Nœud **D** est déclaré dans la mémoire de travail.  
  
-   Nœud **C**1 reste dans la mémoire de travail, car il n’a pas mis à jour avant **P** soit redéclaré.  
  
## <a name="typeddatatable"></a>TypedDataTable  
 Si **redéclarer** est émise sur un **TypedDataRow**, cette ligne est rétractée et puis déclarée dans la mémoire de travail. Si **redéclarer** est émise sur le **TypedDataTable**, toutes les **TypedDataRow**sont rétractées, puis déclarées.  
  
## <a name="dataconnection"></a>DataConnection  
 Tous les **TypedDataRow**récupérées via les **DataConnection** sont retirées. Tous les prédicats qui utilisent la **DataConnection** sont ensuite réévalués, à l’origine de la **DataConnection** pour être actualisé pour créer les **TypedDataRow**s.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de contrôle du moteur](../core/engine-control-functions.md)