---
title: "Comment créer des règles et stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, business rules
- policies, rules
- policies, predicates
- business rules, creating
- creating, policies
- policies, logical operators
- policies, examples
- policies, default actions
- policies
- policies, arguments
- policies, creating
ms.assetid: 59f06a67-edde-443b-9fbb-55ec4429837a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fb3d835b39a4059fc7a4a1644d7653257ea3dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-policies-and-rules"></a>Création de stratégies et de règles
Vous pouvez créer des règles avec des conditions qui sont des groupements logiques d’opérateurs logiques (**AND**, **OR**, et **pas**) appliqué aux prédicats (intégrées ou définis par l’utilisateur des fonctions ou opérateurs) qui acceptent des arguments (références de faits intégrées ou définies par l’utilisateur). Vous pouvez également cliquer sur **Conditions** ou opérateurs logiques et sélectionnez un opérateur logique ou un prédicat intégré dans le menu contextuel.  
  
 Vous pouvez définir les actions (fonctions intégrées ou définies par l’utilisateur) à exécuter si la condition de règle a la valeur **true**.  
  
> [!NOTE]
>  Si vous incluez plusieurs prédicats dans une règle, ils doivent tous apparaître en tant qu'arguments d'un opérateur logique (Le niveau supérieur peut être un membre .NET unique, une colonne de base de données ou un champ/attribut XML qui est de type booléen).  
  
### <a name="to-create-a-policy"></a>Pour créer une stratégie  
  
1.  Dans le volet Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.  
  
     Un nouveau dossier, **Policy1**, est créé sous **stratégies**. Par défaut, la version 1 d'une nouvelle stratégie est créée pour vous.  
  
2.  Cliquez sur **Policy1**.  
  
3.  Tapez un nom dans le volet de propriétés Nom.  
  
### <a name="to-add-a-rule-to-a-policy-version"></a>Pour ajouter une règle à une version de stratégie  
  
-   Dans le volet Explorateur de stratégies, développez [**votre stratégie**], avec le bouton droit **Version 1.0 (non enregistrée)**, puis sélectionnez **ajouter une nouvelle règle**.  
  
### <a name="to-add-a-logical-operator-to-a-rule-condition"></a>Pour ajouter un opérateur logique à une condition de règle  
  
-   Dans la fenêtre de définition de règle, cliquez sur **Conditions**, puis cliquez sur un des **ajouter le AND logique**, **ajouter le OR logique**, ou **ajouter le NOT logique**.  
  
### <a name="to-add-a-built-in-predicate-to-a-rule-condition-or-logical-operator"></a>Pour ajouter un prédicat intégré à une condition de règle ou un opérateur logique  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet, puis cliquez sur le **prédicats** dossier.  
  
2.  Développez une version publiée d'un vocabulaire de prédicat, puis cliquez sur le prédicat voulu.  
  
3.  Faites glisser le prédicat sur l’opérateur logique, ou sur **Conditions** si votre règle doit contenir qu’un seul prédicat.  
  
    > [!NOTE]
    >  Vous pouvez également ajouter un prédicat directement à partir d’une source de données, si l’élément de données agit en tant que prédicat (prend la valeur de **true** ou **false**).  
  
### <a name="to-add-a-built-in-action-to-a-rule"></a>Pour ajouter une action intégrée à une règle  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet, puis cliquez sur le **fonctions** dossier.  
  
2.  Développez une version publiée du vocabulaire de fonction, puis cliquez sur la fonction voulue.  
  
3.  Faites glisser la fonction sur **Actions**. Vous pouvez également cliquer sur **Actions**, puis sélectionnez une action intégrée dans le menu contextuel.  
  
### <a name="to-add-an-argument-to-a-condition-or-action"></a>Pour ajouter un argument à une condition ou une action  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet, puis cliquez sur un dossier de vocabulaire.  
  
2.  Développez une version publiée du vocabulaire, puis cliquez sur le terme voulu. Le terme doit être d'un type attendu par le prédicat ou la fonction.  
  
3.  Faites glisser le terme sur un argument de prédicat dans une condition, ou sur un argument de fonction dans une action.  
  
    > [!NOTE]
    >  Vous pouvez aussi ajouter un argument directement à partir d'une source de données ou, dans le cas d'XML, spécifier le type de fichier dans les propriétés lorsque vous sélectionnez un champ. Cela doit bien sûr être compatible avec les données elles-mêmes et l'élément de données doit être d'un type attendu par le prédicat ou l'action. Pour ajouter un argument directement à partir d'une source de données, cliquez sur l'onglet approprié de la fenêtre Explorateur de faits, accédez à l'élément souhaité, puis faites-le glisser sur un argument de prédicat ou un argument de fonction.  
  
    > [!NOTE]
    >  Vous pouvez ajouter une valeur constante à un argument directement en cliquant sur ce dernier, puis en entrant la valeur constante désirée.