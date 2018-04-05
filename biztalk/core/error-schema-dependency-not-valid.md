---
title: 'Erreur : dépendance de schéma non valide | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.schemaDependencyNotValid
ms.assetid: 431278f0-6cd1-4b3f-8d87-16af4991d354
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36326608f191b520c41cb42890aec029c432fd30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-dependency-not-valid"></a>Erreur : dépendance de schéma non valide
**Code d’erreur**  
  
 BEC2009  
  
 **Explication**  
  
 Tous les schémas dépendants, notamment ceux qui sont importés, inclus ou redéfinis dans le schéma actuel, doivent être ajoutés au projet BizTalk ou doivent exister dans un assembly référencé par ce projet. Schémas **importer**, **incluent**, et **redéfinir** directives qui spécifient les schémas sur un site Web distant doivent être ajoutés à ce projet BizTalk.  
  
 **Action de l’utilisateur**  
  
 Utilisez le **ajouter un élément existant** commande sur le **fichier** menu et le menu contextuel du projet Microsoft® BizTalk® Server ajouter tous les schémas dont dépend ce schéma au projet BizTalk. Vous devrez peut-être télécharger certains de ces schémas, à partir d'un site Web, sur votre disque dur local avant de pouvoir les ajouter au projet.