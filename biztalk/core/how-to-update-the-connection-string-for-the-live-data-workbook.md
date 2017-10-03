---
title: "Comment mettre à jour la chaîne de connexion pour le classeur de données actives | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d2702fb-637c-46db-8b62-08ae15f983ba
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60de5d1ae904bdefffcf490e3a39d000b28a341d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-connection-string-for-the-live-data-workbook"></a><span data-ttu-id="0d4b0-102">Mise à jour de la chaîne de connexion pour le classeur de données actives</span><span class="sxs-lookup"><span data-stu-id="0d4b0-102">How to Update the Connection String for the Live Data Workbook</span></span>
<span data-ttu-id="0d4b0-103">Lorsque vous déplacez la base de données d'importation principale BAM vers un autre serveur, vous devez mettre à jour la chaîne de connexion contenue dans le classeur de données actives BAM pour qu'elle pointe vers le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-103">When you move the BAM Primary Import database to another server, the connection string in a BAM live data workbook must be updated to point to the new server.</span></span> <span data-ttu-id="0d4b0-104">Pour ce faire, vous pouvez utiliser le complément BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-104">You use the BAM Add-in for Excel to make this update.</span></span>  
  
### <a name="to-update-the-live-data-workbook-to-point-to-a-new-server"></a><span data-ttu-id="0d4b0-105">Pour mettre à jour le classeur de données actives pour qu'il pointe vers le nouveau serveur</span><span class="sxs-lookup"><span data-stu-id="0d4b0-105">To update the live data workbook to point to a new server</span></span>  
  
1.  <span data-ttu-id="0d4b0-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-106">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="0d4b0-107">Cliquez sur le **fichier** menu, puis sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-107">Click the **File** menu, and then click **Open**.</span></span> <span data-ttu-id="0d4b0-108">Accédez à votre classeur de données actives BAM, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-108">Navigate to your BAM lived data workbook and click **Open**.</span></span>  
  
3.  <span data-ttu-id="0d4b0-109">Cliquez sur le **BAM** menu dans le **compléments** onglet, puis cliquez sur **connexion DB BAM** pour ouvrir le **sélectionner la base de données BAM** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-109">Click the **BAM** menu in the **Add-Ins** tab, and then click **BAM DB Connection** to open the **Select BAM Database** dialog box.</span></span>  
  
4.  <span data-ttu-id="0d4b0-110">Dans le **SQL Server** texte, tapez le nom du serveur SQL sur lequel l’importation principale BAM de base de données maintenant réside.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-110">In the **SQL Server** text box, type the name of the SQL server on which the BAM Primary Import database now resides.</span></span>  
  
5.  <span data-ttu-id="0d4b0-111">Sélectionnez la base de données d’importation principale BAM à partir de la **nom de la base de données** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-111">Select the BAM Primary Import database from the **Database Name** drop-down list.</span></span>  
  
6.  <span data-ttu-id="0d4b0-112">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-112">Click **OK** to close the dialog box.</span></span>  
  
7.  <span data-ttu-id="0d4b0-113">Enregistrez le classeur.</span><span class="sxs-lookup"><span data-stu-id="0d4b0-113">Save the workbook.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4b0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d4b0-114">See Also</span></span>  
 <span data-ttu-id="0d4b0-115">[La gestion BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="0d4b0-115">[Managing BAM](../core/managing-bam.md) </span></span>  
 [<span data-ttu-id="0d4b0-116">Configuration requise pour utiliser le complément BAM pour Excel</span><span class="sxs-lookup"><span data-stu-id="0d4b0-116">Requirements for Using the BAM Add-In for Excel</span></span>](../core/requirements-for-using-the-bam-add-in-for-excel.md)