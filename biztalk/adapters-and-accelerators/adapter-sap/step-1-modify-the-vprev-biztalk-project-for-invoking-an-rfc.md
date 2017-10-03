---
title: "Étape 1 : Modifier le projet BizTalk vPrev pour appeler une commande RFC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, modifying previous version of BizTalk project for invoking an RFC
- migration
ms.assetid: 2d4a6cd7-d216-4e0f-8f82-41e044cd325b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1f967a268d8baca3ab12f29bbac4b9eccc3cd75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc"></a>Étape 1 : Modifier le projet BizTalk vPrev pour appeler une commande RFC
![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous apporter les modifications suivantes au projet BizTalk vPrev existant :  
  
-   Générer des métadonnées pour la RFC SD_RFC_CUSTOMER_GET à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Mapper le message de demande pour l’appel de la RFC à l’aide de l’adaptateur SAP vPrev à un message de demande pour l’appel de la RFC à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] au message de réponse pour l’adaptateur SAP vPrev.  
  
## <a name="prerequisite"></a>Condition préalable  
  
-   Vous devez disposer d’un projet BizTalk de vPrev pour appeler le RFC SD_RFC_CUSTOMER_GET dans le système SAP.  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>Pour modifier le projet BizTalk vPrev  
  
1.  Générer des métadonnées pour la RFC SD_RFC_CUSTOMER_GET à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous pouvez utiliser la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées.  
  
     Pour obtenir des instructions sur la façon de générer des métadonnées pour RFC, consultez [Parcourir, rechercher et obtenir des métadonnées pour les opérations de RFC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md). Une fois le schéma est généré, un fichier portant le nom semblable à *SapBindingSchema.xsd* est ajouté au projet BizTalk. Ce fichier contient le schéma pour l’appel de la SD_RFC_CUSTOMER_GET à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
2.  Générer les métadonnées pour le document RFC SD_RFC_CUSTOMER_GET crée également un fichier de liaison de port. Dans l’étape suivante, ce fichier de liaison servira à créer un port d’envoi WCF-Custom pour envoyer des messages au système SAP. L’action SOAP pour l’opération est également définie à l’opération pour laquelle vous avez généré des métadonnées. Par exemple, si vous générez des métadonnées pour le document RFC SD_RFC_CUSTOMER_GET, le nom de l’opération dans l’action SOAP sur le port d’envoi sera « SD_RFC_CUSTOMER_GET ». Toutefois, l’opération de nom sur le port d’envoi logique que vous créez lors de la partie de l’orchestration peut être différent, par exemple, « Operation_1 ». Par conséquent, lorsque vous envoyez des messages au système SAP à l’aide du port d’envoi, vous obtenez une erreur. Pour éviter ce problème, vérifiez le nom de l’opération sur la logique port d’envoi dans l’orchestration est le même que le nom de l’opération pour laquelle vous avez généré des métadonnées.  
  
     Par conséquent, dans le cas de ce didacticiel, étant donné que vous générez des métadonnées pour le document RFC SD_RFC_CUSTOMER_GET, modifiez le nom de l’opération de port d’envoi logique à « SD_RFC_CUSTOMER_GET ».  
  
3.  Pour le message de demande, mapper le schéma généré à l’aide de l’adaptateur SAP vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **RequestMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour l’adaptateur SAP vPrev. Pour ce didacticiel, sélectionnez *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*, puis cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *SD_RFC_CUSTOMER_GET_Request*, puis cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**, puis sélectionnez le schéma du message de demande pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour ce didacticiel, sélectionnez *SAP_Migration.SapBindingSchema*, puis cliquez sur OK.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *SD_RFC_CUSTOMER_GET*, puis cliquez sur **OK**.  
  
         Mapper les éléments respectifs dans les deux schémas comme illustré dans la figure suivante. Mapper l’élément CUSTOMER_T à l’aide d’un fonctoid supprimer à gauche de chaîne. Pour ce faire, à partir de la **boîte à outils**, faites glisser le **supprimer à gauche de chaîne** fonctoid et déposez-la sur la grille du mappeur. Connecter le **CUSTOMER_T** élément dans le schéma source vers le fonctoid. De même, connectez le **CUSTOMER_T** élément dans le schéma de destination vers le fonctoid. La figure suivante illustre la façon dont les deux éléments sont mappés par le fonctoid.  
  
         ![Mapper les messages de demande entre les versions d’adaptateur](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")  
  
        > [!NOTE]
        >  Pour plus d’informations sur le fonctoid supprimer à gauche de chaîne, consultez « Fonctoid enlever la chaîne de gauche » à [http://go.microsoft.com/fwlink/?LinkId=105774](http://go.microsoft.com/fwlink/?LinkId=105774).  
  
    8.  Enregistrez le mappage.  
  
4.  Pour le message de réponse, mapper le schéma généré à l’aide de l’adaptateur SAP vPrev au schéma généré à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
    1.  Ajoutez un Mappeur BizTalk au projet BizTalk. Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
         Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **les fichiers de mappage**. Dans le volet droit, sélectionnez **carte**. Spécifiez un nom pour le mappage, tel que **ResponseMap.btm**. Cliquez sur **Ajouter**.  
  
    2.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
    3.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**et sélectionnez le schéma de message de réponse pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour ce didacticiel, sélectionnez *SAP_Migration.SapBindingSchema*, puis cliquez sur **OK**.  
  
    4.  Dans le **nœud racine pour le schéma Source** boîte de dialogue, sélectionnez *SD_RFC_CUSTOMER_GETResponse*, puis cliquez sur **OK**.  
  
    5.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
    6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nom du projet, développez **schémas**et sélectionnez le schéma de message de réponse pour l’adaptateur SAP vPrev. Pour ce didacticiel, sélectionnez *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*, puis cliquez sur **OK**.  
  
    7.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez *SD_RFC_CUSTOMER_GET_Response*, puis cliquez sur **OK**.  
  
    8.  Mapper les éléments respectifs dans les deux schémas comme illustré dans la figure suivante.  
  
         ![Mapper les messages de réponse entre les versions d’adaptateur](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")  
  
    9. Enregistrez le mappage.  
  
5.  Enregistrez et générez la solution BizTalk. Avec le bouton droit de la solution, puis cliquez sur **générer la Solution**.  
  
6.  déployer la solution ; Avec le bouton droit de la solution, puis cliquez sur **déployer la Solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créer un port d’envoi WCF-Custom et configurez-le pour utiliser les mappages que vous avez créé dans cette étape, comme décrit dans [étape 2 : configurer l’Orchestration dans la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : Migration d’un projet BizTalk RFC SAP](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)