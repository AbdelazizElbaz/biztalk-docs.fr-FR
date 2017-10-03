---
title: "Ajout d’un Port d’envoi MX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3ad5d2f-1fcb-49d4-9974-664733308f45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cd4c16658ad0ff6b85976fbc6a97c4f397acbdb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-an-mx-send-port"></a>Ajout d’un Port d’envoi de MX
**Pour ajouter un port d’envoi MX :**  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi dans la zone Nom du type **MX_SendPort**.  
  
3.  Dans la section de Transport, dans la zone Type, cliquez sur la liste déroulante et sélectionnez **fichier**.  
  
4.  Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
5.  Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.  
  
6.  Dans le dossier boîte de dialogue Rechercher, sélectionnez un emplacement de fichier.  
  
7.  Dans la zone Nom de fichier, tapez **%MessageID%.xml**, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de Port d’envoi, cliquez sur la liste déroulante de la zone de pipeline d’envoi, puis sélectionnez le pipeline d’envoi que vous avez déployé dans le projet de pipeline.  
  
9. Dans le volet gauche, cliquez sur **filtres**, puis spécifiez les éléments suivants :  
  
    |||  
    |-|-|  
    |Propriété|Microsoft.Solutions.MX_A4SWIFT. Property.MX_A4SWIFT_Failed|  
    |Opérateur|Sélectionnez ==|  
    |Valeur|False|  
  
10. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
11. Dans le volet Ports d’envoi, cliquez sur **MX_SendPort**, puis cliquez sur **Démarrer**.