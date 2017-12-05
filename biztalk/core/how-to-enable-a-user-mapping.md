---
title: Comment activer un mappage utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enabling, user maps [SSO]
- maps [SSO], enabling
- managing [SSO maps], enabling
ms.assetid: 0f6448c9-944e-45f6-9436-87a4f3743498
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfd87d300314616fe05a033360d84f5d2eb8b8cd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-a-user-mapping"></a><span data-ttu-id="0fcd3-102">Comment activer un mappage utilisateur</span><span class="sxs-lookup"><span data-stu-id="0fcd3-102">How to Enable a User Mapping</span></span>
<span data-ttu-id="0fcd3-103">Vous devez activer un mappage utilisateur avant d'utiliser le mappage dans le système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-103">You must enable a user mapping before it you can use the mapping in the Single Sign-On system.</span></span>  
  
 <span data-ttu-id="0fcd3-104">Lorsque vous activez un mappage utilisateur, il apparaît sous la forme (E)  **\<domaine\>\\< nom d’utilisateur\>**  lorsque vous répertoriez les mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-104">When you enable a user mapping, it will appear as (E) **\<domain\>\\<username\>** when you list the user mappings.</span></span>  
  
 <span data-ttu-id="0fcd3-105">Notez que si vous avez configuré les informations d'identification à l'aide de la commande -setcredentials, le mappage est déjà activé.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-105">Note that if you have set the credentials using the -setcredentials command, the mapping will already be enabled.</span></span>  
  
### <a name="to-enable-a-user-mapping-using-the-administration-utility"></a><span data-ttu-id="0fcd3-106">Pour activer un mappage utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="0fcd3-106">To enable a user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="0fcd3-107">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-107">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="0fcd3-108">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-108">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0fcd3-109">Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-109">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="0fcd3-110">Type **ssomanage-enablemapping \<domaine\>\\< nom d’utilisateur\>\<nom de l’application\>**, où  **\< domaine\>**  correspond au domaine Windows pour le compte d’utilisateur,  **\<nom d’utilisateur\>**  est le nom d’utilisateur Windows pour lequel vous souhaitez activer les informations d’identification et  **\<nom de l’application\>**  est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-110">Type **ssomanage –enablemapping \<domain\>\\<username\>\<application name\>**, where **\<domain\>** is the Windows domain for the user account, **\<username\>** is the Windows user name for which you want to enable the credentials, and **\<application name\>** is the name of the affiliate application you want to remove the user mapping for and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0fcd3-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="0fcd3-112">Pour activer un mappage utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="0fcd3-112">To enable a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="0fcd3-113">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-113">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="0fcd3-114">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-114">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0fcd3-115">Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-115">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="0fcd3-116">Type **ssoclient – enablemapping \<nom de l’application\>**, où  **\<nom de l’application\>**  est le nom de l’application associée Pour supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-116">Type **ssoclient –enablemapping \<application name\>**, where **\<application name\>** is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0fcd3-117">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0fcd3-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcd3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fcd3-118">See Also</span></span>  
 <span data-ttu-id="0fcd3-119">[Comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="0fcd3-119">[How to Create User Mappings](../core/how-to-create-user-mappings.md) </span></span>  
 <span data-ttu-id="0fcd3-120">[Mappages SSO](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="0fcd3-120">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="0fcd3-121">[Gestion des Applications associées](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0fcd3-121">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="0fcd3-122">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="0fcd3-122">Managing User Mappings</span></span>](../core/managing-user-mappings.md)