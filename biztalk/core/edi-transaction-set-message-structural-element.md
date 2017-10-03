---
title: "Élément structurel d’un Message à l’ensemble de transactions EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caea8408-c09c-4525-a9c9-18abe4432594
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d49288e9a311c9766e61fe985b9e279a8660f4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-transaction-set-message-structural-element"></a>Élément structurel d’un Message à l’ensemble de transactions EDI
Le document informatisé (dans le codage X12) ou le message (dans le codage EDIFACT) contient des segments qui constituent les données de message. Le document informatisé est constitué d'un en-tête, d'un ensemble de segments de données et d'un code de fin. Toutes les informations nécessaires pour traiter la transaction sont disponibles au sein du document informatisé.  
  
 Un document informatisé doit commencer par un en-tête de document informatisé ST (dans X12) ou un en-tête de message UNH (dans EDIFACT). Il doit se terminer par un code de fin de document informatisé SE (dans X12) ou un code de fin de message UNT (dans EDIFACT). Le code de fin indique le nombre de segments de données qui inclut les segments d'en-tête et de code de fin.  
  
 Un document informatisé peut contenir une ou plusieurs boucles, qui sont requises pour répéter un ensemble de segments associés.