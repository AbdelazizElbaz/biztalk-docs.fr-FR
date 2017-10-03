---
title: "Développer des applications de base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming
- channel programming, streaming
- WCF channel model, performing operations
- developing applications, by using the WCF channel model
- streaming, using the WCF channel model
- WCF channel model, developingn applications
- channel programming, performing operations
ms.assetid: cb6bf5fd-ff90-44bd-a9dd-03b00f12a78d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77fb9b6ca1fc70a55b59c6708450b8d94a01eff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-database-applications-using-the-wcf-channel-model"></a>Développer des applications de base de données Oracle à l’aide du modèle de canal WCF
Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de base de données Oracle.  
  
 Un avantage de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes que le modèle de service WCF expose est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur la base de données Oracle. Pourquoi ? Dans le modèle de canal WCF vous contrôler directement le contenu des messages que vous envoyez sur le canal.  
  
 Dans certains scénarios, ce niveau supplémentaire de contrôle peut être utile. Par exemple, lorsque vous utilisez le modèle de canal WCF pour effectuer une opération de mise à jour sur une table, vous pouvez sélectivement mettre à jour colonnes dans les lignes de la cible en omettant les colonnes à partir du modèle de mise à jour que vous passez dans le message. La méthode de mise à jour exposée par un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client utilise un paramètre d’enregistrement de fortement typé pour le modèle qui inclut toutes les colonnes dans le schéma de table. Si une colonne est « nillable = false » dans le WSDL, il doit être mis à jour à l’aide du modèle de service WCF.  
  
 Un autre avantage clé qui fournit un modèle de canal WCF sur le modèle de service WCF est prise en charge plus complète de bout en bout pour la diffusion en continu des types de données Oracle LOB (large object). En utilisant le modèle de canal WCF, vous pouvez effectuer la diffusion en continu de bout en bout :  
  
-   Pour mettre à jour une colonne LOB dans une table ou vue à l’aide de l’opération UpdateLOB.  
  
-   DÉCOUVRIR et contenant des paramètres de sortie des données qui sont retournées par les procédures et fonctions de LOB.  
  
-   Sur des données LOB, qui est contenue dans le résultat d’une opération SQLEXECUTE.  
  
-   Sur les colonnes de données LOB qui sont retournées dans l’opération POLLINGSTMT.  
  
-   Sur les colonnes de données LOB qui sont retournées par une opération Select sur une table ou vue.  
  
 Il s’agit, car dans le modèle de canal WCF vous contrôlez directement comment vous fournissez le corps du message sur les messages sortants et le mode de traitement du corps du message sur les messages entrants.  
  
 En revanche, le modèle de service WCF fournit uniquement :  
  
-   De bout en bout pour les données LOB dans une seule opération, l’opération ReadLOB de diffusion en continu.  
  
-   N’arrive pas à mettre à jour la base de données Oracle dans une diffusion en continu des données LOB.  
  
 Les sections de cette rubrique expliquent comment effectuer les opérations sur les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en utilisant le modèle de canal WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de canal WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [Créer un canal à l’aide de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [Appeler des opérations sur la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Exécuter une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Exécuter une opération d’insertion dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Appeler une fonction dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [Diffusion en continu de base de données LOB Types de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)