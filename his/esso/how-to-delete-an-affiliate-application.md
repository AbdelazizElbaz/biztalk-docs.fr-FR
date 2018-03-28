---
title: Comment supprimer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec290d38-0220-4bf2-b596-2d6453e51c8d
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: d0632f7e4217cb9bbccd2ee604688f22eb6de348
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-delete-an-affiliate-application"></a><span data-ttu-id="89635-102">Comment supprimer une Application associée</span><span class="sxs-lookup"><span data-stu-id="89635-102">How to Delete an Affiliate Application</span></span>
<span data-ttu-id="89635-103">Utilisez le composant logiciel enfichable MMC ou la **deleteapps** commande pour supprimer l’application associée spécifiée à partir de la base de données d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="89635-103">Use the MMC Snap-In or the **deleteapps** command to delete the specified affiliate application from the Credential database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89635-104">Lorsque vous supprimez une application associée, le système SSO supprime automatiquement tous les mappages qui y sont associés.</span><span class="sxs-lookup"><span data-stu-id="89635-104">When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89635-105">Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="89635-105">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="89635-106">Pour supprimer une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="89635-106">To delete an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="89635-107">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="89635-107">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="89635-108">Dans le volet d’étendue du composant logiciel enfichable MMC, développez le **Enterprise Single Sign-On** nœud.</span><span class="sxs-lookup"><span data-stu-id="89635-108">In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="89635-109">Cliquez sur l’application associée, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="89635-109">Right-click the affiliate application, and then click **Delete**.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="89635-110">Pour supprimer une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="89635-110">To delete an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="89635-111">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="89635-111">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="89635-112">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="89635-112">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="89635-113">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="89635-113">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="89635-114">Type `ssomanage –deleteapp <application name>`, où  *\<nom de l’application >* est le nom de l’application associée que vous souhaitez supprimer de la base de données d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="89635-114">Type `ssomanage –deleteapp <application name>`, where *\<application name>* is the name of the affiliate application you want to remove from the Credential database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89635-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89635-115">See Also</span></span>  
 <span data-ttu-id="89635-116">[Applications associées SSO](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="89635-116">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="89635-117">[Comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="89635-117">[How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="89635-118">[Gestion des mappages utilisateur](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="89635-118">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="89635-119">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="89635-119">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)