---
title: "Étape 1 : Modifier le projet BizTalk dans la base de données Oracle vPrev | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e3e22ac-126b-46ec-a6dc-3421ad721392
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f8911a31eeec34a5508d29ff598a2f7624e5cd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-modify-the-vprev-biztalk-project-in-oracle-database"></a>Étape 1 : Modifier le projet BizTalk dans la base de données Oracle vPrev
![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous apporter les modifications suivantes au projet BizTalk vPrev existant :  
  
-   Générer les métadonnées pour l’opération d’insertion sur la SCOTT. Table des clients à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   Mapper le message de demande pour effectuer une opération d’insertion à l’aide de l’adaptateur de base de données Oracle vPrev à un message de demande pour effectuer une opération d’insertion à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] au message de réponse pour l’adaptateur de base de données Oracle vPrev.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev pour effectuer une opération d’insertion sur la SCOTT. Table CUSTOMER dans la base de données Oracle.  
  
## <a name="modify-the-vprev-biztalk-project"></a>Modifier le projet BizTalk vPrev  
  
1.  Générer les métadonnées pour l’opération d’insertion sur la SCOTT. Table des clients à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Vous pouvez utiliser la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées.  
  
     Pour obtenir des instructions sur la façon de générer des métadonnées, consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md). Une fois le schéma est généré, un fichier portant le nom semblable à *OracleDBBindingSchema.xsd* est ajouté au projet BizTalk. Ce fichier contient le schéma pour l’envoi d’un message pour effectuer une opération d’insertion sur la SCOTT. Table CUSTOMER dans la base de données Oracle à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
2.  Générer les métadonnées pour l’opération d’insertion crée également un fichier de liaison de port. Dans l’étape suivante, ce fichier de liaison servira à créer un port d’envoi WCF-Custom pour envoyer des messages à la base de données Oracle. L’action SOAP pour l’opération est également définie à l’opération pour laquelle vous avez généré des métadonnées. Par exemple, si vous générez des métadonnées pour l’opération d’insertion, le nom de l’opération dans l’action SOAP sur le port d’envoi sera « Insert ». Toutefois, l’opération de nom sur le port d’envoi logique que vous créez lors de la partie de l’orchestration peut être différent, par exemple, « Operation_1 ». Par conséquent, lorsque vous envoyez des messages à la base de données Oracle à l’aide du port d’envoi, vous obtenez une erreur. Pour éviter ce problème, vérifiez le nom de l’opération sur la logique port d’envoi dans l’orchestration est le même que le nom de l’opération pour laquelle vous avez généré des métadonnées.  
  
     Par conséquent, en cas de ce didacticiel, étant donné que vous générez des métadonnées pour l’opération d’insertion, modifiez le nom de l’opération de port d’envoi logique à « Insert ».  
  
3.  Pour le message de demande, mapper le schéma généré à l’aide de la carte de base de données Oracle vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **RequestMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour l’adaptateur de base de données Oracle vPrev. Pour ce didacticiel, sélectionnez *Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*. Cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *insérer* et cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour ce didacticiel, sélectionnez *Oracle_Migration.OracleDBBindingSchema*. Cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *insérer* et cliquez sur **OK**.  
  
    8.  Mapper les éléments respectifs dans les deux schémas comme illustré dans la figure suivante.  
  
         ![Mapper la requête envoyée à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/4cb59338-40d1-4eb1-bd89-b5a3183959e1.gif "4cb59338-40d1-4eb1-bd89-b5a3183959e1")  
  
    9. Enregistrez le mappage.  
  
4.  Pour le message de réponse, mapper le schéma généré à l’aide de la carte de base de données Oracle vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **ResponseMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**et sélectionnez le schéma de message de réponse pour la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour ce didacticiel, sélectionnez *Oracle_Migration.OracleDBBindingSchema*. Cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *InsertResponse* et cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**et sélectionnez le schéma de message de réponse pour l’adaptateur de base de données Oracle vPrev. Pour ce didacticiel, sélectionnez *Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*. Cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *InsertResponse*, puis cliquez sur **OK**.  
  
    8.  Vous remarquerez que le schéma pour le message de réponse conformes à la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] contient un autre *InsertResult* élément. Vous devez le supprimer à partir de schéma et du mappage du *InsertResponse* élément dans les deux schémas.  
  
         Pour ce faire, à partir de la **boîte à outils**, faites glisser le **supprimer à gauche de chaîne** fonctoid et déposez-la sur la grille du mappeur. Connecter le **InsertResponse** élément dans le schéma source vers le fonctoid. De même, connectez le **InsertResponse** élément dans le schéma de destination vers le fonctoid. La figure suivante illustre la façon dont les deux éléments sont mappés par le fonctoid.  
  
         ![Mapper la réponse reçue à partir de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/7fe18f5b-100f-4fe2-ac92-c111629d7fe9.gif "7fe18f5b-100f-4fe2-ac92-c111629d7fe9")  
  
        > [!NOTE]
        >  Pour plus d’informations, consultez la **fonctoid chaîne de gauche** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
    9. Enregistrez le mappage.  
  
5.  Enregistrez et générez la solution BizTalk. Avec le bouton droit de la solution, puis cliquez sur **générer la Solution**.  
  
6.  déployer la solution ; Avec le bouton droit de la solution, puis cliquez sur **déployer la Solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créer un port d’envoi WCF-custom et configurez-le pour utiliser les mappages que vous avez créé dans cette étape, comme décrit dans [étape 2 : configurer l’Orchestration dans la Console Administration de Biztalk Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Migration des projets BizTalk](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)