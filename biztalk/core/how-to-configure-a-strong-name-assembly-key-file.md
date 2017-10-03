---
title: "Comment configurer un fichier de clé de nom fort Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778a8ec-f5f7-4ae1-a57e-99f6503f044c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e77f72effa1a9c9193f9ce589ebe22b65feb5a85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-strong-name-assembly-key-file"></a><span data-ttu-id="f4ee6-102">Configuration d'un fichier de clé d'assembly de nom fort</span><span class="sxs-lookup"><span data-stu-id="f4ee6-102">How to Configure a Strong Name Assembly Key File</span></span>
<span data-ttu-id="f4ee6-103">Au cours du processus de déploiement d'une solution BizTalk, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] commence par créer les assemblys.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-103">In the process of deploying a BizTalk solution, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] first builds the assemblies.</span></span> <span data-ttu-id="f4ee6-104">Le processus de déploiement requiert la signature avec un nom fort de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-104">The deployment process requires that each assembly is strongly signed.</span></span> <span data-ttu-id="f4ee6-105">Vous pouvez fortement signer vos assemblys en associant le projet avec un fichier de clé de nom fort assembly.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-105">You can strongly sign your assemblies by associating the project with a strong name assembly key file.</span></span> <span data-ttu-id="f4ee6-106">Si ce n'est pas déjà fait, avant de déployer une solution à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], effectuez la procédure suivante pour générer un fichier de clé d'assembly de nom fort et l'attribuer à chaque projet de la solution.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-106">If you haven't already done so, before deploying a solution from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], use the following procedure to generate a strong name assembly key file and assign it to each project in the solution.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f4ee6-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f4ee6-107">Prerequisites</span></span>  
 <span data-ttu-id="f4ee6-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4ee6-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator's group.</span></span> <span data-ttu-id="f4ee6-109">Votre compte doit également disposer d'une autorisation en écriture sur le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="f4ee6-109">In addition, your account must have Write permissions on the global assembly cache (GAC).</span></span> <span data-ttu-id="f4ee6-110">Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-110">The Administrators account on the local computer has this permission.</span></span>  
  
### <a name="to-configure-a-strong-name-assembly-key-file"></a><span data-ttu-id="f4ee6-111">Pour configurer un fichier de clé d'assembly de nom fort</span><span class="sxs-lookup"><span data-stu-id="f4ee6-111">To configure a strong name assembly key file</span></span>  
  
1.  <span data-ttu-id="f4ee6-112">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-112">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="f4ee6-113">À l'invite de commandes, à partir du dossier dans lequel vous voulez stocker le fichier de clé, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="f4ee6-113">At the command prompt, from the folder where you want to store the key file, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="f4ee6-114">**sn /k***nom_fichier* **.snk** </span><span class="sxs-lookup"><span data-stu-id="f4ee6-114">**sn /k**  *file_name* **.snk**</span></span>  
  
     <span data-ttu-id="f4ee6-115">Exemple : **sn /k ErrorHandling.snk**</span><span class="sxs-lookup"><span data-stu-id="f4ee6-115">Example: **sn /k ErrorHandling.snk**</span></span>  
  
     <span data-ttu-id="f4ee6-116">Un message de confirmation, **paire écrite dans la clé** \< *nom_fichier*>**.snk** `,` affiche sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-116">A confirmation message, **Key pair written to** \<*file_name*>**.snk**`,` displays on the command line.</span></span>  
  
3.  <span data-ttu-id="f4ee6-117">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur le projet, puis **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the project and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f4ee6-118">Cliquez sur le **signature** onglet et sélectionnez **Parcourir** dans les **choisir un fichier de clé de nom fort** zone déroulante.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-118">Click the **Signing** tab and choose **Browse** in the **Choose a strong name key file** drop down box.</span></span>  
  
5.  <span data-ttu-id="f4ee6-119">Accédez au fichier de clé, puis cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-119">Browse to the key file and click it.</span></span> <span data-ttu-id="f4ee6-120">Cliquez sur **ouvrez**, puis fermez les propriétés du projet.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-120">Click **Open**, and then close the project properties.</span></span>  
  
6.  <span data-ttu-id="f4ee6-121">Répétez les étapes 3 à 6 pour chaque projet dans la solution que vous souhaitez déployer à l’aide de ce fichier de clé de nom fort assembly.</span><span class="sxs-lookup"><span data-stu-id="f4ee6-121">Repeat steps 3 through 6 for each project in the solution that you want to deploy using this strong name assembly key file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ee6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4ee6-122">See Also</span></span>  
 [<span data-ttu-id="f4ee6-123">Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="f4ee6-123">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)