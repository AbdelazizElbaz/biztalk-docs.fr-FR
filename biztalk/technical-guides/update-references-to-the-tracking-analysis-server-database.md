---
title: "Mettre à jour les références à la base de données de suivi Analysis Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a403325-1394-4668-946f-01b610cb686e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ed784eeca992d32f431a7c6794b7051b7595e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-references-to-the-tracking-analysis-server-database"></a><span data-ttu-id="97387-102">Mettre à jour les références à la base de données de suivi Analysis Server</span><span class="sxs-lookup"><span data-stu-id="97387-102">Update References to the Tracking Analysis Server Database</span></span>
<span data-ttu-id="97387-103">La base de données du serveur analyse des suivis est facultatif et contient les cubes de traitement analytique en ligne (OLAP).</span><span class="sxs-lookup"><span data-stu-id="97387-103">The Tracking Analysis Server database is an optional and contains the online analytical processing (OLAP) cubes.</span></span> <span data-ttu-id="97387-104">Ces cubes OLAP sont des agrégations de données contenues dans la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="97387-104">These OLAP cubes are aggregations of data contained in the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="97387-105">Pour restaurer la base de données du serveur analyse des suivis, utilisez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager pour traiter les cubes MessageMetrics et ServiceMetrics.</span><span class="sxs-lookup"><span data-stu-id="97387-105">To restore the Tracking Analysis Server database, use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager to process the MessageMetrics and ServiceMetrics cubes.</span></span> <span data-ttu-id="97387-106">Pour obtenir des instructions, consultez [la gestion de la sauvegarde et restauration (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (http://go.microsoft.com/fwlink/?LinkId=130939) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.</span><span class="sxs-lookup"><span data-stu-id="97387-106">For instructions, see [Managing Backing Up and Restoring (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (http://go.microsoft.com/fwlink/?LinkId=130939) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="97387-107">Pour restaurer la base de données du serveur analyse des suivis à un autre ordinateur, vous devez également mettre à jour les références au nom de base de données dans la base de données de gestion BizTalk à l’aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="97387-107">To restore the Tracking Analysis Server database to an alternate computer, you must also update references to the database name in the BizTalk Management database by using the following procedure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="97387-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="97387-108">Prerequisites</span></span>  
 <span data-ttu-id="97387-109">Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="97387-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-tracking-analysis-server-database-name"></a><span data-ttu-id="97387-110">Pour mettre à jour les références au nom de base de données du serveur analyse des suivis</span><span class="sxs-lookup"><span data-stu-id="97387-110">To update references to the Tracking Analysis Server database name</span></span>  
  
1.  <span data-ttu-id="97387-111">Dans le système de destination, cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008**, puis cliquez sur **deSQLServerManagementStudio**.</span><span class="sxs-lookup"><span data-stu-id="97387-111">On the destination system, click **Start**, click **Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="97387-112">Dans le **se connecter au serveur** boîte de dialogue, sélectionnez le **type de serveur** en tant que **moteur de base de données**, fournissez un nom de serveur, fournissez les informations d’identification pour se connecter ou le serveur, puis Cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="97387-112">In the **Connect to Server** dialog box, select the **Server type** as **Database Engine**, provide a server name, provide the credentials to connect ot the server, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="97387-113">Ouvrez le serveur approprié en cliquant dessus, en double-cliquant sur **bases de données**, en double-cliquant sur **BizTalkMgmtDb**, puis en cliquant sur **Tables**.</span><span class="sxs-lookup"><span data-stu-id="97387-113">Open the appropriate server by clicking it, double-clicking **Databases**, double-clicking **BizTalkMgmtDb**, and then clicking **Tables**.</span></span>  
  
4.  <span data-ttu-id="97387-114">Dans le volet détails, cliquez sur **adm_Group**, puis pointez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="97387-114">In the details pane, right-click **adm_Group**, and then point to **Open Table**.</span></span>  
  
5.  <span data-ttu-id="97387-115">Modifier les colonnes correspondant à la base de données d’origine pour référencer les valeurs appropriées pour la nouvelle base de données.</span><span class="sxs-lookup"><span data-stu-id="97387-115">Modify the columns corresponding to the original database to reference the appropriate values for the new database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97387-116">*\<DBType >* NomServeurBD et  *\<DBType >* DBName indiquer l’emplacement de la base de données, où  *\<DBType >* correspond au type de la base de données, par exemple, TrackingAnalysis.</span><span class="sxs-lookup"><span data-stu-id="97387-116">*\<DBType>* DBServerName and *\<DBType>* DBName indicate the location of the database, where *\<DBType>* corresponds to the type of the database, for example, TrackingAnalysis.</span></span>  
  
6.  <span data-ttu-id="97387-117">Fermez la table pour enregistrer les nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="97387-117">Close the table to save the new values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97387-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97387-118">See Also</span></span>  
 [<span data-ttu-id="97387-119">Mise à jour des références de base de données</span><span class="sxs-lookup"><span data-stu-id="97387-119">Updating Database References</span></span>](../technical-guides/updating-database-references.md)