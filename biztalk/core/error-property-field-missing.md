---
title: 'Erreur : champ de propriété manquant | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.propFieldMissing
ms.assetid: 8d07e72b-f876-4a37-8c95-ec7aa0033983
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d77311e4c8585cfb7f6108364e6a5085619595a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---property-field-missing"></a>Erreur : champ de propriété manquant
**Code d’erreur**  
  
 BEC2008  
  
 **Explication**  
  
 Le nœud indiqué dans ce schéma est promu à un **élément de champ** nœud dans le schéma de propriété correspondant n’existe pas. Cette condition peut se produire lorsqu’un **élément de champ** nœud est supprimé ou renommé dans un schéma de propriété une fois qu’il a été utilisé comme cible de la promotion des propriétés.  
  
 **Action de l’utilisateur**  
  
 Modifiez le schéma de propriété pour qu’il contienne manquants **élément de champ** nœud, ou utilisez le **promouvoir les propriétés** boîte de dialogue pour supprimer ou de modifier la promotion des propriétés appropriée.