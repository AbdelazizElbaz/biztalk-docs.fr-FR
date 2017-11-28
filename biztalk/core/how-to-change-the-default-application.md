---
title: "Comment modifier l’Application par défaut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, default
- applications, modifying
- modifying, applications
ms.assetid: cfa5e88f-0bbb-4edd-a840-722dcdcce266
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33b4ffb6fbbb2463b20a7d344d0f7f27811de23b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-default-application"></a><span data-ttu-id="0238c-102">Comment modifier l’Application par défaut</span><span class="sxs-lookup"><span data-stu-id="0238c-102">How to Change the Default Application</span></span>
<span data-ttu-id="0238c-103">Cette rubrique décrit comment changer d'application par défaut en modifiant les propriétés d'une application dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0238c-103">This topic describes how to change the default application by editing the properties of an application in the BizTalk Server Administration console.</span></span> <span data-ttu-id="0238c-104">Vous pouvez également modifier l’application par défaut en créant une nouvelle application et en spécifiant que l’application par défaut, comme décrit dans [la création d’une Application](../core/how-to-create-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="0238c-104">You can also change the default application by creating a new application and specifying it as the default application, as described in [How to Create an Application](../core/how-to-create-an-application.md).</span></span>  
  
 <span data-ttu-id="0238c-105">Lorsque vous installez BizTalk Server, une application par défaut baptisée BizTalk Application 1 est créée dans la base de données de gestion BizTalk et apparaît dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0238c-105">When you install BizTalk Server, a default application named BizTalk Application 1 is created in the BizTalk Management database and appears in the BizTalk Server Administration console.</span></span> <span data-ttu-id="0238c-106">Lorsque vous effectuez une mise à niveau d'une version antérieure de BizTalk Server, vos artefacts sont automatiquement placés dans cette application.</span><span class="sxs-lookup"><span data-stu-id="0238c-106">When you upgrade from an earlier version of BizTalk Server, your artifacts are automatically placed in this application.</span></span> <span data-ttu-id="0238c-107">En outre, si vous importez un fichier Windows Installer (.msi) à l'aide de BTSTask sans spécifier d'application, les artefacts de ce fichier .msi sont importés dans l'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="0238c-107">In addition, when you import a Windows Installer (.msi) file by using BTSTask without specifying an application, the artifacts in the .msi file are imported into the default application.</span></span>  
  
 <span data-ttu-id="0238c-108">Vous n'êtes pas autorisé à supprimer l'application par défaut, vous ne pouvez qu'en changer.</span><span class="sxs-lookup"><span data-stu-id="0238c-108">You cannot delete the default application; however, you can change which application is the default.</span></span> <span data-ttu-id="0238c-109">Si vous changez d'application par défaut, vous pouvez si vous le souhaitez supprimer l'ancienne application par défaut.</span><span class="sxs-lookup"><span data-stu-id="0238c-109">If you change the default application, you can then delete the application that was previously the default, if you want.</span></span> <span data-ttu-id="0238c-110">Pour obtenir des instructions, consultez [comment supprimer une Application BizTalk du groupe BizTalk](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span><span class="sxs-lookup"><span data-stu-id="0238c-110">For instructions, see [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span></span>  
  
 <span data-ttu-id="0238c-111">Si vous changez d'application par défaut, tous les artefacts sont conservés dans l'application par défaut initiale.</span><span class="sxs-lookup"><span data-stu-id="0238c-111">When you change the default application, all of the artifacts remain in the application that was originally the default.</span></span> <span data-ttu-id="0238c-112">Si vous le désirez, vous pouvez explicitement les en extraire.</span><span class="sxs-lookup"><span data-stu-id="0238c-112">You can explicitly move the artifacts out of the application, if you want.</span></span> <span data-ttu-id="0238c-113">Pour obtenir des instructions, consultez [comment déplacer un artefact vers une autre Application](../core/how-to-move-an-artifact-to-a-different-application.md).</span><span class="sxs-lookup"><span data-stu-id="0238c-113">For instructions, see [How to Move an Artifact to a Different Application](../core/how-to-move-an-artifact-to-a-different-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0238c-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0238c-114">Prerequisites</span></span>  
 <span data-ttu-id="0238c-115">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0238c-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="0238c-116">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="0238c-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-change-the-default-application"></a><span data-ttu-id="0238c-117">Modification de l'application par défaut</span><span class="sxs-lookup"><span data-stu-id="0238c-117">To change the default application</span></span>  
  
1.  <span data-ttu-id="0238c-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0238c-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0238c-119">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur l’application que vous souhaitez rendre la valeur par défaut, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0238c-119">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, right-click the application that you want to make the default, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0238c-120">Sélectionnez le **transformer en application par défaut** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0238c-120">Select the **Make this the default application** check box, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0238c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0238c-121">See Also</span></span>  
 [<span data-ttu-id="0238c-122">Création et modification des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="0238c-122">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)