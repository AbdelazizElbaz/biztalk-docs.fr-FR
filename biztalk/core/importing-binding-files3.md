---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 5c5cce40f3fbeb580ec7ba854d02cb243e1742b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="97d28-101">importation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="97d28-101">Importing Binding Files</span></span>

## <a name="overview"></a><span data-ttu-id="97d28-102">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="97d28-102">Overview</span></span>
<span data-ttu-id="97d28-103">Avant d’utiliser le serveur BizTalk pour importer un fichier de liaison, vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="97d28-103">Before you use the BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="97d28-104">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards.</span><span class="sxs-lookup"><span data-stu-id="97d28-104">The CLASSPATH is pointing to a specific location for the JD Edwards-specific files.</span></span> <span data-ttu-id="97d28-105">Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="97d28-105">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="97d28-106">Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="97d28-106">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="97d28-107">S'ils sont présents dans la configuration, les mots de passe du système JD Edwards sont enregistrés dans le fichier de liaison sous la forme *****.</span><span class="sxs-lookup"><span data-stu-id="97d28-107">JD Edwards system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="97d28-108">Déploiement remplace la configuration de l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="97d28-108">Deployment overwrites Receive Location configuration.</span></span> <span data-ttu-id="97d28-109">Lors du déploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur importation.</span><span class="sxs-lookup"><span data-stu-id="97d28-109">When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
## <a name="import-the-binding-files"></a><span data-ttu-id="97d28-110">Importer les fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="97d28-110">Import the Binding Files</span></span>  
  
1.  <span data-ttu-id="97d28-111">Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server** Pour démarrer la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="97d28-111">On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="97d28-112">Développez successivement Administration de BizTalk Server, **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="97d28-112">Expand BizTalk Server Administration, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="97d28-113">Cliquez sur l’application souhaitée, pointez sur **importation**, puis cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="97d28-113">Right-click the desired application, point to **Import**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="97d28-114">Dans le **importer les liaisons** boîte de dialogue Parcourir et sélectionner les fichiers de liaison, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="97d28-114">In the **Import Bindings** dialog box, browse and select the binding files, and then click **Open**.</span></span>  
  
## <a name="cleaning-the-target-computer"></a><span data-ttu-id="97d28-115">Nettoyage de l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="97d28-115">Cleaning the Target Computer</span></span>  
<span data-ttu-id="97d28-116">Supprimez les ports d’envoi et les emplacements de réception qui sont liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="97d28-116">Remove the send ports and the receive locations that are bound to the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d28-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97d28-117">See Also</span></span>  
 <span data-ttu-id="97d28-118">[Ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="97d28-118">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="97d28-119">Importer le JD Edwards OneWorld application</span><span class="sxs-lookup"><span data-stu-id="97d28-119">Import the JD Edwards OneWorld app</span></span>](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)