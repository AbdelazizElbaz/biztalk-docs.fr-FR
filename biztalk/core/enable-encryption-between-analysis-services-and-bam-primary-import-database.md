---
title: "Comment activer le chiffrement entre Analysis Services et la base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Analysis Services, enabling encryption
- Primary Import database [BAM], SQL Server Analysis Services
- Primary Import database [BAM], enabling encryption
- SQL Server Analysis Services, Primary Import database [BAM]
ms.assetid: 8107c557-e57c-4569-9ff7-abcb7a8e5243
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77069c3690a73957936c786bc05c2690b9df7a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-encryption-between-analysis-services-and-the-bam-primary-import-database"></a><span data-ttu-id="a6eda-102">Activation du chiffrement entre Analysis Services et la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="a6eda-102">How to Enable Encryption Between Analysis Services and the BAM Primary Import Database</span></span>
<span data-ttu-id="a6eda-103">Durant l'installation ou la mise à niveau de l'analyse BAM, le chiffrement n'est pas activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="a6eda-103">Encryption is not enabled by default during an installation or upgrade of BAM.</span></span> <span data-ttu-id="a6eda-104">Pour activer le chiffrement, vous devez définir l'indicateur UseEncryption du fichier XML de configuration BAM sur la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="a6eda-104">To enable encryption, you must set the UseEncryption flag in the BAM configuration XML file to a value of 1.</span></span>  
  
 <span data-ttu-id="a6eda-105">Vous devez aussi activer le chiffrement dans SQL Server Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="a6eda-105">You must also enable encryption in SQL Server Analysis Services.</span></span> <span data-ttu-id="a6eda-106">Pour plus d’informations sur l’activation du chiffrement, consultez [sécurisation des communications Client avec une Instance Analysis Services](http://go.microsoft.com/fwlink/?LinkId=190805) (http://go.microsoft.com/fwlink/?LinkId=190805).</span><span class="sxs-lookup"><span data-stu-id="a6eda-106">For more information about enabling encryption, see [Securing Client Communication with an Analysis Services Instance](http://go.microsoft.com/fwlink/?LinkId=190805) (http://go.microsoft.com/fwlink/?LinkId=190805).</span></span>  
  
### <a name="to-enable-encryption-between-sql-server-analysis-services-and-the-bam-primary-import-database"></a><span data-ttu-id="a6eda-107">Pour activer le chiffrement entre SQL Server Analysis Services et la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="a6eda-107">To enable encryption between SQL Server Analysis Services and the BAM Primary Import Database</span></span>  
  
1.  <span data-ttu-id="a6eda-108">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6eda-108">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="a6eda-109">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6eda-109">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3.  <span data-ttu-id="a6eda-110">Type **bm get-config - FileName :\<fichier de sortie >**.</span><span class="sxs-lookup"><span data-stu-id="a6eda-110">Type **bm get-config -FileName:\<output file>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6eda-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a6eda-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="a6eda-112">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="a6eda-112">Press **ENTER**.</span></span>  
  
5.  <span data-ttu-id="a6eda-113">Ouvrez le fichier de configuration de fichier que vous avez exporté dans un éditeur de texte, puis définissez la valeur de l'indicateur de propriété UseEncryption sur 1.</span><span class="sxs-lookup"><span data-stu-id="a6eda-113">Open the file configuration file that you have exported in a text editor and change the value of the UseEncryption property flag to 1.</span></span>  
  
    -   <span data-ttu-id="a6eda-114">Paramètre par défaut : \<nom de la propriété = « UseEncryption » > 0\<cette propriété ></span><span class="sxs-lookup"><span data-stu-id="a6eda-114">Default Setting: \<Property Name="UseEncryption">0\</Property></span></span>  
  
    -   <span data-ttu-id="a6eda-115">Nouveau paramètre : \<nom de la propriété = « UseEncryption » > 1\<cette propriété ></span><span class="sxs-lookup"><span data-stu-id="a6eda-115">New Setting: \<Property Name="UseEncryption">1\</Property></span></span>  
  
6.  <span data-ttu-id="a6eda-116">Mettre à jour la configuration BAM en tapant **bm update-config - FileName :\<le fichier de configuration >**.</span><span class="sxs-lookup"><span data-stu-id="a6eda-116">Update the BAM configuration by typing **bm update-config -FileName:\<config file>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6eda-117">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a6eda-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6eda-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6eda-118">See Also</span></span>  
 [<span data-ttu-id="a6eda-119">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="a6eda-119">BAM Management Utility</span></span>](../core/bam-management-utility.md)