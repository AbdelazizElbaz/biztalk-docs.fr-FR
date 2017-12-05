---
title: "Remplacez l’utilitaire de jeton de clé publique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Replace Public Key Token Utility
- utilities, Replace Public Key Token Utility
- public key token
ms.assetid: ed8673b9-af06-4bd7-b8b7-7371e4dd0fed
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 344b25b83060143b339a6791ecae6f3ab7028055
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="replace-public-key-token-utility"></a><span data-ttu-id="ba62d-102">Utilitaire de remplacement d'un jeton de clé publique</span><span class="sxs-lookup"><span data-stu-id="ba62d-102">Replace Public Key Token Utility</span></span>
<span data-ttu-id="ba62d-103">Cet utilitaire permet de remplacer un jeton de clé publique ou une variable d'un fichier par un jeton de clé publique dérivé d'un fichier de clé d'assembly de nom fort (.snk).</span><span class="sxs-lookup"><span data-stu-id="ba62d-103">This utility can be used to replace either a public key token or variable in a file with a public key token derived from a strong name assembly key (.snk) file.</span></span>  
  
 <span data-ttu-id="ba62d-104">Cet utilitaire peut être utile lorsqu’un développeur écrit un script qui utilise le [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md) pour déployer un assembly.</span><span class="sxs-lookup"><span data-stu-id="ba62d-104">This utility might be useful when a developer is writing a script that uses the [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) to deploy an assembly.</span></span> <span data-ttu-id="ba62d-105">Pour que le déploiement réussisse, le nom de l'assembly doit être complet et donc inclure son jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-105">For the deployment to succeed, the fully qualified name of the assembly must be provided, which includes its public key token.</span></span> <span data-ttu-id="ba62d-106">Le jeton de clé publique d'un assembly est extrait d'un fichier .snk et affecté à l'assembly lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="ba62d-106">The public key token for an assembly is extracted from an .snk file and assigned to the assembly when it is built.</span></span> <span data-ttu-id="ba62d-107">Avant que l'assembly soit déployé dans un nouvel environnement, cependant, il est souvent recréé à l'aide d'un jeton de clé publique différent.</span><span class="sxs-lookup"><span data-stu-id="ba62d-107">Before the assembly is deployed into a new environment, however, it is often rebuilt using a different public key token.</span></span> <span data-ttu-id="ba62d-108">Par conséquent, le développeur peut ne pas connaître le jeton de clé publique utilisé pour l'assembly au moment de l'exécution du script de déploiement.</span><span class="sxs-lookup"><span data-stu-id="ba62d-108">As a result, the developer may not know what public key token will be used for the assembly when the deployment script is run.</span></span>  
  
 <span data-ttu-id="ba62d-109">Il existe deux façons d'utiliser l'utilitaire de remplacement d'un jeton de clé publique pour résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="ba62d-109">There are two ways that you can use the Replace Public Key Token utility to address this situation:</span></span>  
  
-   <span data-ttu-id="ba62d-110">**Scénario 1.**</span><span class="sxs-lookup"><span data-stu-id="ba62d-110">**Scenario 1.**</span></span> <span data-ttu-id="ba62d-111">Dans le script de déploiement, le développeur peut utiliser un jeton de clé publique ou un espace réservé représentant le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-111">In the deployment script, the developer can use either a public key token or a placeholder representing the public key token.</span></span> <span data-ttu-id="ba62d-112">Avant d'exécuter le script, l'utilisateur peut exécuter l'utilitaire de remplacement d'un jeton de clé publique pour remplacer le jeton de clé publique ou l'espace réservé du fichier de script par le jeton de clé publique extrait du fichier .snk utilisé pour créer l'assembly de l'environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="ba62d-112">Before running the script, a user can run the Replace Public Key Token utility to substitute the public key token or placeholder in the script file with the public key token extracted from the .snk file that was used to build the assembly for the destination environment.</span></span>  
  
-   <span data-ttu-id="ba62d-113">**Scénario 2.**</span><span class="sxs-lookup"><span data-stu-id="ba62d-113">**Scenario 2.**</span></span> <span data-ttu-id="ba62d-114">Le développeur peut configurer le script pour qu’il remplace automatiquement le jeton de clé publique, comme suit : au début du script, appelez l’utilitaire de jeton de clé publique qu’elle pointe vers un fichier .snk qui contient le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-114">The developer can configure the script to automatically substitute the new public key token, as follows: At the start of the script, invoke the Replace Public Key Token utility and point it to a .snk file that contains the public key token.</span></span> <span data-ttu-id="ba62d-115">Dans le script, utilisez la variable d'environnement %NEWTOKEN% pour représenter le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-115">Within the script, use the environment variable %NEWTOKEN% to represent the public key token.</span></span> <span data-ttu-id="ba62d-116">Pendant l'exécution du script, l'utilitaire extrait la valeur du jeton de clé publique du fichier .snk et la définit dans une variable d'environnement %NEWTOKEN%.</span><span class="sxs-lookup"><span data-stu-id="ba62d-116">When the script runs, the utility extracts the value of the public key token from the .snk file and sets it into an environment variable %NEWTOKEN%.</span></span> <span data-ttu-id="ba62d-117">Chaque instance de la variable %NEWTOKEN% est alors remplacée par le jeton de clé publique du fichier .snk spécifié.</span><span class="sxs-lookup"><span data-stu-id="ba62d-117">When the script runs, each instance of %NEWTOKEN% will be with substituted with the public key token from the specified .snk file.</span></span> <span data-ttu-id="ba62d-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba62d-118">For example:</span></span>  
  
    ```  
    ReplacePKT.bat key.snk  
    ...  
    ...  
    gacutil /u Assembly, ... PublicKey=%NEWTOKEN% ...  
    ```  
  
## <a name="location-in-sdk"></a><span data-ttu-id="ba62d-119">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="ba62d-119">Location in SDK</span></span>  
 <span data-ttu-id="ba62d-120">L'utilitaire de remplacement d'un jeton de clé publique se trouve dans :</span><span class="sxs-lookup"><span data-stu-id="ba62d-120">The Replace Public Key Token utility is located in:</span></span>  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="ba62d-121">SDK\Utilities\ReplacePublicKeyToken\\.</span><span class="sxs-lookup"><span data-stu-id="ba62d-121">SDK\Utilities\ReplacePublicKeyToken\\.</span></span>  
  
 <span data-ttu-id="ba62d-122">Il se compose de trois fichiers :</span><span class="sxs-lookup"><span data-stu-id="ba62d-122">The Replace Public Key Token utility comprises three files:</span></span>  
  
-   <span data-ttu-id="ba62d-123">ReplacePKT.bat</span><span class="sxs-lookup"><span data-stu-id="ba62d-123">ReplacePKT.bat</span></span>  
  
-   <span data-ttu-id="ba62d-124">ReplacePKT.vbs</span><span class="sxs-lookup"><span data-stu-id="ba62d-124">ReplacePKT.vbs</span></span>  
  
-   <span data-ttu-id="ba62d-125">ReplacePKT.wsf</span><span class="sxs-lookup"><span data-stu-id="ba62d-125">ReplacePKT.wsf</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ba62d-126">Procédures</span><span class="sxs-lookup"><span data-stu-id="ba62d-126">Procedures</span></span>  
 <span data-ttu-id="ba62d-127">Procédez comme indiqué ci-dessous pour remplacer toutes les instances d'un jeton de clé publique ou d'un espace réservé d'un fichier par un jeton de clé publique extrait d'un fichier .snk (scénario 1).</span><span class="sxs-lookup"><span data-stu-id="ba62d-127">Use the following procedure to replace all instances of a public key token or a placeholder in a file with a public key token extracted from an .snk file, as described in Scenario 1.</span></span>  
  
#### <a name="to-replace-instances-of-a-public-key-token-or-a-placeholder-in-a-file"></a><span data-ttu-id="ba62d-128">Pour remplacer toutes les instances d'un jeton de clé publique ou d'un espace réservé d'un fichier</span><span class="sxs-lookup"><span data-stu-id="ba62d-128">To replace instances of a public key token or a placeholder in a file</span></span>  
  
1.  <span data-ttu-id="ba62d-129">Assurez-vous que les trois fichiers de l'utilitaire de remplacement d'un jeton de clé publique (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf), le fichier de script et le fichier .snk sont tous présents sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ba62d-129">Make sure that the three Replace Public Key Token utility files (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf), the script file, and the .snk file are all available from the local computer.</span></span>  
  
2.  <span data-ttu-id="ba62d-130">Dans une fenêtre de commande, remplacez le répertoire par le dossier contenant les fichiers de l'utilitaire de remplacement d'un jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-130">In a command window, change the directory to the folder containing the Replace Public Key utility files.</span></span>  
  
3.  <span data-ttu-id="ba62d-131">À partir d'une invite de commande, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ba62d-131">From a command prompt, run the following command:</span></span>  
  
4.  <span data-ttu-id="ba62d-132">**ReplacePKT \<**  *fichier .snk*  **\> \<**  *ancien jeton de clé publique*  **\> \<**  *fichier à remplacer***\>**</span><span class="sxs-lookup"><span data-stu-id="ba62d-132">**ReplacePKT \<** *.snk file* **\> \<** *old public key token* **\> \<** *file to replace* **\>**</span></span>  
  
    |<span data-ttu-id="ba62d-133">Option</span><span class="sxs-lookup"><span data-stu-id="ba62d-133">Option</span></span>|<span data-ttu-id="ba62d-134"> Description</span><span class="sxs-lookup"><span data-stu-id="ba62d-134">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="ba62d-135">**\<***fichier .snk***\>**</span><span class="sxs-lookup"><span data-stu-id="ba62d-135">**\<** *.snk file* **\>**</span></span>|<span data-ttu-id="ba62d-136">Chemin d'accès complet du fichier .snk contenant le jeton de clé publique que vous voulez substituer au jeton ou à l'espace réservé existant.</span><span class="sxs-lookup"><span data-stu-id="ba62d-136">Full path of the .snk file containing the public key token that you want substitute for the existing public key token or placeholder.</span></span>|  
    |<span data-ttu-id="ba62d-137">**\<***ancien jeton de clé publique***\>**</span><span class="sxs-lookup"><span data-stu-id="ba62d-137">**\<** *old public key token* **\>**</span></span>|<span data-ttu-id="ba62d-138">Jeton de clé publique ou espace réservé à remplacer.</span><span class="sxs-lookup"><span data-stu-id="ba62d-138">Public key token or placeholder that you want to replace.</span></span>|  
    |<span data-ttu-id="ba62d-139">**\<***fichier à remplacer***\>**</span><span class="sxs-lookup"><span data-stu-id="ba62d-139">**\<** *file to replace* **\>**</span></span>|<span data-ttu-id="ba62d-140">Chemin d'accès complet du fichier dans lequel vous voulez remplacer le jeton de clé publique ou l'espace réservé.</span><span class="sxs-lookup"><span data-stu-id="ba62d-140">Full path of the file in which you want to replace the public key token or placeholder.</span></span>|  
  
     <span data-ttu-id="ba62d-141">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba62d-141">Example:</span></span>  
  
     <span data-ttu-id="ba62d-142">**ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**</span><span class="sxs-lookup"><span data-stu-id="ba62d-142">**ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**</span></span>  
  
 <span data-ttu-id="ba62d-143">Procédez comme indiqué ci-dessous pour définir automatiquement une variable d'environnement de script utilisant un jeton de clé publique dérivé d'un fichier .snk (scénario 2).</span><span class="sxs-lookup"><span data-stu-id="ba62d-143">Use the following procedure to automatically set an environment variable in a script that uses a public key token derived from an .snk file, as described in Scenario 2.</span></span>  
  
#### <a name="to-set-an-environment-variable-that-uses-a-public-key-token"></a><span data-ttu-id="ba62d-144">Pour définir une variable d'environnement utilisant un jeton de clé publique</span><span class="sxs-lookup"><span data-stu-id="ba62d-144">To set an environment variable that uses a public key token</span></span>  
  
1.  <span data-ttu-id="ba62d-145">Au début du fichier de script, ajoutez la ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="ba62d-145">At the beginning of your script file, add the following line of code:</span></span>  
  
    ```  
    ReplacePKT <filename>.snk  
    ```  
  
     <span data-ttu-id="ba62d-146">Où \< *nom de fichier* \> est le nom du fichier .snk à partir de laquelle dériver le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-146">Where \<*filename*\> is the name of the .snk file from which to derive the public key token.</span></span>  
  
    ```  
    Example: ReplacePKT.bat MyToken.snk  
    ```  
  
2.  <span data-ttu-id="ba62d-147">Dans le fichier de script, utilisez `%NEWTOKEN%` pour représenter le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ba62d-147">In your script file, use `%NEWTOKEN%` to represent the public key token.</span></span>  
  
     <span data-ttu-id="ba62d-148">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba62d-148">Example:</span></span>  
  
    ```  
    PublicKey=%NEWTOKEN%  
    ```  
  
3.  <span data-ttu-id="ba62d-149">Lorsque vous fournissez le fichier de script aux utilisateurs, incluez les trois fichiers composant l'utilitaire de remplacement d'un jeton de clé publique (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf).</span><span class="sxs-lookup"><span data-stu-id="ba62d-149">When you deliver your script file to your users, include the three files that comprise the Replace Public Key Token utility (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf).</span></span> <span data-ttu-id="ba62d-150">Veillez à ce que ces utilisateurs copient tous les fichiers dans un même dossier du système avant d'exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="ba62d-150">Make sure that users of your script copy all of the files to the same folder on the file system before running your script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba62d-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba62d-151">See Also</span></span>  
 [<span data-ttu-id="ba62d-152">Utilitaires du SDK</span><span class="sxs-lookup"><span data-stu-id="ba62d-152">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)