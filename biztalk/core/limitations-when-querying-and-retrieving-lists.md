---
title: "Limitations lors de l’interrogation et la récupération de listes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, querying limitations
- querying, limitations [JD Edwards OneWorld adapters]
ms.assetid: 1b6f5d2a-d1e2-4c78-8f4a-f00d10f008b9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f2e0f813a793aa05756ef52925081375203f2f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-when-querying-and-retrieving-lists"></a>Limitations lors de la requête et de l'extraction de listes
L'architecture de communication de JD Edwards OneWorld est une architecture à message unique et à réponse unique. Il est impossible de renvoyer une liste de messages ou un tableau. Le code sous-jacent est C++, lequel permet d'effectuer un appel vers une structure unique à l'aide d'un pointeur, de la modifier puis de quitter.  
  
## <a name="querying-and-retrieving-lists"></a>Requête et extraction de listes  
 Sur la base de critères spécifiés, il est impossible de rechercher et de récupérer des listes d'enregistrements à l'aide de l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld en raison d'une limitation rencontrée avec l'architecture de la fonction commerciale de JD Edwards OneWorld.  
  
 Dans JD Edwards OneWorld, la connexion à la base de données s'effectue via l'utilisation d'un ensemble d'appels propriétaires (et complexes) de la fonction interne. Ceux-ci masquent la version de la base de données sous-jacente en exigeant que des appels explicites de bas niveau créent successivement des listes de colonnes à extraire ou à mettre à jour et des structures de tri et de sélection spécialisées. Les ensembles d'API ne sont pas exposés via la méthode de connectivité Java (ou toute autre) ; il est donc impossible de traiter des jeux d'enregistrements par l'intermédiaire des fonctions commerciales.  
  
 Grâce au jeu d'outils de JD Edwards OneWorld, vous pouvez créer des fonctions commerciales qui permettent de traiter un seul enregistrement ou d'exécuter des opérations sur un groupe d'enregistrements ; en revanche, il est plus difficile d'accéder à des listes d'éléments en dehors de celles des outils de JD Edwards OneWorld.  
  
 Pour contourner ce problème, vous pouvez créer une fonction commerciale personnalisée renvoyant une liste de clés d'enregistrement suite à une requête. Vous devez segmenter les listes, car JDENET (l'API de messagerie propriétaire interne de JD Edwards OneWorld) est limité au niveau de la taille du tampon d'un message pour la gestion des jeux de résultats volumineux ou non liés. Le code client doit effectuer des itérations (boucles) au moyen de plusieurs appels successifs vers la fonction commerciale jusqu'à ce qu'un indicateur attestant de l'achèvement de la liste soit renvoyé.  
  
## <a name="controlling-iteration"></a>Contrôle de l'itération  
 Les appels vers les fonctions commerciales de JD Edwards OneWorld sont sans état ; aussi, il est impossible que la fonction commerciale conserve un curseur ouvert et renvoie un nombre de lignes supérieur lors d'une requête. Les informations de positionnement doivent être transmises à la fonction commerciale de JD Edwards OneWorld XE lors de chaque appel.  
  
 Voici une liste des techniques permettant de contrôler l'itération :  
  
-   Dans JD Edwards OneWorld, inscrivez le jeu de résultats sur un fichier de stockage temporaire, ce qui a pour effet de renvoyer un ID (tel qu'un nom de fichier ou le numéro d'une tâche) pouvant être communiqué au cours de plusieurs appels successifs, conjointement avec le numéro d'enregistrement permettant de positionner le curseur. Les appels successifs sont positionnés dans la liste en fonction des numéros d'enregistrement transmis.  
  
    > [!NOTE]
    >  La charge des appels effectués via l'adaptateur BizTalk pour JD Edwards OneWorld peut être équilibrée ; toutefois, le service des appels est généralement pris en charge par un serveur d'applications unique selon les informations d'identification et la fonction commerciale appelée. Aussi, si un appel entraîne la création d'un fichier temporaire sur un serveur, les appels suivants seront pris en charge par ce dernier. Pour plus d'informations, consultez la section relative au mappage de la configuration de l'objet dans les guides CNC de JD Edwards OneWorld.  
  
-   Les informations de positionnement (telles qu'une valeur de clé primaire) peuvent être retournées par l'intermédiaire du second appel ou des appels suivants ; la requête peut être renvoyée sur la base de la clé en tant que paramètre supplémentaire. Cette méthode est employée dans le code de navigation du référentiel de l'adaptateur BizTalk pour JD Edwards OneWorld.  
  
    > [!NOTE]
    >  Parmi les deux premières techniques, il est recommandé d'utiliser les valeurs de clé primaire et de renvoyer la requête. Cette méthode est celle qui exige le moins de code et qui permet de transférer la charge de mise en cache et d'optimisation sur la base de données.  
  
-   L'application appelante peut stocker une liste de clés primaires (telle qu'une référence croisée). Par exemple, lorsqu'un système de gestion de la relation client (CRM) crée un enregistrement client puis l'ajoute à JD Edwards OneWorld via un appel de fonction commerciale, la fonction commerciale qui permet de l'ajouter définit la valeur du champ AN8 (numéro d'adresse courte) et apparaît dans la zone tampon de retour. Ce numéro peut ensuite être écrit dans un champ de référence au sein de l'enregistrement personnalisé d'origine ou il peut également être stocké dans une table de références croisées personnalisée.  
  
-   La plupart des enregistrements principaux de JD Edwards OneWorld possèdent un concept de recherche ou une clé secondaire. Cette clé peut servir à stocker les informations essentielles sur le système appelant. Les fonctions commerciales peuvent effectuer la recherche au niveau de JD Edwards OneWorld. Lorsque les paramètres sont transmis à la fonction commerciale afin de créer un enregistrement client, la valeur de clé longue est définie.  
  
 Pour plus d'informations sur ces concepts, consultez la rubrique Interopérabilité dans le système d'aide de JD Edwards OneWorld.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification et Architecture](../core/planning-and-architecture17.md)