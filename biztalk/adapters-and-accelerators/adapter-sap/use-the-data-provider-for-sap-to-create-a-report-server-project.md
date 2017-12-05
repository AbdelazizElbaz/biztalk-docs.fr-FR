---
title: "Utiliser le fournisseur de données pour SAP pour créer un projet Report Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fe985b5-ba67-4179-a31c-4f41106c32be
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c7905fc7114feeca8b53589e1aa32a09495ca1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-the-data-provider-for-sap-to-create-a-report-server-project"></a>Utiliser le fournisseur de données pour SAP pour créer un projet Report Server
Vous devez créer un serveur de rapports de projet, à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], afin de générer des rapports pour les données disponibles dans un système SAP. Cette rubrique fournit des instructions sur la création d’un projet Report Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que vous avez installé le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] lors de l’installation du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation. Pour plus d’informations sur [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, consultez le guide d’installation disponible à l’adresse \< *lecteur d’installation*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
  
### <a name="to-create-a-report-server-project"></a>Pour créer un projet Report Server  
  
1.  Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et créer un projet Report Server. Pour créer un projet Report Server, procédez comme suit :  
  
    1.  Cliquez sur le **fichier** menu, cliquez sur **nouveau**, puis cliquez sur **projet**.  
  
    2.  Dans le **nouveau projet** boîte de dialogue, à partir de la **types de projet** liste, sélectionnez **projets Business Intelligence**. À partir de **modèles installés de Visual Studio** liste, sélectionnez **projet Report Server**.  
  
    3.  Spécifiez un nom et l’emplacement du projet, cliquez sur **OK**. Pour cette rubrique, spécifiez le nom du projet en tant que `SAP_ Report`.  
  
2.  Ajouter une nouvelle source de données :  
  
    1.  À partir de l’Explorateur de solutions, cliquez sur **Sources de données partagées**, puis cliquez sur **ajouter une nouvelle Source de données**.  
  
    2.  Dans le **Source de données partagée** boîte de dialogue le **général** onglet, spécifiez un nom pour la source de données. Pour cette rubrique, spécifiez le nom de `SAPDataSource`.  
  
    3.  À partir de la **Type** liste, sélectionnez **fournisseur de données pour SAP**.  
  
    4.  Dans le **chaîne de connexion** , spécifiez la chaîne de connexion pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. Pour plus d’informations sur la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
         ![Créer une source de données](../../adapters-and-accelerators/adapter-sap/media/8494c1a5-5e68-4178-a005-a6ea56d97ad7.gif "8494c1a5-5e68-4178-a005-a6ea56d97ad7")  
  
        > [!NOTE]
        >  Vous pouvez choisir spécifier les informations d’identification dans le cadre de la chaîne de connexion ou les comme décrit dans l’étape suivante.  
  
    5.  Dans le **informations d’identification** onglet, choisissez une des valeurs suivantes, puis cliquez sur **OK**:  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Utiliser un nom d'utilisateur et un mot de passe spécifiques**|Spécifiez un nom d’utilisateur et un mot de passe pour se connecter au système SAP.|  
        |**Invite pour les informations d’identification**|Entrez les informations d’identification pour le système SAP, tandis que le rapport est généré. **Remarque :** les informations d’identification que vous spécifiez pour cette option remplace les informations d’identification, si spécifié, dans le cadre de la chaîne de connexion.|  
        |**Aucune information d’identification**|Choisissez cette option si vous fournissez le nom d’utilisateur et un mot de passe dans le cadre de la chaîne de connexion.|  
  
        > [!NOTE]
        >  Le mode d’authentification Windows n’est pas prise en charge pour les projets du serveur de rapports.  
  
3.  Ajouter un nouveau rapport :  
  
    1.  À partir de l’Explorateur de solutions, cliquez sur **rapports**, puis cliquez sur **ajouter un nouveau rapport**.  
  
         Cela démarre l’Assistant rapport.  
  
    2.  Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.  
  
    3.  Dans le **sélectionner la Source de données** boîte de dialogue, choisissez le **source de données partagée** option, sélectionnez le **SAPDataSource** vous créé à l’étape précédente, puis cliquez sur  **Suivant**.  
  
    4.  Si vous avez choisi le **demander les informations d’identification** permettant de spécifier les informations d’identification de l’utilisateur lors de la création de la source de données, un **Entrez les informations d’identification de données Source** boîte de dialogue s’affiche. Spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP, puis cliquez sur **OK**.  
  
         Si vous avez choisi une autre option permettant de spécifier les informations d’identification, l’Assistant passe à l’étape suivante.  
  
    5.  Dans le **concevoir la requête** boîte de dialogue, spécifiez une chaîne de requête qui est utilisée pour générer un rapport. Exemple :  
  
        ```  
        SELECT TOP 2 KUNNR, NAME1 FROM KNA1 WHERE NAME1 LIKE @PARAM  
        ```  
  
         Cette requête récupère les deux enregistrements supérieur de la table KNA1 où le NAME1 est le nom que vous spécifiez lors de la génération du rapport.  
  
         Cliquez sur **Suivant**.  
  
    6.  Dans les boîtes de dialogue suivantes, vous pouvez concevoir le format dans lequel vous souhaitez que le rapport s’affiche. Si vous souhaitez utiliser le format par défaut, cliquez sur **Terminer >> &#124;** pour accéder directement à la **Terminer** boîte de dialogue.  
  
    7.  Dans le **fin de l’Assistant** boîte de dialogue, spécifiez un nom pour le rapport, passez en revue le résumé, puis cliquez sur **Terminer**. Pour cette rubrique, spécifiez le nom du rapport en tant que `SAPReport`.  
  
     Vous pouvez maintenant afficher le rapport. Pour obtenir des instructions sur la façon d’afficher le rapport, consultez [afficher les rapports pour SAP](../../adapters-and-accelerators/adapter-sap/view-the-reports-for-sap.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données pour SAP avec SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)