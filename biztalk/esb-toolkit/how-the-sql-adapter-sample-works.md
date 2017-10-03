---
title: "Fonctionne de l’exemple d’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77811152-cc8e-4090-89eb-e3a402a46e5e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ff56f2f2f88d35290ffd897d107910e206ac98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-sql-adapter-sample-works"></a>Fonctionne de l’exemple d’adaptateur SQL
L’exemple d’adaptateur SQL fournit un itinéraire bidirectionnelle exemple configuré avec le service de routage et d’un service de messagerie de transformation.  
  
 Le service de routage est configuré avec un programme de résolution statique, qui spécifie que le message doit être routé pour exécuter une procédure stockée SQL dans la base de données GlobalBankESB nommé InsertProduct à l’aide du fournisseur de l’adaptateur WCF-Custom.  
  
 Le service de transformation spécifie un mappage qui convertit le message entrant au format accepté par la procédure stockée de InsertProduct.