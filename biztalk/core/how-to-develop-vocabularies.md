---
title: "Le développement des vocabulaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- vocabularies, creating
ms.assetid: 5c16eb98-2257-44f2-8a29-899e02f7e556
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2644cc938cbe5e42f4e124453d863741755d965d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-vocabularies"></a>Développement des vocabulaires
Les conditions et les actions des règles sont basées sur des sources associées éventuellement à des informations de liaison détaillées et difficiles à lire qui renseignent peu ou pas du tout l'utilisateur sur ce à quoi elles font référence. L'infrastructure de règles d'entreprise vous permet de créer des vocabulaires pour simplifier le développement des règles en offrant aux utilisateurs une terminologie intuitive et spécifique à chaque domaine qu'ils peuvent associer aux conditions et aux actions des règles.  
  
 Vous pouvez identifier des sources de données pour utiliser et créer un vocabulaire ainsi que pour y ajouter des définitions. Vous pouvez enregistrer une version de votre vocabulaire dans le magasin de règles et, une fois qu'elle est terminée, la publier afin de fournir aux utilisateurs un ensemble de termes bien définis et immuables liés aux références de données.  
  
 Si vous devez apporter des modifications à votre vocabulaire par la suite, il vous suffira de créer une nouvelle version de ce dernier, version qui reflètera ces changements.  
  
> [!CAUTION]
>  Si une nouvelle version d'un vocabulaire est créée, les règles créées à partir d'une version précédente feront toujours référence à cette version.  
  
### <a name="to-create-a-vocabulary"></a>Pour créer un vocabulaire  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.  
  
2.  Cliquez sur le **vocabulaires** dossier, puis cliquez sur **ajouter un nouveau vocabulaire**.  
  
     Un nouveau **vocabulaire** dossier apparaît sous le **vocabulaires** dossier.  
  
3.  Cliquez sur la nouvelle **vocabulaire** dossier, puis modifiez son nom dans la fenêtre Propriétés.  
  
    > [!NOTE]
    >  Vous devez tout enregistrer (toutes les versions des définitions) avant de pouvoir renommer un vocabulaire ou une stratégie.