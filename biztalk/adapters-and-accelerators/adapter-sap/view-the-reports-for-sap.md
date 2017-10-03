---
title: Afficher les rapports pour SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0932ffc5-cde0-4d14-822f-713b760c3f12
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d446a24ca9432842d52062acb494f92060bbaaf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="view-the-reports-for-sap"></a>Afficher les rapports pour SAP
Après avoir créé le rapport, vous pouvez l’afficher à l’aide de Visual Studio ou de l’héberger sur le serveur de rapports sur Internet Information Services (IIS) et l’accès sur le réseau. Cette rubrique fournit des instructions sur la façon d’afficher des rapports à la fois dans Visual Studio et à l’aide d’IIS.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’effectuer les procédures fournies dans cette rubrique, vous devez avoir généré un rapport comme décrit dans [utiliser le fournisseur de données pour SAP pour créer un projet Report Server](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md).  
  
### <a name="to-view-the-reports-in-visual-studio"></a>Pour afficher les rapports dans Visual Studio  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue pages de propriétés de rapport, cliquez sur **Configuration Manager**et désactivez la case à cocher sous la **déployer** colonne. Cliquez sur **Fermer**.  
  
3.  Dans la boîte de dialogue pages de propriétés de rapport, pour le **StartItem** propriété, sélectionnez le nom du rapport, puis cliquez sur **OK**.  
  
     ![Spécifier des propriétés pour le projet Report Server](../../adapters-and-accelerators/adapter-sap/media/b3c500f7-840d-461f-945c-66db239d81b9.gif "b3c500f7-840d-461f-945c-66db239d81b9")  
  
4.  Cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **Build**.  
  
5.  Appuyez sur `F5` pour exécuter le projet pour générer le rapport.  
  
    > [!IMPORTANT]
    >  Dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], vous pouvez voir le rapport en cliquant sur le **aperçu** onglet. Dans ce cas, les boîtes de dialogue suivantes seront ouvre dans l’onglet Aperçu.  
  
6.  Ouvre une boîte de dialogue avec le même nom que vous avez spécifié pour le rapport. Lors de la création de la source de données, si vous avez choisi le **demander les informations d’identification** option, entrez le nom d’utilisateur et un mot de passe pour le système SAP, puis cliquez sur **afficher le rapport**.  
  
     ![Spécifiez les informations d’identification SAP pour générer un rapport](../../adapters-and-accelerators/adapter-sap/media/fa831aae-b2d1-4ba2-a23f-f7beeb8f898e.gif "fa831aae-b2d1-4ba2-a23f-f7beeb8f898e")  
  
7.  Si la requête que vous avez spécifié lors de la création du projet de serveur de rapports requiert un paramètre, vous devez entrer la valeur du paramètre. Par exemple, pour la requête spécifiée dans le [utiliser le fournisseur de données pour SAP pour créer un projet Report Server](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) rubrique, vous devez spécifier une valeur pour le paramètre, les PARAM.  
  
     Spécifiez la valeur du paramètre, si nécessaire, puis cliquez sur **afficher le rapport**.  
  
     ![Spécifiez des paramètres pour générer un rapport](../../adapters-and-accelerators/adapter-sap/media/5deec152-771b-46b4-84da-dd176193d7f3.gif "5deec152-771b-46b4-84da-dd176193d7f3")  
  
### <a name="to-host-the-reports-on-report-server"></a>Pour héberger les rapports sur le serveur de rapports  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue pages de propriétés de rapport, cliquez sur **Configuration Manager**, puis sélectionnez la case à cocher sous la **déployer** colonne. Cliquez sur **Fermer**.  
  
3.  Dans la boîte de dialogue pages de propriétés de rapport, pour le **StartItem** propriété, sélectionnez le nom du rapport.  
  
4.  Dans la boîte de dialogue pages de propriétés de rapport, pour le **TargetServerURL** propriété, spécifiez une URL pour le serveur de rapports, puis cliquez sur **OK**. Exemple :  
  
    ```  
    http://localhost/reportserver  
    ```  
  
     ![Spécifiez l’URL du serveur de rapports](../../adapters-and-accelerators/adapter-sap/media/397ddfd6-f3d2-4327-9bc3-1efa22dc2249.gif "397ddfd6-f3d2-4327-9bc3-1efa22dc2249")  
  
5.  Cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **Build**.  
  
6.  Cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **déployer**.  
  
7.  Démarrez les services IIS. Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `inetmgr`, puis appuyez sur `Enter`.  
  
8.  Dans le **Gestionnaire des Services Internet (IIS)** -composant logiciel enfichable, développez le nom de l’ordinateur, **Sites Web**, développez **Site Web par défaut**, avec le bouton droit  **ReportServer**, puis cliquez sur **Parcourir**.  
  
9. Dans le volet droit, cliquez sur le nom du projet, puis cliquez sur le nom du rapport.  
  
10. Lors de la création de la source de données, si vous avez choisi le **demander les informations d’identification** option, entrez le nom d’utilisateur et un mot de passe pour le système SAP, cliquez sur **afficher le rapport**.  
  
11. Si la requête que vous avez spécifié lors de la création du projet de serveur de rapports requiert un paramètre, vous devez entrer la valeur du paramètre. Par exemple, pour la requête spécifiée dans le [utiliser le fournisseur de données pour SAP pour créer un projet Report Server](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) rubrique, vous devez spécifier une valeur pour le paramètre, les PARAM.  
  
     Spécifiez la valeur du paramètre, si nécessaire, puis cliquez sur **afficher le rapport**.  
  
     ![Spécifiez des paramètres pour générer un rapport](../../adapters-and-accelerators/adapter-sap/media/221c8c12-4e4f-47f5-9289-9e9212cf6e25.gif "221c8c12-4e4f-47f5-9289-9e9212cf6e25")  
  
    > [!TIP]
    >  Vous pouvez également afficher directement à partir du navigateur web en fournissant l’URL pour le rapport. Une URL standard pour le rapport `is http://localhohost/reportserver/<report_name>`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données pour SAP avec SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)