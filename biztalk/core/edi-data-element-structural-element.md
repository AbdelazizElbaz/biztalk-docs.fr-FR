---
title: "Élément structurel d’élément données EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 775e8b87-b952-46d2-a506-5174d216a9aa
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600edb30ff157a520ac67eebce58428a62e27c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-data-element-structural-element"></a>Élément structurel d'un élément de données EDI
L'élément de données constitue l'unité principale des données d'un message. Les éléments de données sont séparés par un séparateur d'éléments de données, représenté par un astérisque dans un message X12 et par un signe plus dans un message EDIFACT. Le caractère facultatif des éléments de données est défini sur trois niveaux : obligatoire, facultatif ou conditionnel.  
  
 Un élément de données peut être soit simple soit composite : les éléments de données simples sont des éléments numériques correspondant au plus petit niveau de données ; les éléments de données composites constituent des concaténations de sous-éléments, c'est-à-dire des éléments de données simples séparés par des séparateurs de composants. Par défaut, le séparateur de composants est représenté par le signe deux-points pour les normes X12 et EDIFACT.  
  
 Dans le cas des messages EDIFACT, si les données à envoyer via EDI nécessitent l'envoi de caractères définis comme étant des séparateurs, vous devez utiliser un caractère d'échappement pour signaler que l'élément suivant n'est pas un séparateur mais bien une partie des données. Par défaut, le caractère d'échappement est le point d'interrogation (?).  
  
> [!NOTE]
>  La norme X12 ne prend pas en charge le caractère d'échappement. Lorsqu'un séparateur est rencontré dans les données d'un échange X12, au niveau de l'envoi ou de la réception, ce dernier est interrompu.