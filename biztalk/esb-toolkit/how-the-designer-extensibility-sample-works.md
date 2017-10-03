---
title: "Fonctionne de l’exemple de l’extensibilité du Concepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f4dc622-28b8-498d-961f-df969cff9dcb
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74b72be8acb8fed465598814d2f76b32c6e3550d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-designer-extensibility-sample-works"></a>Fonctionne de l’exemple de l’extensibilité du Concepteur
Chaque projet dans l’exemple de l’extensibilité du concepteur contient deux classes : une **extendeur** classe et un **fournisseur d’extensions** classe. Ces classes sont conçues pour étendre les fonctionnalités et définir les propriétés de la **ItineraryDsl** éléments de modèle.  
  
 Le **fournisseur d’extensions** classes dérivées de la **ExtensionProviderBase** classe et avez le **ExtensionProviderAttribute** appliquée avec des propriétés qui identifier l’extension et son objectif. Ces valeurs seront affichées à l’utilisateur dans le concepteur lorsque l’utilisateur le **extendeur** propriété sur un élément de modèle. Lorsque le **fournisseur d’extensions** initialiser des classes, appelez le constructeur du **ExtensionProviderBase** et lui passer le type de la classe d’extendeur.  
  
 Le **extendeur** classes ont un **ObjectExtender** attribut appliqué leur ; pour le **ObjectExtender** attribut, elles passent le type de l’objet dans le  **ItineraryDsl** qu’ils étendent. La classe de base pour ces classes varie selon le type d’extension. Pour les extensions de programme de résolution, la classe de base est **ObjectExtender\<résolveur >**. Pour les extensions de Service de l’itinéraire, la classe de base est **ItineraryServiceExtenderBase**. Dans le **extendeur** classes, les attributs suivants sont appliqués aux propriétés : attributs nécessaires pour un affichage correct dans une grille des propriétés, les attributs inclus dans la bibliothèque d’entreprise Microsoft à des fins de validation, attributs nécessaires pour une sérialisation appropriée, et/ou des attributs qui déterminent la façon dont les propriétés sont conservées.  
  
 Lorsque ces assemblys sont compilés et placés dans le dossier Lib, ils sont chargés et mis en cache par le concepteur au moment de l’exécution. Extendeurs sont si nécessaire, le **ItineraryDsl** utilise la réflexion pour charger des assemblys applicables à partir du cache en examinant les types exportés et les attributs sur ces types.