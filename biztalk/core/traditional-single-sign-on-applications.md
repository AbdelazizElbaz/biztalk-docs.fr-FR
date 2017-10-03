---
title: "Seule l’authentification sur les Applications traditionnelles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a49bdae7-215a-43fb-875e-f64abb37aef0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4396ecfab477fe1ae17b1abbb09ebf71c9bcb58c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="traditional-single-sign-on-applications"></a>Seule l’authentification sur les Applications traditionnelles
L'architecture de programmation de l'authentification unique (SSO) contient un composant de mappage permettant d'effectuer des mappages entre des applications et des utilisateurs, un composant de recherche permettant de rechercher des informations d'identification destinées à une utilisation spécifiée, et un composant d'administration permettant d'effectuer des tâches d'administration. L'authentification unique comporte en outre une interface de tickets permettant à votre application d'émettre et d'échanger des tickets.  
  
## <a name="mapping"></a>Mappage  
 Le mappage est le processus qui consiste à relier un utilisateur spécifié à une application spécifiée. Vous pouvez effectuer des mappages entre des applications associées et des utilisateurs qui utilisent `ISSOMapping`, `ISSOMapper` et `ISSOMapper2`. `ISSOMapping` permet de créer, supprimer, activer et désactiver des mappages. `ISSOMapper` et `ISSOMapper2` permettent d'obtenir et de définir des données de mappage pour l'utilisateur actuel.  
  
## <a name="lookup"></a>Lookup  
 L'intérêt principal de l'interface de programmation de l'authentification unique est la capacité à rechercher les informations d'identification des utilisateurs spécifiés. Vous pouvez rechercher des informations d'identification à l'aide de `ISSOLookup1` et `ISSOLookup2`. `ISSOLookup1`, permet à l'utilisateur de récupérer leurs propres informations d'identification externes. `ISSOLookup2` permet quant à lui de rechercher les informations d'identification d'un utilisateur distant pour une application associée locale. Le premier est nécessaire pour les applications d'authentification unique traditionnelles et le deuxième est utile pour écrire une application d'authentification unique initiée par l'hôte.  
  
## <a name="administration"></a>Administration  
 Vous pouvez exécuter un grand nombre de fonctionnalités d'administration de façon programmée à l'aide de `ISSOAdmin`, `ISSOAdmin2` et `ISSOConfigStore`. Ces tâches incluent la configuration de l'authentification unique ainsi que la création et la description d'une application devant faire l'objet d'une authentification unique. Vous pouvez également créer et modifier des bases de données SSO à l'aide de `ISSOConfigDB`, `ISSOConfigOM` et `ISSOConfigSS`. Enfin, vous pouvez administrer les composants de synchronisation de mot de passe à l'aide de `ISSOPSAdmin`.  
  
## <a name="communication-and-ticketing"></a>Communication et tickets  
 Votre application émettra très probablement des messages de sorte que votre utilisateur puisse communiquer avec une application distante. Pour communiquer avec une application distante de façon plus sécurisée, vous devez émettre et échanger un ticket d'authentification unique. Vous pouvez également émettre et échanger des tickets de façon programmée.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications à authentification uniques](../core/single-sign-on-applications.md)