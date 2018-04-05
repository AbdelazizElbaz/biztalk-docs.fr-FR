---
title: Méthode UpdateEx | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UpdateEx method
ms.assetid: 2fa9c9cc-fd01-4765-8c31-facac188a19d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a6a64c6709eb9806612518c551372ba45d1a454
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updateex-method"></a>Méthode UpdateEx
Utilisé pour mettre à jour les propriétés basées sur les paramètres de clé d’entrée (key1, key2... keyn). Lors de l'utilisation d'`UpdateEx`, vous ne pouvez pas supprimer d'éléments d'une collection. Une méthode distincte facilite la suppression. Pour plus d’informations, consultez [méthode DeleteOnly](../core/deleteonly-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
UpdateEx (key1, key2, ... keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre| Description|  
|---------------|-----------------|  
|`key`|Un ensemble de paramètres qui doit exister dans la base de données du serveur ou une erreur se produit. Ces clés correspondent au jeu de clés Get défini pour l'interface de composant spécifique.|  
|`correctionMode`|Indicateur booléen. Lorsqu'il est défini sur true, il permet d'apporter des modifications aux interfaces de composant avec des éléments ayant une date d'effet, soit en mettant à jour les valeurs de champ soit en insérant de nouveaux éléments dans une collection. Plus précisément, il permet de modifier les éléments dont l'EFFDT est antérieure à la date d'effet actuelle. Sans cet indicateur défini sur TRUE, toute modification apportée à ces éléments génère une erreur renvoyée par le serveur PeopleSoft.<br /><br /> L'argument `correctionMode` est uniquement exposé pour ces interfaces de composant qui contiennent des éléments ayant une date d'effet. Dans le cas contraire, il n'apparaît pas dans le cadre de l'argument.<br /><br /> Vous devez éviter de définir `correctionMode` sur True dans un environnement de production. (Il s'agit également de la recommandation de PeopleSoft.) Les événements qui se sont déjà produits, tels que déterminés par la clé EFFDT passée, ne doivent pas être modifiés. Cela permet la création d'une piste d'audit. L'indicateur `correctionMode` dans `UpdateEx` permet le contournement de ce mécanisme de sécurité. Pour les événements passés, la pratique recommandée consiste à les désactiver en définissant un champ dans l'élément et en ajoutant l'élément mis à jour (au lieu de le supprimer).|  
|`interactiveMode`|Indicateur utilisé pour la gestion des erreurs.<br /><br /> Lors de l’accès aux propriétés dans une interface de composant, l’adaptateur BizTalk pour PeopleSoft Enterprise utilise les API fournies par PeopleSoft qui lisent et écrivent des champs individuels dans l’interface de composant ; Toutefois, ces modifications ne sont pas propagées au serveur PeopleSoft une à la fois. Au contraire, psjoa.jar (avec lequel l'adaptateur BizTalk pour PeopleSoft Enterprise interagit) regroupe toutes les modifications et les envoie au serveur dans un seul package. En cas d'échec d'une des mises à jour individuelles, une erreur générique est renvoyée, sans identifier l'erreur réelle. Si le mode interactif est défini sur TRUE, chaque mise à jour de champ est envoyée au serveur individuellement. Cela a un impact considérable sur les performances mais des informations spécifiques sur l'erreur sont fournies en cas d'échec de la mise à jour (par exemple, si une valeur non valide est utilisée pour la définition d'un champ).<br /><br /> `interactiveMode` offre des performances optimales et fournit des rapports d'erreurs au niveau de la mise à jour du champ. Pour utiliser correctement cette fonctionnalité, il est recommandé d'effectuer des appels normaux avec `interactiveMode` défini sur FALSE. Cela ne doit avoir aucun impact sur les performances. Si une erreur est renvoyée, le même appel peut faire l'objet d'une nouvelle tentative avec l'indicateur `interactiveMode` défini sur True. Lorsque l'appel échoue, le serveur renvoie un message d'erreur plus précis.|  
  
### <a name="remarks"></a>Notes  
 Lorsque vous appelez cette fonction, les propriétés de l'enregistrement correspondant aux clés sont remplacées par les propriétés du paramètre d'entrée. Toutes les collections comprenant les enregistrements originaux sont supprimées et remplacées par celles du paramètre d'entrée. Les tailles de ces collections ne doivent pas correspondre car la procédure dans `UpdateEx` consiste à supprimer tous les éléments de collection existants et de les insérer dans les collections données.  
  
 Si les propriétés de l'interface de composant contiennent des éléments ayant une date d'effet, le paramètre des propriétés doit contenir tous les éléments ayant une date d'effet future car la liste d'origine est remplacée. Cela fournit le mécanisme d'ajout et de suppression des éléments ayant une date d'effet future. Cependant, si les propriétés contiennent aussi des éléments ayant une date d'effet passée, une erreur est renvoyée car de tels éléments ne peuvent pas être modifiés. Si l'élément ayant une date d'effet actuelle est également inclus, il est ignoré. Cela permet au client d’appeler `Get()` avec la `getHistoryItems` paramètre la valeur False et modifier les éléments à date d’effet futures ou ajouter de nouveaux éléments à date d’effet futures et transmettre la structure en tant que paramètre pour le `UpdateEx()` (fonction).  
  
 Si l’interface de composant n’a pas de clé, comme dans le cas où une seule instance peut exister, le `UpdateEx()` méthode présente sous la forme :  
  
```  
UpdateEx(correctionMode, interactiveMode, properties)  
```  
  
> [!NOTE]
>  La méthode de l'adaptateur BizTalk pour PeopleSoft Enterprise `UpdateEx()` est fournie si les fonctions `Get` et `Save` de PeopleSoft sont activées dans l'interface de composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)