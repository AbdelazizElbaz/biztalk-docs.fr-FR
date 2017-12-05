---
title: "Comment désactiver un mappage utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, maps
- managing [SSO maps], disabling
- maps [SSO], disabling
ms.assetid: 9b6eaff2-674b-49f7-8d5c-3e040a7dc7f8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b17ab68356d5d39f3f839f736261d4a7ef79c78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-a-user-mapping"></a><span data-ttu-id="6e93f-102">Comment désactiver un mappage utilisateur</span><span class="sxs-lookup"><span data-stu-id="6e93f-102">How to Disable a User Mapping</span></span>
<span data-ttu-id="6e93f-103">Vous pouvez désactiver un mappage utilisateur pour désactiver les opérations qui lui sont associées.</span><span class="sxs-lookup"><span data-stu-id="6e93f-103">You can disable a user mapping when you want to turn off all operations associated with a given mapping.</span></span> <span data-ttu-id="6e93f-104">Vous devez désactiver un mappage utilisateur avant de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="6e93f-104">You must disable a user mapping before you can remove it.</span></span>  
  
 <span data-ttu-id="6e93f-105">Lorsque vous désactivez un mappage utilisateur, il apparaît comme (D)  *\<domaine\>\\< nom d’utilisateur\>*  lorsque vous répertoriez les mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6e93f-105">When you disable a user mapping, it will appear as (D) *\<domain\>\\<username\>* when you list the user mappings.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a><span data-ttu-id="6e93f-106">Pour désactiver un mappage utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="6e93f-106">To disable a user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="6e93f-107">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-107">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="6e93f-108">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6e93f-108">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6e93f-109">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6e93f-109">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="6e93f-110">Type  **ssomanage-disablemapping  *\<domaine\>*\\*\<nom d’utilisateur\> \<application nom\>***, où  *\<domaine\>*  correspond au domaine Windows pour le compte d’utilisateur, et  *\<nom d’utilisateur\>*  est le nom d’utilisateur Windows pour lequel vous souhaitez désactiver les informations d’identification, et  *\<nom de l’application\>*  est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6e93f-110">Type **ssomanage –disablemapping *\<domain\>*\\*\<username\> \<application name\>***, where *\<domain\>* is the Windows domain for the user account, and *\<username\>* is the Windows user name for which you want to disable the credentials, and *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e93f-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6e93f-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="6e93f-112">Pour désactiver un mappage utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="6e93f-112">To disable a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="6e93f-113">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-113">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="6e93f-114">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6e93f-114">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6e93f-115">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6e93f-115">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="6e93f-116">Type **ssoclient – disablemapping  *\<nom de l’application\>***, où  *\<nom de l’application\>*  est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6e93f-116">Type **ssoclient –disablemapping *\<application name\>***, where *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e93f-117">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6e93f-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e93f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e93f-118">See Also</span></span>  
 <span data-ttu-id="6e93f-119">[Mappages SSO](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="6e93f-119">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="6e93f-120">[Gestion des Applications associées](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6e93f-120">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="6e93f-121">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="6e93f-121">Managing User Mappings</span></span>](../core/managing-user-mappings.md)