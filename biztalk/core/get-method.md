---
title: "Get (méthode) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Get method
ms.assetid: 0e621077-f0ef-495c-ba6b-0c6154f48113
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d56b060cc261f707a4aa7b0d6a496a62707c4dca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-method"></a>Méthode Get
Permet de récupérer les propriétés basées sur les paramètres de clé d’entrée (key1, key2... keyn). Le paramètre sortant est une structure contenant les propriétés de l'enregistrement correspondant aux paramètres de clé. Si l’interface de composant a une seule instance (autrement dit, aucune clé n’existe), la fonction Get ne contient pas de n’importe quel paramètre de clé. Consultez également [méthode Find](../core/find-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Get (key1, key2, ... keyn, properties)  
Get (key1, key2, ... keyn, getHistoryItems, properties)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre| Description|  
|---------------|-----------------|  
|`key`|Ensemble de paramètres qui doit exister dans la base de données du serveur, sans quoi une erreur survient. Ces clés correspondent au jeu de clés Get défini pour l’Interface de composant particulier.|  
|`properties`|Contient une structure complète des propriétés de l'interface de composant, qui est renvoyée une fois l'appel terminé.|  
|`getHistoryItems`|Valeur booléenne. Si les propriétés de l'interface de composant contiennent des éléments ayant une date d'effet en dessous de 0 (et donc, un champ de clé nommé EFFDT), le paramètre supplémentaire `getHistoryItems` est requis.<br /><br /> Si la valeur est :<br /><br /> -Valeur est true, tous les éléments sont retournés en tant que séquence (qui peut être incorporée dans n’importe quel niveau). à savoir tous les éléments passés, actuels et futurs.<br />-False — uniquement actuel et tous les éléments ayant une date futures effet sont renvoyés. Si les appels suivants à la mise à jour sur la même instance sont effectués, puis `getHistoryItems` doit être défini à False.|  
  
### <a name="remarks"></a>Notes  
 Si les propriétés de l'interface de composant contiennent des éléments ayant une date d'effet en dessous de 0 (et donc, un champ de clé nommé EFFDT), un paramètre supplémentaire `getHistoryItems` est requis. Ce paramètre est de type booléen. S'il est défini sur True, tous les éléments ayant une date d'effet sont renvoyés en tant que séquence (qui peut être incorporée à tous les niveaux), Ces incluent tous les éléments ayant une date d’effet, l’élément ayant une date effective actuelle, ainsi que tous les éléments ayant une date futures efficaces. Si le `getHistoryItems` paramètre est défini sur False, uniquement actuel et tous les éléments ayant une date futures effet sont renvoyés. Si d'autres appels relatifs à la mise à jour de la même instance sont effectués par la suite, `getHistoryItems` doit être défini sur False. Voir aussi [méthode UpdateEx](../core/updateex-method.md).  
  
 Si l'interface de composant ne possède pas de clé (par exemple, s'il n'existe qu'une seule instance), la méthode `Get()` a la forme :  
  
```  
Get(properties)  
```  
  
 Pour plus d'informations sur les éléments ayant une date d'effet, consultez la documentation de PeopleSoft Enterprise.  
  
> [!NOTE]
>  La méthode de l'adaptateur BizTalk pour PeopleSoft Enterprise `Get()` est fournie si la fonction `Get` de PeopleSoft est activée dans l'interface de composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)