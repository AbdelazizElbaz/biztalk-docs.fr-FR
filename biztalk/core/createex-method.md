---
title: Méthode CreateEx | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CreateEx method
ms.assetid: b62bbe25-b24d-42a7-a44c-c83521a6f0a6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b163bfbe7811c37208297aa0a61bfe91cabacde4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="createex-method"></a>Méthode CreateEx
Crée un enregistrement à l'aide d'un jeu de clés uniques et des propriétés spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateEx  
(key1, key2, ..., keyn, interactiveMode, properties)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre| Description|  
|---------------|-----------------|  
|`Key in/out parameter`|Paramètres de clé individuelle (key1, key2, ... keyn) devant être fournis.<br /><br /> Ce jeu de clés ne doit pas exister dans la base de données du serveur : ils doivent donc être uniques.<br /><br /> Ces clés correspondent au jeu de clés CreateEx défini pour l'interface de composant spécifique.|  
|`interactiveMode`|Gestion des erreurs.<br /><br /> Lorsqu'il accède aux propriétés dans une interface de composant, l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise utilise les API fournies par PeopleSoft qui lisent et écrivent des champs individuels dans l'interface de composant. Cependant, ces modifications ne sont pas propagées au serveur PeopleSoft les unes après les autres. Au lieu de cela, psjoa.jar (avec lequel l’adaptateur BizTalk pour PeopleSoft Enterprise interagit) regroupe toutes les modifications et envoie les modifications au serveur dans un seul package.<br /><br /> En cas d'échec d'une des mises à jour individuelles, une erreur générique est renvoyée, sans identifier l'erreur réelle. Si le mode interactif est défini sur TRUE, chaque mise à jour de champ est envoyée au serveur individuellement. Cela a un impact considérable sur les performances mais des informations spécifiques sur l'erreur sont fournies en cas d'échec de la mise à jour (par exemple, si une valeur non valide est utilisée pour la définition d'un champ).<br /><br /> InteractiveMode offre des performances optimales et fournit des rapports d'erreurs au niveau de la mise à jour du champ. Pour utiliser correctement cette fonctionnalité, il est recommandé d'effectuer des appels normaux lorsque interactiveMode est défini sur False. Cela ne doit avoir aucun impact sur les performances. Si une erreur est renvoyée, le même appel peut faire l'objet d'une nouvelle tentative avec l'indicateur interactiveMode défini sur TRUE. Lorsque l'appel échoue, le serveur renvoie un message d'erreur plus précis.|  
|`properties`|Structure contenant toutes les propriétés de l'interface de composant. Lorsque la méthode `CreateEx` est appelée, ces propriétés sont insérées dans l'enregistrement créé avec la ou les clés spécifiées.|  
  
## <a name="remarks"></a>Notes  
 Dans certaines situations, il est fréquent d'appeler `CreateEx()` sans un jeu de clés explicites. Cependant, la fonction `CreateEx` renvoie les clés. Ce comportement est pris en charge avec PeopleCode, qui est déclenché sur le serveur. Par exemple, pour créer un bon de commande, il est possible que le client ignore quel est le prochain numéro de bon de commande disponible. En spécifiant NEXT comme clé de numéro de bon de commande, l'appel déclenche PeopleCode, qui détermine le prochain bon de commande disponible. Ces informations doivent être renvoyées vers le client appelant, à l'aide des paramètres de clés d'entrée/sortie.  
  
> [!NOTE]
>  Pour ce mécanisme fonctionne, la clé doit également être une propriété de niveau 0. Sinon, la clé d’origine est retournée.  
  
 La méthode de l'adaptateur BizTalk pour PeopleSoft Enterprise `CreateEx()` est fournie si les fonctions Create et Save de PeopleSoft sont activées dans l'interface de composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)