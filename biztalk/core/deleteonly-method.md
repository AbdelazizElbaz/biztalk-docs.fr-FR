---
title: "Méthode DeleteOnly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DeleteOnly method
ms.assetid: 99e1d7af-1450-439b-882f-de677e593bee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3982c67b4c2eb572a57a4ad602b1d302f9b53ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deleteonly-method"></a>Méthode DeleteOnly
Permet de supprimer des éléments dans un regroupement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DeleteOnly(key1, key2, ..., keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre| Description|  
|---------------|-----------------|  
|`key`|Constitue un ensemble de paramètres qui doit être fourni. Ce jeu de clés doit exister dans la base de données du serveur, sans quoi une erreur survient. Ces clés correspondent au jeu de clés Get défini pour l'interface de composant spécifique.|  
|`correctionMode`|Indicateur booléen. Lorsque ce paramètre est défini sur true, il permet la suppression d'éléments ayant une date d'effet passée dans une collection. Plus précisément, il permet de supprimer des éléments dont l'EFFDT est antérieure à la date d'effet actuelle. Sans cet indicateur défini sur TRUE, toute modification apportée à ces éléments génère une erreur renvoyée par le serveur PeopleSoft. **Remarque :** le `correctionMode` argument est uniquement exposé pour ces interfaces de composant qui contiennent des éléments d’effet. Sinon, il n’est pas affiché dans le cadre de l’argument.|  
|`interactiveMode`|Utilisé pour la gestion des erreurs.<br /><br /> Lorsqu'il accède aux propriétés dans une interface de composant, l'adaptateur BizTalk pour PeopleSoft Enterprise utilise les API fournies par PeopleSoft qui lisent et écrivent des champs individuels dans l'interface de composant. Cependant, ces modifications ne sont pas propagées au serveur PeopleSoft les unes après les autres. Au lieu de cela, psjoa.jar (avec lequel l’adaptateur BizTalk pour PeopleSoft Enterprise interagit) regroupe toutes les modifications et envoie les modifications au serveur dans un seul package. En cas d'échec d'une des mises à jour individuelles, une erreur générique est renvoyée, sans identifier l'erreur réelle. Si le mode interactif est défini sur TRUE, chaque mise à jour de champ est envoyée au serveur individuellement. Cela a un impact considérable sur les performances mais des informations spécifiques sur l'erreur sont fournies en cas d'échec de la mise à jour (par exemple, si une valeur non valide est utilisée pour la définition d'un champ).<br /><br /> Le paramètre `interactiveMode` offre des performances optimales et fournit des rapports d'erreurs au niveau de la mise à jour du champ. Pour utiliser correctement cette fonctionnalité, il est recommandé d'effectuer des appels normaux avec `interactiveMode` défini sur FALSE. Cela ne doit avoir aucun impact sur les performances. Si une erreur est renvoyée, le même appel peut faire l'objet d'une nouvelle tentative avec l'indicateur interactiveMode défini sur TRUE. Lorsque l'appel échoue, le serveur renvoie un message d'erreur plus précis.|  
|`properties`|Contient un sous-ensemble de la structure existant sur le serveur. Tous les éléments terminaux sont supprimés.|  
  
## <a name="remarks"></a>Notes  
 Les propriétés possèdent le même type de données que celui de la méthode `CreateEx` ou `UpdateEx` de cette interface de composant. Toutefois, seules les valeurs des clés sont importantes. Les autres valeurs sont ignorées. Les valeurs des clés doivent correspondre à celles se trouvant sur le serveur. Dans le cas contraire, une exception est générée.  
  
 Ce qui suit présente l'utilisation des valeurs des clés. Une collection contient les éléments suivants :  
  
-   item0  
  
-   item1  
  
-   item2  
  
-   item3  
  
 Vous pouvez supprimer item1 et item3 en fournissant les clés qui leur sont associées dans les propriétés :  
  
-   item1  
  
-   item3  
  
 Après l'appel, le serveur dispose des éléments restants suivants dans la collection :  
  
-   item0  
  
-   item2  
  
 Le deuxième exemple affiche les éléments contenant d'autres collections :  
  
-   item0  
  
    -   item0a  
  
-   item1  
  
    -   item1a  
  
    -   item1b  
  
    -   item1c  
  
-   item2  
  
    -   item2a  
  
    -   item2b  
  
 Vous pouvez supprimer item1b ainsi que tous les éléments item2 en fournissant les clés qui leur sont associées :  
  
-   item1  
  
    -   item1b  
  
-   item2  
  
 En fournissant une sous-collection vide pour item2, vous le transformez en élément terminal et toute cette sous-branche est supprimée. Après l'appel, le serveur dispose des éléments restants suivants :  
  
-   item0  
  
    -   item0a  
  
-   item1  
  
    -   item1a  
  
    -   item1c  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)