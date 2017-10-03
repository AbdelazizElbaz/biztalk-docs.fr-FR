---
title: "À l’aide de l’Explorateur de stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, Policy Explorer
- policies, Policy Explorer
- business rules, Policy Explorer
- Policy Explorer [Business Rule Composer]
ms.assetid: 249b1b72-ba84-4695-ba2b-16f081710b20
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66b88618f10bf204701e6fcd68d7d95007966c50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-policy-explorer"></a>À l’aide de l’Explorateur de stratégies
Vous pouvez utiliser l'Explorateur de stratégies pour gérer les stratégies et les règles du magasin de règles. Vous pouvez créer, modifier et supprimer des stratégies et des règles, ou tester, publier, déployer et annuler le déploiement de stratégies.  
  
 Le tableau suivant décrit les options de l'Explorateur de stratégies pouvant être utilisées dans le processus de développement de nouvelles règles et stratégies.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Ajouter une nouvelle stratégie**|Créer une stratégie (ensemble de règles).|  
|**Ajouter une nouvelle Version**|Créer une version vide de la stratégie sélectionnée. Vous pouvez copier des règles provenant d'autres versions et les coller dans la nouvelle version.|  
|**Copier (Version de stratégie)**|Copier la version de stratégie sélectionnée dans le Presse-papiers.|  
|**Copier (règle)**|Copier la règle sélectionnée dans le Presse-papiers.|  
|**Couper (règle)**|Copier la règle sélectionnée dans le Presse-papiers et la supprimer.|  
|**Coller (Version de stratégie)**|Coller une version de stratégie et son contenu dans une stratégie sélectionnée.|  
|**Coller (règle)**|Coller une règle dans la version de stratégie sélectionnée.|  
|**Supprimer (Version de stratégie)**|Supprimer la version de stratégie sélectionnée.|  
|**Supprimer (règle)**|Supprimer la règle sélectionnée.|  
|**Delete**|Supprimer la stratégie sélectionnée ainsi que toutes ses versions.|  
|**Ajouter une nouvelle règle**|Créer une règle dans la version de stratégie sélectionnée.|  
|**Enregistrer**|Enregistrer toutes les modifications apportées à la version sélectionnée et à ses règles.|  
|**Publier**|Publier la version de stratégie sélectionnée. Notez que vous ne pouvez pas directement modifier une version publiée. Pour ce faire, vous devez la copier, puis la coller dans une nouvelle version.|  
|**Recharger**|Recharger la version de stratégie sélectionnée et ses règles, en choisissant d'ignorer ou non les modifications effectuées dans cette version et de rétablir le contenu à partir du magasin de règles.|  
|**Déployer**|Déployer une version de stratégie publiée. Vous devez déployer une version de stratégie afin qu'elle devienne accessible aux applications basées sur des règles.|  
|**Annuler le déploiement**|Annuler le déploiement d'une version de stratégie. Une fois une version est annulée, il n’est plus disponible aux applications basées sur une règle.|  
|**Tester la stratégie**|Tester la version de stratégie sélectionnée avant son déploiement.|  
  
## <a name="properties-window"></a>Fenêtre Propriétés  
 Le tableau suivant décrit les propriétés d’une version de stratégie.  
  
|Propriété|Valeur|  
|--------------|-----------|  
|**Nom**|Nom de la stratégie.<br /><br /> Vous pouvez uniquement modifier cette valeur en modifiant le **nom** propriété de la stratégie (version de stratégie pas).|  
|**Extracteur de faits**|Informations sur l’extracteur de faits pour la version de stratégie.|  
|**Profondeur maximale d’exécution de la boucle**|Profondeur maximale de l'algorithme de chaînage avant, avant qu’une exception de boucle d’exécution ne soit émise.<br /><br /> Le nombre de boucles par défaut est 65536.|  
|**Durée de la conversion**|Durée maximale de la conversion des règles avant qu’une exception d’expiration de conversion ne soit émise.<br /><br /> La valeur par défaut est 60 000 millisecondes.|  
|**Translator**|Informations sur le convertisseur utilisé pour convertir les règles.|  
|**Version actuelle**|Version de la stratégie actuellement sélectionnée dans l’Explorateur de stratégies.|  
|**Description de la version**|Description de la version actuelle.|  
  
 Le tableau suivant décrit les propriétés d’une règle.  
  
|Propriété|Valeur|  
|--------------|-----------|  
|**Actif**|Indique si la règle est activée ou désactivée.|  
|**Nom**|Nom de la règle.|  
|**Priorité**|Priorité de la règle au sein de la stratégie. Plus l’index est élevé, plus la priorité de la règle l'est également. Les actions de la règle avec la plus grande priorité seront déclenchées en premier.<br /><br /> La valeur par défaut est de 0 et représente la priorité moyenne.|