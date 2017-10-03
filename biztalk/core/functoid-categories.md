---
title: "Catégories de fonctoids | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 029905e2-f01a-436a-b2ed-a364379c9cc5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89db4168af133e616f48ded54cce98cd54bb8ec8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="functoid-categories"></a>Catégories de fonctoids
Les fonctoids BizTalk sont répartis en catégories en fonction de l’utilisation qui en est prévue. Par exemple, les fonctoids de base de données sont conçus pour permettre l'extraction des données d'une base de données au moment de l'exécution, les fonctoids mathématiques sont utilisés pour la réalisation d'opérations mathématiques, et ainsi de suite. Dans le Mappeur BizTalk, les fonctoids s’affichent par catégories dans la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. 

## <a name="categories--description"></a>Catégories & description
Le tableau suivant présente les catégories de fonctoids, propose une brève description de la catégorie et dresse la liste des fonctoids figurant dans chaque catégorie. Les liens vers leurs pages de référence sont également indiqués.  
  
|Catégorie de fonctoids <br/><br/> Description de la catégorie|Fonctoids figurant dans la catégorie|  
|---|---|  
|**Avancé** <br /><br /> Principalement utilisé avec des enregistrements de boucle. Également utilisé pour l’exécution de script arbitraire ou de code compilé.|Assert, Index, itération, bouclage, copie de masse, la valeur Nil, nombre d’enregistrements, scripts, extracteur de Table, Table de bouclage, valeur de mappage, le mappage (mise à plat)|  
|**Conversion** <br /><br /> Utilisé pour la conversion depuis et vers le format ASCII et entre les bases numériques.|ASCII vers caractère, de caractères ASCII, hexadécimal, Octal|  
|**Cumulative** <br /><br /> Utilisé pour effectuer des opérations mathématiques dans des enregistrements de boucle, telles que des moyennes et des concaténations.|Cumulative moyenne, Cumulative concaténer, Minimum cumulé de Maximum, cumulé, somme cumulée|  
|**Base de données** <br /><br /> Utilisé pour extraire des données d’une base de données et les utiliser dans des messages de l’instance de destination.|Message de retour d’erreur, la recherche, au Format de base de données, obtenir l’ID de l’Application, obtenir la valeur de l’Application, obtenir l’ID courant, obtenir la valeur courante, de supprimer l’ID de l’Application, définir l’ID courant, extracteur de valeur|  
|**Date et heure** <br /><br /> Utilisé pour obtenir la date et l’heure actuelles et calculer les différences de temps.|Ajouter des jours, Date, Date et heure, temps|  
|**Logiques** <br /><br /> Utilisé pour effectuer un ensemble d’opérations logiques telles que Supérieur à et Existence logique.|Égal à, supérieur à, supérieur ou égal à, IsNil, inférieur à, inférieur ou égal à, AND logique, Date logique, Existence logique, logique numérique, logique pas, ou logique, chaîne logique, différent de|  
|**Mathématiques** <br /><br /> Utilisé pour effectuer un ensemble d’opérations mathématiques telles que l'addition et la multiplication.|Valeur absolue, Addition, Division, entier, valeur maximale, valeur minimale, Modulo, Multiplication, Round, racine carrée, soustraction|  
|**Scientifique** <br /><br /> Utilisé pour effectuer un ensemble d’opérations scientifiques telles que des logarithmes et de la trigonométrie.|10 ^ n, Arc tangente, logarithme de Base spécifiée, le logarithme, cosinus, fonction exponentielle naturelle, logarithme naturel, sinus, tangente, X ^ Y|  
|**Chaîne** <br /><br /> Utilisé pour effectuer un ensemble de fonctions de chaîne, telles que la suppression et la concaténation.|Minuscules, de taille, concaténation de chaînes, chaîne chaîne d’extraction, la recherche de chaîne, gauche, supprimer à gauche de la chaîne, chaîne de droite, chaîne supprimer à droite, en majuscules|  
  
> [!NOTE]
>  La fonction d'un fonctoid est généralement indiquée par son nom.  
  
> [!NOTE]
>  Tous les fonctoids inclus dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont inline c#, à l’exception de la **base de données** fonctoids.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoids de base](../core/basic-functoids.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)