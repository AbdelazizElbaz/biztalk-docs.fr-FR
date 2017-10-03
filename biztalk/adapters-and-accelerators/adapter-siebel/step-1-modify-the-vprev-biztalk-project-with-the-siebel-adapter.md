---
title: "Étape 1 : Modifier le projet BizTalk vPrev avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7bd95e2-bd51-420f-8156-6f17cc0e91d6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5465a80fd7b75dcbf7ec864b196d2fd5033cb003
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-modify-the-vprev-biztalk-project-with-the-siebel-adapter"></a>Étape 1 : Modifier le projet BizTalk vPrev avec l’adaptateur Siebel
![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous apporter les modifications suivantes au projet BizTalk vPrev existant :  
  
-   Générer des métadonnées pour l’opération d’insertion sur le composant de gestion de compte à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
-   Mapper le message de demande pour effectuer une opération d’insertion à l’aide de l’adaptateur Siebel vPrev à un message de demande pour effectuer une opération d’insertion à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] au message de réponse pour l’adaptateur Siebel vPrev.  
  
## <a name="prerequisite"></a>Condition préalable  
  
-   Vous devez disposer d’un projet BizTalk de vPrev pour effectuer une opération d’insertion sur le composant de gestion de compte dans le système Siebel.  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>Pour modifier le projet BizTalk vPrev  
  
1.  Générer des métadonnées pour l’opération d’insertion sur le composant de gestion de compte à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Vous pouvez utiliser la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées.  
  
     Pour obtenir des instructions sur la façon de générer des métadonnées, consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md). Une fois le schéma est généré, un fichier portant le nom semblable à *SiebelBindingSchema.xsd* est ajouté au projet BizTalk. Ce fichier contient le schéma pour l’envoi d’un message pour effectuer l’opération d’insertion sur le composant de gestion de compte à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
2.  Générer les métadonnées pour l’opération d’insertion crée également un fichier de liaison de port. Dans l’étape suivante, ce fichier de liaison servira à créer un port d’envoi WCF-Custom pour envoyer des messages au système Siebel. L’action SOAP pour l’opération est également définie à l’opération pour laquelle vous avez généré des métadonnées. Par exemple, si vous générez des métadonnées pour l’opération d’insertion, le nom de l’opération dans l’action SOAP sur le port d’envoi sera « Insert ». Toutefois, l’opération de nom sur le port d’envoi logique que vous créez lors de la partie de l’orchestration peut être différent, par exemple, « Operation_1 ». Par conséquent, lorsque vous envoyez des messages au système Siebel à l’aide du port d’envoi, vous obtenez une erreur. Pour éviter ce problème, vérifiez le nom de l’opération sur la logique port d’envoi dans l’orchestration est le même que le nom de l’opération pour laquelle vous avez généré des métadonnées.  
  
     Par conséquent, en cas de ce didacticiel, étant donné que vous générez des métadonnées pour l’opération d’insertion, modifiez le nom de l’opération de port d’envoi logique à « Insert ».  
  
3.  Pour le message de demande, mapper le schéma généré à l’aide de l’adaptateur Siebel vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **RequestMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour l’adaptateur Siebel vPrev. Pour ce didacticiel, sélectionnez *Siebel_BussComp_Migration.AccountService_Account_x5d*. Cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *insérer*, puis cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Pour ce didacticiel, sélectionnez *Siebel_BussComp_Migration.SiebelDBBindingSchema*, puis cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *insérer*, puis cliquez sur **OK**.  
  
    8.  Mapper les éléments suivants dans les deux schémas : **Currency_Code**, **Current_Volume**, **Customer_Account_Group**, **emplacement**, **Main_Phone_Number**, **nom**, **Party_Name**, **Primary_Address_Id**,  
  
    9. Enregistrez le mappage.  
  
4.  Pour le message de réponse, mapper le schéma généré à l’aide de l’adaptateur Siebel vPrev le schéma généré à l’aide de la WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans la boîte de dialogue Ajouter un nouvel élément dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **ResponseMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**et sélectionnez le schéma de message de réponse pour la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Pour ce didacticiel, sélectionnez *Siebel_BussComp_Migration.SiebelDBBindingSchema*. Cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *InsertResponse* et cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**et sélectionnez le schéma de message de réponse pour l’adaptateur Siebel vPrev. Pour ce didacticiel, sélectionnez *Siebel_BussComp_Migration.AccountService_Account_x5d*. Cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *InsertResponse* et cliquez sur **OK**.  
  
    8.  Carte le **: chaîne de tableau** élément dans le schéma source à la **exposée : chaîne** élément dans le schéma de destination, comme illustré dans la figure suivante.  
  
         ![Mapper les messages de réponse entre les versions d’adaptateur](../../adapters-and-accelerators/adapter-siebel/media/6352035b-79c0-4850-a8f7-e4f6581c8532.gif "6352035b-79c0-4850-a8f7-e4f6581c8532")  
  
    9. Enregistrez le mappage.  
  
5.  Enregistrez et générez la solution BizTalk. Avec le bouton droit de la solution, puis cliquez sur **générer la Solution**.  
  
6.  déployer la solution ; Avec le bouton droit de la solution, puis cliquez sur **déployer la Solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créer un port d’envoi WCF-custom et configurez-le pour utiliser les mappages que vous avez créé dans cette étape, comme décrit dans [étape 2 : configurer l’Orchestration dans la Console Administration de BizTalk Server pour utiliser l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : Migration des projets BizTalk dans Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)