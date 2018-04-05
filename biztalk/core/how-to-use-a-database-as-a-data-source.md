---
title: L’utilisation d’une base de données comme Source de données | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, data sources
ms.assetid: a68057ed-836f-499f-bb80-f644d81bcfc5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3a9201ee729288a819a3d527a6ecb4fefd32797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-database-as-a-data-source"></a>Utilisation d'une base de données en tant que source de données
Vous pouvez spécifier une base de données en tant que source de données. Vous pouvez ensuite sélectionner une table ou une colonne d'une table dans la base de données et la faire glisser vers une règle ou une définition de vocabulaire pour l'utiliser en tant que fait.  
  
> [!NOTE]
>  Vous pouvez choisir de lier à la base de données/table de lignes à l’aide **DataConnection** ou **TypedDataTable** en sélectionnant « Connexion de données » ou « Ligne de la table de base de données » dans le **type de liaison de base de données**  zone de liste déroulante dans la fenêtre Propriétés pour le **bases de données** onglet de l’Explorateur de faits. **DataConnection** liaison est utilisée par défaut.  
  
### <a name="to-specify-a-sql-database-as-a-data-source"></a>Pour spécifier une base de données SQL en tant que source de données  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **bases de données** onglet.  
  
2.  Cliquez sur le **serveurs** nœud, puis cliquez sur **Parcourir**.  
  
3.  Dans la liste déroulante, sélectionnez un serveur de base de données disponible.  
  
4.  Sélectionnez un type d'authentification. Si vous sélectionnez l'authentification SQL, entrez un nom de connexion et un mot de passe. Lorsque vous avez entré vos informations d’authentification, cliquez sur **OK**.  
  
     ![Capture d’écran de bases de données du navigateur de l’arborescence. ] (../core/media/ebiz-dbbrows.gif "ebiz_dbbrows")  
Navigation dans une base de données  
  
> [!NOTE]
>  Les vues de base de données SQL Server ne sont pas prises en charge.