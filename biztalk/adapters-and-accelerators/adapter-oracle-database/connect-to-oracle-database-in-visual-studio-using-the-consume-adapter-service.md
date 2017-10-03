---
title: "Se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting, to the Oracle database
- connection, to the Oracle database
ms.assetid: db2789d0-2d61-472b-ad0c-4ef0707e9c64
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9ecd6867776b8adf918f901369f526bc0479bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service"></a>Se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service
Complément Consume Adapter Service est installé lorsque vous installez WCF LOB Adapter SDK. Complément Consume Adapter Service charge toutes les liaisons WCF-Custom installés sur l’ordinateur. Pour vous connecter à la base de données Oracle à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans un projet BizTalk, vous devez utiliser le **oracleDBBinding**.  
  
 Cette rubrique fournit des instructions sur l’utilisation de la macro complémentaire Consume Adapter Service.  
  
## <a name="connecting-to-an-oracle-database-using-the-consume-adapter-service-add-in"></a>Connexion à Oracle à l’aide de la base de données le Consume Adapter Service Add-in  
 Les étapes suivantes pour vous connecter à une base de données Oracle à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans une solution BizTalk :  
  
    1.  Cliquez sur le projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
    2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
        |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
    3.  Cliquez sur **Ajouter**. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] s’ouvre.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **oracleDBBinding** et cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à la base de données Oracle.  
  
    1.  Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte. Vérifiez que vous respectez les points suivants lorsque vous spécifiez le nom d’utilisateur et un mot de passe pour se connecter à une base de données Oracle :  
  
        -   **Nom d’utilisateur**. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur la base de données Oracle. Noms d’utilisateur sur la base de données Oracle respectent la casse. Vous devez vous assurer que vous fournissez des noms d’utilisateur Oracle pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans le cas attendu par votre base de données Oracle. En règle générale, cela signifie que le nom d’utilisateur dans les informations d’identification SCOTT/TIGER doit être en majuscule : « SCOTT ».  
  
        -   **Mot de passe**. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur la base de données Oracle. Pour la version 10g et versions antérieures, les mots de passe sur le système Oracle ne respectent pas la casse.  
  
    2.  Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.  
  
4.  Cliquez sur le **propriétés URI** onglet et spécifier des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Par exemple, si vous souhaitez cibler l’opération POLLINGSTMT, vous devez définir le **PollingStatement** propriété de liaison. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur **Se connecter**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie.  
  
     ![Consume Adapter Service connecté de boîte de dialogue](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à la base de données Oracle dans Visual Studio à l’aide de la référence de Service ajouter de carte](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md)   
 [Se connecter à la base de données Oracle à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)