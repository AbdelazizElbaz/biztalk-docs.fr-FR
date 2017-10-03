---
title: Texte SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SWIFT, text
ms.assetid: 90851d38-7789-4b1b-813b-7943f77ab984
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80d8ee0343cbf8ac96d57119ef198d623159b26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-text"></a>Texte SWIFT
Le texte du message constitue la charge utile du message (FIN) financier et contient tous les champs de données à l’exception des champs contenant l’expéditeur, le récepteur et le type de message. Ces trois champs sont contenus dans l’en-tête. Certains messages contiennent également un en-tête utilisateur facultatif, qui peuvent également fournir des informations de traitement.  
  
 Chaque charge de message FIN se compose d’une série de champs dans un ordre défini. Ces champs sont conformes aux règles suivantes :  
  
-   Les champs peuvent être obligatoires ou facultatifs dans la séquence.  
  
-   Une séquence peut contenir sous-séquences, et une sous-séquence peut se répètent dans une séquence.  
  
-   Vous pouvez utiliser un champ dans plusieurs types de messages.  
  
-   Un champ peut comporter des éléments ou sous-champs. Un élément ou un sous-champ peut-être être commune à plusieurs champs.  
  
-   Chaque séquence répétitive est représentée par un nœud de groupe.  
  
-   Chaque champ peut lui-même avoir plusieurs noeuds niveaux, chacune décrite comme un enregistrement.  
  
-   Un élément de schéma représente le sous-champ de niveau le plus bas.  
  
-   Courantes des enregistrements et des éléments sont définis dans le schéma commun et de base, comme décrit ci-dessous.  
  
-   Certains champs peuvent être représentés dans plusieurs formats (tels que les champs de tiers). Ces champs sont définis en tant que champs de choix dans le schéma.  
  
 Certains champs ont limité des ensembles de valeurs. La plupart des cas, le schéma répertorie ces valeurs. Définitions de schéma également incluent la validation de jeu de caractères.