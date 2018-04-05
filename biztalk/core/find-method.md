---
title: Find (méthode) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Find method
ms.assetid: 676827a6-82af-4922-bf9e-aca5bd23624b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5432c68c36dcf8e769351af6d57f3cd3ed712b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="find-method"></a>Find (méthode)
Utilisé pour renvoyer la liste des clés qui correspondent aux clés partielles fournies. Notez que pour une interface de composant qui n'inclut qu'une instance (sans clé), la fonction `Find()` n'est pas générée. Voir aussi [Get (méthode)](../core/get-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Find (partialKey, keyList)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre| Description|  
|---------------|-----------------|  
|`partialKey`|Structure dans laquelle les clés individuelles sont facultatives.|  
|`keyList`|Liste de clés qui correspond au paramètre `partialKey`. Il est un paramètre de sortie.<br /><br /> Les clés correspondent au jeu de clés Find défini pour l'interface de composant spécifique.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous spécifiez les clés partielles, il est possible d'utiliser la recherche par caractères génériques disponible via la fonction `Find()` interne de PeopleSoft. Par exemple, la valeur de clé partielle ACCOUNT « 11 » renvoie toutes les clés ACCOUNT commençant par « 11 », tandis que la valeur « %40 » renvoie toutes les clés ACCOUNT contenant la valeur « 40 ». Une clé partielle « _4_4 » renvoie toutes les clés ACCOUNT incluant le caractère « 4 » en deuxième et quatrième position.  
  
 Remarque : Avec l’implémentation actuelle du serveur PeopleSoft, si plus de 300 éléments correspondent aux critères de recherche, l’appel échoue. Il s'agit d'une restriction du serveur PeopleSoft. La méthode de l'adaptateur BizTalk pour PeopleSoft Enterprise `Find()` est fournie si la fonction `Find` de PeopleSoft est activée dans l'interface de composant et si les clés Get sont disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)