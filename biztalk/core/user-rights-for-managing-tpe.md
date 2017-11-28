---
title: "Droits d’utilisateur pour la gestion de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Tracking Profile Editor
- Tracking Profile Editor, security
ms.assetid: a0353c4d-2aaa-49ac-8e50-88885962abba
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3319a807b1357201dade0c53d04c26146c2b1e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="user-rights-for-managing-tpe"></a><span data-ttu-id="a348b-102">Droits d'utilisateur pour la gestion de l'Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="a348b-102">User Rights for Managing TPE</span></span>
<span data-ttu-id="a348b-103">Les développeur de solutions, les administrateurs système ou le personnel de services informatiques ou de back office doivent disposer de droits d'administration pour extraire ou déployer le modèle de suivi dans une base de données associée à un assembly.</span><span class="sxs-lookup"><span data-stu-id="a348b-103">Solution developers, system administrators, or IT/Operations personnel must have administrative rights to retrieve or deploy the tracking profile into a database associated with an assembly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a348b-104">Vous ne pouvez pas vous servir de l'Éditeur de modèle de suivi pour définir des rôles d'utilisateur ou accorder ou refuser des autorisations d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a348b-104">You cannot define user roles or grant or deny user permissions using Tracking Profile Editor (TPE).</span></span> <span data-ttu-id="a348b-105">Vous pouvez uniquement définir ces rôles d'utilisateur et les autorisations associées dans Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a348b-105">You can only define these user roles and associated permissions in Microsoft SQL Server.</span></span>  
  
 <span data-ttu-id="a348b-106">Grâce à l'Éditeur de modèle de suivi, les administrateurs peuvent :</span><span class="sxs-lookup"><span data-stu-id="a348b-106">With TPE, administrators can:</span></span>  
  
-   <span data-ttu-id="a348b-107">Extraire un modèle de suivi actif associé à un ou plusieurs assemblys à partir de la base de données de gestion BizTalk</span><span class="sxs-lookup"><span data-stu-id="a348b-107">Retrieve an active tracking profile associated with one or more assemblies from the BizTalk Management database</span></span>  
  
-   <span data-ttu-id="a348b-108">Modifier le modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="a348b-108">Modify the tracking profile</span></span>  
  
-   <span data-ttu-id="a348b-109">Appliquer un nouveau modèle de suivi ou un modèle de suivi modifié dans la base de données de gestion BizTalk</span><span class="sxs-lookup"><span data-stu-id="a348b-109">Apply a new or modified tracking profile into the BizTalk Management database</span></span>  
  
-   <span data-ttu-id="a348b-110">Modifier des fichiers de modèle de suivi enregistrés (.btt)</span><span class="sxs-lookup"><span data-stu-id="a348b-110">Modify saved tracking profile files (.btt)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a348b-111">Les fichiers de modèle de suivi ne constituent pas l'instance finale présidant au contenu d'un modèle.</span><span class="sxs-lookup"><span data-stu-id="a348b-111">Tracking profile files are not the final authority on the contents of a profile.</span></span> <span data-ttu-id="a348b-112">L'Éditeur de modèle de suivi peut enregistrer un modèle dans un fichier même si ses principales attributions sont l'extraction du contenu du modèle des bases de données BizTalk Server et BAM et la publication de ce dernier dans ces mêmes bases de données.</span><span class="sxs-lookup"><span data-stu-id="a348b-112">TPE can save a profile to a file, although it primarily pulls from and publishes the profile contents to the BizTalk Server and BAM databases.</span></span> <span data-ttu-id="a348b-113">Les fichiers de modèle de suivi peuvent toujours être utilisés pour modifier ou mettre à jour le modèle stocké tant que leur contenu correspond aux informations stockées dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="a348b-113">Tracking profile files can still be used to edit or update the stored profile as long as the file contents match the information stored in the databases.</span></span> <span data-ttu-id="a348b-114">De plus, les fichiers de modèle de suivi peuvent être intégrés à un package d'application BizTalk Sever.</span><span class="sxs-lookup"><span data-stu-id="a348b-114">In addition, tracking profile files can be packaged within a BizTalk Server application package.</span></span> <span data-ttu-id="a348b-115">Les packages d’applications qui incluent des fichiers de profil de suivi automatiquement appellent BTTDeploy.exe pour appliquer le modèle de suivi lorsque le package MSI est importé dans une installation de BizTalk Server donnée.</span><span class="sxs-lookup"><span data-stu-id="a348b-115">Application packages that include tracking profile files automatically invoke BTTDeploy.exe to apply the tracking profile when the MSI package is imported to a given BizTalk Server installation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a348b-116">Dans le workflow de l'Éditeur de modèle de suivi, en supposant, comme c'est généralement le cas, que les tâches de développement et de déploiement sont séparées, la personne responsable du déploiement doit disposer d'un accès en lecture seule au fichier .btt et au fichier d'assembly associé.</span><span class="sxs-lookup"><span data-stu-id="a348b-116">In the TPE workflow, assuming the development and deployment tasks are separated, as is typically the case, the person responsible for deployment should have read-only access to the .btt file and the associated assembly file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a348b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a348b-117">See Also</span></span>  
 <span data-ttu-id="a348b-118">[Flux de travail BAM](../core/bam-workflow.md) </span><span class="sxs-lookup"><span data-stu-id="a348b-118">[BAM Workflow](../core/bam-workflow.md) </span></span>  
 [<span data-ttu-id="a348b-119">Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="a348b-119">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)