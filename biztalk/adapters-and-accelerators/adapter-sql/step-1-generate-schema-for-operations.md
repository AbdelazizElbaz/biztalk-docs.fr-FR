---
title: "Étape 1 : Générer le schéma pour les opérations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63218a5e-9af2-40af-9992-ac5e204d2832
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16372bd950088b89f8e7808cda751f5fc3833944
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-generate-schema-for-operations"></a>Étape 1 : Générer le schéma pour les opérations
![Étape 1 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous générez des schémas pour les opérations que vous effectuez sur la base de données SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour ce didacticiel, vous devez générer le schéma pour les éléments suivants :  
  
-   **Notification** (opération entrante).  
  
-   **UPDATE_EMPLOYEE** (opération sortante) de procédure stockée.  
  
-   **Insérer** opération sur le **Purchase_Order** table (opération sortante).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de poursuivre le didacticiel, assurez-vous que :  
  
-   Vous devez avoir terminé les étapes de [avant de vous développer des Applications BizTalk](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6).  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.  
  
### <a name="to-generate-schema-for-operations"></a>Pour générer le schéma pour les opérations  
  
1.  Créer un nouveau projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour ce didacticiel, nommez le projet en tant que `Employee_PurchaseOrder`.  
  
2.  Se connecter à la base de données ADAPTER_SAMPLES SQL Server à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Pour obtenir des instructions sur la façon de se connecter à l’aide de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], consultez [se connecter à SQL Server dans Visual Studio à l’aide de Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).  
  
    > [!NOTE]
    >  Vous pouvez également vous connecter à SQL Server à l’aide du [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Toutefois, pour ce didacticiel, vous allez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
3.  Génération du schéma pour le **Notification** opération entrante.  
  
    1.  Après la connexion à la base de données ADAPTER_SAMPLES, dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], à partir de la **type de contrat Select** , sélectionnez **Service (opérations entrantes)**.  
  
    2.  À partir de la **sélectionner une catégorie** , cliquez sur le nœud racine (**/**).  
  
    3.  À partir de la **catégories et opérations disponibles** boîte, sélectionnez **Notification** et cliquez sur **ajouter**. Le **Notification** opération est maintenant affichée dans le **ajouté des catégories et opérations** boîte. Cliquez sur **OK**.  
  
4.  Génération du schéma pour le **UPDATE_EMPLOYEE** procédure stockée et l’opération d’insertion sur **Purchase_Order** table.  
  
    1.  Répétez l’étape 2 pour se connecter à la base de données ADAPTER_SAMPLES dans SQL Server à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
        > [!NOTE]
        >  Impossible de générer le schéma pour les opérations entrantes et sortantes en même temps. Par conséquent, à l’étape 3, après avoir cliqué sur **OK** pour générer le schéma pour **Notification** opération, le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] se ferme. Vous devez vous reconnecter à la base de données SQL Server pour générer le schéma pour les opérations sortantes.  
  
    2.  À partir de la **type de contrat Select** , sélectionnez **Client (Outbound operations)**.  
  
    3.  À partir de la **sélectionner une catégorie** , cliquez sur le **fortement typée procédures** nœud. À partir de la **catégories disponibles et l’opération**boîte s, sélectionnez **UPDATE_EMPLOYEE**, puis cliquez sur **ajouter**.  
  
        > [!IMPORTANT]
        >  Le **UPDATE_EMPLOYEE** procédure stockée est également disponible sous la **procédures** nœud. Toutefois, si vous générez le schéma de la procédure stockée sous le **procédures** nœud, le schéma de message de réponse n’est pas disponible au moment du design, mais est reçu avec le message de réponse après avoir exécuté la procédure stockée.  
        >   
        >  Dans ce didacticiel, vous allez mapper le schéma de réponse de la procédure stockée pour le schéma d’entrée de l’opération d’insertion sur la **Purchase_Order** table. Par conséquent, vous devez le schéma pour le **UPDATE_EMPLOYEE** une procédure stockée au moment du design et que vous devez sélectionner la procédure stockée sous le **fortement typée procédures**. En procédant ainsi, vous obtenez le schéma de la procédure stockée au moment du design.  
  
    4.  À partir de la **sélectionner une catégorie** , développez le **Tables** nœud et cliquez sur le nœud **Purchase_Order** table. À partir de la **catégories disponibles et l’opération**boîte s, sélectionnez **insérer**, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez généré des schémas pour **Notification** (opération entrante), **UPDATE_EMPLOYEE** procédure stockée, et **insérer** opération sur le  **Purchase_Order** table. Après avoir généré le schéma, le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ajoute les fichiers suivants à votre projet BizTalk :  
  
-   Fichiers XSD qui contiennent le schéma du message de demande appeler des opérations sur SQL Server.  
  
-   Les fichiers de liaison XML que vous pouvez utiliser pour créer d’envoi WCF-Custom et recevoir des ports dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 Pour plus d’informations sur la génération de schémas, consultez [Parcourir, rechercher et obtenir des métadonnées pour les opérations SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créer des messages dans le projet BizTalk pour les schémas dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Leçon 1 : Générer des schémas et créer des Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)