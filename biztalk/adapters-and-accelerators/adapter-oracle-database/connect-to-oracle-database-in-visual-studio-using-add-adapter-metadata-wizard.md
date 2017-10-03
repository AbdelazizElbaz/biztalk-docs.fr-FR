---
title: "Se connecter à la base de données Oracle dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 726b3f82-887c-407a-bb9f-dcb9443155b0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbf023a306e7caabeb3e207f90831167f46e8009
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-database-in-visual-studio-using-add-adapter-metadata-wizard"></a>Se connecter à la base de données Oracle dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est également exposé comme un adaptateur BizTalk et, par conséquent, vous pouvez utiliser la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les opérations à effectuer sur la base de données Oracle à l’aide de l’adaptateur.  
  
 Cette rubrique fournit des instructions sur l’utilisation de la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
## <a name="connecting-to-an-oracle-database-using-the-add-adapter-metadata-wizard"></a>Connexion à Oracle de la base de données à l’aide de l’Assistant Ajout d’adaptateur métadonnées  
 Les étapes suivantes pour vous connecter à une base de données Oracle à l’aide du [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-connect-to-an-oracle-database"></a>Pour vous connecter à une base de données Oracle  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] dans une solution BizTalk :  
  
    1.  Cliquez sur le projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
    2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
        |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
    3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
    4.  Dans l’Assistant Ajout de métadonnées d’adaptateur, sélectionnez **WCF-OracleDB**. Sélectionnez l’ordinateur sur lequel BizTalk Server est installé et le nom de la base de données BizTalk.  
  
        > [!IMPORTANT]
        >  Si vous disposez déjà d’un port WCF-OracleDB configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.  
  
    5.  Cliquez sur **Suivant**.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **oracleDBBinding** et cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à la base de données Oracle.  
  
    1.  Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte. Vérifiez que vous respectez les points suivants lorsque vous spécifiez le nom d’utilisateur et un mot de passe pour se connecter à une base de données Oracle :  
  
        -   **Nom d’utilisateur**. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur la base de données Oracle. Noms d’utilisateur sur la base de données Oracle respectent la casse. Vous devez vous assurer que vous fournissez des noms d’utilisateur Oracle pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans le cas attendu par votre base de données Oracle. En règle générale, cela signifie que le nom d’utilisateur dans les informations d’identification SCOTT/TIGER doit être en majuscule : « SCOTT ».  
  
        -   **Mot de passe**. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur la base de données Oracle. Pour la version 10g et versions antérieures, les mots de passe sur le système Oracle ne respectent pas la casse.  
  
    2.  Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.  
  
4.  Cliquez sur le **propriétés URI** onglet et spécifier des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Par exemple, si vous souhaitez cibler l’opération POLLINGSTMT, vous devez définir le **PollingStatement** propriété de liaison. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).
  
    > [!NOTE]
    >  Si vous générez des métadonnées à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur et que vous avez sélectionné un WCF-OracleDB existant un port d’envoi, vous devez ne pas spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur **Se connecter**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie.  
  
     ![Consume Adapter Service connecté de boîte de dialogue](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à la base de données Oracle dans Visual Studio à l’aide de la référence de Service ajouter de carte](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md)   
 [Se connecter à la base de données Oracle à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)