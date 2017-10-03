---
title: "Comment supprimer un schéma à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, schemas
- applications, schemas
- schemas, deleting
- managing [schemas], deleting
- managing [schemas], applications
- schemas, applications
ms.assetid: 17dd5869-b56c-4166-9f02-03e04e691eda
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6535764af00156325c006388a88803207329e5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-schema-from-an-application"></a><span data-ttu-id="169d8-102">Suppression d'un schéma d'une application</span><span class="sxs-lookup"><span data-stu-id="169d8-102">How to Remove a Schema from an Application</span></span>
<span data-ttu-id="169d8-103">Cette rubrique décrit comment supprimer un schéma dans une application à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="169d8-103">This topic describes how to use the BizTalk Server Administration console to remove a schema from an application.</span></span> <span data-ttu-id="169d8-104">Cette procédure supprime également le schéma de la base de données de gestion BizTalk du groupe.</span><span class="sxs-lookup"><span data-stu-id="169d8-104">This procedure removes the schema from the BizTalk Management database for the group as well.</span></span> <span data-ttu-id="169d8-105">Il peut être utile de supprimer un schéma après avoir déployé une nouvelle version du schéma.</span><span class="sxs-lookup"><span data-stu-id="169d8-105">You might want to remove a schema after deploying a new version of the schema.</span></span> <span data-ttu-id="169d8-106">Pour plus d’informations et des considérations importantes pour la mise à jour des artefacts de l’application, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="169d8-106">For more information and important considerations for updating application artifacts, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="169d8-107">Lorsque vous supprimez un schéma et une version précédente du schéma ayant le même espace de noms racine dans l'application, la version précédente devient active.</span><span class="sxs-lookup"><span data-stu-id="169d8-107">When you remove a schema, and a previous version of the schema having the same root namespace exists in the application, the previous version will become active.</span></span>  
  
 <span data-ttu-id="169d8-108">Lorsque vous supprimez un schéma, voici ce qui se produit :</span><span class="sxs-lookup"><span data-stu-id="169d8-108">When you remove a schema, the following occurs:</span></span>  
  
-   <span data-ttu-id="169d8-109">Le schéma est supprimé de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="169d8-109">The schema is deleted from the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="169d8-110">L'assembly BizTalk qui contient le schéma est supprimé de la base de données de gestion BizTalk, mais pas du système de fichiers local ou du Global Assembly Cache (GAC), s'il existe dans ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="169d8-110">The BizTalk assembly that contains the schema is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
-   <span data-ttu-id="169d8-111">par conséquent, tous les artefacts contenus dans l'assembly sont également supprimés de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="169d8-111">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are removed deleted the BizTalk Management database as well.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="169d8-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="169d8-112">Prerequisites</span></span>  
 <span data-ttu-id="169d8-113">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="169d8-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="169d8-114">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="169d8-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-schema"></a><span data-ttu-id="169d8-115">Pour supprimer un schéma</span><span class="sxs-lookup"><span data-stu-id="169d8-115">To remove a schema</span></span>  
  
1.  <span data-ttu-id="169d8-116">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="169d8-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="169d8-117">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le schéma à supprimer, puis l’application contenant le schéma.</span><span class="sxs-lookup"><span data-stu-id="169d8-117">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema to remove and the application containing the schema.</span></span>  
  
3.  <span data-ttu-id="169d8-118">Cliquez sur **schémas**, cliquez sur le schéma, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="169d8-118">Click **Schemas**, right-click the schema, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169d8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="169d8-119">See Also</span></span>  
 [<span data-ttu-id="169d8-120">Gestion des schémas</span><span class="sxs-lookup"><span data-stu-id="169d8-120">Managing Schemas</span></span>](../core/managing-schemas.md)