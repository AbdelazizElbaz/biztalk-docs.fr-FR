---
title: "Étape 1 : Modifier le projet BizTalk à l’aide de l’adaptateur SQL vPrev | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25ad959b-2818-47b8-9a09-3681abb75887
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f0eb02594251fa5ab1c209c1d2655056cf489df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter"></a>Étape 1 : Modifier le projet BizTalk à l’aide de l’adaptateur SQL vPrev
![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous apporter les modifications suivantes au projet BizTalk vPrev existant :  
  
-   Générer des métadonnées pour l’opération d’insertion sur la table Customer à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Mapper le message de demande pour effectuer une opération d’insertion à l’aide de l’adaptateur SQL vPrev à un message de demande pour effectuer une opération d’insertion à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] au message de réponse reçu à l’aide de l’adaptateur SQL vPrev.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer d’un projet BizTalk de vPrev pour effectuer une opération d’insertion sur la table Customer dans la base de données SQL Server.  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>Pour modifier le projet BizTalk vPrev  
  
1.  Générer des métadonnées pour l’opération d’insertion sur la table Customer à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez utiliser la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées.  
  
     Pour obtenir des instructions sur la façon de générer des métadonnées, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md). Une fois le schéma est généré, un fichier portant le nom semblable à *TableOperation.dbo.Customer.xsd* est ajouté au projet BizTalk. Ce fichier contient le schéma pour l’envoi d’un message pour effectuer une opération d’insertion sur la table Customer dans la base de données SQL Server à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
2.  Générer les métadonnées pour l’opération d’insertion crée également un fichier de liaison de port. Dans l’étape suivante, ce fichier de liaison servira à créer un port d’envoi WCF-Custom pour envoyer des messages à la base de données SQL Server. L’action SOAP pour l’opération est également définie à l’opération pour laquelle vous avez généré des métadonnées. Par exemple, si vous générez des métadonnées pour l’opération d’insertion, le nom de l’opération dans l’action SOAP sur le port d’envoi sera « Insert ». Toutefois, l’opération de nom sur le port d’envoi logique que vous créez lors de la partie de l’orchestration peut être différent, par exemple, « Operation_1 ». Par conséquent, lorsque vous envoyez des messages à la base de données SQL Server à l’aide du port d’envoi, vous obtenez une erreur. Pour éviter ce problème, vérifiez le nom de l’opération sur la logique port d’envoi dans l’orchestration est le même que le nom de l’opération pour laquelle vous avez généré des métadonnées.  
  
     Par conséquent, en cas de ce didacticiel, étant donné que vous générez des métadonnées pour l’opération d’insertion, modifiez le nom de l’opération de port d’envoi logique à « Insert ».  
  
3.  Pour le message de demande, mapper le schéma généré à l’aide de la carte de base de données SQL vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **RequestMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande de l’adaptateur SQL vPrev. Pour ce didacticiel, sélectionnez *New_Migration.InsertCustomerService*, puis cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *insérer*, puis cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour ce didacticiel, sélectionnez *New_Migration.TableOperation.dbo.Customer*, puis cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *insérer*, puis cliquez sur **OK**.  
  
    8.  Mapper les éléments respectifs dans les deux schémas comme illustré dans la figure suivante.  
  
         ![Mapper les schémas de demande](../../adapters-and-accelerators/adapter-sql/media/850bbf52-fc3e-42c5-b879-51c6e39a502d.gif "850bbf52-fc3e-42c5-b879-51c6e39a502d")  
  
    9. Enregistrez le mappage.  
  
4.  Pour le message de réponse, mapper le schéma généré à l’aide de l’adaptateur SQL vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **ResponseMap.btm**, puis cliquez sur **ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma de message de réponse pour la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour ce didacticiel, sélectionnez *New_Migration.TableOperation.dbo.Customer*, puis cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *InsertResponse*, puis cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma de message de réponse pour le vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour ce didacticiel, sélectionnez *New_Migration.InsertCustomerService*, puis cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *InsertResponse*, puis cliquez sur **OK**.  
  
    8.  Vous remarquerez quelques différences entre les schémas de réponse pour générées par les deux cartes. Ces différences peuvent être décrites comme suit :  
  
        -   À l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], si vous insérez un enregistrement dans une table qui contient une clé primaire (et est également un champ d’identité) à la réponse pour l’insertion opération renvoie la valeur du champ d’identité pour la ligne insérée. Par conséquent, le schéma pour le message de réponse conformes à la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] contient un autre *InsertResult* élément. Cet élément contient un tableau qui contient les champs d’identité pour les lignes insérées.  
  
        -   À l’aide de la vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], si vous insérez un enregistrement dans une table, l’adaptateur retourne uniquement un élément vide de « Réussite » en tant que partie du message de réponse.  
  
         Par conséquent, les schémas sont mappés de sorte que la réponse à partir de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] contenant la valeur pour les champs d’identité est « copiée » dans le cadre de l’élément « Réussite », qui fait partie du message de réponse à partir de la vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez utiliser le fonctoid copie de masse à copier des éléments d’un schéma dans un autre.  
  
         Pour utiliser le fonctoid copie de masse à partir de la **boîte à outils**, faites glisser le fonctoid copie de masse et déposez-la sur la grille du mappeur. Connecter le **InsertResult** élément dans le schéma source vers le fonctoid. De même, connectez le **réussite** élément dans le schéma de destination vers le fonctoid. La figure suivante illustre la façon dont les deux éléments sont mappés par le fonctoid.  
  
         ![Mapper les schémas de réponse](../../adapters-and-accelerators/adapter-sql/media/c4a347ae-8d2d-4357-b18d-37f36bef17c7.gif "c4a347ae-8d2d-4357-b18d-37f36bef17c7")  
  
        > [!NOTE]
        >  Pour plus d’informations sur le fonctoid copie de masse, consultez [http://go.microsoft.com/fwlink/?LinkId=119749](http://go.microsoft.com/fwlink/?LinkId=119749).  
  
    9. Enregistrez le mappage.  
  
5.  Enregistrez et générez la solution BizTalk. Avec le bouton droit de la solution, puis cliquez sur **générer la Solution**.  
  
6.  déployer la solution ; Avec le bouton droit de la solution, puis cliquez sur **déployer la Solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créer un port d’envoi WCF-custom et configurez-le pour utiliser les mappages que vous avez créé dans cette étape, comme décrit dans [étape 2 : configurer l’Orchestration dans la Console Administration de BizTalk Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Migrer des projets BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)