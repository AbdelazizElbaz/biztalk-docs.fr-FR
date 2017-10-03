---
title: "Comment récupérer le fichier de Configuration BAM à l’aide de l’utilitaire de gestion BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ce5e0c-467a-486c-8eec-217a2a26d7b4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb7dee70d3a5b8dc7226203df9f48aefe1d5fc0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a><span data-ttu-id="0eaa1-102">Extraction du fichier de configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="0eaa1-102">How to Retrieve the BAM Configuration File Using the BAM Management Utility</span></span>
<span data-ttu-id="0eaa1-103">Les administrateurs et les développeurs peuvent utiliser l'utilitaire de gestion de l'analyse BAM pour récupérer la configuration existante de l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="0eaa1-103">Administrators and developers can use the BAM Management utility to retrieve the current configuration of the BAM infrastructure.</span></span> <span data-ttu-id="0eaa1-104">La configuration récupérée peut être utilisée pour migrer une installation BAM sur un nouveau serveur. Elle peut également être modifiée et utilisée pour mettre à jour une installation BAM existante.</span><span class="sxs-lookup"><span data-stu-id="0eaa1-104">The retrieved configuration can be used to migrate a BAM installation to a new server or it can be modified and used to update an existing BAM installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0eaa1-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0eaa1-105">Prerequisites</span></span>  
 <span data-ttu-id="0eaa1-106">La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0eaa1-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="0eaa1-107">Bases de données BAM configurées</span><span class="sxs-lookup"><span data-stu-id="0eaa1-107">Configured BAM databases</span></span>  
  
-   <span data-ttu-id="0eaa1-108">Autorisations de lecture dans la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="0eaa1-108">Permissions to read the BAM Primary Import database</span></span>  
  
### <a name="to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a><span data-ttu-id="0eaa1-109">Pour extraire le fichier de configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="0eaa1-109">To retrieve the BAM configuration file using the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="0eaa1-110">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0eaa1-110">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="0eaa1-111">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="0eaa1-111">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="0eaa1-112">Tapez la commande suivante à l’invite de ligne de commande : **bm get-config - FileName :\<fichier de sortie >**, où \< *fichier de sortie*> est remplacé par le nom de votre configuration d’analyse BAM fichier.</span><span class="sxs-lookup"><span data-stu-id="0eaa1-112">Type the following at the command line prompt: **bm get-config -FileName:\<output file>**, where \<*output file*> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="0eaa1-113">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="0eaa1-113">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eaa1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eaa1-114">See Also</span></span>  
 [<span data-ttu-id="0eaa1-115">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="0eaa1-115">BAM Management Utility</span></span>](../core/bam-management-utility.md)