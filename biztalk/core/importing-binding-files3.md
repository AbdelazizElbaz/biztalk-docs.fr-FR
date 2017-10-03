---
title: Importation de liaison DAT3 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- target computer, cleaning
- importing binding files
- cleaning target computer
ms.assetid: 955bb3e1-3dbc-43ce-9126-205d838ae662
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1d95c40e3e556068e15a269ee4cbb7e995429a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="b2c5f-102">importation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="b2c5f-102">Importing Binding Files</span></span>
<span data-ttu-id="b2c5f-103">Avant d’utiliser le serveur BizTalk pour importer un fichier de liaison, vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b2c5f-103">Before you use the BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="b2c5f-104">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-104">The CLASSPATH is pointing to a specific location for the JD Edwards-specific files.</span></span> <span data-ttu-id="b2c5f-105">Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-105">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="b2c5f-106">Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-106">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="b2c5f-107">S'ils sont présents dans la configuration, les mots de passe du système JD Edwards sont enregistrés dans le fichier de liaison sous la forme *****.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-107">JD Edwards system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="b2c5f-108">Pour plus d’informations, consultez [limitations concernant le déploiement](../core/deployment-limitations2.md).</span><span class="sxs-lookup"><span data-stu-id="b2c5f-108">For more information, see [Deployment Limitations](../core/deployment-limitations2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2c5f-109">Déploiement remplace la configuration de l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-109">Deployment overwrites Receive Location configuration.</span></span> <span data-ttu-id="b2c5f-110">Lors du déploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur importation.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-110">When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
## <a name="importing-the-binding-files"></a><span data-ttu-id="b2c5f-111">Importation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="b2c5f-111">Importing the Binding Files</span></span>  
 <span data-ttu-id="b2c5f-112">La procédure suivante permet d'importer les fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-112">Use the following procedure to import the binding files.</span></span>  
  
#### <a name="to-import-the-binding-files"></a><span data-ttu-id="b2c5f-113">Pour importer les fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="b2c5f-113">To import the binding files</span></span>  
  
1.  <span data-ttu-id="b2c5f-114">Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server** Pour démarrer la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-114">On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="b2c5f-115">Développez successivement Administration de BizTalk Server, **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-115">Expand BizTalk Server Administration, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="b2c5f-116">Cliquez sur l’application souhaitée, pointez sur **importation**, puis cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-116">Right-click the desired application, point to **Import**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="b2c5f-117">Dans le **importer les liaisons** boîte de dialogue Parcourir et sélectionner les fichiers de liaison, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-117">In the **Import Bindings** dialog box, browse and select the binding files, and then click **Open**.</span></span>  
  
## <a name="cleaning-the-target-computer"></a><span data-ttu-id="b2c5f-118">Nettoyage de l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="b2c5f-118">Cleaning the Target Computer</span></span>  
 <span data-ttu-id="b2c5f-119">La procédure suivante permet de nettoyer l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-119">Use the following procedure to clean the target computer.</span></span>  
  
#### <a name="to-clean-the-target-computer"></a><span data-ttu-id="b2c5f-120">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="b2c5f-120">To clean the target computer</span></span>  
  
-   <span data-ttu-id="b2c5f-121">Supprimez les ports d’envoi et les emplacements de réception qui sont liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-121">Remove the send ports and the receive locations that are bound to the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c5f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2c5f-122">See Also</span></span>  
 <span data-ttu-id="b2c5f-123">[Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="b2c5f-123">[Creating JD Edwards OneWorld Send Handlers](../core/creating-jd-edwards-oneworld-send-handlers.md) </span></span>  
 [<span data-ttu-id="b2c5f-124">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="b2c5f-124">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies4.md)